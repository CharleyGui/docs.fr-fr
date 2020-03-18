---
title: 'Comment : Afficher le contenu de l’assemblage'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 179b240bb06a319ff71009e14323d5c8f2740e5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187384"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="b3995-102">Comment : Afficher le contenu de l’assemblage</span><span class="sxs-lookup"><span data-stu-id="b3995-102">How to: View assembly contents</span></span>

<span data-ttu-id="b3995-103">Vous pouvez utiliser [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) pour visualiser les informations de langage MSIL (Microsoft Intermediate Language) dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="b3995-103">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="b3995-104">Si le fichier examiné est un assemblage, ces informations peuvent inclure les attributs et les références de l’assemblage à d’autres modules et assemblages.</span><span class="sxs-lookup"><span data-stu-id="b3995-104">If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies.</span></span> <span data-ttu-id="b3995-105">Ces informations peuvent être utiles pour déterminer si un fichier est un assemblage ou une partie d’un assemblage et si le fichier a des références à d’autres modules ou assemblages.</span><span class="sxs-lookup"><span data-stu-id="b3995-105">This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.</span></span>

<span data-ttu-id="b3995-106">Pour afficher le contenu d’un assemblage à l’aide *d’Ildasm.exe*, entrez **le nom d’assemblage ildasm \<>** à une invite de commande.</span><span class="sxs-lookup"><span data-stu-id="b3995-106">To display the contents of an assembly using *Ildasm.exe*, enter **ildasm \<assembly name>** at a command prompt.</span></span> <span data-ttu-id="b3995-107">Par exemple, la commande suivante démonte l’assemblage *Hello.exe.*</span><span class="sxs-lookup"><span data-stu-id="b3995-107">For example, the following command disassembles the *Hello.exe* assembly.</span></span>

```cmd
ildasm Hello.exe
```

<span data-ttu-id="b3995-108">Pour afficher les informations manifestes de l’assemblage, cliquez deux fois sur l’icône **Manifeste** dans la fenêtre du démontage MSIL.</span><span class="sxs-lookup"><span data-stu-id="b3995-108">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>

## <a name="example"></a><span data-ttu-id="b3995-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="b3995-109">Example</span></span>

<span data-ttu-id="b3995-110">L’exemple suivant commence par un programme de base "Hello World".</span><span class="sxs-lookup"><span data-stu-id="b3995-110">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="b3995-111">Après avoir compilé le programme, utilisez *Ildasm.exe* pour démonter l’assemblage *Hello.exe* et voir le manifeste de l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="b3995-111">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>

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

<span data-ttu-id="b3995-112">Exécution de la commande *ildasm.exe* sur *l’assemblage Hello.exe* et double-cliquer sur l’icône **Manifeste** dans la fenêtre de démontage MSIL produit la sortie suivante:</span><span class="sxs-lookup"><span data-stu-id="b3995-112">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>

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

<span data-ttu-id="b3995-113">Le tableau suivant décrit chaque directive dans le manifeste d’assemblage de l’assemblée *Hello.exe* utilisée dans l’exemple :</span><span class="sxs-lookup"><span data-stu-id="b3995-113">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:</span></span>

|<span data-ttu-id="b3995-114">Directive</span><span class="sxs-lookup"><span data-stu-id="b3995-114">Directive</span></span>|<span data-ttu-id="b3995-115">Description</span><span class="sxs-lookup"><span data-stu-id="b3995-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b3995-116">**.assembly nom \<d’assemblée extern>**</span><span class="sxs-lookup"><span data-stu-id="b3995-116">**.assembly extern \<assembly name>**</span></span>|<span data-ttu-id="b3995-117">Spécifie un autre assembly qui contient des éléments référencés par le module actuel (dans cet exemple, `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="b3995-117">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|
|<span data-ttu-id="b3995-118">**>symbolique .publickeytoken \<**</span><span class="sxs-lookup"><span data-stu-id="b3995-118">**.publickeytoken \<token>**</span></span>|<span data-ttu-id="b3995-119">Spécifie le jeton de la clé réelle de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="b3995-119">Specifies the token of the actual key of the referenced assembly.</span></span>|
|<span data-ttu-id="b3995-120">**numéro \<de version .ver>**</span><span class="sxs-lookup"><span data-stu-id="b3995-120">**.ver \<version number>**</span></span>|<span data-ttu-id="b3995-121">Spécifie le numéro de version de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="b3995-121">Specifies the version number of the referenced assembly.</span></span>|
|<span data-ttu-id="b3995-122">**.nom \<de l’assemblée>**</span><span class="sxs-lookup"><span data-stu-id="b3995-122">**.assembly \<assembly name>**</span></span>|<span data-ttu-id="b3995-123">Spécifie le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b3995-123">Specifies the assembly name.</span></span>|
|<span data-ttu-id="b3995-124">**.hash \<algorithme int32 valeur>**</span><span class="sxs-lookup"><span data-stu-id="b3995-124">**.hash algorithm \<int32 value>**</span></span>|<span data-ttu-id="b3995-125">Spécifie l’algorithme de hachage utilisé.</span><span class="sxs-lookup"><span data-stu-id="b3995-125">Specifies the hash algorithm used.</span></span>|
|<span data-ttu-id="b3995-126">**numéro \<de version .ver>**</span><span class="sxs-lookup"><span data-stu-id="b3995-126">**.ver \<version number>**</span></span>|<span data-ttu-id="b3995-127">Spécifie le numéro de version de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b3995-127">Specifies the version number of the assembly.</span></span>|
|<span data-ttu-id="b3995-128">**.module \<nom de fichier>**</span><span class="sxs-lookup"><span data-stu-id="b3995-128">**.module \<file name>**</span></span>|<span data-ttu-id="b3995-129">Spécifie le nom des modules qui composent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b3995-129">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="b3995-130">Dans cet exemple, l’assembly se compose d’un seul fichier.</span><span class="sxs-lookup"><span data-stu-id="b3995-130">In this example, the assembly consists of only one file.</span></span>|
|<span data-ttu-id="b3995-131">**.sous-système \<de valeur>**</span><span class="sxs-lookup"><span data-stu-id="b3995-131">**.subsystem \<value>**</span></span>|<span data-ttu-id="b3995-132">Spécifie l’environnement d’application nécessaire pour le programme.</span><span class="sxs-lookup"><span data-stu-id="b3995-132">Specifies the application environment required for the program.</span></span> <span data-ttu-id="b3995-133">Dans cet exemple, la valeur 3 indique que cet exécutable est exécuté à partir d’une console.</span><span class="sxs-lookup"><span data-stu-id="b3995-133">In this example, the value 3 indicates that this executable is run from a console.</span></span>|
|<span data-ttu-id="b3995-134">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="b3995-134">**.corflags**</span></span>|<span data-ttu-id="b3995-135">Actuellement un champ réservé dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b3995-135">Currently a reserved field in the metadata.</span></span>|

<span data-ttu-id="b3995-136">Un manifeste d’assembly peut contenir plusieurs directives différentes, en fonction du contenu de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b3995-136">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="b3995-137">Pour une longue liste des directives de l’assemblée manifeste, voir la documentation Ecma, en particulier "Partition II: Metadata Definition and Semantics" et "Partition III: CIL Instruction Set":</span><span class="sxs-lookup"><span data-stu-id="b3995-137">For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":</span></span>

- [<span data-ttu-id="b3995-138">ECMA C et Common Language Infrastructure standards</span><span class="sxs-lookup"><span data-stu-id="b3995-138">ECMA C# and Common Language Infrastructure standards</span></span>](../components.md#applicable-standards)
- [<span data-ttu-id="b3995-139">Standard ECMA-335 - Infrastructure linguistique commune (CLI)</span><span class="sxs-lookup"><span data-stu-id="b3995-139">Standard ECMA-335 - Common Language Infrastructure (CLI)</span></span>](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a><span data-ttu-id="b3995-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3995-140">See also</span></span>

- [<span data-ttu-id="b3995-141">Domaines et assemblages d’applications</span><span class="sxs-lookup"><span data-stu-id="b3995-141">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="b3995-142">Domaines d’application et assemblages de sujets de comment vers le haut</span><span class="sxs-lookup"><span data-stu-id="b3995-142">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="b3995-143">Ildasm.exe (désassembleur IL)</span><span class="sxs-lookup"><span data-stu-id="b3995-143">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
