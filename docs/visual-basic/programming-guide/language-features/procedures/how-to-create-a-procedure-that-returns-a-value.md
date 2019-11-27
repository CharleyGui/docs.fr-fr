---
title: 'Comment : créer une procédure qui retourne une valeur'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 218dbb52abc0100724d38d10be91ef24252d5226
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349721"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="0ca98-102">Comment : créer une procédure qui retourne une valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ca98-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="0ca98-103">Vous utilisez une procédure `Function` pour retourner une valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="0ca98-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="0ca98-104">Pour créer une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="0ca98-104">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="0ca98-105">En dehors de toute autre procédure, utilisez une instruction `Function`, suivie d’une instruction `End Function`.</span><span class="sxs-lookup"><span data-stu-id="0ca98-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="0ca98-106">Dans l’instruction `Function`, suivez le mot clé `Function` avec le nom de la procédure, puis la liste de paramètres entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="0ca98-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="0ca98-107">Suivez les parenthèses avec une clause `As` pour spécifier le type de données de la valeur retournée.</span><span class="sxs-lookup"><span data-stu-id="0ca98-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="0ca98-108">Placez les instructions de code de la procédure entre les instructions `Function` et `End Function`.</span><span class="sxs-lookup"><span data-stu-id="0ca98-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="0ca98-109">Utilisez une instruction `Return` pour retourner la valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="0ca98-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="0ca98-110">La procédure `Function` suivante calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, en fonction des valeurs des deux autres côtés.</span><span class="sxs-lookup"><span data-stu-id="0ca98-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="0ca98-111">L’exemple suivant montre un appel typique à `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="0ca98-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0ca98-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ca98-112">See also</span></span>

- [<span data-ttu-id="0ca98-113">Procédures</span><span class="sxs-lookup"><span data-stu-id="0ca98-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="0ca98-114">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="0ca98-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="0ca98-115">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="0ca98-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="0ca98-116">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="0ca98-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="0ca98-117">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="0ca98-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0ca98-118">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="0ca98-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="0ca98-119">Guide pratique : retourner une valeur d’une procédure</span><span class="sxs-lookup"><span data-stu-id="0ca98-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="0ca98-120">Guide pratique : appeler une procédure qui retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="0ca98-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
