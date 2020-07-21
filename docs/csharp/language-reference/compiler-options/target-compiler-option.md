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
ms.openlocfilehash: 80cec001b27000e71b74f380a0f33e30602c01af
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86473907"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="419e9-102">-target (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="419e9-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="419e9-103">L’option du compilateur **-target** peut être spécifiée dans l’une des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="419e9-103">The **-target** compiler option can be specified in one of the following forms:</span></span>  
  
 [<span data-ttu-id="419e9-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="419e9-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="419e9-105">Pour créer un fichier. exe pour les applications du Windows 8. x Store.</span><span class="sxs-lookup"><span data-stu-id="419e9-105">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="419e9-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="419e9-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="419e9-107">Pour créer un fichier .exe.</span><span class="sxs-lookup"><span data-stu-id="419e9-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="419e9-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="419e9-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="419e9-109">Pour créer une bibliothèque de code.</span><span class="sxs-lookup"><span data-stu-id="419e9-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="419e9-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="419e9-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="419e9-111">Pour créer un module.</span><span class="sxs-lookup"><span data-stu-id="419e9-111">To create a module.</span></span>  
  
 [<span data-ttu-id="419e9-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="419e9-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="419e9-113">Pour créer un programme Windows.</span><span class="sxs-lookup"><span data-stu-id="419e9-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="419e9-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="419e9-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="419e9-115">Pour créer un fichier .winmdobj intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="419e9-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="419e9-116">À moins que vous ne spécifiiez **-target : module**, **-target** entraîne le placement d’un manifeste d’assembly .NET Framework dans un fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="419e9-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="419e9-117">Pour plus d’informations, consultez [assemblys dans .net](../../../standard/assembly/index.md) et [attributs communs](../attributes/global.md).</span><span class="sxs-lookup"><span data-stu-id="419e9-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../attributes/global.md).</span></span>  
  
 <span data-ttu-id="419e9-118">Le manifeste de l’assembly est placé dans le premier fichier de sortie .exe dans la compilation ou dans le premier fichier DLL, en l’absence de fichier de sortie .exe.</span><span class="sxs-lookup"><span data-stu-id="419e9-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="419e9-119">Par exemple, dans la ligne de commande suivante, le manifeste est placé dans `1.exe` :</span><span class="sxs-lookup"><span data-stu-id="419e9-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="419e9-120">Le compilateur crée un seul manifeste d’assembly par compilation.</span><span class="sxs-lookup"><span data-stu-id="419e9-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="419e9-121">Les informations sur tous les fichiers d’une compilation sont placées dans le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="419e9-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="419e9-122">Tous les fichiers de sortie sauf ceux créés avec **-target : module** peuvent contenir un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="419e9-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="419e9-123">Lorsque vous générez plusieurs fichiers de sortie sur la ligne de commande, un seul manifeste d’assembly peut être créé et il doit aller dans le premier fichier de sortie spécifié sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="419e9-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="419e9-124">Quel que soit le premier fichier de sortie (**-target:exe**, **-target:winexe**, **-target:library** ou **-target:module**), tous les autres fichiers de sortie générés dans la même compilation doivent être des modules (**-target:module**).</span><span class="sxs-lookup"><span data-stu-id="419e9-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="419e9-125">Si vous créez un assembly, vous pouvez indiquer que tout ou partie de votre code est conforme CLS avec l’attribut <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="419e9-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="419e9-126">Pour plus d’informations sur la définition de cette option de compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="419e9-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="419e9-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="419e9-127">See also</span></span>

- [<span data-ttu-id="419e9-128">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="419e9-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="419e9-129">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="419e9-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="419e9-130">-subsystemversion (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="419e9-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
