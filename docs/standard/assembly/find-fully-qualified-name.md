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
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a><span data-ttu-id="504bf-102">Comment : Trouver le nom entièrement qualifié d’une assemblée</span><span class="sxs-lookup"><span data-stu-id="504bf-102">How to: Find an assembly's fully qualified name</span></span>

<span data-ttu-id="504bf-103">Pour découvrir le nom entièrement qualifié d’une assemblée-cadre .NET dans le cache d’assemblage global, utilisez l’outil Global Assembly Cache ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="504bf-103">To discover the fully qualified name of a .NET Framework assembly in the global assembly cache, use the Global Assembly Cache tool ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="504bf-104">Voir [comment: Voir le contenu de la cache d’assemblage global](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="504bf-104">See [How to: View the contents of the global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>

<span data-ttu-id="504bf-105">Pour les assemblages de base .NET, et pour les assemblages cadres .NET qui ne sont pas dans le cache d’assemblage global, vous pouvez obtenir le nom d’assemblage entièrement qualifié de plusieurs façons:</span><span class="sxs-lookup"><span data-stu-id="504bf-105">For .NET Core assemblies, and for .NET Framework assemblies that aren't in the global assembly cache, you can get the fully qualified assembly name in a number of ways:</span></span>

- <span data-ttu-id="504bf-106">Vous pouvez utiliser le code pour produire les informations sur la console ou à une variable, ou vous pouvez utiliser [l’Ildasm.exe (il Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) pour examiner les métadonnées de l’assemblage, qui contient le nom entièrement qualifié.</span><span class="sxs-lookup"><span data-stu-id="504bf-106">You can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

- <span data-ttu-id="504bf-107">Si l'assembly est déjà chargé par l'application, vous pouvez récupérer la valeur de la propriété <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> pour obtenir le nom complet.</span><span class="sxs-lookup"><span data-stu-id="504bf-107">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="504bf-108">Vous pouvez <xref:System.Type.Assembly> utiliser la <xref:System.Type> propriété d’un défini dans <xref:System.Reflection.Assembly> cet assemblage pour récupérer une référence à l’objet.</span><span class="sxs-lookup"><span data-stu-id="504bf-108">You can use the <xref:System.Type.Assembly> property of a <xref:System.Type> defined in that assembly to retrieve a reference to the <xref:System.Reflection.Assembly> object.</span></span> <span data-ttu-id="504bf-109">Cet exemple en fournit une illustration.</span><span class="sxs-lookup"><span data-stu-id="504bf-109">The example provides an illustration.</span></span>

- <span data-ttu-id="504bf-110">Si vous connaissez le chemin du système de `static` fichiers de `Shared` l’assemblage, <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> vous pouvez appeler la méthode (C) ou (Visual Basic) pour obtenir le nom d’assemblage entièrement qualifié.</span><span class="sxs-lookup"><span data-stu-id="504bf-110">If you know the assembly's file system path, you can call the `static` (C#) or `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="504bf-111">Voici un exemple simple.</span><span class="sxs-lookup"><span data-stu-id="504bf-111">The following is a simple example.</span></span>

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

- <span data-ttu-id="504bf-112">Vous pouvez utiliser le [Désassembleur IL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) pour examiner les métadonnées de l’assembly, qui contiennent le nom complet.</span><span class="sxs-lookup"><span data-stu-id="504bf-112">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

<span data-ttu-id="504bf-113">Pour plus d’informations sur le réglage des attributs d’assemblage tels que la version, la culture et le nom de l’assemblage, voir [attributs d’assemblage de set](set-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="504bf-113">For more information about setting assembly attributes such as version, culture, and assembly name, see [Set assembly attributes](set-attributes.md).</span></span> <span data-ttu-id="504bf-114">Pour plus d’informations sur donner à un assemblage un nom fort, voir [Créer et utiliser des assemblages nommés fort](create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="504bf-114">For more information about giving an assembly a strong name, see [Create and use strong-named assemblies](create-use-strong-named.md).</span></span>

## <a name="example"></a><span data-ttu-id="504bf-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="504bf-115">Example</span></span>

<span data-ttu-id="504bf-116">L’exemple suivant montre comment afficher le nom entièrement qualifié d’un assemblage contenant une classe spécifiée à la console.</span><span class="sxs-lookup"><span data-stu-id="504bf-116">The following example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="504bf-117">Il utilise <xref:System.Type.Assembly?displayProperty=nameWithType> la propriété pour récupérer une référence à un assemblage à partir d’un type qui est défini dans cet assemblage.</span><span class="sxs-lookup"><span data-stu-id="504bf-117">It uses the <xref:System.Type.Assembly?displayProperty=nameWithType> property to retrieve a reference to an assembly from a type that's defined in that assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="504bf-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="504bf-118">See also</span></span>

- [<span data-ttu-id="504bf-119">Noms d’assembly</span><span class="sxs-lookup"><span data-stu-id="504bf-119">Assembly names</span></span>](names.md)
- [<span data-ttu-id="504bf-120">Créer des assemblys</span><span class="sxs-lookup"><span data-stu-id="504bf-120">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="504bf-121">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="504bf-121">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="504bf-122">Cache d’assemblage global</span><span class="sxs-lookup"><span data-stu-id="504bf-122">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="504bf-123">Comment le temps d’exécution localise les assemblages</span><span class="sxs-lookup"><span data-stu-id="504bf-123">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
