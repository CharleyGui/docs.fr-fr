---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: d7fc73aa24e3d2e323170f38f0f5d689f9c3abaf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065552"
---
# <a name="-noconfig"></a><span data-ttu-id="29558-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="29558-102">-noconfig</span></span>

<span data-ttu-id="29558-103">Spécifie que le compilateur ne doit pas référencer automatiquement les assemblys .NET Framework couramment utilisés ou importer les `System` `Microsoft.VisualBasic` espaces de noms et.</span><span class="sxs-lookup"><span data-stu-id="29558-103">Specifies that the compiler should not automatically reference the commonly used .NET Framework assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29558-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29558-104">Syntax</span></span>  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="29558-105">Notes</span><span class="sxs-lookup"><span data-stu-id="29558-105">Remarks</span></span>  

 <span data-ttu-id="29558-106">L' `-noconfig` option indique au compilateur de ne pas compiler avec le fichier Vbc. rsp, qui se trouve dans le même répertoire que le fichier Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="29558-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="29558-107">Le fichier Vbc. rsp fait référence aux assemblys .NET Framework couramment utilisés et importe `System` les `Microsoft.VisualBasic` espaces de noms et.</span><span class="sxs-lookup"><span data-stu-id="29558-107">The Vbc.rsp file references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="29558-108">Le compilateur fait implicitement référence à l’assembly System.dll, sauf si l' `-nostdlib` option est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="29558-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="29558-109">L' `-nostdlib` option indique au compilateur de ne pas compiler avec vbc. rsp ou de référencer automatiquement l’assembly de System.dll.</span><span class="sxs-lookup"><span data-stu-id="29558-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29558-110">Les assemblys Mscorlib.dll et Microsoft.VisualBasic.dll sont toujours référencés.</span><span class="sxs-lookup"><span data-stu-id="29558-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="29558-111">Vous pouvez modifier le fichier Vbc. rsp pour spécifier des options de compilateur supplémentaires qui doivent être incluses dans chaque compilation de Vbc.exe (sauf si vous spécifiez l' `-noconfig` option).</span><span class="sxs-lookup"><span data-stu-id="29558-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="29558-112">Pour plus d’informations, consultez [@ (spécifier un fichier réponse)](specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="29558-112">For more information, see [@ (Specify Response File)](specify-response-file.md).</span></span>  
  
 <span data-ttu-id="29558-113">Le compilateur traite les options passées à la `vbc` commande en dernier.</span><span class="sxs-lookup"><span data-stu-id="29558-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="29558-114">Par conséquent, toute option sur la ligne de commande remplace le paramètre de la même option dans le fichier Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="29558-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29558-115">L' `-noconfig` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="29558-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29558-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29558-116">See also</span></span>

- [<span data-ttu-id="29558-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29558-117">-nostdlib (Visual Basic)</span></span>](nostdlib.md)
- [<span data-ttu-id="29558-118">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29558-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="29558-119">@ (spécifier un fichier réponse)</span><span class="sxs-lookup"><span data-stu-id="29558-119">@ (Specify Response File)</span></span>](specify-response-file.md)
- [<span data-ttu-id="29558-120">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29558-120">-reference (Visual Basic)</span></span>](reference.md)
