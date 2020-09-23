---
title: 'Comment : appeler une procédure de propriété'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 0b35751136937d4cee5b3ca9669b43d3fbdf71a1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071949"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="45948-102">Comment : appeler une procédure de propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45948-102">How to: Call a Property Procedure (Visual Basic)</span></span>

<span data-ttu-id="45948-103">Vous appelez une procédure de propriété en stockant une valeur dans la propriété ou en récupérant sa valeur.</span><span class="sxs-lookup"><span data-stu-id="45948-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="45948-104">Vous accédez à une propriété de la même façon que vous accédez à une variable.</span><span class="sxs-lookup"><span data-stu-id="45948-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="45948-105">La procédure de la propriété `Set` stocke une valeur et sa `Get` procédure récupère la valeur.</span><span class="sxs-lookup"><span data-stu-id="45948-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="45948-106">Toutefois, vous n’appelez pas explicitement ces procédures par nom.</span><span class="sxs-lookup"><span data-stu-id="45948-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="45948-107">Vous utilisez la propriété dans une instruction d’assignation ou une expression, de la même façon que vous stockez ou récupérez la valeur d’une variable.</span><span class="sxs-lookup"><span data-stu-id="45948-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="45948-108">Visual Basic effectue les appels aux procédures de la propriété.</span><span class="sxs-lookup"><span data-stu-id="45948-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="45948-109">Pour appeler la procédure d’extraction d’une propriété</span><span class="sxs-lookup"><span data-stu-id="45948-109">To call a property's Get procedure</span></span>  
  
1. <span data-ttu-id="45948-110">Utilisez le nom de la propriété dans une expression de la même façon que vous utilisez un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="45948-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="45948-111">Vous pouvez utiliser une propriété partout où vous pouvez utiliser une variable ou une constante.</span><span class="sxs-lookup"><span data-stu-id="45948-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="45948-112">- ou -</span><span class="sxs-lookup"><span data-stu-id="45948-112">-or-</span></span>  
  
     <span data-ttu-id="45948-113">Utilisez le nom de propriété après le signe égal ( `=` ) dans une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="45948-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="45948-114">L’exemple suivant lit la valeur de la <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> propriété, en appelant implicitement sa `Get` procédure.</span><span class="sxs-lookup"><span data-stu-id="45948-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="45948-115">Si la propriété accepte des arguments, placez le nom de la propriété entre parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="45948-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="45948-116">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="45948-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="45948-117">Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="45948-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="45948-118">Veillez à fournir les arguments dans l’ordre dans lequel la propriété définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="45948-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="45948-119">La valeur de la propriété participe à l’expression de la même manière qu’une variable ou une constante, ou elle est stockée dans la variable ou la propriété à gauche de l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="45948-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="45948-120">Pour appeler la procédure Set d’une propriété</span><span class="sxs-lookup"><span data-stu-id="45948-120">To call a property's Set procedure</span></span>  
  
1. <span data-ttu-id="45948-121">Utilisez le nom de la propriété sur le côté gauche d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="45948-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="45948-122">L’exemple suivant définit la valeur de la <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> propriété, en appelant implicitement la `Set` procédure.</span><span class="sxs-lookup"><span data-stu-id="45948-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="45948-123">Si la propriété accepte des arguments, placez le nom de la propriété entre parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="45948-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="45948-124">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="45948-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="45948-125">Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="45948-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="45948-126">Veillez à fournir les arguments dans l’ordre dans lequel la propriété définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="45948-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="45948-127">La valeur générée sur le côté droit de l’instruction d’assignation est stockée dans la propriété.</span><span class="sxs-lookup"><span data-stu-id="45948-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45948-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45948-128">See also</span></span>

- [<span data-ttu-id="45948-129">Procédures Property</span><span class="sxs-lookup"><span data-stu-id="45948-129">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="45948-130">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="45948-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="45948-131">Property Statement</span><span class="sxs-lookup"><span data-stu-id="45948-131">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="45948-132">Différences entre les propriétés et les variables en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45948-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="45948-133">Comment : créer une propriété</span><span class="sxs-lookup"><span data-stu-id="45948-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="45948-134">Comment : déclarer une propriété avec des niveaux d'accès mixtes</span><span class="sxs-lookup"><span data-stu-id="45948-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="45948-135">Comment : déclarer et appeler une propriété par défaut en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45948-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="45948-136">Comment : placer une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="45948-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="45948-137">Comment : obtenir une valeur d'une propriété</span><span class="sxs-lookup"><span data-stu-id="45948-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
- [<span data-ttu-id="45948-138">Get, instruction</span><span class="sxs-lookup"><span data-stu-id="45948-138">Get Statement</span></span>](../../../language-reference/statements/get-statement.md)
- [<span data-ttu-id="45948-139">Instruction Set</span><span class="sxs-lookup"><span data-stu-id="45948-139">Set Statement</span></span>](../../../language-reference/statements/set-statement.md)
