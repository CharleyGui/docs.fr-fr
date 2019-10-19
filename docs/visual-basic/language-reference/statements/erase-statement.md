---
title: Erase, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 7dec2a859f664ee8dcbb305082ec33aeacbaccb4
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583389"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="c057f-102">Erase, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c057f-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="c057f-103">Utilisé pour libérer des variables de tableau et libérer la mémoire utilisée pour leurs éléments.</span><span class="sxs-lookup"><span data-stu-id="c057f-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c057f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c057f-104">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="c057f-105">Composants</span><span class="sxs-lookup"><span data-stu-id="c057f-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="c057f-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="c057f-106">Required.</span></span> <span data-ttu-id="c057f-107">Liste des variables de tableau à effacer.</span><span class="sxs-lookup"><span data-stu-id="c057f-107">List of array variables to be erased.</span></span> <span data-ttu-id="c057f-108">Les variables multiples sont séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="c057f-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c057f-109">Notes</span><span class="sxs-lookup"><span data-stu-id="c057f-109">Remarks</span></span>  
 <span data-ttu-id="c057f-110">L’instruction `Erase` peut apparaître uniquement au niveau de la procédure.</span><span class="sxs-lookup"><span data-stu-id="c057f-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="c057f-111">Cela signifie que vous pouvez libérer des tableaux à l’intérieur d’une procédure, mais pas au niveau de la classe ou du module.</span><span class="sxs-lookup"><span data-stu-id="c057f-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="c057f-112">L’instruction `Erase` équivaut à assigner des `Nothing` à chaque variable de tableau.</span><span class="sxs-lookup"><span data-stu-id="c057f-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c057f-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="c057f-113">Example</span></span>  
 <span data-ttu-id="c057f-114">L’exemple suivant utilise l’instruction `Erase` pour effacer deux tableaux et libérer leur mémoire (respectivement les éléments de stockage 1000 et 100).</span><span class="sxs-lookup"><span data-stu-id="c057f-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="c057f-115">L’instruction `ReDim` affecte ensuite une nouvelle instance de tableau au tableau à trois dimensions.</span><span class="sxs-lookup"><span data-stu-id="c057f-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="c057f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c057f-116">See also</span></span>

- [<span data-ttu-id="c057f-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="c057f-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="c057f-118">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="c057f-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
