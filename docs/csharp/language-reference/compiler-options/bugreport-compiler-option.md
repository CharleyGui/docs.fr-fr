---
description: -bugreport (Options du compilateur C#)
title: -bugreport (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 2c358b2dda400f6077ffb5ba1dfc8e6e1127fa52
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125993"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="ccbb2-103">-bugreport (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="ccbb2-103">-bugreport (C# Compiler Options)</span></span>
<span data-ttu-id="ccbb2-104">Spécifie que les informations de débogage doivent être placées dans un fichier pour une future analyse.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-104">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccbb2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccbb2-105">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ccbb2-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="ccbb2-106">Arguments</span></span>  
 `file`  
 <span data-ttu-id="ccbb2-107">Nom du fichier qui doit contenir votre rapport de bogues.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-107">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccbb2-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="ccbb2-108">Remarks</span></span>  
 <span data-ttu-id="ccbb2-109">L’option **-bugreport** spécifie que les informations suivantes doivent être placées dans `file` :</span><span class="sxs-lookup"><span data-stu-id="ccbb2-109">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="ccbb2-110">Une copie de tous les fichiers de code source de la compilation.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-110">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="ccbb2-111">Une liste des options du compilateur utilisées dans la compilation.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-111">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="ccbb2-112">Les informations de version concernant votre compilateur, votre runtime et votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-112">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="ccbb2-113">Les assemblys et modules référencés, enregistrés sous la forme de chiffres hexadécimaux, sauf les assemblys qui sont fournis avec le .NET Framework et le SDK.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-113">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that ship with the .NET Framework and SDK.</span></span>  
  
- <span data-ttu-id="ccbb2-114">Les résultats de la compilation, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-114">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="ccbb2-115">Une description du problème, qui vous sera demandée.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-115">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="ccbb2-116">Une description de vos suggestions de résolution du problème, qui vous sera demandée.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-116">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="ccbb2-117">Si cette option est utilisée avec **-errorreport:prompt** ou **-errorreport:send**, les informations figurant dans le fichier seront envoyées à Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-117">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="ccbb2-118">Étant donné qu’une copie de tous les fichiers de code source sera placée dans `file`, vous souhaiterez peut-être reproduire l’erreur de code suspecte dans le programme le plus court possible.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-118">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="ccbb2-119">Cette option de compilateur n’est pas disponible dans Visual Studio et ne peut pas être changée par programmation.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-119">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="ccbb2-120">Notez que le contenu du fichier généré expose le code source, ce qui pourrait entraîner une divulgation d’informations non voulue.</span><span class="sxs-lookup"><span data-stu-id="ccbb2-120">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccbb2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccbb2-121">See also</span></span>

- [<span data-ttu-id="ccbb2-122">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="ccbb2-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ccbb2-123">-errorReport (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="ccbb2-123">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="ccbb2-124">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="ccbb2-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
