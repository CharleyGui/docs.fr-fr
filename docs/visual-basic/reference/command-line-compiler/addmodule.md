---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2db122acc03056a9cb6f355119d4c4e6da6ed175
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097785"
---
# <a name="-addmodule"></a><span data-ttu-id="2bba2-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="2bba2-102">-addmodule</span></span>

<span data-ttu-id="2bba2-103">Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir du ou des fichiers spécifiés, pour le projet en cours de compilation.</span><span class="sxs-lookup"><span data-stu-id="2bba2-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bba2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bba2-104">Syntax</span></span>  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="2bba2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2bba2-105">Arguments</span></span>  

 `fileList`  
 <span data-ttu-id="2bba2-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2bba2-106">Required.</span></span> <span data-ttu-id="2bba2-107">Liste de fichiers délimités par des virgules qui contiennent des métadonnées, mais qui ne contiennent pas de manifestes d’assembly.</span><span class="sxs-lookup"><span data-stu-id="2bba2-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="2bba2-108">Les noms de fichiers contenant des espaces doivent être placés entre guillemets ("").</span><span class="sxs-lookup"><span data-stu-id="2bba2-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bba2-109">Notes</span><span class="sxs-lookup"><span data-stu-id="2bba2-109">Remarks</span></span>  

 <span data-ttu-id="2bba2-110">Les fichiers listés par le `fileList` paramètre doivent être créés avec l' `-target:module` option, ou avec un autre compilateur équivalent à `-target:module` .</span><span class="sxs-lookup"><span data-stu-id="2bba2-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="2bba2-111">Tous les modules ajoutés avec `-addmodule` doivent se trouver dans le même répertoire que le fichier de sortie au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2bba2-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="2bba2-112">Autrement dit, vous pouvez spécifier un module dans n’importe quel répertoire au moment de la compilation, mais le module doit se trouver dans le répertoire de l’application au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2bba2-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="2bba2-113">Si ce n’est pas le cas, vous recevez une <xref:System.TypeLoadException> erreur.</span><span class="sxs-lookup"><span data-stu-id="2bba2-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="2bba2-114">Si vous spécifiez (implicitement ou explicitement) une option[-target (Visual Basic)](target.md) autre que `-target:module` avec `-addmodule` , les fichiers que vous transmettez pour faire `-addmodule` partie de l’assembly du projet.</span><span class="sxs-lookup"><span data-stu-id="2bba2-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="2bba2-115">Un assembly est requis pour exécuter un fichier de sortie qui a un ou plusieurs fichiers ajoutés avec `-addmodule` .</span><span class="sxs-lookup"><span data-stu-id="2bba2-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="2bba2-116">Utilisez [-Reference (Visual Basic)](reference.md) pour importer les métadonnées d’un fichier qui contient un assembly.</span><span class="sxs-lookup"><span data-stu-id="2bba2-116">Use [-reference (Visual Basic)](reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bba2-117">L' `-addmodule` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2bba2-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bba2-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="2bba2-118">Example</span></span>  

 <span data-ttu-id="2bba2-119">Le code suivant crée un module.</span><span class="sxs-lookup"><span data-stu-id="2bba2-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="2bba2-120">Le code suivant importe les types du module.</span><span class="sxs-lookup"><span data-stu-id="2bba2-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="2bba2-121">Lorsque vous exécutez `t1` , il génère `802` .</span><span class="sxs-lookup"><span data-stu-id="2bba2-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bba2-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bba2-122">See also</span></span>

- [<span data-ttu-id="2bba2-123">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2bba2-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="2bba2-124">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2bba2-124">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="2bba2-125">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2bba2-125">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="2bba2-126">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="2bba2-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
