---
title: Valeurs des variables objets
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 8b93063d2d97802b1a7fdbc93e01040ff3337753
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351799"
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="79006-102">Valeurs des variables objets (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79006-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="79006-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span><span class="sxs-lookup"><span data-stu-id="79006-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="79006-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span><span class="sxs-lookup"><span data-stu-id="79006-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="79006-105">Object Classifier Functions</span><span class="sxs-lookup"><span data-stu-id="79006-105">Object Classifier Functions</span></span>  
 <span data-ttu-id="79006-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span><span class="sxs-lookup"><span data-stu-id="79006-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="79006-107">Fonction</span><span class="sxs-lookup"><span data-stu-id="79006-107">Function</span></span>|<span data-ttu-id="79006-108">Returns True if the Object variable refers to</span><span class="sxs-lookup"><span data-stu-id="79006-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="79006-109">An array of values, rather than a single value</span><span class="sxs-lookup"><span data-stu-id="79006-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="79006-110">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span><span class="sxs-lookup"><span data-stu-id="79006-110">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="79006-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span><span class="sxs-lookup"><span data-stu-id="79006-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="79006-112">An exception object, which derives from <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="79006-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="79006-113">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span><span class="sxs-lookup"><span data-stu-id="79006-113">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="79006-114">A number, or a string that can be interpreted as a number</span><span class="sxs-lookup"><span data-stu-id="79006-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="79006-115">A reference type (such as a string, array, delegate, or class type)</span><span class="sxs-lookup"><span data-stu-id="79006-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="79006-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span><span class="sxs-lookup"><span data-stu-id="79006-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="79006-117">TypeOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="79006-117">TypeOf Operator</span></span>  
 <span data-ttu-id="79006-118">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span><span class="sxs-lookup"><span data-stu-id="79006-118">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="79006-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span><span class="sxs-lookup"><span data-stu-id="79006-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="79006-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span><span class="sxs-lookup"><span data-stu-id="79006-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```vb  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 <span data-ttu-id="79006-121">The preceding example writes the following lines to the **Debug** window:</span><span class="sxs-lookup"><span data-stu-id="79006-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="79006-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="79006-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="79006-123">Object Arrays</span><span class="sxs-lookup"><span data-stu-id="79006-123">Object Arrays</span></span>  
 <span data-ttu-id="79006-124">You can declare and use an array of `Object` variables.</span><span class="sxs-lookup"><span data-stu-id="79006-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="79006-125">This is useful when you need to handle a variety of data types and object classes.</span><span class="sxs-lookup"><span data-stu-id="79006-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="79006-126">All the elements in an array must have the same declared data type.</span><span class="sxs-lookup"><span data-stu-id="79006-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="79006-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span><span class="sxs-lookup"><span data-stu-id="79006-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79006-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79006-128">See also</span></span>

- [<span data-ttu-id="79006-129">Variables objets</span><span class="sxs-lookup"><span data-stu-id="79006-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="79006-130">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="79006-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="79006-131">Assignation des variables objets</span><span class="sxs-lookup"><span data-stu-id="79006-131">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="79006-132">Guide pratique : référencer l'instance actuelle d'un objet</span><span class="sxs-lookup"><span data-stu-id="79006-132">How to: Refer to the Current Instance of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="79006-133">Guide pratique : déterminer le type désigné par une variable objet</span><span class="sxs-lookup"><span data-stu-id="79006-133">How to: Determine What Type an Object Variable Refers To</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [<span data-ttu-id="79006-134">Guide pratique : déterminer si deux objets sont liés</span><span class="sxs-lookup"><span data-stu-id="79006-134">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="79006-135">Guide pratique : déterminer si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="79006-135">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [<span data-ttu-id="79006-136">Types de données</span><span class="sxs-lookup"><span data-stu-id="79006-136">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
