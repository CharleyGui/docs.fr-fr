---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: c5bf988d819a8df8aed99588abbb30e19d14b1ac
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084981"
---
# <a name="-verbose"></a><span data-ttu-id="888fe-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="888fe-102">-verbose</span></span>

<span data-ttu-id="888fe-103">Fait en sorte que le compilateur génère des messages d’État et d’erreur détaillés.</span><span class="sxs-lookup"><span data-stu-id="888fe-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="888fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="888fe-104">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="888fe-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="888fe-105">Arguments</span></span>  

 <span data-ttu-id="888fe-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="888fe-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="888fe-107">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="888fe-107">Optional.</span></span> <span data-ttu-id="888fe-108">La spécification de `-verbose` est identique à la spécification de `-verbose+` , ce qui amène le compilateur à émettre des messages détaillés.</span><span class="sxs-lookup"><span data-stu-id="888fe-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="888fe-109">La valeur par défaut de cette option est `-verbose-` .</span><span class="sxs-lookup"><span data-stu-id="888fe-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="888fe-110">Notes</span><span class="sxs-lookup"><span data-stu-id="888fe-110">Remarks</span></span>  

 <span data-ttu-id="888fe-111">L' `-verbose` option affiche des informations sur le nombre total d’erreurs émises par le compilateur, signale les assemblys qui sont chargés par un module et affiche les fichiers en cours de compilation.</span><span class="sxs-lookup"><span data-stu-id="888fe-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="888fe-112">L' `-verbose` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="888fe-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="888fe-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="888fe-113">Example</span></span>  

 <span data-ttu-id="888fe-114">Le code suivant compile `In.vb` et dirige le compilateur pour afficher les informations d’État détaillées.</span><span class="sxs-lookup"><span data-stu-id="888fe-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="888fe-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="888fe-115">See also</span></span>

- [<span data-ttu-id="888fe-116">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="888fe-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="888fe-117">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="888fe-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
