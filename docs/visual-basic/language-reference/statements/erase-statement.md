---
title: Erase (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 33d88b5ce71ceab8d4b4b59d356c53a804c360be
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873293"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="8ff5c-102">Erase, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ff5c-102">Erase Statement (Visual Basic)</span></span>

<span data-ttu-id="8ff5c-103">Utilisé pour libérer des variables de tableau et libérer la mémoire utilisée pour leurs éléments.</span><span class="sxs-lookup"><span data-stu-id="8ff5c-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff5c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ff5c-104">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="8ff5c-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="8ff5c-105">Parts</span></span>  

 `arraylist`  
 <span data-ttu-id="8ff5c-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8ff5c-106">Required.</span></span> <span data-ttu-id="8ff5c-107">Liste des variables de tableau à effacer.</span><span class="sxs-lookup"><span data-stu-id="8ff5c-107">List of array variables to be erased.</span></span> <span data-ttu-id="8ff5c-108">Les variables multiples sont séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="8ff5c-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ff5c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="8ff5c-109">Remarks</span></span>  

 <span data-ttu-id="8ff5c-110">L' `Erase` instruction peut apparaître uniquement au niveau de la procédure.</span><span class="sxs-lookup"><span data-stu-id="8ff5c-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="8ff5c-111">Cela signifie que vous pouvez libérer des tableaux à l’intérieur d’une procédure, mais pas au niveau de la classe ou du module.</span><span class="sxs-lookup"><span data-stu-id="8ff5c-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="8ff5c-112">L' `Erase` instruction équivaut à assigner `Nothing` à chaque variable de tableau.</span><span class="sxs-lookup"><span data-stu-id="8ff5c-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ff5c-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ff5c-113">Example</span></span>  

 <span data-ttu-id="8ff5c-114">L’exemple suivant utilise l' `Erase` instruction pour effacer deux tableaux et libérer leur mémoire (respectivement les éléments de stockage 1000 et 100).</span><span class="sxs-lookup"><span data-stu-id="8ff5c-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="8ff5c-115">L' `ReDim` instruction assigne ensuite une nouvelle instance de tableau au tableau à trois dimensions.</span><span class="sxs-lookup"><span data-stu-id="8ff5c-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="8ff5c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ff5c-116">See also</span></span>

- [<span data-ttu-id="8ff5c-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="8ff5c-117">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="8ff5c-118">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="8ff5c-118">ReDim Statement</span></span>](redim-statement.md)
