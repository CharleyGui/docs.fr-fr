---
title: "Comment : obtenir une valeur d'une propriété"
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 85512d4311d3e731a2c4e129d6a01f9b3273b333
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74339828"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="1a209-102">Comment : obtenir une valeur d'une propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a209-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="1a209-103">You retrieve a property's value by including the property name in an expression.</span><span class="sxs-lookup"><span data-stu-id="1a209-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="1a209-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span><span class="sxs-lookup"><span data-stu-id="1a209-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="1a209-105">You use the property just as you would use a variable.</span><span class="sxs-lookup"><span data-stu-id="1a209-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="1a209-106">Visual Basic makes the calls to the property's procedures.</span><span class="sxs-lookup"><span data-stu-id="1a209-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="1a209-107">To retrieve a value from a property</span><span class="sxs-lookup"><span data-stu-id="1a209-107">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="1a209-108">Use the property name in an expression the same way you would use a variable name.</span><span class="sxs-lookup"><span data-stu-id="1a209-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="1a209-109">You can use a property anywhere you can use a variable or a constant.</span><span class="sxs-lookup"><span data-stu-id="1a209-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="1a209-110">ou</span><span class="sxs-lookup"><span data-stu-id="1a209-110">-or-</span></span>  
  
     <span data-ttu-id="1a209-111">Use the property name following the equal (`=`) sign in an assignment statement.</span><span class="sxs-lookup"><span data-stu-id="1a209-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="1a209-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span><span class="sxs-lookup"><span data-stu-id="1a209-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="1a209-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span><span class="sxs-lookup"><span data-stu-id="1a209-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="1a209-114">If there are no arguments, you can optionally omit the parentheses.</span><span class="sxs-lookup"><span data-stu-id="1a209-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="1a209-115">Place the arguments in the argument list within the parentheses, separated by commas.</span><span class="sxs-lookup"><span data-stu-id="1a209-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="1a209-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span><span class="sxs-lookup"><span data-stu-id="1a209-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="1a209-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span><span class="sxs-lookup"><span data-stu-id="1a209-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a209-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a209-118">See also</span></span>

- [<span data-ttu-id="1a209-119">Procédures</span><span class="sxs-lookup"><span data-stu-id="1a209-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="1a209-120">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="1a209-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="1a209-121">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="1a209-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1a209-122">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="1a209-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="1a209-123">Differences Between Properties and Variables in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a209-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="1a209-124">Guide pratique : créer une propriété</span><span class="sxs-lookup"><span data-stu-id="1a209-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="1a209-125">Guide pratique : déclarer une propriété avec des niveaux d’accès mixtes</span><span class="sxs-lookup"><span data-stu-id="1a209-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="1a209-126">Guide pratique : appeler une procédure de propriété</span><span class="sxs-lookup"><span data-stu-id="1a209-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="1a209-127">How to: Declare and Call a Default Property in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1a209-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="1a209-128">Guide pratique : placer une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="1a209-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
