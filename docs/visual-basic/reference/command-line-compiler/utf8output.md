---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: adcb518cbe8397549c3ae3b3a8ca9f0ecf9dc38e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004668"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="7299a-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7299a-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="7299a-103">Affiche les résultats de la compilation au format d'encodage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7299a-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7299a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7299a-104">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7299a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7299a-105">Arguments</span></span>  
 <span data-ttu-id="7299a-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="7299a-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="7299a-107">facultatif.</span><span class="sxs-lookup"><span data-stu-id="7299a-107">Optional.</span></span> <span data-ttu-id="7299a-108">La valeur par défaut de cette option est `-utf8output-`, ce qui signifie que la sortie du compilateur n’utilise pas l’encodage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7299a-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="7299a-109">Les options `-utf8output` et `-utf8output+` sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="7299a-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7299a-110">Notes</span><span class="sxs-lookup"><span data-stu-id="7299a-110">Remarks</span></span>  
 <span data-ttu-id="7299a-111">Dans certaines configurations internationales, la sortie du compilateur ne peut pas s’afficher correctement dans la console.</span><span class="sxs-lookup"><span data-stu-id="7299a-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="7299a-112">Dans ce cas, utilisez `-utf8output` et redirigez la sortie du compilateur vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="7299a-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7299a-113">L’option `-utf8output` n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="7299a-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7299a-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="7299a-114">Example</span></span>  
 <span data-ttu-id="7299a-115">Le code suivant compile `In.vb` et indique au compilateur d’afficher la sortie à l’aide de l’encodage UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7299a-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7299a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7299a-116">See also</span></span>

- [<span data-ttu-id="7299a-117">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7299a-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7299a-118">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="7299a-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
