---
title: 'Comment : afficher le contenu d’un assembly'
description: Vous pouvez utiliser le désassembleur IL pour afficher les attributs et les références d’un assembly à d’autres modules et assemblys.
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: be2311c601effbebd519e33b7a5e13d49f44bd05
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687500"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="6193a-103">Comment : afficher le contenu d’un assembly</span><span class="sxs-lookup"><span data-stu-id="6193a-103">How to: View assembly contents</span></span>

<span data-ttu-id="6193a-104">Vous pouvez utiliser [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) pour visualiser les informations de langage MSIL (Microsoft Intermediate Language) dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="6193a-104">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="6193a-105">Si le fichier examiné est un assembly, ces informations peuvent inclure les attributs et les références de l’assembly à d’autres modules et assemblys.</span><span class="sxs-lookup"><span data-stu-id="6193a-105">If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies.</span></span> <span data-ttu-id="6193a-106">Ces informations peuvent être utiles pour déterminer si un fichier est un assembly ou une partie d’un assembly et si le fichier a des références à d’autres modules ou assemblys.</span><span class="sxs-lookup"><span data-stu-id="6193a-106">This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.</span></span>

<span data-ttu-id="6193a-107">Pour afficher le contenu d’un assembly à l’aide de *Ildasm.exe* , entrez **Ildasm \<assembly name>** à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="6193a-107">To display the contents of an assembly using *Ildasm.exe* , enter **ildasm \<assembly name>** at a command prompt.</span></span> <span data-ttu-id="6193a-108">Par exemple, la commande suivante désassemble l’assembly *Hello.exe* .</span><span class="sxs-lookup"><span data-stu-id="6193a-108">For example, the following command disassembles the *Hello.exe* assembly.</span></span>

```cmd
ildasm Hello.exe
```

<span data-ttu-id="6193a-109">Pour afficher les informations de manifeste d’assembly, double-cliquez sur l’icône de **manifeste** dans la fenêtre du désassembleur MSIL.</span><span class="sxs-lookup"><span data-stu-id="6193a-109">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>

## <a name="example"></a><span data-ttu-id="6193a-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="6193a-110">Example</span></span>

<span data-ttu-id="6193a-111">L’exemple suivant démarre avec un programme « Hello World » de base.</span><span class="sxs-lookup"><span data-stu-id="6193a-111">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="6193a-112">Après avoir compilé le programme, utilisez *Ildasm.exe* pour désassembler l’assembly *Hello.exe* et afficher le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6193a-112">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

<span data-ttu-id="6193a-113">L’exécution de la *ildasm.exe* de commande sur l’assembly *Hello.exe* et le double-clic sur l’icône du **manifeste** dans la fenêtre du désassembleur MSIL génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6193a-113">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

<span data-ttu-id="6193a-114">Le tableau suivant décrit chaque directive dans le manifeste de l’assembly de l’assembly *Hello.exe* utilisé dans l’exemple :</span><span class="sxs-lookup"><span data-stu-id="6193a-114">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:</span></span>

|<span data-ttu-id="6193a-115">Directive</span><span class="sxs-lookup"><span data-stu-id="6193a-115">Directive</span></span>|<span data-ttu-id="6193a-116">Description</span><span class="sxs-lookup"><span data-stu-id="6193a-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="6193a-117">**. assembly extern \<assembly name>**</span><span class="sxs-lookup"><span data-stu-id="6193a-117">**.assembly extern \<assembly name>**</span></span>|<span data-ttu-id="6193a-118">Spécifie un autre assembly qui contient des éléments référencés par le module actuel (dans cet exemple, `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="6193a-118">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|
|<span data-ttu-id="6193a-119">**. PublicKeyToken \<token>**</span><span class="sxs-lookup"><span data-stu-id="6193a-119">**.publickeytoken \<token>**</span></span>|<span data-ttu-id="6193a-120">Spécifie le jeton de la clé réelle de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="6193a-120">Specifies the token of the actual key of the referenced assembly.</span></span>|
|<span data-ttu-id="6193a-121">**. ver \<version number>**</span><span class="sxs-lookup"><span data-stu-id="6193a-121">**.ver \<version number>**</span></span>|<span data-ttu-id="6193a-122">Spécifie le numéro de version de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="6193a-122">Specifies the version number of the referenced assembly.</span></span>|
|<span data-ttu-id="6193a-123">**. assembly \<assembly name>**</span><span class="sxs-lookup"><span data-stu-id="6193a-123">**.assembly \<assembly name>**</span></span>|<span data-ttu-id="6193a-124">Spécifie le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6193a-124">Specifies the assembly name.</span></span>|
|<span data-ttu-id="6193a-125">**. algorithme de hachage \<int32 value>**</span><span class="sxs-lookup"><span data-stu-id="6193a-125">**.hash algorithm \<int32 value>**</span></span>|<span data-ttu-id="6193a-126">Spécifie l’algorithme de hachage utilisé.</span><span class="sxs-lookup"><span data-stu-id="6193a-126">Specifies the hash algorithm used.</span></span>|
|<span data-ttu-id="6193a-127">**. ver \<version number>**</span><span class="sxs-lookup"><span data-stu-id="6193a-127">**.ver \<version number>**</span></span>|<span data-ttu-id="6193a-128">Spécifie le numéro de version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6193a-128">Specifies the version number of the assembly.</span></span>|
|<span data-ttu-id="6193a-129">**. module \<file name>**</span><span class="sxs-lookup"><span data-stu-id="6193a-129">**.module \<file name>**</span></span>|<span data-ttu-id="6193a-130">Spécifie le nom des modules qui composent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6193a-130">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="6193a-131">Dans cet exemple, l’assembly se compose d’un seul fichier.</span><span class="sxs-lookup"><span data-stu-id="6193a-131">In this example, the assembly consists of only one file.</span></span>|
|<span data-ttu-id="6193a-132">**. sous-système \<value>**</span><span class="sxs-lookup"><span data-stu-id="6193a-132">**.subsystem \<value>**</span></span>|<span data-ttu-id="6193a-133">Spécifie l’environnement d’application nécessaire pour le programme.</span><span class="sxs-lookup"><span data-stu-id="6193a-133">Specifies the application environment required for the program.</span></span> <span data-ttu-id="6193a-134">Dans cet exemple, la valeur 3 indique que cet exécutable est exécuté à partir d’une console.</span><span class="sxs-lookup"><span data-stu-id="6193a-134">In this example, the value 3 indicates that this executable is run from a console.</span></span>|
|<span data-ttu-id="6193a-135">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="6193a-135">**.corflags**</span></span>|<span data-ttu-id="6193a-136">Actuellement un champ réservé dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="6193a-136">Currently a reserved field in the metadata.</span></span>|

<span data-ttu-id="6193a-137">Un manifeste d’assembly peut contenir plusieurs directives différentes, en fonction du contenu de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6193a-137">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="6193a-138">Pour obtenir une liste complète des directives du manifeste de l’assembly, consultez la documentation ECMA, en particulier « Partition II : Metadata Definition and Semantics » et « Partition III : CIL Instruction Set » :</span><span class="sxs-lookup"><span data-stu-id="6193a-138">For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":</span></span>

- [<span data-ttu-id="6193a-139">Normes ECMA C# et Common Language Infrastructure</span><span class="sxs-lookup"><span data-stu-id="6193a-139">ECMA C# and Common Language Infrastructure standards</span></span>](../components.md#applicable-standards)
- [<span data-ttu-id="6193a-140">Standard ECMA-335-Common Language Infrastructure (CLI)</span><span class="sxs-lookup"><span data-stu-id="6193a-140">Standard ECMA-335 - Common Language Infrastructure (CLI)</span></span>](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a><span data-ttu-id="6193a-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6193a-141">See also</span></span>

- [<span data-ttu-id="6193a-142">Domaines d’application et assemblys</span><span class="sxs-lookup"><span data-stu-id="6193a-142">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="6193a-143">Rubriques de procédures relatives aux domaines d’application et aux assemblys</span><span class="sxs-lookup"><span data-stu-id="6193a-143">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="6193a-144">Ildasm.exe (Désassembleur IL)</span><span class="sxs-lookup"><span data-stu-id="6193a-144">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
