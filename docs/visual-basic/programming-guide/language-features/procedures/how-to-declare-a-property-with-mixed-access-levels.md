---
title: "Comment : déclarer une propriété avec des niveaux d'accès mixtes"
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349698"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a><span data-ttu-id="12d9d-102">Comment : déclarer une propriété avec des niveaux d'accès mixtes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12d9d-102">How to: Declare a Property with Mixed Access Levels (Visual Basic)</span></span>
<span data-ttu-id="12d9d-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span><span class="sxs-lookup"><span data-stu-id="12d9d-103">If you want the `Get` and `Set` procedures on a property to have different access levels, you can use the more permissive level in the `Property` statement and the more restrictive level in either the `Get` or `Set` statement.</span></span> <span data-ttu-id="12d9d-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span><span class="sxs-lookup"><span data-stu-id="12d9d-104">You use mixed access levels on a property when you want certain parts of the code to be able to get the property's value, and certain other parts of the code to be able to change the value.</span></span>  
  
 <span data-ttu-id="12d9d-105">For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="12d9d-105">For more information on access levels, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a><span data-ttu-id="12d9d-106">To declare a property with mixed access levels</span><span class="sxs-lookup"><span data-stu-id="12d9d-106">To declare a property with mixed access levels</span></span>  
  
1. <span data-ttu-id="12d9d-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span><span class="sxs-lookup"><span data-stu-id="12d9d-107">Declare the property in the normal way, and specify the less restrictive access level (such as `Public`) in the `Property` statement.</span></span>  
  
2. <span data-ttu-id="12d9d-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span><span class="sxs-lookup"><span data-stu-id="12d9d-108">Declare either the `Get` or the `Set` procedure specifying the more restrictive access level (such as `Friend`).</span></span>  
  
3. <span data-ttu-id="12d9d-109">Do not specify an access level on the other property procedure.</span><span class="sxs-lookup"><span data-stu-id="12d9d-109">Do not specify an access level on the other property procedure.</span></span> <span data-ttu-id="12d9d-110">It assumes the access level declared in the `Property` statement.</span><span class="sxs-lookup"><span data-stu-id="12d9d-110">It assumes the access level declared in the `Property` statement.</span></span> <span data-ttu-id="12d9d-111">You can restrict access on only one of the property procedures.</span><span class="sxs-lookup"><span data-stu-id="12d9d-111">You can restrict access on only one of the property procedures.</span></span>  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     <span data-ttu-id="12d9d-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span><span class="sxs-lookup"><span data-stu-id="12d9d-112">In the preceding example, the `Get` procedure has the same `Protected` access as the property itself, while the `Set` procedure has `Private` access.</span></span> <span data-ttu-id="12d9d-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span><span class="sxs-lookup"><span data-stu-id="12d9d-113">A class derived from `employee` can read the `salary` value, but only the `employee` class can set it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12d9d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12d9d-114">See also</span></span>

- [<span data-ttu-id="12d9d-115">Procédures</span><span class="sxs-lookup"><span data-stu-id="12d9d-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="12d9d-116">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="12d9d-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="12d9d-117">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="12d9d-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="12d9d-118">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="12d9d-118">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="12d9d-119">Differences Between Properties and Variables in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12d9d-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="12d9d-120">Guide pratique : créer une propriété</span><span class="sxs-lookup"><span data-stu-id="12d9d-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="12d9d-121">Guide pratique : appeler une procédure de propriété</span><span class="sxs-lookup"><span data-stu-id="12d9d-121">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="12d9d-122">How to: Declare and Call a Default Property in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12d9d-122">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="12d9d-123">Guide pratique : placer une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="12d9d-123">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="12d9d-124">Guide pratique : obtenir une valeur d’une propriété</span><span class="sxs-lookup"><span data-stu-id="12d9d-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
