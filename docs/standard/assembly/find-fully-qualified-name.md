---
title: 'Comment : Trouver le nom entièrement qualifié d’une assemblée'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348199"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a>Comment : Trouver le nom entièrement qualifié d’une assemblée

Pour découvrir le nom entièrement qualifié d’une assemblée-cadre .NET dans le cache d’assemblage global, utilisez l’outil Global Assembly Cache ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)). Voir [comment: Voir le contenu de la cache d’assemblage global](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).

Pour les assemblages de base .NET, et pour les assemblages cadres .NET qui ne sont pas dans le cache d’assemblage global, vous pouvez obtenir le nom d’assemblage entièrement qualifié de plusieurs façons:

- Vous pouvez utiliser le code pour produire les informations sur la console ou à une variable, ou vous pouvez utiliser [l’Ildasm.exe (il Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) pour examiner les métadonnées de l’assemblage, qui contient le nom entièrement qualifié.

- Si l'assembly est déjà chargé par l'application, vous pouvez récupérer la valeur de la propriété <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> pour obtenir le nom complet. Vous pouvez <xref:System.Type.Assembly> utiliser la <xref:System.Type> propriété d’un défini dans <xref:System.Reflection.Assembly> cet assemblage pour récupérer une référence à l’objet. Cet exemple en fournit une illustration.

- Si vous connaissez le chemin du système de `static` fichiers de `Shared` l’assemblage, <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> vous pouvez appeler la méthode (C) ou (Visual Basic) pour obtenir le nom d’assemblage entièrement qualifié. Voici un exemple simple.

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

Pour plus d’informations sur le réglage des attributs d’assemblage tels que la version, la culture et le nom de l’assemblage, voir [attributs d’assemblage de set](set-attributes.md). Pour plus d’informations sur donner à un assemblage un nom fort, voir [Créer et utiliser des assemblages nommés fort](create-use-strong-named.md).

## <a name="example"></a> Exemple

L’exemple suivant montre comment afficher le nom entièrement qualifié d’un assemblage contenant une classe spécifiée à la console. Il utilise <xref:System.Type.Assembly?displayProperty=nameWithType> la propriété pour récupérer une référence à un assemblage à partir d’un type qui est défini dans cet assemblage.

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

- [Noms d’assembly](names.md)
- [Créer des assemblys](create.md)
- [Créer et utiliser des assemblys avec nom fort](create-use-strong-named.md)
- [Cache d’assemblage global](../../framework/app-domains/gac.md)
- [Comment le temps d’exécution localise les assemblages](../../framework/deployment/how-the-runtime-locates-assemblies.md)
