---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 71613af0f1c319801296180d49dbacfedf0ceca4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005251"
---
# <a name="-recurse"></a><span data-ttu-id="3311a-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="3311a-102">-recurse</span></span>
<span data-ttu-id="3311a-103">Compile les fichiers de code source dans tous les répertoires enfants du répertoire spécifié ou du répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="3311a-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3311a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3311a-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="3311a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3311a-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="3311a-106">facultatif.</span><span class="sxs-lookup"><span data-stu-id="3311a-106">Optional.</span></span> <span data-ttu-id="3311a-107">Répertoire dans lequel vous voulez commencer la recherche.</span><span class="sxs-lookup"><span data-stu-id="3311a-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="3311a-108">S’il n’est pas spécifié, la recherche commence dans le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="3311a-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="3311a-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3311a-109">Required.</span></span> <span data-ttu-id="3311a-110">Le ou les fichiers à rechercher.</span><span class="sxs-lookup"><span data-stu-id="3311a-110">The file(s) to search for.</span></span> <span data-ttu-id="3311a-111">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="3311a-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3311a-112">Notes</span><span class="sxs-lookup"><span data-stu-id="3311a-112">Remarks</span></span>  
 <span data-ttu-id="3311a-113">Vous pouvez utiliser des caractères génériques dans un nom de fichier pour compiler tous les fichiers correspondants dans le répertoire du projet sans utiliser `-recurse`.</span><span class="sxs-lookup"><span data-stu-id="3311a-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="3311a-114">Si aucun nom de fichier de sortie n’est spécifié, le compilateur base le nom du fichier de sortie sur le premier fichier d’entrée traité.</span><span class="sxs-lookup"><span data-stu-id="3311a-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="3311a-115">Il s’agit généralement du premier fichier de la liste des fichiers compilés lorsqu’ils sont affichés par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="3311a-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="3311a-116">Pour cette raison, il est préférable de spécifier un fichier de sortie à l’aide de l’option `-out`.</span><span class="sxs-lookup"><span data-stu-id="3311a-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3311a-117">L’option `-recurse` n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="3311a-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3311a-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="3311a-118">Example</span></span>  
 <span data-ttu-id="3311a-119">La commande suivante compile tous les fichiers Visual Basic dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="3311a-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="3311a-120">La commande suivante compile tous les fichiers Visual Basic du répertoire `Test\ABC` et des répertoires situés en dessous de celui-ci, puis génère `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="3311a-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3311a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3311a-121">See also</span></span>

- [<span data-ttu-id="3311a-122">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3311a-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3311a-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3311a-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)
- [<span data-ttu-id="3311a-124">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="3311a-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
