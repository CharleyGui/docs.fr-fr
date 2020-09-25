---
description: -nowarn (options du compilateur C#)
title: -nowarn (options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 31a7ee5eacb2e7cd6b24c4a2276ce6e07fcc67e1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194022"
---
# <a name="-nowarn-c-compiler-options"></a><span data-ttu-id="a1121-103">-nowarn (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="a1121-103">-nowarn (C# Compiler Options)</span></span>

<span data-ttu-id="a1121-104">L’option **-nowarn** vous permet de désactiver l’affichage d’un ou plusieurs avertissements par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="a1121-104">The **-nowarn** option lets you suppress the compiler from displaying one or more warnings.</span></span> <span data-ttu-id="a1121-105">Séparez les numéros des avertissements par une virgule.</span><span class="sxs-lookup"><span data-stu-id="a1121-105">Separate multiple warning numbers with a comma.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1121-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1121-106">Syntax</span></span>  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a1121-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="a1121-107">Arguments</span></span>  

 <span data-ttu-id="a1121-108">`number1`, `number2`</span><span class="sxs-lookup"><span data-stu-id="a1121-108">`number1`, `number2`</span></span>  
 <span data-ttu-id="a1121-109">Numéro de chaque avertissement que le compilateur ne doit pas afficher.</span><span class="sxs-lookup"><span data-stu-id="a1121-109">Warning number(s) that you want the compiler to suppress.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1121-110">Notes</span><span class="sxs-lookup"><span data-stu-id="a1121-110">Remarks</span></span>  

 <span data-ttu-id="a1121-111">Vous devez spécifier uniquement la partie numérique de l’identificateur d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="a1121-111">You should only specify the numeric part of the warning identifier.</span></span> <span data-ttu-id="a1121-112">Par exemple, si vous souhaitez supprimer l’avertissement CS0028, spécifiez `-nowarn:28`.</span><span class="sxs-lookup"><span data-stu-id="a1121-112">For example, if you want to suppress CS0028, you could specify `-nowarn:28`.</span></span>  
  
 <span data-ttu-id="a1121-113">Le compilateur ignore automatiquement les numéros des avertissements passés à `-nowarn` qui étaient valides dans les versions précédentes, mais qui ont été supprimés dans le compilateur.</span><span class="sxs-lookup"><span data-stu-id="a1121-113">The compiler will silently ignore warning numbers passed to `-nowarn` that were valid in previous releases, but that have been removed from the compiler.</span></span> <span data-ttu-id="a1121-114">Par exemple, l’avertissement CS0679 était valide dans le compilateur dans Visual Studio .NET 2002, mais il a été supprimé depuis cette version.</span><span class="sxs-lookup"><span data-stu-id="a1121-114">For example, CS0679 was valid in the compiler in Visual Studio .NET 2002 but was subsequently removed.</span></span>  
  
 <span data-ttu-id="a1121-115">Les avertissements suivants ne peuvent pas être supprimés avec l’option `-nowarn` :</span><span class="sxs-lookup"><span data-stu-id="a1121-115">The following warnings cannot be suppressed by the `-nowarn` option:</span></span>  
  
- <span data-ttu-id="a1121-116">Avertissement du compilateur (niveau 1) CS2002</span><span class="sxs-lookup"><span data-stu-id="a1121-116">Compiler Warning (level 1) CS2002</span></span>  
  
- <span data-ttu-id="a1121-117">Avertissement du compilateur (niveau 1) CS2023</span><span class="sxs-lookup"><span data-stu-id="a1121-117">Compiler Warning (level 1) CS2023</span></span>  
  
- <span data-ttu-id="a1121-118">Avertissement du compilateur (niveau 1) CS2029</span><span class="sxs-lookup"><span data-stu-id="a1121-118">Compiler Warning (level 1) CS2029</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a1121-119">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1121-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="a1121-120">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="a1121-120">Open the **Properties** page for the project.</span></span> <span data-ttu-id="a1121-121">Pour plus de détails, consultez [Générer, page du Concepteur de projet (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="a1121-121">For details, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="a1121-122">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="a1121-122">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="a1121-123">Modifiez la propriété **Supprimer les avertissements**.</span><span class="sxs-lookup"><span data-stu-id="a1121-123">Modify the **Suppress Warnings** property.</span></span>  
  
 <span data-ttu-id="a1121-124">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="a1121-124">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1121-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1121-125">See also</span></span>

- [<span data-ttu-id="a1121-126">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="a1121-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a1121-127">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="a1121-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="a1121-128">Erreurs du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="a1121-128">C# Compiler Errors</span></span>](../compiler-messages/index.md)
