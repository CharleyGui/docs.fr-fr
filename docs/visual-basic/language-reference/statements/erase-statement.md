---
title: Erase, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 6d2052ceccbecd772c4e4bb18052aed74223a36e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343698"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="643e1-102">Erase, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="643e1-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="643e1-103">Used to release array variables and deallocate the memory used for their elements.</span><span class="sxs-lookup"><span data-stu-id="643e1-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="643e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="643e1-104">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="643e1-105">Composants</span><span class="sxs-lookup"><span data-stu-id="643e1-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="643e1-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="643e1-106">Required.</span></span> <span data-ttu-id="643e1-107">List of array variables to be erased.</span><span class="sxs-lookup"><span data-stu-id="643e1-107">List of array variables to be erased.</span></span> <span data-ttu-id="643e1-108">Les variables multiples sont séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="643e1-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="643e1-109">Notes</span><span class="sxs-lookup"><span data-stu-id="643e1-109">Remarks</span></span>  
 <span data-ttu-id="643e1-110">The `Erase` statement can appear only at procedure level.</span><span class="sxs-lookup"><span data-stu-id="643e1-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="643e1-111">This means you can release arrays inside a procedure but not at class or module level.</span><span class="sxs-lookup"><span data-stu-id="643e1-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="643e1-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span><span class="sxs-lookup"><span data-stu-id="643e1-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="643e1-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="643e1-113">Example</span></span>  
 <span data-ttu-id="643e1-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span><span class="sxs-lookup"><span data-stu-id="643e1-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="643e1-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span><span class="sxs-lookup"><span data-stu-id="643e1-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="643e1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="643e1-116">See also</span></span>

- [<span data-ttu-id="643e1-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="643e1-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="643e1-118">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="643e1-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
