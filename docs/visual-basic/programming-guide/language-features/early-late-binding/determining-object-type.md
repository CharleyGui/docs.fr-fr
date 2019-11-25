---
title: Détermination du type Object
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: a77cc0603a0b61f58a4aa703c4b1e6ef4c26729c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345201"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="1361e-102">Détermination du type Object (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1361e-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="1361e-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span><span class="sxs-lookup"><span data-stu-id="1361e-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="1361e-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span><span class="sxs-lookup"><span data-stu-id="1361e-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="1361e-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span><span class="sxs-lookup"><span data-stu-id="1361e-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="1361e-106">TypeName and TypeOf…Is</span><span class="sxs-lookup"><span data-stu-id="1361e-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="1361e-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span><span class="sxs-lookup"><span data-stu-id="1361e-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="1361e-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="1361e-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="1361e-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span><span class="sxs-lookup"><span data-stu-id="1361e-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="1361e-110">A word of caution is due here.</span><span class="sxs-lookup"><span data-stu-id="1361e-110">A word of caution is due here.</span></span> <span data-ttu-id="1361e-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span><span class="sxs-lookup"><span data-stu-id="1361e-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="1361e-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span><span class="sxs-lookup"><span data-stu-id="1361e-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="1361e-113">These objects are derived from and inherit methods from <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="1361e-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="1361e-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span><span class="sxs-lookup"><span data-stu-id="1361e-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="1361e-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span><span class="sxs-lookup"><span data-stu-id="1361e-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="1361e-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span><span class="sxs-lookup"><span data-stu-id="1361e-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="1361e-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span><span class="sxs-lookup"><span data-stu-id="1361e-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="1361e-118">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="1361e-118">To run the example</span></span>  
  
1. <span data-ttu-id="1361e-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span><span class="sxs-lookup"><span data-stu-id="1361e-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2. <span data-ttu-id="1361e-120">From the button on your form, call the `TestObject` procedure.</span><span class="sxs-lookup"><span data-stu-id="1361e-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3. <span data-ttu-id="1361e-121">Add the following code to your form:</span><span class="sxs-lookup"><span data-stu-id="1361e-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="1361e-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1361e-122">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="1361e-123">Appel d’une propriété ou méthode à l’aide d’un nom de chaîne</span><span class="sxs-lookup"><span data-stu-id="1361e-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="1361e-124">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="1361e-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="1361e-125">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="1361e-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="1361e-126">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="1361e-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="1361e-127">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="1361e-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
