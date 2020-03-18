---
title: -target (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: af7bd917f57c8752a2026fbb98aa8b22adc98db7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204514"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="ec19c-102">-target (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="ec19c-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="ec19c-103">**L’option compilateur cible** peut être spécifiée dans l’une des quatre formes :</span><span class="sxs-lookup"><span data-stu-id="ec19c-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="ec19c-104">-cible:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="ec19c-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="ec19c-105">Pour créer un fichier .exe pour windows 8.x Store applications.</span><span class="sxs-lookup"><span data-stu-id="ec19c-105">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="ec19c-106">/target:exe</span><span class="sxs-lookup"><span data-stu-id="ec19c-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="ec19c-107">Pour créer un fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="ec19c-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="ec19c-108">/target:library</span><span class="sxs-lookup"><span data-stu-id="ec19c-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="ec19c-109">Pour créer une bibliothèque de code.</span><span class="sxs-lookup"><span data-stu-id="ec19c-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="ec19c-110">-cible:module</span><span class="sxs-lookup"><span data-stu-id="ec19c-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="ec19c-111">Pour créer un module.</span><span class="sxs-lookup"><span data-stu-id="ec19c-111">To create a module.</span></span>  
  
 [<span data-ttu-id="ec19c-112">/target:winexe</span><span class="sxs-lookup"><span data-stu-id="ec19c-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="ec19c-113">Pour créer un programme Windows.</span><span class="sxs-lookup"><span data-stu-id="ec19c-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="ec19c-114">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="ec19c-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="ec19c-115">Pour créer un fichier .winmdobj intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="ec19c-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="ec19c-116">Sauf si vous spécifiez **-cible:module**, **-cible** provoque un manifeste d’assemblage cadre .NET à placer dans un fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="ec19c-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="ec19c-117">Pour plus d’informations, voir [Assemblées en .NET](../../../standard/assembly/index.md) et [Attributs communs](../../programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="ec19c-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="ec19c-118">Le manifeste de l’assembly est placé dans le premier fichier de sortie .exe dans la compilation ou dans le premier fichier DLL, en l’absence de fichier de sortie .exe.</span><span class="sxs-lookup"><span data-stu-id="ec19c-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="ec19c-119">Par exemple, dans la ligne de commande suivante, le manifeste est placé dans `1.exe` :</span><span class="sxs-lookup"><span data-stu-id="ec19c-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="ec19c-120">Le compilateur crée un seul manifeste d’assembly par compilation.</span><span class="sxs-lookup"><span data-stu-id="ec19c-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="ec19c-121">Les informations sur tous les fichiers d’une compilation sont placées dans le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ec19c-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="ec19c-122">Tous les fichiers de sortie, sauf ceux créés avec **-cible:module** peut contenir un manifeste d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="ec19c-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="ec19c-123">Lorsque vous générez plusieurs fichiers de sortie sur la ligne de commande, un seul manifeste d’assembly peut être créé et il doit aller dans le premier fichier de sortie spécifié sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ec19c-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="ec19c-124">Quel que soit le premier fichier de sortie (**-target:exe**, **-target:winexe**, **-target:library** ou **-target:module**), tous les autres fichiers de sortie générés dans la même compilation doivent être des modules (**-target:module**).</span><span class="sxs-lookup"><span data-stu-id="ec19c-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="ec19c-125">Si vous créez un assembly, vous pouvez indiquer que tout ou partie de votre code est conforme CLS avec l’attribut <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ec19c-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="ec19c-126">Pour plus d’informations sur la définition de cette option de compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec19c-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec19c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec19c-127">See also</span></span>

- [<span data-ttu-id="ec19c-128">Options de compilateur C</span><span class="sxs-lookup"><span data-stu-id="ec19c-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ec19c-129">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="ec19c-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="ec19c-130">-subsystemversion (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="ec19c-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
