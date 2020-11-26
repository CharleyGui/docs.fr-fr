---
description: -optimize (Options du compilateur C#)
title: -optimize (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: 1862794e4d823e38ce19780300a0b04f4e57dc44
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193983"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="51d56-103">-optimize (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="51d56-103">-optimize (C# Compiler Options)</span></span>

<span data-ttu-id="51d56-104">L’option **-optimize** active ou désactive les optimisations effectuées par le compilateur pour réduire la taille de votre fichier de sortie et le rendre plus rapide et plus efficace.</span><span class="sxs-lookup"><span data-stu-id="51d56-104">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51d56-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51d56-105">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="51d56-106">Notes</span><span class="sxs-lookup"><span data-stu-id="51d56-106">Remarks</span></span>  

 <span data-ttu-id="51d56-107">**-optimize** indique aussi au Common Language Runtime d’optimiser le code au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="51d56-107">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="51d56-108">Par défaut, les optimisations sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="51d56-108">By default, optimizations are disabled.</span></span> <span data-ttu-id="51d56-109">Pour activer les optimisations, spécifiez **-optimize+**.</span><span class="sxs-lookup"><span data-stu-id="51d56-109">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="51d56-110">Quand vous créez un module destiné à être utilisé par un assembly, utilisez les mêmes paramètres **-optimize** que ceux de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="51d56-110">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="51d56-111">**-o** est la forme abrégée de **-optimize**.</span><span class="sxs-lookup"><span data-stu-id="51d56-111">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="51d56-112">Il est possible de combiner les options **-optimize** et [-debug](./debug-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="51d56-112">It is possible to combine the **-optimize** and [-debug](./debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="51d56-113">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="51d56-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="51d56-114">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="51d56-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="51d56-115">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="51d56-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="51d56-116">Modifiez la propriété **Optimiser le code**.</span><span class="sxs-lookup"><span data-stu-id="51d56-116">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="51d56-117">Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="51d56-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51d56-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="51d56-118">Example</span></span>  

 <span data-ttu-id="51d56-119">Compilez `t2.cs` et activez les optimisations du compilateur :</span><span class="sxs-lookup"><span data-stu-id="51d56-119">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="51d56-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51d56-120">See also</span></span>

- [<span data-ttu-id="51d56-121">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="51d56-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="51d56-122">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="51d56-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
