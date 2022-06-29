## Runtime'da Dinamik Instance Oluşturmak

```csharp
public object GetInstance(string strNamesapace)
{         
     Type t = Type.GetType(strNamesapace); 
     return  Activator.CreateInstance(t);         
}
```
Yukarıda ki kod basit olarak nesnenin namespace ini alarak nesne alıyor. Tam olarak full qualified name (mesela Vehicle.Car) ise `Type.GetType` null olacaktır. Bunun için aşağıdaki kodu kullanabiliriz.

```csharp
public object GetInstance(string strFullyQualifiedName)
{
     Type type = Type.GetType(strFullyQualifiedName);
     if (type != null)
         return Activator.CreateInstance(type);
     foreach (var asm in AppDomain.CurrentDomain.GetAssemblies())
     {
         type = asm.GetType(strFullyQualifiedName);
         if (type != null)
             return Activator.CreateInstance(type);
     }
     return null;
 }
```

Son olarak bu metodu aşağıdaki gibi kullanabiliriz.

```csharp
object objClassInstance = GetInstance("Vehicles.Car");

```