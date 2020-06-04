---
title: 'Comment : assigner un tableau à un autre tableau'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: c38def1ba9f3720bc760d6f6e4264510c884c930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413077"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="2f522-102">Comment : assigner un tableau à un autre tableau (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f522-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>

<span data-ttu-id="2f522-103">Étant donné que les tableaux sont des objets, vous pouvez les utiliser dans des instructions d’assignation comme d’autres types d’objets.</span><span class="sxs-lookup"><span data-stu-id="2f522-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="2f522-104">Une variable de tableau contient un pointeur vers les données qui constituent les éléments de tableau et les informations de rang et de longueur, et une assignation copie uniquement ce pointeur.</span><span class="sxs-lookup"><span data-stu-id="2f522-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>

### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="2f522-105">Pour assigner un tableau à un autre tableau</span><span class="sxs-lookup"><span data-stu-id="2f522-105">To assign one array to another array</span></span>

1. <span data-ttu-id="2f522-106">Assurez-vous que les deux tableaux ont le même rang (nombre de dimensions) et les types de données d’éléments compatibles.</span><span class="sxs-lookup"><span data-stu-id="2f522-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>

2. <span data-ttu-id="2f522-107">Utilisez une instruction d’assignation standard pour assigner le tableau source au tableau de destination.</span><span class="sxs-lookup"><span data-stu-id="2f522-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="2f522-108">Ne suivez pas le nom d’un tableau avec des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="2f522-108">Do not follow either array name with parentheses.</span></span>

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

<span data-ttu-id="2f522-109">Lorsque vous affectez un tableau à un autre, les règles suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="2f522-109">When you assign one array to another, the following rules apply:</span></span>

- <span data-ttu-id="2f522-110">**Égalité des rangs.**</span><span class="sxs-lookup"><span data-stu-id="2f522-110">**Equal Ranks.**</span></span> <span data-ttu-id="2f522-111">Le rang (nombre de dimensions) du tableau de destination doit être le même que celui du tableau source.</span><span class="sxs-lookup"><span data-stu-id="2f522-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>

  <span data-ttu-id="2f522-112">Si les rangs des deux tableaux sont égaux, les dimensions n’ont pas besoin d’être égales.</span><span class="sxs-lookup"><span data-stu-id="2f522-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="2f522-113">Le nombre d’éléments d’une dimension donnée peut changer pendant l’assignation.</span><span class="sxs-lookup"><span data-stu-id="2f522-113">The number of elements in a given dimension can change during assignment.</span></span>

- <span data-ttu-id="2f522-114">**Types d’éléments.**</span><span class="sxs-lookup"><span data-stu-id="2f522-114">**Element Types.**</span></span> <span data-ttu-id="2f522-115">Soit les deux tableaux doivent avoir des éléments de *type référence* , soit les deux tableaux doivent avoir des éléments de *type valeur* .</span><span class="sxs-lookup"><span data-stu-id="2f522-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="2f522-116">Pour plus d'informations, consultez [Value Types and Reference Types](../data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="2f522-116">For more information, see [Value Types and Reference Types](../data-types/value-types-and-reference-types.md).</span></span>

  - <span data-ttu-id="2f522-117">Si les deux tableaux ont des éléments de type valeur, les types de données d’élément doivent être exactement les mêmes.</span><span class="sxs-lookup"><span data-stu-id="2f522-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="2f522-118">La seule exception à cela est que vous pouvez assigner un tableau d' `Enum` éléments à un tableau du type de base de ce `Enum` .</span><span class="sxs-lookup"><span data-stu-id="2f522-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>

  - <span data-ttu-id="2f522-119">Si les deux tableaux ont des éléments de type référence, le type d’élément source doit dériver du type d’élément de destination.</span><span class="sxs-lookup"><span data-stu-id="2f522-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="2f522-120">Dans ce cas, les deux tableaux ont la même relation d’héritage que leurs éléments.</span><span class="sxs-lookup"><span data-stu-id="2f522-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="2f522-121">C’est ce que l’on appelle la *covariance de tableau*.</span><span class="sxs-lookup"><span data-stu-id="2f522-121">This is called *array covariance*.</span></span>

<span data-ttu-id="2f522-122">Le compilateur signale une erreur si les règles ci-dessus ne sont pas respectées, par exemple si les types de données ne sont pas compatibles ou si les rangs sont inégaux.</span><span class="sxs-lookup"><span data-stu-id="2f522-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="2f522-123">Vous pouvez ajouter la gestion des erreurs à votre code pour vous assurer que les tableaux sont compatibles avant de tenter une attribution.</span><span class="sxs-lookup"><span data-stu-id="2f522-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="2f522-124">Vous pouvez également utiliser le mot clé d' [opérateur TryCast](../../../language-reference/operators/trycast-operator.md) si vous souhaitez éviter de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="2f522-124">You can also use the [TryCast Operator](../../../language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f522-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f522-125">See also</span></span>

- [<span data-ttu-id="2f522-126">Tableaux</span><span class="sxs-lookup"><span data-stu-id="2f522-126">Arrays</span></span>](index.md)
- [<span data-ttu-id="2f522-127">Résolution des problèmes de tableaux</span><span class="sxs-lookup"><span data-stu-id="2f522-127">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="2f522-128">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="2f522-128">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="2f522-129">Conversions de tableau</span><span class="sxs-lookup"><span data-stu-id="2f522-129">Array Conversions</span></span>](../data-types/array-conversions.md)
