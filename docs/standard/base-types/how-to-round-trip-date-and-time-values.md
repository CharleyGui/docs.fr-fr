---
title: "Comment : effectuer un aller-retour de valeurs de date et d'heure"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET], round-trip values
- time zones [.NET], round-trip date and time values
- time [.NET], round-trip values
- formatting strings [.NET], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
ms.openlocfilehash: 4dce882e29afd5084dc84d3e176e6121c55f4af8
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889086"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="e2162-102">Comment : effectuer un aller-retour de valeurs de date et d'heure</span><span class="sxs-lookup"><span data-stu-id="e2162-102">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="e2162-103">Dans de nombreuses applications, une valeur de date et d’heure est destinée à identifier clairement un point unique dans le temps.</span><span class="sxs-lookup"><span data-stu-id="e2162-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="e2162-104">Cet article explique comment enregistrer et restaurer une valeur <xref:System.DateTime> , une valeur <xref:System.DateTimeOffset> et une valeur de date et d’heure avec des informations de fuseau horaire afin que la valeur restaurée identifie la même heure que la valeur enregistrée.</span><span class="sxs-lookup"><span data-stu-id="e2162-104">This article shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

## <a name="round-trip-a-datetime-value"></a><span data-ttu-id="e2162-105">Aller-retour d’une valeur DateTime</span><span class="sxs-lookup"><span data-stu-id="e2162-105">Round-trip a DateTime value</span></span>

1. <span data-ttu-id="e2162-106">Convertissez la valeur <xref:System.DateTime> en sa représentation sous forme de chaîne en appelant la méthode <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> avec le spécificateur de format « o ».</span><span class="sxs-lookup"><span data-stu-id="e2162-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="e2162-107">Enregistrez la représentation sous forme de chaîne de la valeur <xref:System.DateTime> dans un fichier ou passez-la dans un processus, un domaine d’application ou une limite d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e2162-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="e2162-108">Récupérez la chaîne qui représente la valeur <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="e2162-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="e2162-109">Appelez la méthode <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> et passez <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> en tant que valeur du paramètre `styles`.</span><span class="sxs-lookup"><span data-stu-id="e2162-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="e2162-110">L’exemple suivant montre comment effectuer un aller-retour d’une valeur <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="e2162-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="e2162-111">Durant l’aller-retour d’une valeur <xref:System.DateTime>, cette technique permet de conserver correctement l’heure pour toutes les heures locales et universelles.</span><span class="sxs-lookup"><span data-stu-id="e2162-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="e2162-112">Par exemple, si une <xref:System.DateTime> valeur locale est enregistrée sur un système situé dans le fuseau horaire Pacifique (États-Unis) et qu’elle est restaurée sur un système situé dans le fuseau horaire du Centre des États-Unis, la date et l’heure de restauration sont deux heures après l’heure d’origine, ce qui reflète la différence de temps entre les deux fuseaux horaires.</span><span class="sxs-lookup"><span data-stu-id="e2162-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="e2162-113">En revanche, cette technique n’est pas nécessairement exacte pour les heures non spécifiées.</span><span class="sxs-lookup"><span data-stu-id="e2162-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="e2162-114">Toutes les valeurs <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> est <xref:System.DateTimeKind.Unspecified> sont traitées comme s’il s’agissait d’heures locales.</span><span class="sxs-lookup"><span data-stu-id="e2162-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="e2162-115">S’il ne s’agit pas d’une heure locale, le <xref:System.DateTime> n’identifie pas correctement le point correct dans le temps.</span><span class="sxs-lookup"><span data-stu-id="e2162-115">If it's not a local time, the <xref:System.DateTime> doesn't successfully identify the correct point in time.</span></span> <span data-ttu-id="e2162-116">La solution pour contourner cette limitation consiste à associer étroitement une valeur de date et d’heure avec son fuseau horaire pour l’opération d’enregistrement et de restauration.</span><span class="sxs-lookup"><span data-stu-id="e2162-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

## <a name="round-trip-a-datetimeoffset-value"></a><span data-ttu-id="e2162-117">Aller-retour d’une valeur DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="e2162-117">Round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="e2162-118">Convertissez la valeur <xref:System.DateTimeOffset> en sa représentation sous forme de chaîne en appelant la méthode <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> avec le spécificateur de format « o ».</span><span class="sxs-lookup"><span data-stu-id="e2162-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="e2162-119">Enregistrez la représentation sous forme de chaîne de la valeur <xref:System.DateTimeOffset> dans un fichier ou passez-la dans un processus, un domaine d’application ou une limite d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e2162-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="e2162-120">Récupérez la chaîne qui représente la valeur <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="e2162-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="e2162-121">Appelez la méthode <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> et passez <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> en tant que valeur du paramètre `styles`.</span><span class="sxs-lookup"><span data-stu-id="e2162-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="e2162-122">L’exemple suivant montre comment effectuer un aller-retour d’une valeur <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="e2162-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="e2162-123">Cette technique identifie toujours clairement une valeur <xref:System.DateTimeOffset> comme point unique dans le temps.</span><span class="sxs-lookup"><span data-stu-id="e2162-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="e2162-124">La valeur peut ensuite être convertie en temps universel coordonné (UTC) en appelant la méthode <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType>, ou convertie en heure dans un fuseau horaire particulier en appelant la méthode <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> ou <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e2162-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e2162-125">La principale limitation de cette technique est que les opérations arithmétiques de date et heure, effectuées sur une valeur <xref:System.DateTimeOffset> qui représente l’heure dans un fuseau horaire particulier, risquent de ne pas produire des résultats exacts pour ce fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="e2162-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="e2162-126">En effet, quand une valeur <xref:System.DateTimeOffset> est instanciée, elle est dissociée de son fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="e2162-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="e2162-127">Ainsi, les règles d’ajustement de ce fuseau horaire ne sont plus applicables quand vous effectuez des calculs de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="e2162-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="e2162-128">Vous pouvez contourner ce problème en définissant un type personnalisé qui inclut à la fois une valeur de date et heure et son fuseau horaire correspondant.</span><span class="sxs-lookup"><span data-stu-id="e2162-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="e2162-129">Aller-retour d’une valeur de date et d’heure avec son fuseau horaire</span><span class="sxs-lookup"><span data-stu-id="e2162-129">Round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="e2162-130">Définissez une classe ou une structure avec deux champs.</span><span class="sxs-lookup"><span data-stu-id="e2162-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="e2162-131">Le premier champ est un objet <xref:System.DateTime> ou <xref:System.DateTimeOffset>, et le second est un objet <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="e2162-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="e2162-132">L’exemple suivant est une version simple de ce type.</span><span class="sxs-lookup"><span data-stu-id="e2162-132">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="e2162-133">Marquez la classe avec l’attribut <xref:System.SerializableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e2162-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="e2162-134">Sérialisez l’objet à l’aide de la méthode <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e2162-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="e2162-135">Restaurez l’objet à l’aide de la méthode <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2162-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="e2162-136">Castez (en C#) ou convertissez (en Visual Basic) l’objet désérialisé en objet du type approprié.</span><span class="sxs-lookup"><span data-stu-id="e2162-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="e2162-137">L’exemple suivant montre comment effectuer un aller-retour d’un objet qui stocke des informations de date et d’heure dans un fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="e2162-137">The following example illustrates how to round-trip an object that stores both time zone and date and time information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="e2162-138">Cette technique devrait toujours refléter clairement le point dans le temps correct avant et après son enregistrement et sa restauration, à condition que l’implémentation de l’objet combiné de date et d’heure et de fuseau horaire ne permette pas à la valeur de date de se désynchroniser de la valeur de fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="e2162-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="e2162-139">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="e2162-139">Compile the code</span></span>

<span data-ttu-id="e2162-140">Ces exemples requièrent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e2162-140">These examples require that:</span></span>

- <span data-ttu-id="e2162-141">Les espaces de noms suivants doivent être importés avec les `using` directives C# ou les `Imports` instructions Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="e2162-141">The following namespaces be imported with C# `using` directives or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="e2162-142"><xref:System> (C# uniquement)</span><span class="sxs-lookup"><span data-stu-id="e2162-142"><xref:System> (C# only)</span></span>

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- <span data-ttu-id="e2162-143">Chaque exemple de code, autre que la `DateInTimeZone` classe, est inclus dans une classe ou un module Visual Basic, encapsulé dans des méthodes et appelé à partir de la `Main` méthode.</span><span class="sxs-lookup"><span data-stu-id="e2162-143">Each code example, other than the `DateInTimeZone` class, be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2162-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2162-144">See also</span></span>

- [<span data-ttu-id="e2162-145">Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="e2162-145">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../datetime/choosing-between-datetime.md)
- [<span data-ttu-id="e2162-146">Chaînes de format de date et d’heure standard</span><span class="sxs-lookup"><span data-stu-id="e2162-146">Standard Date and Time Format Strings</span></span>](standard-date-and-time-format-strings.md)
