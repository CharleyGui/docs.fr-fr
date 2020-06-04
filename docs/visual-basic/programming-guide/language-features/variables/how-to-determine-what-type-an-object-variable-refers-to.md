---
title: 'Comment : déterminer le type désigné par une variable objet'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: d3224000f5958a8619e38c4d2f6dc5dbb275ad45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410488"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="b0769-102">Comment : déterminer le type désigné par une variable objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0769-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="b0769-103">Une variable objet contient un pointeur vers des données stockées ailleurs.</span><span class="sxs-lookup"><span data-stu-id="b0769-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="b0769-104">Le type de ces données peut changer au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b0769-104">The type of that data can change during run time.</span></span> <span data-ttu-id="b0769-105">À tout moment, vous pouvez utiliser la <xref:System.Type.GetTypeCode%2A> méthode pour déterminer le type au moment de l’exécution actuel ou l' [opérateur typeof](../../../language-reference/operators/typeof-operator.md) pour déterminer si le type d’exécution actuel est compatible avec un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="b0769-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="b0769-106">Pour déterminer le type exact auquel une variable objet fait actuellement référence</span><span class="sxs-lookup"><span data-stu-id="b0769-106">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="b0769-107">Sur la variable objet, appelez la <xref:System.Object.GetType%2A> méthode pour récupérer un <xref:System.Type?displayProperty=nameWithType> objet.</span><span class="sxs-lookup"><span data-stu-id="b0769-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="b0769-108">Sur la <xref:System.Type?displayProperty=nameWithType> classe, appelez la méthode partagée <xref:System.Type.GetTypeCode%2A> pour récupérer la <xref:System.TypeCode> valeur d’énumération du type de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b0769-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="b0769-109">Vous pouvez tester la <xref:System.TypeCode> valeur d’énumération en fonction des membres d’énumération intéressants, tels que `Double` .</span><span class="sxs-lookup"><span data-stu-id="b0769-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="b0769-110">Pour déterminer si le type d’une variable objet est compatible avec un type spécifié</span><span class="sxs-lookup"><span data-stu-id="b0769-110">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="b0769-111">Utilisez l' `TypeOf` opérateur en association avec l' [opérateur is](../../../language-reference/operators/is-operator.md) pour tester l’objet avec une `TypeOf` expression... `Is` .</span><span class="sxs-lookup"><span data-stu-id="b0769-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="b0769-112">L' `TypeOf` expression... `Is` retourne `True` si le type au moment de l’exécution de l’objet est compatible avec le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="b0769-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="b0769-113">Le critère de compatibilité varie selon que le type spécifié est une classe, une structure ou une interface.</span><span class="sxs-lookup"><span data-stu-id="b0769-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="b0769-114">En général, les types sont compatibles si l’objet est du même type que, hérite de ou implémente le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="b0769-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="b0769-115">Pour plus d’informations, consultez [opérateur typeof](../../../language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b0769-115">For more information, see [TypeOf Operator](../../../language-reference/operators/typeof-operator.md).</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="b0769-116">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="b0769-116">Compile the code</span></span>

<span data-ttu-id="b0769-117">Notez que le type spécifié ne peut pas être une variable ou une expression.</span><span class="sxs-lookup"><span data-stu-id="b0769-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="b0769-118">Il doit s’agir du nom d’un type défini, tel qu’une classe, une structure ou une interface.</span><span class="sxs-lookup"><span data-stu-id="b0769-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="b0769-119">Cela comprend les types intrinsèques tels que `Integer` et `String` .</span><span class="sxs-lookup"><span data-stu-id="b0769-119">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0769-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0769-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="b0769-121">Variables objets</span><span class="sxs-lookup"><span data-stu-id="b0769-121">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="b0769-122">Valeurs des variables objets</span><span class="sxs-lookup"><span data-stu-id="b0769-122">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="b0769-123">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="b0769-123">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
