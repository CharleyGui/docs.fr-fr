---
title: Single (type de données)
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
ms.openlocfilehash: ecb0f5f6416a2dd4ddd6888cb80ed3ac11ee58df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415529"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="110db-102">Single, type de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="110db-102">Single Data Type (Visual Basic)</span></span>

<span data-ttu-id="110db-103">Contient les nombres à virgule flottante simple précision IEEE 32 bits (4 octets) signés dont la valeur est comprise entre-3.4028235 E + 38 et-1.401298 E-45 pour les valeurs négatives et de 1.401298 E-45 à 3.4028235 E + 38 pour les valeurs positives.</span><span class="sxs-lookup"><span data-stu-id="110db-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="110db-104">Les nombres à simple précision stockent une approximation d’un nombre réel.</span><span class="sxs-lookup"><span data-stu-id="110db-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="110db-105">Notes</span><span class="sxs-lookup"><span data-stu-id="110db-105">Remarks</span></span>  

 <span data-ttu-id="110db-106">Utilisez le `Single` type de données pour contenir des valeurs à virgule flottante qui ne nécessitent pas la largeur complète des données `Double` .</span><span class="sxs-lookup"><span data-stu-id="110db-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="110db-107">Dans certains cas, l’common language runtime peut être en mesure de `Single` regrouper vos variables de près et d’économiser la consommation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="110db-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="110db-108">La valeur par défaut de `Single` est 0.</span><span class="sxs-lookup"><span data-stu-id="110db-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="110db-109">Conseils de programmation</span><span class="sxs-lookup"><span data-stu-id="110db-109">Programming Tips</span></span>  
  
- <span data-ttu-id="110db-110">**Précision.**</span><span class="sxs-lookup"><span data-stu-id="110db-110">**Precision.**</span></span> <span data-ttu-id="110db-111">Lorsque vous travaillez avec des nombres à virgule flottante, gardez à l’esprit qu’ils n’ont pas toujours une représentation précise en mémoire.</span><span class="sxs-lookup"><span data-stu-id="110db-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="110db-112">Cela peut entraîner des résultats inattendus de certaines opérations, telles que la comparaison de valeurs et l' `Mod` opérateur.</span><span class="sxs-lookup"><span data-stu-id="110db-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="110db-113">Pour plus d’informations, consultez [Dépannage des types de données](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="110db-113">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="110db-114">**Étendue.**</span><span class="sxs-lookup"><span data-stu-id="110db-114">**Widening.**</span></span> <span data-ttu-id="110db-115">Le `Single` type de données s’étend à `Double` .</span><span class="sxs-lookup"><span data-stu-id="110db-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="110db-116">Cela signifie que vous pouvez convertir `Single` en `Double` sans rencontrer d' <xref:System.OverflowException?displayProperty=nameWithType> erreur.</span><span class="sxs-lookup"><span data-stu-id="110db-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="110db-117">**Zéros de fin.**</span><span class="sxs-lookup"><span data-stu-id="110db-117">**Trailing Zeros.**</span></span> <span data-ttu-id="110db-118">Les types de données à virgule flottante n’ont pas de représentation interne des 0 caractères de fin.</span><span class="sxs-lookup"><span data-stu-id="110db-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="110db-119">Par exemple, ils ne font pas la distinction entre 4,2000 et 4,2.</span><span class="sxs-lookup"><span data-stu-id="110db-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="110db-120">Par conséquent, les caractères de fin 0 ne s’affichent pas lorsque vous affichez ou imprimez des valeurs à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="110db-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="110db-121">**Caractères de type.**</span><span class="sxs-lookup"><span data-stu-id="110db-121">**Type Characters.**</span></span> <span data-ttu-id="110db-122">L'ajout du caractère de type littéral `F` à un littéral force ce dernier en type de données `Single`.</span><span class="sxs-lookup"><span data-stu-id="110db-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="110db-123">L'ajout du caractère de type identificateur `!` à un identificateur force ce dernier en type `Single`.</span><span class="sxs-lookup"><span data-stu-id="110db-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="110db-124">**Type .NET Framework.**</span><span class="sxs-lookup"><span data-stu-id="110db-124">**Framework Type.**</span></span> <span data-ttu-id="110db-125">Le type correspondant dans le .NET Framework est la structure <xref:System.Single?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="110db-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="110db-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="110db-126">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="110db-127">Types de données</span><span class="sxs-lookup"><span data-stu-id="110db-127">Data Types</span></span>](index.md)
- [<span data-ttu-id="110db-128">Décimal (type de données)</span><span class="sxs-lookup"><span data-stu-id="110db-128">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="110db-129">Double (type de données)</span><span class="sxs-lookup"><span data-stu-id="110db-129">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="110db-130">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="110db-130">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="110db-131">Liste des conversions</span><span class="sxs-lookup"><span data-stu-id="110db-131">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="110db-132">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="110db-132">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="110db-133">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="110db-133">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
