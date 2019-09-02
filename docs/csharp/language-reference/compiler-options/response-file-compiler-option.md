---
title: '@ (Options du compilateur C#)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: d8e5c0ec148754c3e4cebfa32ad9f44a0bb0119e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202907"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="c1a9c-102">@ (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="c1a9c-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="c1a9c-103">L’option @ vous permet de spécifier un fichier qui contient les options du compilateur et les fichiers de code source à compiler.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1a9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1a9c-104">Syntax</span></span>  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="c1a9c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c1a9c-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="c1a9c-106">Fichier qui répertorie des options du compilateur ou des fichiers de code source à compiler.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1a9c-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="c1a9c-107">Remarks</span></span>  
 <span data-ttu-id="c1a9c-108">Les options du compilateur et les fichiers de code source seront traités par le compilateur exactement comme s’ils avaient été spécifiés sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="c1a9c-109">Pour spécifier plusieurs fichiers réponse dans une compilation, spécifiez plusieurs options de fichier réponse.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="c1a9c-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="c1a9c-110">For example:</span></span>  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="c1a9c-111">Dans un fichier réponse, plusieurs options du compilateur et fichiers de code source peuvent apparaître sur une même ligne.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="c1a9c-112">En revanche, si vous spécifiez une seule option du compilateur, celle-ci doit obligatoirement figurer sur une seule et même ligne.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="c1a9c-113">Les fichiers réponse peuvent contenir des commentaires, précédés du symbole #.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="c1a9c-114">La spécification d’options du compilateur à partir d’un fichier réponse est identique à la spécification de ces commandes sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="c1a9c-115">Pour plus d’informations, consultez [Génération à partir de la ligne de commande](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="c1a9c-115">See [Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="c1a9c-116">Le compilateur traite les options de commande au fur et à mesure qu’il les rencontre.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="c1a9c-117">Par conséquent, des arguments de ligne de commande peuvent substituer des options précédemment affichées dans des fichiers réponse.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="c1a9c-118">Inversement, les options d’un fichier réponse substituent les options affichées précédemment dans la ligne de commande ou dans d’autres fichiers réponse.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="c1a9c-119">C# fournit le fichier csc.rsp, qui se trouve dans le même répertoire que le fichier csc.exe.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="c1a9c-120">Pour plus d’informations sur csc.rsp, consultez [-noconfig](./noconfig-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c1a9c-120">See [-noconfig](./noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="c1a9c-121">Cette option du compilateur ne peut pas être définie dans l’environnement de développement Visual Studio, ni être modifiée par programmation.</span><span class="sxs-lookup"><span data-stu-id="c1a9c-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1a9c-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="c1a9c-122">Example</span></span>  
 <span data-ttu-id="c1a9c-123">Voici quelques lignes extraites d’un exemple de fichier réponse :</span><span class="sxs-lookup"><span data-stu-id="c1a9c-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1a9c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1a9c-124">See also</span></span>

- [<span data-ttu-id="c1a9c-125">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="c1a9c-125">C# Compiler Options</span></span>](./index.md)
