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
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a><span data-ttu-id="36701-103">Comment : Rechercher le nom qualifié complet d’un assembly</span><span class="sxs-lookup"><span data-stu-id="36701-103">How to: Find an assembly's fully qualified name</span></span>

<span data-ttu-id="36701-104">Pour découvrir le nom qualifié complet d’un assembly de .NET Framework dans le Global Assembly Cache, utilisez l’outil global assembly cache ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="36701-104">To discover the fully qualified name of a .NET Framework assembly in the global assembly cache, use the Global Assembly Cache tool ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="36701-105">Consultez [Comment : afficher le contenu du global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="36701-105">See [How to: View the contents of the global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>

<span data-ttu-id="36701-106">Pour les assemblys .NET Core, et pour les assemblys .NET Framework qui ne sont pas dans le Global Assembly Cache, vous pouvez obtenir le nom complet de l’assembly de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="36701-106">For .NET Core assemblies, and for .NET Framework assemblies that aren't in the global assembly cache, you can get the fully qualified assembly name in a number of ways:</span></span>

- <span data-ttu-id="36701-107">Vous pouvez utiliser le code pour sortir les informations dans la console ou dans une variable, ou vous pouvez utiliser le [Ildasm.exe (Désassembleur il)](../../framework/tools/ildasm-exe-il-disassembler.md) pour examiner les métadonnées de l’assembly, qui contient le nom complet.</span><span class="sxs-lookup"><span data-stu-id="36701-107">You can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

- <span data-ttu-id="36701-108">Si l'assembly est déjà chargé par l'application, vous pouvez récupérer la valeur de la propriété <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> pour obtenir le nom complet.</span><span class="sxs-lookup"><span data-stu-id="36701-108">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="36701-109">Vous pouvez utiliser la <xref:System.Type.Assembly> propriété d’un <xref:System.Type> défini dans cet assembly pour récupérer une référence à l' <xref:System.Reflection.Assembly> objet.</span><span class="sxs-lookup"><span data-stu-id="36701-109">You can use the <xref:System.Type.Assembly> property of a <xref:System.Type> defined in that assembly to retrieve a reference to the <xref:System.Reflection.Assembly> object.</span></span> <span data-ttu-id="36701-110">Cet exemple en fournit une illustration.</span><span class="sxs-lookup"><span data-stu-id="36701-110">The example provides an illustration.</span></span>

- <span data-ttu-id="36701-111">Si vous connaissez le chemin d’accès au système de fichiers de l’assembly, vous pouvez appeler la `static` méthode (C#) ou `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> pour obtenir le nom complet de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="36701-111">If you know the assembly's file system path, you can call the `static` (C#) or `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="36701-112">Voici un exemple simple.</span><span class="sxs-lookup"><span data-stu-id="36701-112">The following is a simple example.</span></span>

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

- <span data-ttu-id="36701-113">Vous pouvez utiliser le [Désassembleur IL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) pour examiner les métadonnées de l’assembly, qui contiennent le nom complet.</span><span class="sxs-lookup"><span data-stu-id="36701-113">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

<span data-ttu-id="36701-114">Pour plus d’informations sur la définition des attributs d’assembly, tels que la version, la culture et le nom de l’assembly, consultez [définir des attributs d’assembly](set-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="36701-114">For more information about setting assembly attributes such as version, culture, and assembly name, see [Set assembly attributes](set-attributes.md).</span></span> <span data-ttu-id="36701-115">Pour plus d’informations sur l’attribution d’un nom fort à un assembly, consultez [créer et utiliser des assemblys avec nom fort](create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="36701-115">For more information about giving an assembly a strong name, see [Create and use strong-named assemblies](create-use-strong-named.md).</span></span>

## <a name="example"></a><span data-ttu-id="36701-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="36701-116">Example</span></span>

<span data-ttu-id="36701-117">L’exemple suivant montre comment afficher le nom qualifié complet d’un assembly contenant une classe spécifiée dans la console.</span><span class="sxs-lookup"><span data-stu-id="36701-117">The following example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="36701-118">Elle utilise la <xref:System.Type.Assembly?displayProperty=nameWithType> propriété pour récupérer une référence à un assembly à partir d’un type défini dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="36701-118">It uses the <xref:System.Type.Assembly?displayProperty=nameWithType> property to retrieve a reference to an assembly from a type that's defined in that assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="36701-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36701-119">See also</span></span>

- [<span data-ttu-id="36701-120">Noms d’assemblys</span><span class="sxs-lookup"><span data-stu-id="36701-120">Assembly names</span></span>](names.md)
- [<span data-ttu-id="36701-121">Créer des assemblys</span><span class="sxs-lookup"><span data-stu-id="36701-121">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="36701-122">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="36701-122">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="36701-123">Global assembly cache</span><span class="sxs-lookup"><span data-stu-id="36701-123">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="36701-124">Comment le runtime localise les assemblys</span><span class="sxs-lookup"><span data-stu-id="36701-124">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
