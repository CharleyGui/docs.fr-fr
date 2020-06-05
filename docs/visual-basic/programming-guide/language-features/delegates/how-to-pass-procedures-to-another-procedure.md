---
title: 'Guide pratique : passer des procédures à une autre procédure'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 36f623068372614ae034a8a7b31bffb7496f98b1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410693"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="2be8a-102">Comment : passer des procédures à une autre procédure en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2be8a-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="2be8a-103">Cet exemple montre comment utiliser des délégués pour passer une procédure à une autre procédure.</span><span class="sxs-lookup"><span data-stu-id="2be8a-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="2be8a-104">Un délégué est un type que vous pouvez utiliser comme tout autre type dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2be8a-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="2be8a-105">L' `AddressOf` opérateur retourne un objet délégué lorsqu’il est appliqué à un nom de procédure.</span><span class="sxs-lookup"><span data-stu-id="2be8a-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="2be8a-106">Cet exemple contient une procédure avec un paramètre délégué qui peut prendre une référence à une autre procédure, obtenue avec l' `AddressOf` opérateur.</span><span class="sxs-lookup"><span data-stu-id="2be8a-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="2be8a-107">Créer le délégué et les procédures de correspondance</span><span class="sxs-lookup"><span data-stu-id="2be8a-107">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="2be8a-108">Créez un délégué nommé `MathOperator` .</span><span class="sxs-lookup"><span data-stu-id="2be8a-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="2be8a-109">Créez une procédure nommée `AddNumbers` avec des paramètres et une valeur de retour qui correspondent à ceux de `MathOperator` , afin que les signatures correspondent.</span><span class="sxs-lookup"><span data-stu-id="2be8a-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. <span data-ttu-id="2be8a-110">Créez une procédure nommée `SubtractNumbers` avec une signature qui correspond à `MathOperator` .</span><span class="sxs-lookup"><span data-stu-id="2be8a-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. <span data-ttu-id="2be8a-111">Créez une procédure nommée `DelegateTest` qui accepte un délégué comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="2be8a-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="2be8a-112">Cette procédure peut accepter une référence à `AddNumbers` ou `SubtractNumbers` , car leurs signatures correspondent à la `MathOperator` signature.</span><span class="sxs-lookup"><span data-stu-id="2be8a-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. <span data-ttu-id="2be8a-113">Créez une procédure nommée `Test` qui appelle `DelegateTest` une seule fois avec le délégué pour `AddNumbers` en tant que paramètre, et à nouveau avec le délégué pour `SubtractNumbers` en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="2be8a-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     <span data-ttu-id="2be8a-114">Lorsque `Test` est appelé, il affiche tout d’abord le résultat de `AddNumbers` Status sur `5` et `3` , qui est 8.</span><span class="sxs-lookup"><span data-stu-id="2be8a-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="2be8a-115">Le résultat de `SubtractNumbers` Status sur `9` et `3` est affiché, ce qui correspond à 6.</span><span class="sxs-lookup"><span data-stu-id="2be8a-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be8a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2be8a-116">See also</span></span>

- [<span data-ttu-id="2be8a-117">Délégués</span><span class="sxs-lookup"><span data-stu-id="2be8a-117">Delegates</span></span>](index.md)
- [<span data-ttu-id="2be8a-118">AddressOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="2be8a-118">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="2be8a-119">Delegate, instruction</span><span class="sxs-lookup"><span data-stu-id="2be8a-119">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="2be8a-120">Comment : appeler une méthode déléguée</span><span class="sxs-lookup"><span data-stu-id="2be8a-120">How to: Invoke a Delegate Method</span></span>](how-to-invoke-a-delegate-method.md)
