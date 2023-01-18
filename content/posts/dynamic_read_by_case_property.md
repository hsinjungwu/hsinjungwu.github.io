---
title: "動態讀取 By Case 的第三方物件 Public Field "
date: 2023-01-16T20:25:00+08:00
draft: false
dropCap: false
tags:
  - "HowTo"
---

剛來公司時某個舊專案 `BigProject` 因為要對接多個同父異母專案的物件 `ExtObject`，有時需特例處理各專案額外開的 `Public Field`。 😱

### 暴力法

由於有歷史包袱，所以在一開始時是使用 [反射][reflection] 暴力處理。

```cs
public static bool SetFieldValue(string fn, object val, object obj)
{
    try
    {
        Type t = obj.GetType();
        object v = Convert.ChangeType(val,t.GetField(fn).FieldType);
        t.GetField(fn).SetValue(obj, v);
        return true;
    }
    catch
    {
        return false;
    }
}
       
public static T GetFieldValue<T>(string fn, object obj)
{
    try
    {
        Type t = obj.GetType();
        FieldInfo fi = t.GetField(fn);
        return (T)fi.GetValue(obj);
    }
    catch
    {
        return default;
    }
}       
```       

### 溝通後

但後來在對方有機會改版的情況下請對方新增下列函數，我們也相對應使用 `NewBigProject` 套用 `NewExtObject` ，所以未來的新專案都沒事了！🤩

```cs
internal static class PropertyHelper
{
    public static TValue GetValue<TValue>(object prop)
    {
        return (TValue)Convert.ChangeType(prop, typeof(TValue));
    }

    public static void SetValue<TValue>(ref TValue prop, object value)
    {
        prop = (TValue)Convert.ChangeType(value, typeof(TValue));
    }
}

internal class NewExtObject {
    public int iField;
    private Dictionary<string, object> map = new Dictionary<string, object>()
    {
        { "f", iField },
    };
    
    public TValue GetValue<TValue>(string name)
    {
        return PropertyHelper.GetValue<TValue>(map[name]);
    }

    public void SetValue(string name, object iptValue)
    {
        switch (name)
        {
            case "f":
                PropertyHelper.SetValue(ref iField, iptValue);
                break;
        }
    }
}
```

### 靜極思動

而人是懶惰的，由於偶爾還是要處理 `BigProject` 與 `ExtObject`，就想說有沒有辦法讓 `NewBigProject` 與 `ExtObject` 也能溝通。

一開始的想法是要用 `MyObject` 封裝 `ExtObject`。接著再取同名函數，然後內部使用 [反射][reflection] 處理。

```cs
public class MyObject     
{    
    private ExtObject _o;
    
    public MyObject(ExtObject obj)
    {
        _o = obj;
    }
    
    public TValue GetValue<TValue>(string name)
    {
        MethodInfo miGetValue = _o.GetType().GetMethod("GetValue");
        if (miGetValue == null) return default;
        //泛型還需要特別處理
        MethodInfo gGetValue = miGetValue.MakeGenericMethod(typeof(TValue));
        object ro = gGetValue.Invoke(_o, new object[] { name });
        return (TValue)Convert.ChangeType(ro, typeof(TValue));               
    }
}
```

**使用擴充方法**

但最初就是要捨棄 [反射][reflection] 現在又走老路感覺很奇怪。於是想到了可以使用 [擴充方法](https://learn.microsoft.com/zh-tw/dotnet/csharp/programming-guide/classes-and-structs/extension-methods) 而且好處是

> 您可以使用擴充方法來擴充類別或介面，但無法覆寫它們。而且永遠不會呼叫擁有與介面或類別方法相同名稱和簽章的擴充方法。 

```cs
public static TValue GetValue<TValue>(this ExtObject opt, string name)
{
    throw new Exception("dll is too old to support GetValue Method");
}
```

回傳例外的原因是它永遠不該被呼叫。

[reflection]: https://learn.microsoft.com/zh-tw/dotnet/csharp/programming-guide/concepts/reflection
