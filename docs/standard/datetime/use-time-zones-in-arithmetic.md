---
title: 'Procédure : utiliser des fuseaux horaires en arithmétique de date et heure'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d504aa9ad7d6e4084192a2434ac408e8fa7a041
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588540"
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="97dd3-102">Procédure : utiliser des fuseaux horaires en arithmétique de date et heure</span><span class="sxs-lookup"><span data-stu-id="97dd3-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="97dd3-103">En règle générale, lorsque vous effectuer la date et l’heure à l’aide d’arithmétique <xref:System.DateTime> ou <xref:System.DateTimeOffset> valeurs, le résultat ne reflète pas les règles d’ajustement de fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="97dd3-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="97dd3-104">Cela est vrai même lorsque le fuseau horaire de la valeur de date et d’heure est clairement identifiable (par exemple, lors de la <xref:System.DateTime.Kind%2A> propriété est définie sur <xref:System.DateTimeKind.Local>).</span><span class="sxs-lookup"><span data-stu-id="97dd3-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="97dd3-105">Cette rubrique montre comment effectuer des opérations arithmétiques sur les valeurs de date et d’heure qui appartiennent à un fuseau horaire particulier.</span><span class="sxs-lookup"><span data-stu-id="97dd3-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="97dd3-106">Les résultats de ces opérations arithmétiques reflètent les règles d’ajustement du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="97dd3-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="97dd3-107">Pour appliquer des règles d’ajustement dans les opérations arithmétiques de date et d’heure</span><span class="sxs-lookup"><span data-stu-id="97dd3-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="97dd3-108">Implémentez une méthode de couplage étroit d’une valeur de date et d’heure avec le fuseau horaire auquel elle appartient.</span><span class="sxs-lookup"><span data-stu-id="97dd3-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="97dd3-109">Par exemple, déclarez une structure qui inclut à la fois la valeur de date et d’heure et son fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="97dd3-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="97dd3-110">L’exemple suivant utilise cette approche pour lier un <xref:System.DateTime> valeur avec son fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="97dd3-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="97dd3-111">Convertir une heure en temps universel coordonné (UTC) en appelant le <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> méthode ou le <xref:System.TimeZoneInfo.ConvertTime%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="97dd3-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="97dd3-112">Effectuez l’opération arithmétique sur l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="97dd3-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="97dd3-113">Convertissez l’heure UTC au fuseau horaire associé de l’heure d’origine en appelant le <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="97dd3-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="97dd3-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="97dd3-114">Example</span></span>

<span data-ttu-id="97dd3-115">L’exemple suivant ajoute deux heures et trente minutes à 9 mars 2008, à 1:30 A.M.,</span><span class="sxs-lookup"><span data-stu-id="97dd3-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="97dd3-116">heure du Centre des États-Unis.</span><span class="sxs-lookup"><span data-stu-id="97dd3-116">Central Standard Time.</span></span> <span data-ttu-id="97dd3-117">Le passage du fuseau horaire à l’heure d’été se produit trente minutes plus tard, à 2:00,</span><span class="sxs-lookup"><span data-stu-id="97dd3-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="97dd3-118">le 9 mars 2008.</span><span class="sxs-lookup"><span data-stu-id="97dd3-118">on March 9, 2008.</span></span> <span data-ttu-id="97dd3-119">Étant donné que cet exemple suit les quatre étapes répertoriées à la section précédente, il signale correctement l’heure obtenue, soit 5:00,</span><span class="sxs-lookup"><span data-stu-id="97dd3-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="97dd3-120">le 9 mars 2008.</span><span class="sxs-lookup"><span data-stu-id="97dd3-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="97dd3-121">Les deux <xref:System.DateTime> et <xref:System.DateTimeOffset> valeurs sont dissociées de tout fuseau horaire auquel elles peuvent appartenir.</span><span class="sxs-lookup"><span data-stu-id="97dd3-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="97dd3-122">Pour effectuer des opérations arithmétiques de date et d’heure d’une manière qui applique automatiquement les règles d’ajustement d’un fuseau horaire, le fuseau horaire auquel toute valeur de date et d’heure appartient doit être identifiable immédiatement.</span><span class="sxs-lookup"><span data-stu-id="97dd3-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="97dd3-123">Cela signifie qu’une date et une heure et leur fuseau horaire associé doivent être étroitement couplés.</span><span class="sxs-lookup"><span data-stu-id="97dd3-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="97dd3-124">Il existe plusieurs manières de procéder, dont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="97dd3-124">There are several ways to do this, which include the following:</span></span>

* <span data-ttu-id="97dd3-125">Supposez que toutes les heures utilisées dans une application appartiennent à un fuseau horaire particulier.</span><span class="sxs-lookup"><span data-stu-id="97dd3-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="97dd3-126">Bien qu’appropriée dans certains cas, cette approche présente une souplesse limitée et une portabilité éventuellement limitée.</span><span class="sxs-lookup"><span data-stu-id="97dd3-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

* <span data-ttu-id="97dd3-127">Définissez un type qui couple étroitement une valeur de date et d’heure avec son fuseau horaire associé en incluant les deux comme champs.</span><span class="sxs-lookup"><span data-stu-id="97dd3-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="97dd3-128">Cette approche est utilisée dans l’exemple de code qui définit une structure pour stocker la date et l’heure, et le fuseau horaire, dans deux champs membres.</span><span class="sxs-lookup"><span data-stu-id="97dd3-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="97dd3-129">L’exemple montre comment effectuer des opérations arithmétiques sur <xref:System.DateTime> valeurs afin que les règles d’ajustement de fuseau horaire sont appliquées au résultat.</span><span class="sxs-lookup"><span data-stu-id="97dd3-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="97dd3-130">Toutefois, <xref:System.DateTimeOffset> valeurs peuvent être utilisées tout aussi facilement.</span><span class="sxs-lookup"><span data-stu-id="97dd3-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="97dd3-131">L’exemple suivant illustre la façon dont le code dans l’exemple d’origine peut être adapté pour utiliser <xref:System.DateTimeOffset> au lieu de <xref:System.DateTime> valeurs.</span><span class="sxs-lookup"><span data-stu-id="97dd3-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="97dd3-132">Notez que si cet ajout est effectué simplement sur le <xref:System.DateTimeOffset> valeur sans tout d’abord sa conversion en heure UTC, le résultat indique le point correct dans le temps, mais son décalage ne reflète pas celui du fuseau horaire désigné pour cette heure.</span><span class="sxs-lookup"><span data-stu-id="97dd3-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="97dd3-133">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="97dd3-133">Compiling the code</span></span>

<span data-ttu-id="97dd3-134">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="97dd3-134">This example requires:</span></span>

* <span data-ttu-id="97dd3-135">Que l'espace de noms <xref:System> soit importé avec l'instruction `using` (obligatoire en C#).</span><span class="sxs-lookup"><span data-stu-id="97dd3-135">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="97dd3-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97dd3-136">See also</span></span>

- [<span data-ttu-id="97dd3-137">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="97dd3-137">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="97dd3-138">Exécution d’opérations arithmétiques avec des dates et heures</span><span class="sxs-lookup"><span data-stu-id="97dd3-138">Performing arithmetic operations with dates and times</span></span>](../../../docs/standard/datetime/performing-arithmetic-operations.md)
