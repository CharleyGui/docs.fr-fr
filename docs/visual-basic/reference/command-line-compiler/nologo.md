---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 07e1718554b158635b9d8b04958834e804e1fe9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964375"
---
# <a name="-nologo-visual-basic"></a><span data-ttu-id="cc744-102">-nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc744-102">-nologo (Visual Basic)</span></span>
<span data-ttu-id="cc744-103">Supprime l’affichage de la bannière de copyright et des messages d’information pendant la compilation.</span><span class="sxs-lookup"><span data-stu-id="cc744-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc744-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc744-104">Syntax</span></span>  
  
```  
-nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="cc744-105">Notes</span><span class="sxs-lookup"><span data-stu-id="cc744-105">Remarks</span></span>  
 <span data-ttu-id="cc744-106">Si vous spécifiez `-nologo`, le compilateur n’affiche pas de bannière de copyright.</span><span class="sxs-lookup"><span data-stu-id="cc744-106">If you specify `-nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="cc744-107">Par défaut, l'option `-nologo` n'est pas activée.</span><span class="sxs-lookup"><span data-stu-id="cc744-107">By default, `-nologo` is not in effect.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc744-108">L' `-nologo` option n’est pas disponible dans l’environnement de développement Visual Studio; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="cc744-108">The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc744-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="cc744-109">Example</span></span>  
 <span data-ttu-id="cc744-110">Le code suivant compile `T2.vb` et n’affiche pas de bannière de copyright.</span><span class="sxs-lookup"><span data-stu-id="cc744-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc744-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc744-111">See also</span></span>

- [<span data-ttu-id="cc744-112">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc744-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="cc744-113">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="cc744-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
