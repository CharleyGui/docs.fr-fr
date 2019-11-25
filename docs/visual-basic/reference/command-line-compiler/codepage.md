---
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: a38fb4be9347b3372b4a459fce2e96b9e38c3a51
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343547"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="d123c-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d123c-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="d123c-103">Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation.</span><span class="sxs-lookup"><span data-stu-id="d123c-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d123c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d123c-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="d123c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d123c-105">Arguments</span></span>  
  
|<span data-ttu-id="d123c-106">Terme</span><span class="sxs-lookup"><span data-stu-id="d123c-106">Term</span></span>|<span data-ttu-id="d123c-107">Définition</span><span class="sxs-lookup"><span data-stu-id="d123c-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="d123c-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="d123c-108">Required.</span></span> <span data-ttu-id="d123c-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span><span class="sxs-lookup"><span data-stu-id="d123c-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d123c-110">Notes</span><span class="sxs-lookup"><span data-stu-id="d123c-110">Remarks</span></span>  
 <span data-ttu-id="d123c-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span><span class="sxs-lookup"><span data-stu-id="d123c-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="d123c-112">The `-codepage` option applies to all source-code files in your compilation.</span><span class="sxs-lookup"><span data-stu-id="d123c-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="d123c-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="d123c-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="d123c-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span><span class="sxs-lookup"><span data-stu-id="d123c-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="d123c-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span><span class="sxs-lookup"><span data-stu-id="d123c-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="d123c-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span><span class="sxs-lookup"><span data-stu-id="d123c-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d123c-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span><span class="sxs-lookup"><span data-stu-id="d123c-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d123c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d123c-118">See also</span></span>

- [<span data-ttu-id="d123c-119">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d123c-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
