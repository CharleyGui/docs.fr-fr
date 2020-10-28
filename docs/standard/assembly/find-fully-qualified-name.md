---
title: 'Comment : Rechercher le nom qualifié complet d’un assembly'
description: Cet article explique comment obtenir le nom complet d’un assembly .NET.
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET], fully qualified type names
- names [.NET], assemblies
- assemblies [.NET], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 223def7d992f5fae64c95aa6886f20980184eddc
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687616"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a>Comment : Rechercher le nom qualifié complet d’un assembly

Pour découvrir le nom qualifié complet d’un assembly de .NET Framework dans le Global Assembly Cache, utilisez l’outil global assembly cache ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)). Consultez [Comment : afficher le contenu du global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).

Pour les assemblys .NET Core, et pour les assemblys .NET Framework qui ne sont pas dans le Global Assembly Cache, vous pouvez obtenir le nom complet de l’assembly de plusieurs façons :

- Vous pouvez utiliser le code pour sortir les informations dans la console ou dans une variable, ou vous pouvez utiliser le [Ildasm.exe (Désassembleur il)](../../framework/tools/ildasm-exe-il-disassembler.md) pour examiner les métadonnées de l’assembly, qui contient le nom complet.

- Si l'assembly est déjà chargé par l'application, vous pouvez récupérer la valeur de la propriété <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> pour obtenir le nom complet. Vous pouvez utiliser la <xref:System.Type.Assembly> propriété d’un <xref:System.Type> défini dans cet assembly pour récupérer une référence à l' <xref:System.Reflection.Assembly> objet. Cet exemple en fournit une illustration.

- Si vous connaissez le chemin d’accès au système de fichiers de l’assembly, vous pouvez appeler la `static` méthode (C#) ou `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> pour obtenir le nom complet de l’assembly. Voici un exemple simple.

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

Pour plus d’informations sur la définition des attributs d’assembly, tels que la version, la culture et le nom de l’assembly, consultez [définir des attributs d’assembly](set-attributes.md). Pour plus d’informations sur l’attribution d’un nom fort à un assembly, consultez [créer et utiliser des assemblys avec nom fort](create-use-strong-named.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment afficher le nom qualifié complet d’un assembly contenant une classe spécifiée dans la console. Elle utilise la <xref:System.Type.Assembly?displayProperty=nameWithType> propriété pour récupérer une référence à un assembly à partir d’un type défini dans cet assembly.

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

- [Noms d’assemblys](names.md)
- [Créer des assemblys](create.md)
- [Créer et utiliser des assemblys avec nom fort](create-use-strong-named.md)
- [Global assembly cache](../../framework/app-domains/gac.md)
- [Comment le runtime localise les assemblys](../../framework/deployment/how-the-runtime-locates-assemblies.md)
