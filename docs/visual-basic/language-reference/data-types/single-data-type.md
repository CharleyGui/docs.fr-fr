---
title: Single, type de données
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 60a688c510f6e36dca5809566b37a388429e18c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343919"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="5869c-102">Single, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5869c-102">Single Data Type (Visual Basic)</span></span>

<span data-ttu-id="5869c-103">Contient les nombres à virgule flottante simple précision IEEE 32 bits (4 octets) signés dont la valeur est comprise entre-3.4028235 E + 38 et-1.401298 E-45 pour les valeurs négatives et de 1.401298 E-45 à 3.4028235 E + 38 pour les valeurs positives.</span><span class="sxs-lookup"><span data-stu-id="5869c-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="5869c-104">Les nombres à simple précision stockent une approximation d’un nombre réel.</span><span class="sxs-lookup"><span data-stu-id="5869c-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5869c-105">Notes</span><span class="sxs-lookup"><span data-stu-id="5869c-105">Remarks</span></span>  

 <span data-ttu-id="5869c-106">Utilisez le type de données `Single` pour contenir des valeurs à virgule flottante qui ne nécessitent pas la largeur totale des données de `Double`.</span><span class="sxs-lookup"><span data-stu-id="5869c-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="5869c-107">Dans certains cas, l’common language runtime peut être en mesure de regrouper vos variables de `Single` étroitement et de réduire la consommation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="5869c-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="5869c-108">La valeur par défaut de `Single` est 0.</span><span class="sxs-lookup"><span data-stu-id="5869c-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="5869c-109">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="5869c-109">Programming Tips</span></span>  
  
- <span data-ttu-id="5869c-110">**Précision.**</span><span class="sxs-lookup"><span data-stu-id="5869c-110">**Precision.**</span></span> <span data-ttu-id="5869c-111">Lorsque vous travaillez avec des nombres à virgule flottante, gardez à l’esprit qu’ils n’ont pas toujours une représentation précise en mémoire.</span><span class="sxs-lookup"><span data-stu-id="5869c-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="5869c-112">Cela peut entraîner des résultats inattendus de certaines opérations, telles que la comparaison de valeurs et l’opérateur `Mod`.</span><span class="sxs-lookup"><span data-stu-id="5869c-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="5869c-113">Pour plus d’informations, consultez [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="5869c-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="5869c-114">**Étendue.**</span><span class="sxs-lookup"><span data-stu-id="5869c-114">**Widening.**</span></span> <span data-ttu-id="5869c-115">Le type de données `Single` s’étend à `Double`.</span><span class="sxs-lookup"><span data-stu-id="5869c-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="5869c-116">Cela signifie que vous pouvez convertir `Single` en `Double` sans rencontrer d’erreur <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5869c-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="5869c-117">**Zéros de fin.**</span><span class="sxs-lookup"><span data-stu-id="5869c-117">**Trailing Zeros.**</span></span> <span data-ttu-id="5869c-118">Les types de données à virgule flottante n’ont pas de représentation interne des 0 caractères de fin.</span><span class="sxs-lookup"><span data-stu-id="5869c-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="5869c-119">Par exemple, ils ne font pas la distinction entre 4,2000 et 4,2.</span><span class="sxs-lookup"><span data-stu-id="5869c-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="5869c-120">Par conséquent, les caractères de fin 0 ne s’affichent pas lorsque vous affichez ou imprimez des valeurs à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="5869c-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="5869c-121">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="5869c-121">**Type Characters.**</span></span> <span data-ttu-id="5869c-122">L'ajout du caractère de type littéral `F` à un littéral force ce dernier en type de données `Single`.</span><span class="sxs-lookup"><span data-stu-id="5869c-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="5869c-123">L'ajout du caractère de type identificateur `!` à un identificateur force ce dernier en type `Single`.</span><span class="sxs-lookup"><span data-stu-id="5869c-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="5869c-124">**Type de Framework.**</span><span class="sxs-lookup"><span data-stu-id="5869c-124">**Framework Type.**</span></span> <span data-ttu-id="5869c-125">Le type correspondant dans le .NET Framework est la structure <xref:System.Single?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5869c-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5869c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5869c-126">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="5869c-127">Types de données</span><span class="sxs-lookup"><span data-stu-id="5869c-127">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="5869c-128">Decimal (type de données)</span><span class="sxs-lookup"><span data-stu-id="5869c-128">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [<span data-ttu-id="5869c-129">Double (type de données)</span><span class="sxs-lookup"><span data-stu-id="5869c-129">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [<span data-ttu-id="5869c-130">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="5869c-130">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="5869c-131">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="5869c-131">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="5869c-132">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="5869c-132">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="5869c-133">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="5869c-133">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
