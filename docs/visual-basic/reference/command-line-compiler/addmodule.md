---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: dd98b45d75ff421dc81666ed47695132a49bfa3a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524481"
---
# <a name="-addmodule"></a><span data-ttu-id="18a55-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="18a55-102">-addmodule</span></span>
<span data-ttu-id="18a55-103">Entraîne la mise à disposition par le compilateur de toutes les informations de type à partir du ou des fichiers spécifiés, pour le projet en cours de compilation.</span><span class="sxs-lookup"><span data-stu-id="18a55-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18a55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18a55-104">Syntax</span></span>  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="18a55-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="18a55-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="18a55-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="18a55-106">Required.</span></span> <span data-ttu-id="18a55-107">Liste de fichiers délimités par des virgules qui contiennent des métadonnées, mais qui ne contiennent pas de manifestes d’assembly.</span><span class="sxs-lookup"><span data-stu-id="18a55-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="18a55-108">Les noms de fichiers contenant des espaces doivent être placés entre guillemets ("").</span><span class="sxs-lookup"><span data-stu-id="18a55-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18a55-109">Notes</span><span class="sxs-lookup"><span data-stu-id="18a55-109">Remarks</span></span>  
 <span data-ttu-id="18a55-110">Les fichiers figurant dans le paramètre `fileList` doivent être créés avec l’option `-target:module`, ou avec un autre compilateur équivalent à `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="18a55-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="18a55-111">Tous les modules ajoutés avec `-addmodule` doivent se trouver dans le même répertoire que le fichier de sortie au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="18a55-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="18a55-112">Autrement dit, vous pouvez spécifier un module dans n’importe quel répertoire au moment de la compilation, mais le module doit se trouver dans le répertoire de l’application au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="18a55-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="18a55-113">Si ce n’est pas le cas, vous recevez une erreur de <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="18a55-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="18a55-114">Si vous spécifiez (implicitement ou explicitement) une option[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) autre que `-target:module` avec `-addmodule`, les fichiers que vous transmettez à `-addmodule` feront partie de l’assembly du projet.</span><span class="sxs-lookup"><span data-stu-id="18a55-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="18a55-115">Un assembly est requis pour exécuter un fichier de sortie qui a un ou plusieurs fichiers ajoutés avec `-addmodule`.</span><span class="sxs-lookup"><span data-stu-id="18a55-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="18a55-116">Utilisez [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) pour importer les métadonnées d’un fichier qui contient un assembly.</span><span class="sxs-lookup"><span data-stu-id="18a55-116">Use [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18a55-117">L’option `-addmodule` n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="18a55-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18a55-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="18a55-118">Example</span></span>  
 <span data-ttu-id="18a55-119">Le code suivant crée un module.</span><span class="sxs-lookup"><span data-stu-id="18a55-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="18a55-120">Le code suivant importe les types du module.</span><span class="sxs-lookup"><span data-stu-id="18a55-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="18a55-121">Lorsque vous exécutez `t1`, il génère `802`.</span><span class="sxs-lookup"><span data-stu-id="18a55-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a55-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18a55-122">See also</span></span>

- [<span data-ttu-id="18a55-123">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18a55-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="18a55-124">-cible (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18a55-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="18a55-125">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18a55-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="18a55-126">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="18a55-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
