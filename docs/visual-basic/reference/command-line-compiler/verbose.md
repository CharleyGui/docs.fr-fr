---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 8c5bc1d2ce331b8fe9461f91d64fbeab5a070b59
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004976"
---
# <a name="-verbose"></a><span data-ttu-id="e7cda-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="e7cda-102">-verbose</span></span>
<span data-ttu-id="e7cda-103">Fait en sorte que le compilateur génère des messages d’État et d’erreur détaillés.</span><span class="sxs-lookup"><span data-stu-id="e7cda-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7cda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7cda-104">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7cda-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e7cda-105">Arguments</span></span>  
 <span data-ttu-id="e7cda-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e7cda-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="e7cda-107">facultatif.</span><span class="sxs-lookup"><span data-stu-id="e7cda-107">Optional.</span></span> <span data-ttu-id="e7cda-108">La spécification de `-verbose` revient à spécifier `-verbose+`, ce qui amène le compilateur à émettre des messages détaillés.</span><span class="sxs-lookup"><span data-stu-id="e7cda-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="e7cda-109">La valeur par défaut de cette option est `-verbose-`.</span><span class="sxs-lookup"><span data-stu-id="e7cda-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7cda-110">Notes</span><span class="sxs-lookup"><span data-stu-id="e7cda-110">Remarks</span></span>  
 <span data-ttu-id="e7cda-111">L’option `-verbose` affiche des informations sur le nombre total d’erreurs émises par le compilateur, signale les assemblys qui sont chargés par un module et affiche les fichiers en cours de compilation.</span><span class="sxs-lookup"><span data-stu-id="e7cda-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7cda-112">L’option `-verbose` n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e7cda-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7cda-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7cda-113">Example</span></span>  
 <span data-ttu-id="e7cda-114">Le code suivant compile `In.vb` et indique au compilateur d’afficher les informations d’État détaillées.</span><span class="sxs-lookup"><span data-stu-id="e7cda-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7cda-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7cda-115">See also</span></span>

- [<span data-ttu-id="e7cda-116">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7cda-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e7cda-117">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="e7cda-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
