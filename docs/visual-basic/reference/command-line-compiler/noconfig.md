---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: ca184fa130d62dc118d0de551ac58f3165064029
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964395"
---
# <a name="-noconfig"></a><span data-ttu-id="8d7f8-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="8d7f8-102">-noconfig</span></span>
<span data-ttu-id="8d7f8-103">Spécifie que le compilateur ne doit pas référencer automatiquement les assemblys .NET Framework couramment utilisés `System` ou `Microsoft.VisualBasic` importer les espaces de noms et.</span><span class="sxs-lookup"><span data-stu-id="8d7f8-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d7f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d7f8-104">Syntax</span></span>  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="8d7f8-105">Notes</span><span class="sxs-lookup"><span data-stu-id="8d7f8-105">Remarks</span></span>  
 <span data-ttu-id="8d7f8-106">L' `-noconfig` option indique au compilateur de ne pas compiler avec le fichier Vbc. rsp, qui se trouve dans le même répertoire que le fichier Vbc. exe.</span><span class="sxs-lookup"><span data-stu-id="8d7f8-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="8d7f8-107">Le fichier Vbc. rsp fait référence aux assemblys .NET Framework couramment utilisés et importe `System` les `Microsoft.VisualBasic` espaces de noms et.</span><span class="sxs-lookup"><span data-stu-id="8d7f8-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="8d7f8-108">Le compilateur fait implicitement référence à l’assembly System. `-nostdlib` dll à moins que l’option ne soit spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8d7f8-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="8d7f8-109">L' `-nostdlib` option indique au compilateur de ne pas compiler avec vbc. rsp ou de référencer automatiquement l’assembly System. dll.</span><span class="sxs-lookup"><span data-stu-id="8d7f8-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d7f8-110">Les assemblys mscorlib. dll et Microsoft. VisualBasic. dll sont toujours référencés.</span><span class="sxs-lookup"><span data-stu-id="8d7f8-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="8d7f8-111">Vous pouvez modifier le fichier Vbc. rsp pour spécifier des options de compilateur supplémentaires qui doivent être incluses dans chaque compilation vbc. exe (sauf si `-noconfig` vous spécifiez l’option).</span><span class="sxs-lookup"><span data-stu-id="8d7f8-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="8d7f8-112">Pour plus d’informations, consultez [@ (Spécifier un fichier réponse)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="8d7f8-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="8d7f8-113">Le compilateur traite les options passées à la `vbc` commande en dernier.</span><span class="sxs-lookup"><span data-stu-id="8d7f8-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="8d7f8-114">Par conséquent, toute option sur la ligne de commande remplace le paramètre de la même option dans le fichier Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="8d7f8-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d7f8-115">L' `-noconfig` option n’est pas disponible dans l’environnement de développement Visual Studio; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="8d7f8-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d7f8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d7f8-116">See also</span></span>

- [<span data-ttu-id="8d7f8-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d7f8-117">-nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [<span data-ttu-id="8d7f8-118">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d7f8-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8d7f8-119">@ (spécifier un fichier réponse)</span><span class="sxs-lookup"><span data-stu-id="8d7f8-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [<span data-ttu-id="8d7f8-120">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d7f8-120">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
