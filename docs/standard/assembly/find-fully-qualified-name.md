---
title: "How to: Find an assembly's fully qualified name"
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 49ebaeabee7a346fb84f09e5a9e34590d1ea9811
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348199"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a>How to: Find an assembly's fully qualified name

To discover the fully qualified name of a .NET Framework assembly in the global assembly cache, use the Global Assembly Cache tool ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)). See [How to: View the contents of the global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).

For .NET Core assemblies, and for .NET Framework assemblies that aren't in the global assembly cache, you can get the fully qualified assembly name in a number of ways:

- You can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.

- Si l'assembly est déjà chargé par l'application, vous pouvez récupérer la valeur de la propriété <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> pour obtenir le nom complet. You can use the <xref:System.Type.Assembly> property of a <xref:System.Type> defined in that assembly to retrieve a reference to the <xref:System.Reflection.Assembly> object. Cet exemple en fournit une illustration.

- If you know the assembly's file system path, you can call the `static` (C#) or `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name. Voici un exemple simple.

  ```csharp
  using System;
  using System.Reflection;

  public class Example
  {
     public static void Main()
     {
        Console.WriteLine(AssemblyName.GetAssemblyName(@".\UtilityLibrary.dll"));
     }
  }
  // The example displays output like the following:
  //   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

  ```vb
  Imports System.Reflection

  Public Module Example
     Public Sub Main
        Console.WriteLine(AssemblyName.GetAssemblyName(".\UtilityLibrary.dll"))
     End Sub
  End Module
  ' The example displays output like the following:
  '   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

- Vous pouvez utiliser le [Désassembleur IL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) pour examiner les métadonnées de l’assembly, qui contiennent le nom complet.

For more information about setting assembly attributes such as version, culture, and assembly name, see [Set assembly attributes](set-attributes.md). For more information about giving an assembly a strong name, see [Create and use strong-named assemblies](create-use-strong-named.md).

## <a name="example"></a>Exemple

The following example shows how to display the fully qualified name of an assembly containing a specified class to the console. It uses the <xref:System.Type.Assembly?displayProperty=nameWithType> property to retrieve a reference to an assembly from a type that's defined in that assembly.

```cpp
#using <System.dll>
#using <System.Data.dll>

using namespace System;
using namespace System::Reflection;

ref class asmname
{
public:
    static void Main()
    {
        Type^ t = System::Data::DataSet::typeid;
        String^ s = t->Assembly->FullName->ToString();
        Console::WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
};

int main()
{
    asmname::Main();
}
```

```csharp
using System;
using System.Reflection;

class asmname
{
    public static void Main()
    {
        Type t = typeof(System.Data.DataSet);
        string s = t.Assembly.FullName.ToString();
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
}
```

```vb
Imports System.Reflection

Class asmname
    Public Shared Sub Main()
        Dim t As Type = GetType(System.Data.DataSet)
        Dim s As String = t.Assembly.FullName.ToString()
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s)
    End Sub
End Class
```

## <a name="see-also"></a>Voir aussi

- [Assembly names](names.md)
- [Create assemblies](create.md)
- [Create and use strong-named assemblies](create-use-strong-named.md)
- [Global assembly cache](../../framework/app-domains/gac.md)
- [Méthode de localisation des assemblys par le runtime](../../framework/deployment/how-the-runtime-locates-assemblies.md)
