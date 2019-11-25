---
title: Overloaded properties and methods
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: a5017d371f8a01436020443b2e3466c78fc35d21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346090"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="ba0ef-102">Overloaded properties and methods (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba0ef-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="ba0ef-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>

## <a name="overloading-usage"></a><span data-ttu-id="ba0ef-104">Overloading usage</span><span class="sxs-lookup"><span data-stu-id="ba0ef-104">Overloading usage</span></span>

<span data-ttu-id="ba0ef-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="ba0ef-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span><span class="sxs-lookup"><span data-stu-id="ba0ef-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

<span data-ttu-id="ba0ef-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span><span class="sxs-lookup"><span data-stu-id="ba0ef-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

<span data-ttu-id="ba0ef-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="ba0ef-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span><span class="sxs-lookup"><span data-stu-id="ba0ef-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

<span data-ttu-id="ba0ef-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="ba0ef-111">Overloading rules</span><span class="sxs-lookup"><span data-stu-id="ba0ef-111">Overloading rules</span></span>

 <span data-ttu-id="ba0ef-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="ba0ef-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span><span class="sxs-lookup"><span data-stu-id="ba0ef-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>

- <span data-ttu-id="ba0ef-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>

- <span data-ttu-id="ba0ef-115">Names of parameters</span><span class="sxs-lookup"><span data-stu-id="ba0ef-115">Names of parameters</span></span>

- <span data-ttu-id="ba0ef-116">Return types of procedures</span><span class="sxs-lookup"><span data-stu-id="ba0ef-116">Return types of procedures</span></span>

<span data-ttu-id="ba0ef-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>

<span data-ttu-id="ba0ef-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="ba0ef-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>

<span data-ttu-id="ba0ef-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="ba0ef-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>

<span data-ttu-id="ba0ef-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>

### <a name="example"></a><span data-ttu-id="ba0ef-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="ba0ef-123">Example</span></span>

<span data-ttu-id="ba0ef-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="ba0ef-125">To use this example to create an overloaded method</span><span class="sxs-lookup"><span data-stu-id="ba0ef-125">To use this example to create an overloaded method</span></span>

1. <span data-ttu-id="ba0ef-126">Open a new project and add a class named `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-126">Open a new project and add a class named `TaxClass`.</span></span>

2. <span data-ttu-id="ba0ef-127">Ajoutez le code suivant à la classe `TaxClass` .</span><span class="sxs-lookup"><span data-stu-id="ba0ef-127">Add the following code to the `TaxClass` class.</span></span>

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. <span data-ttu-id="ba0ef-128">Add the following procedure to your form.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-128">Add the following procedure to your form.</span></span>

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. <span data-ttu-id="ba0ef-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>

5. <span data-ttu-id="ba0ef-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>

<span data-ttu-id="ba0ef-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="ba0ef-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="ba0ef-133">Tax is $5.12" is displayed.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="ba0ef-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="ba0ef-135">Tax is $5.12" is displayed.</span><span class="sxs-lookup"><span data-stu-id="ba0ef-135">Tax is $5.12" is displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba0ef-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba0ef-136">See also</span></span>

- [<span data-ttu-id="ba0ef-137">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="ba0ef-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="ba0ef-138">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba0ef-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="ba0ef-139">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="ba0ef-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="ba0ef-140">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="ba0ef-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="ba0ef-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="ba0ef-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="ba0ef-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="ba0ef-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)
- [<span data-ttu-id="ba0ef-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="ba0ef-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)
- [<span data-ttu-id="ba0ef-144">Surcharges</span><span class="sxs-lookup"><span data-stu-id="ba0ef-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="ba0ef-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="ba0ef-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
