---
title: Conversions de tableau
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
ms.openlocfilehash: 375c75c954f3be535272d674d9b786cad46b1a01
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077187"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="1fa6a-102">Conversion des tableaux (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fa6a-102">Array Conversions (Visual Basic)</span></span>

<span data-ttu-id="1fa6a-103">Vous pouvez convertir un type tableau en un type de tableau différent, à condition que vous respectiez les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="1fa6a-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="1fa6a-104">**Même rang.**</span><span class="sxs-lookup"><span data-stu-id="1fa6a-104">**Equal Rank.**</span></span> <span data-ttu-id="1fa6a-105">Les rangs des deux tableaux doivent être identiques, autrement dit, ils doivent avoir le même nombre de dimensions.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="1fa6a-106">Toutefois, les longueurs des dimensions respectives ne doivent pas nécessairement être identiques.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="1fa6a-107">**Type de données de l’élément.**</span><span class="sxs-lookup"><span data-stu-id="1fa6a-107">**Element Data Type.**</span></span> <span data-ttu-id="1fa6a-108">Les types de données des éléments des deux tableaux doivent être des types référence.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="1fa6a-109">Vous ne pouvez pas convertir un `Integer` tableau en `Long` tableau, ni même en `Object` tableau, car au moins un type valeur est impliqué.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="1fa6a-110">Pour plus d'informations, consultez [Value Types and Reference Types](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="1fa6a-110">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="1fa6a-111">**Convertibilité.**</span><span class="sxs-lookup"><span data-stu-id="1fa6a-111">**Convertibility.**</span></span> <span data-ttu-id="1fa6a-112">Une conversion, étendue ou restrictive, doit être possible entre les types d’éléments des deux tableaux.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="1fa6a-113">Un exemple qui ne respecte pas cette exigence est une tentative de conversion entre un `String` tableau et un tableau d’une classe dérivée de <xref:System.Attribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1fa6a-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1fa6a-114">Ces deux types n’ont rien en commun et aucune conversion n’existe entre eux.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="1fa6a-115">La conversion d’un type tableau en un autre est étendue ou restrictive, selon que la conversion des éléments respectifs est étendue ou restrictive.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="1fa6a-116">Pour plus d’informations, consultez [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="1fa6a-116">For more information, see [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="1fa6a-117">Conversion en tableau d’objets</span><span class="sxs-lookup"><span data-stu-id="1fa6a-117">Conversion to an Object Array</span></span>  

 <span data-ttu-id="1fa6a-118">Lorsque vous déclarez un `Object` tableau sans l’initialiser, son type d’élément est `Object` tant qu’il reste non initialisé.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="1fa6a-119">Quand vous le définissez sur un tableau d’une classe spécifique, il prend le type de cette classe.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="1fa6a-120">Toutefois, son type sous-jacent est toujours `Object` , et vous pouvez le définir par la suite sur un autre tableau d’une classe non liée.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="1fa6a-121">Étant donné que toutes les classes dérivent de `Object` , vous pouvez modifier le type d’élément du tableau, de n’importe quelle classe à une autre classe.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="1fa6a-122">Dans l’exemple suivant, aucune conversion n’existe entre les types `student` et `String` , mais les deux dérivent de `Object` , donc toutes les affectations sont valides.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
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
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="1fa6a-123">Type sous-jacent d’un tableau</span><span class="sxs-lookup"><span data-stu-id="1fa6a-123">Underlying Type of an Array</span></span>  

 <span data-ttu-id="1fa6a-124">Si vous déclarez à l’origine un tableau avec une classe spécifique, son type d’élément sous-jacent est cette classe.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="1fa6a-125">Si vous la définissez par la suite sur un tableau d’une autre classe, il doit y avoir une conversion entre les deux classes.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="1fa6a-126">Dans l’exemple suivant, `students` est un `student` tableau.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="1fa6a-127">Étant donné qu’il n’existe aucune conversion entre `String` et `student` , la dernière instruction échoue.</span><span class="sxs-lookup"><span data-stu-id="1fa6a-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="1fa6a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fa6a-128">See also</span></span>

- [<span data-ttu-id="1fa6a-129">Data types</span><span class="sxs-lookup"><span data-stu-id="1fa6a-129">Data Types</span></span>](index.md)
- [<span data-ttu-id="1fa6a-130">Conversions de type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fa6a-130">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="1fa6a-131">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="1fa6a-131">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="1fa6a-132">Conversions entre des chaînes et d’autres types</span><span class="sxs-lookup"><span data-stu-id="1fa6a-132">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="1fa6a-133">Comment : convertir un objet en un autre type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fa6a-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="1fa6a-134">Data types</span><span class="sxs-lookup"><span data-stu-id="1fa6a-134">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="1fa6a-135">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="1fa6a-135">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="1fa6a-136">Tableaux</span><span class="sxs-lookup"><span data-stu-id="1fa6a-136">Arrays</span></span>](../arrays/index.md)
