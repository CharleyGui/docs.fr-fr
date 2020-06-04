---
title: Erase (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 31aeaf822bc9c1de59a5c5f68406c6521216ae0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404717"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="03bf5-102">Erase, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03bf5-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="03bf5-103">Utilisé pour libérer des variables de tableau et libérer la mémoire utilisée pour leurs éléments.</span><span class="sxs-lookup"><span data-stu-id="03bf5-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03bf5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03bf5-104">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="03bf5-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="03bf5-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="03bf5-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="03bf5-106">Required.</span></span> <span data-ttu-id="03bf5-107">Liste des variables de tableau à effacer.</span><span class="sxs-lookup"><span data-stu-id="03bf5-107">List of array variables to be erased.</span></span> <span data-ttu-id="03bf5-108">Les variables multiples sont séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="03bf5-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03bf5-109">Notes</span><span class="sxs-lookup"><span data-stu-id="03bf5-109">Remarks</span></span>  
 <span data-ttu-id="03bf5-110">L' `Erase` instruction peut apparaître uniquement au niveau de la procédure.</span><span class="sxs-lookup"><span data-stu-id="03bf5-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="03bf5-111">Cela signifie que vous pouvez libérer des tableaux à l’intérieur d’une procédure, mais pas au niveau de la classe ou du module.</span><span class="sxs-lookup"><span data-stu-id="03bf5-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="03bf5-112">L' `Erase` instruction équivaut à assigner `Nothing` à chaque variable de tableau.</span><span class="sxs-lookup"><span data-stu-id="03bf5-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03bf5-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="03bf5-113">Example</span></span>  
 <span data-ttu-id="03bf5-114">L’exemple suivant utilise l' `Erase` instruction pour effacer deux tableaux et libérer leur mémoire (respectivement les éléments de stockage 1000 et 100).</span><span class="sxs-lookup"><span data-stu-id="03bf5-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="03bf5-115">L' `ReDim` instruction assigne ensuite une nouvelle instance de tableau au tableau à trois dimensions.</span><span class="sxs-lookup"><span data-stu-id="03bf5-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="03bf5-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03bf5-116">See also</span></span>

- [<span data-ttu-id="03bf5-117">Résultat</span><span class="sxs-lookup"><span data-stu-id="03bf5-117">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="03bf5-118">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="03bf5-118">ReDim Statement</span></span>](redim-statement.md)
