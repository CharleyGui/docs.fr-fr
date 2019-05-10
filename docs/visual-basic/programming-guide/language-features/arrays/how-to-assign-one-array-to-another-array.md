---
title: 'Procédure : Assigner un tableau à un autre tableau (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: a39888f19e5033a5c6622313fb7451d6463b2f7c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64858884"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="2746f-102">Procédure : Assigner un tableau à un autre tableau (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2746f-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>

<span data-ttu-id="2746f-103">Étant donné que les tableaux sont des objets, vous pouvez les utiliser dans les instructions d’assignation, comme d’autres types d’objets.</span><span class="sxs-lookup"><span data-stu-id="2746f-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="2746f-104">Une variable de tableau conserve un pointeur vers les données constituant les éléments du tableau et les informations de classement et de longueur et une attribution de copie uniquement ce pointeur.</span><span class="sxs-lookup"><span data-stu-id="2746f-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>

### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="2746f-105">Pour assigner un tableau à un autre tableau</span><span class="sxs-lookup"><span data-stu-id="2746f-105">To assign one array to another array</span></span>

1. <span data-ttu-id="2746f-106">Assurez-vous que les deux tableaux ont le même rang (nombre de dimensions) et les types de données d’élément compatibles.</span><span class="sxs-lookup"><span data-stu-id="2746f-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>

2. <span data-ttu-id="2746f-107">Utilisez une instruction d’assignation standard pour assigner le tableau source vers le tableau de destination.</span><span class="sxs-lookup"><span data-stu-id="2746f-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="2746f-108">Ne suivez pas les noms du tableau de parenthèses.</span><span class="sxs-lookup"><span data-stu-id="2746f-108">Do not follow either array name with parentheses.</span></span>

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

<span data-ttu-id="2746f-109">Lorsque vous affectez un tableau à un autre, les règles suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="2746f-109">When you assign one array to another, the following rules apply:</span></span>

- <span data-ttu-id="2746f-110">**Rangs identiques.**</span><span class="sxs-lookup"><span data-stu-id="2746f-110">**Equal Ranks.**</span></span> <span data-ttu-id="2746f-111">Le rang (nombre de dimensions) du tableau de destination doit être identique à celui du tableau source.</span><span class="sxs-lookup"><span data-stu-id="2746f-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>

  <span data-ttu-id="2746f-112">Condition les rangs des deux tableaux sont égaux, les dimensions n’avez pas besoin être égale.</span><span class="sxs-lookup"><span data-stu-id="2746f-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="2746f-113">Le nombre d’éléments dans une dimension donnée peut changer lors de l’attribution.</span><span class="sxs-lookup"><span data-stu-id="2746f-113">The number of elements in a given dimension can change during assignment.</span></span>

- <span data-ttu-id="2746f-114">**Types d’éléments.**</span><span class="sxs-lookup"><span data-stu-id="2746f-114">**Element Types.**</span></span> <span data-ttu-id="2746f-115">Soit les deux tableaux doivent avoir *type référence* éléments ou les deux tableaux doit avoir *type valeur* éléments.</span><span class="sxs-lookup"><span data-stu-id="2746f-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="2746f-116">Pour plus d'informations, consultez [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="2746f-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>

  - <span data-ttu-id="2746f-117">Si les deux tableaux ont des éléments de type valeur, les types de données d’élément doivent être exactement le même.</span><span class="sxs-lookup"><span data-stu-id="2746f-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="2746f-118">La seule exception à cela est que vous pouvez assigner un tableau de `Enum` éléments vers un tableau de type de base de qui `Enum`.</span><span class="sxs-lookup"><span data-stu-id="2746f-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>

  - <span data-ttu-id="2746f-119">Si les deux tableaux ont des éléments de type référence, le type d’élément source doit dériver du type d’élément de destination.</span><span class="sxs-lookup"><span data-stu-id="2746f-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="2746f-120">Lorsque c’est le cas, les deux tableaux ont la même relation d’héritage que leurs éléments.</span><span class="sxs-lookup"><span data-stu-id="2746f-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="2746f-121">Il s’agit *covariance de tableau*.</span><span class="sxs-lookup"><span data-stu-id="2746f-121">This is called *array covariance*.</span></span>

<span data-ttu-id="2746f-122">Le compilateur signale une erreur si les règles ci-dessus sont violées, par exemple si les types de données ne sont pas compatibles ou les rangs sont inégaux.</span><span class="sxs-lookup"><span data-stu-id="2746f-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="2746f-123">Vous pouvez ajouter à votre code pour vous assurer que les tableaux sont compatibles avant de tenter une affectation de gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="2746f-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="2746f-124">Vous pouvez également utiliser le [opérateur TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md) mot clé si vous souhaitez éviter de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="2746f-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="2746f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2746f-125">See also</span></span>

- [<span data-ttu-id="2746f-126">Tableaux</span><span class="sxs-lookup"><span data-stu-id="2746f-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="2746f-127">Dépannage des tableaux</span><span class="sxs-lookup"><span data-stu-id="2746f-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="2746f-128">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="2746f-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="2746f-129">Conversions de tableau</span><span class="sxs-lookup"><span data-stu-id="2746f-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
