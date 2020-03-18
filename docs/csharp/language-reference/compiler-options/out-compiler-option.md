---
title: -out (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 6c8408c0c613e361dae0c1db19f854e9421ca467
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970379"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="daae8-102">-out (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="daae8-102">-out (C# Compiler Options)</span></span>
<span data-ttu-id="daae8-103">L’option **-out** spécifie le nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="daae8-103">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daae8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="daae8-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="daae8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="daae8-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="daae8-106">Nom du fichier de sortie créé par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="daae8-106">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daae8-107">Notes </span><span class="sxs-lookup"><span data-stu-id="daae8-107">Remarks</span></span>  
 <span data-ttu-id="daae8-108">Sur la ligne de commande, il est possible de spécifier plusieurs fichiers de sortie pour une même compilation.</span><span class="sxs-lookup"><span data-stu-id="daae8-108">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="daae8-109">Le compilateur s’attend à trouver un ou plusieurs fichiers de code source à la suite de l’option **-out**.</span><span class="sxs-lookup"><span data-stu-id="daae8-109">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="daae8-110">Ensuite, tous les fichiers de code source sont compilés dans le fichier de sortie spécifié par cette option **-out**.</span><span class="sxs-lookup"><span data-stu-id="daae8-110">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="daae8-111">Spécifiez le nom complet et l’extension du fichier que vous voulez créer.</span><span class="sxs-lookup"><span data-stu-id="daae8-111">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="daae8-112">Si vous ne spécifiez pas le nom du fichier de sortie :</span><span class="sxs-lookup"><span data-stu-id="daae8-112">If you do not specify the name of the output file:</span></span>  
  
- <span data-ttu-id="daae8-113">Un fichier .exe prend le nom du fichier de code source qui contient la méthode **Main**.</span><span class="sxs-lookup"><span data-stu-id="daae8-113">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
- <span data-ttu-id="daae8-114">Un fichier .dll ou .netmodule prend le nom du premier fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="daae8-114">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="daae8-115">Un fichier de code source ayant servi à compiler un fichier de sortie ne peut pas être utilisé dans une même compilation pour compiler un autre fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="daae8-115">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="daae8-116">Au moment de générer plusieurs fichiers de sortie lors d’une compilation en ligne de commande, gardez à l’esprit que seul un fichier de sortie peut faire office d’assembly et que seul le premier fichier de sortie spécifié (implicitement ou explicitement avec **-out**) peut être l’assembly.</span><span class="sxs-lookup"><span data-stu-id="daae8-116">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="daae8-117">Les modules générés dans le cadre d’une compilation deviennent des fichiers associés à un assembly également généré pendant la compilation.</span><span class="sxs-lookup"><span data-stu-id="daae8-117">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="daae8-118">Utilisez [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) pour afficher le manifeste d’assembly et identifier les fichiers associés.</span><span class="sxs-lookup"><span data-stu-id="daae8-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="daae8-119">L’option de compilateur -out est nécessaire pour faire d’un fichier exe la cible d’un assembly friend.</span><span class="sxs-lookup"><span data-stu-id="daae8-119">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="daae8-120">Pour plus d’informations, consultez [Assemblys friend](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="daae8-120">For more information see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="daae8-121">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="daae8-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="daae8-122">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="daae8-122">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="daae8-123">Cliquez sur la page de propriétés **Application**.</span><span class="sxs-lookup"><span data-stu-id="daae8-123">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="daae8-124">Modifiez la propriété **Nom de l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="daae8-124">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="daae8-125">Pour définir cette option de compilateur par programmation : <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> est une propriété en lecture seule, qui est déterminée par une combinaison du type de projet (exe, bibliothèque, etc.) et le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="daae8-125">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="daae8-126">Il est nécessaire de modifier l’une de ces propriétés (ou les deux) pour définir le nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="daae8-126">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="daae8-127"> Exemple</span><span class="sxs-lookup"><span data-stu-id="daae8-127">Example</span></span>  
 <span data-ttu-id="daae8-128">Compilez `t.cs` et créez le fichier de sortie `t.exe`, puis générez `t2.cs` et créez le fichier de sortie de module `mymodule.netmodule` :</span><span class="sxs-lookup"><span data-stu-id="daae8-128">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="daae8-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daae8-129">See also</span></span>

- [<span data-ttu-id="daae8-130">Options de compilateur C</span><span class="sxs-lookup"><span data-stu-id="daae8-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="daae8-131">Assemblées d’amis</span><span class="sxs-lookup"><span data-stu-id="daae8-131">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
- [<span data-ttu-id="daae8-132">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="daae8-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
