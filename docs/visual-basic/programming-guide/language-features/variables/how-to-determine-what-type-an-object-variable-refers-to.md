---
title: 'Procédure : Déterminer le type auquel une variable objet fait référence (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 935623dd4b6edca188f932aca0e560130199e8f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626567"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="fdf33-102">Procédure : Déterminer le type auquel une variable objet fait référence (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdf33-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="fdf33-103">Une variable objet contient un pointeur vers des données stockées ailleurs.</span><span class="sxs-lookup"><span data-stu-id="fdf33-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="fdf33-104">Le type de ces données peut changer au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fdf33-104">The type of that data can change during run time.</span></span> <span data-ttu-id="fdf33-105">À tout moment, vous pouvez utiliser la <xref:System.Type.GetTypeCode%2A> méthode pour déterminer le type au moment de l’exécution actuel ou l' [opérateur typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md) pour déterminer si le type d’exécution actuel est compatible avec un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="fdf33-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="fdf33-106">Pour déterminer le type exact auquel une variable objet fait actuellement référence</span><span class="sxs-lookup"><span data-stu-id="fdf33-106">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="fdf33-107">Sur la variable objet, appelez la <xref:System.Object.GetType%2A> méthode pour récupérer un <xref:System.Type?displayProperty=nameWithType> objet.</span><span class="sxs-lookup"><span data-stu-id="fdf33-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="fdf33-108">Sur la <xref:System.Type?displayProperty=nameWithType> classe, appelez la méthode <xref:System.Type.GetTypeCode%2A> partagée pour récupérer la <xref:System.TypeCode> valeur d’énumération du type de l’objet.</span><span class="sxs-lookup"><span data-stu-id="fdf33-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="fdf33-109">Vous pouvez tester la <xref:System.TypeCode> valeur d’énumération en fonction des membres d’énumération intéressants `Double`, tels que.</span><span class="sxs-lookup"><span data-stu-id="fdf33-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="fdf33-110">Pour déterminer si le type d’une variable objet est compatible avec un type spécifié</span><span class="sxs-lookup"><span data-stu-id="fdf33-110">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="fdf33-111">Utilisez l' `TypeOf` opérateur en association avec l' [opérateur is](../../../../visual-basic/language-reference/operators/is-operator.md) pour tester l’objet avec un `TypeOf`... `Is` expression.</span><span class="sxs-lookup"><span data-stu-id="fdf33-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="fdf33-112">`TypeOf`... l’expression `True` retourne si le type au moment de l’exécution de l’objet est compatible avec le type spécifié. `Is`</span><span class="sxs-lookup"><span data-stu-id="fdf33-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="fdf33-113">Le critère de compatibilité varie selon que le type spécifié est une classe, une structure ou une interface.</span><span class="sxs-lookup"><span data-stu-id="fdf33-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="fdf33-114">En général, les types sont compatibles si l’objet est du même type que, hérite de ou implémente le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="fdf33-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="fdf33-115">Pour plus d’informations, consultez [opérateur typeof](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="fdf33-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="fdf33-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="fdf33-116">Compiling the Code</span></span>

<span data-ttu-id="fdf33-117">Notez que le type spécifié ne peut pas être une variable ou une expression.</span><span class="sxs-lookup"><span data-stu-id="fdf33-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="fdf33-118">Il doit s’agir du nom d’un type défini, tel qu’une classe, une structure ou une interface.</span><span class="sxs-lookup"><span data-stu-id="fdf33-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="fdf33-119">Cela comprend les types intrinsèques `Integer` tels `String`que et.</span><span class="sxs-lookup"><span data-stu-id="fdf33-119">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdf33-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fdf33-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="fdf33-121">Variables objets</span><span class="sxs-lookup"><span data-stu-id="fdf33-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="fdf33-122">Valeurs des variables objets</span><span class="sxs-lookup"><span data-stu-id="fdf33-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="fdf33-123">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="fdf33-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
