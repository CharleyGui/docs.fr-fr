---
title: '@ (spécifier un fichier réponse) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: b84d50334e56305c27c5c0bc54578ba871a28365
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937285"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="e7cfb-102">@ (spécifier un fichier réponse) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7cfb-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="e7cfb-103">Spécifie un fichier qui contient les options du compilateur et les fichiers de code source à compiler.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7cfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7cfb-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7cfb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e7cfb-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="e7cfb-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-106">Required.</span></span> <span data-ttu-id="e7cfb-107">Fichier qui répertorie les options du compilateur ou les fichiers de code source à compiler.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="e7cfb-108">Placez le nom de fichier entre guillemets ("") s’il contient un espace.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7cfb-109">Notes</span><span class="sxs-lookup"><span data-stu-id="e7cfb-109">Remarks</span></span>  
 <span data-ttu-id="e7cfb-110">Le compilateur traite les options du compilateur et les fichiers de code source spécifiés dans un fichier réponse comme s’ils avaient été spécifiés sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="e7cfb-111">Pour spécifier plusieurs fichiers réponse dans une compilation, spécifiez plusieurs options de fichier réponse, comme ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="e7cfb-112">Dans un fichier réponse, plusieurs options de compilateur et fichiers de code source peuvent apparaître sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="e7cfb-113">Une seule spécification d’option de compilateur doit apparaître sur une ligne (ne peut pas s’étendre sur plusieurs lignes).</span><span class="sxs-lookup"><span data-stu-id="e7cfb-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="e7cfb-114">Les fichiers réponse peuvent comporter des commentaires qui commencent `#` par le symbole.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="e7cfb-115">Vous pouvez combiner les options spécifiées sur la ligne de commande avec les options spécifiées dans un ou plusieurs fichiers réponse.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="e7cfb-116">Le compilateur traite les options de commande au fur et à mesure qu’il les rencontre.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="e7cfb-117">Par conséquent, les arguments de ligne de commande peuvent remplacer les options précédemment listées dans les fichiers réponse.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="e7cfb-118">À l’inverse, les options d’un fichier réponse remplacent les options listées précédemment sur la ligne de commande ou dans d’autres fichiers réponse.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="e7cfb-119">Visual Basic fournit le fichier Vbc. rsp, qui se trouve dans le même répertoire que le fichier Vbc. exe.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="e7cfb-120">Le fichier Vbc. rsp est inclus par défaut, sauf `-noconfig` si l’option est utilisée.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="e7cfb-121">Pour plus d’informations, consultez [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="e7cfb-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7cfb-122">L' `@` option n’est pas disponible dans l’environnement de développement Visual Studio; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7cfb-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7cfb-123">Example</span></span>  
 <span data-ttu-id="e7cfb-124">Les lignes suivantes proviennent d’un exemple de fichier réponse.</span><span class="sxs-lookup"><span data-stu-id="e7cfb-124">The following lines are from a sample response file.</span></span>  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="e7cfb-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7cfb-125">Example</span></span>  
 <span data-ttu-id="e7cfb-126">L’exemple suivant montre comment utiliser l' `@` option avec le fichier réponse nommé. `File1.rsp`</span><span class="sxs-lookup"><span data-stu-id="e7cfb-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7cfb-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7cfb-127">See also</span></span>

- [<span data-ttu-id="e7cfb-128">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7cfb-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e7cfb-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="e7cfb-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="e7cfb-130">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="e7cfb-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
