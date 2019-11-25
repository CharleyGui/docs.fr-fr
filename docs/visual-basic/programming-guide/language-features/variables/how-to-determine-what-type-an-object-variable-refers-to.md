---
title: 'Comment : déterminer le type désigné par une variable objet'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 9f9b89e2fea0bd69cba6d50fa1d1fb9cc3927685
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348619"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="093bb-102">Comment : déterminer le type désigné par une variable objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="093bb-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="093bb-103">An object variable contains a pointer to data that is stored elsewhere.</span><span class="sxs-lookup"><span data-stu-id="093bb-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="093bb-104">The type of that data can change during run time.</span><span class="sxs-lookup"><span data-stu-id="093bb-104">The type of that data can change during run time.</span></span> <span data-ttu-id="093bb-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span><span class="sxs-lookup"><span data-stu-id="093bb-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="093bb-106">To determine the exact type an object variable currently refers to</span><span class="sxs-lookup"><span data-stu-id="093bb-106">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="093bb-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span><span class="sxs-lookup"><span data-stu-id="093bb-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="093bb-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span><span class="sxs-lookup"><span data-stu-id="093bb-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="093bb-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span><span class="sxs-lookup"><span data-stu-id="093bb-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="093bb-110">To determine whether an object variable's type is compatible with a specified type</span><span class="sxs-lookup"><span data-stu-id="093bb-110">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="093bb-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span><span class="sxs-lookup"><span data-stu-id="093bb-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="093bb-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span><span class="sxs-lookup"><span data-stu-id="093bb-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="093bb-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span><span class="sxs-lookup"><span data-stu-id="093bb-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="093bb-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span><span class="sxs-lookup"><span data-stu-id="093bb-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="093bb-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="093bb-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="093bb-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="093bb-116">Compiling the Code</span></span>

<span data-ttu-id="093bb-117">Note that the specified type cannot be a variable or expression.</span><span class="sxs-lookup"><span data-stu-id="093bb-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="093bb-118">It must be the name of a defined type, such as a class, structure, or interface.</span><span class="sxs-lookup"><span data-stu-id="093bb-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="093bb-119">This includes intrinsic types such as `Integer` and `String`.</span><span class="sxs-lookup"><span data-stu-id="093bb-119">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="093bb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="093bb-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="093bb-121">Variables objets</span><span class="sxs-lookup"><span data-stu-id="093bb-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="093bb-122">Valeurs des variables objets</span><span class="sxs-lookup"><span data-stu-id="093bb-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="093bb-123">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="093bb-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
