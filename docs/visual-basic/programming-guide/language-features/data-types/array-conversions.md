---
title: Conversion des tableaux (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 475f3f5357f7c989a30ca9e6c5d32b8cc989436f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581862"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="a19f8-102">Conversion des tableaux (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a19f8-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="a19f8-103">Vous pouvez convertir un type tableau en un type de tableau différent, à condition que vous respectiez les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="a19f8-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="a19f8-104">**Même rang.**</span><span class="sxs-lookup"><span data-stu-id="a19f8-104">**Equal Rank.**</span></span> <span data-ttu-id="a19f8-105">Les rangs des deux tableaux doivent être identiques, autrement dit, ils doivent avoir le même nombre de dimensions.</span><span class="sxs-lookup"><span data-stu-id="a19f8-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="a19f8-106">Toutefois, les longueurs des dimensions respectives ne doivent pas nécessairement être identiques.</span><span class="sxs-lookup"><span data-stu-id="a19f8-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="a19f8-107">**Type de données de l’élément.**</span><span class="sxs-lookup"><span data-stu-id="a19f8-107">**Element Data Type.**</span></span> <span data-ttu-id="a19f8-108">Les types de données des éléments des deux tableaux doivent être des types référence.</span><span class="sxs-lookup"><span data-stu-id="a19f8-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="a19f8-109">Vous ne pouvez pas convertir un tableau `Integer` en tableau `Long`, ni même en tableau `Object`, car au moins un type valeur est impliqué.</span><span class="sxs-lookup"><span data-stu-id="a19f8-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="a19f8-110">Pour plus d'informations, consultez [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="a19f8-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="a19f8-111">**Convertibilité.**</span><span class="sxs-lookup"><span data-stu-id="a19f8-111">**Convertibility.**</span></span> <span data-ttu-id="a19f8-112">Une conversion, étendue ou restrictive, doit être possible entre les types d’éléments des deux tableaux.</span><span class="sxs-lookup"><span data-stu-id="a19f8-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="a19f8-113">Un exemple qui ne respecte pas cette exigence est une tentative de conversion entre un tableau `String` et un tableau d’une classe dérivée de <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a19f8-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a19f8-114">Ces deux types n’ont rien en commun et aucune conversion n’existe entre eux.</span><span class="sxs-lookup"><span data-stu-id="a19f8-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="a19f8-115">La conversion d’un type tableau en un autre est étendue ou restrictive, selon que la conversion des éléments respectifs est étendue ou restrictive.</span><span class="sxs-lookup"><span data-stu-id="a19f8-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="a19f8-116">Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="a19f8-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="a19f8-117">Conversion en tableau d’objets</span><span class="sxs-lookup"><span data-stu-id="a19f8-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="a19f8-118">Lorsque vous déclarez un tableau de `Object` sans l’initialiser, son type d’élément est `Object` tant qu’il n’est pas initialisé.</span><span class="sxs-lookup"><span data-stu-id="a19f8-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="a19f8-119">Quand vous le définissez sur un tableau d’une classe spécifique, il prend le type de cette classe.</span><span class="sxs-lookup"><span data-stu-id="a19f8-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="a19f8-120">Toutefois, son type sous-jacent est toujours `Object`, et vous pouvez le définir par la suite sur un autre tableau d’une classe non liée.</span><span class="sxs-lookup"><span data-stu-id="a19f8-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="a19f8-121">Étant donné que toutes les classes dérivent de `Object`, vous pouvez remplacer le type d’élément du tableau de toute classe par une autre classe.</span><span class="sxs-lookup"><span data-stu-id="a19f8-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="a19f8-122">Dans l’exemple suivant, aucune conversion n’existe entre les types `student` et `String`, mais les deux dérivent de `Object`, donc toutes les affectations sont valides.</span><span class="sxs-lookup"><span data-stu-id="a19f8-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```vb  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="a19f8-123">Type sous-jacent d’un tableau</span><span class="sxs-lookup"><span data-stu-id="a19f8-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="a19f8-124">Si vous déclarez à l’origine un tableau avec une classe spécifique, son type d’élément sous-jacent est cette classe.</span><span class="sxs-lookup"><span data-stu-id="a19f8-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="a19f8-125">Si vous la définissez par la suite sur un tableau d’une autre classe, il doit y avoir une conversion entre les deux classes.</span><span class="sxs-lookup"><span data-stu-id="a19f8-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="a19f8-126">Dans l’exemple suivant, `students` est un tableau de `student`.</span><span class="sxs-lookup"><span data-stu-id="a19f8-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="a19f8-127">Étant donné qu’il n’existe aucune conversion entre `String` et `student`, la dernière instruction échoue.</span><span class="sxs-lookup"><span data-stu-id="a19f8-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="a19f8-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a19f8-128">See also</span></span>

- [<span data-ttu-id="a19f8-129">Types de données</span><span class="sxs-lookup"><span data-stu-id="a19f8-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="a19f8-130">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a19f8-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="a19f8-131">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="a19f8-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="a19f8-132">Conversion entre des chaînes et d’autres types</span><span class="sxs-lookup"><span data-stu-id="a19f8-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="a19f8-133">Comment : convertir un objet en un autre type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a19f8-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="a19f8-134">Types de données</span><span class="sxs-lookup"><span data-stu-id="a19f8-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="a19f8-135">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="a19f8-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a19f8-136">Tableaux</span><span class="sxs-lookup"><span data-stu-id="a19f8-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
