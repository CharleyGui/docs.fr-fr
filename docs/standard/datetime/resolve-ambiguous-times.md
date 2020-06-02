---
title: 'Comment : résoudre des heures ambiguës'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: ad69c0984a9d8c01ebd2198486cd0f6492a6116e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281503"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="55925-102">Comment : résoudre des heures ambiguës</span><span class="sxs-lookup"><span data-stu-id="55925-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="55925-103">Une heure ambiguë est une heure qui correspond à plusieurs heures UTC.</span><span class="sxs-lookup"><span data-stu-id="55925-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="55925-104">Cela se produit lorsque l’heure de l’horloge est retardée, comme lors du passage à l’heure d’hiver dans un fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="55925-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="55925-105">Lorsque vous gérez une heure ambiguë, vous pouvez procéder de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="55925-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="55925-106">Proposez une méthode de mappage à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="55925-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="55925-107">Par exemple, vous pouvez supposer qu’une heure ambiguë est toujours exprimée dans le cadre de l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="55925-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

- <span data-ttu-id="55925-108">Si l’heure ambiguë est un élément de données entré par l’utilisateur, vous pouvez laisser l’utilisateur résoudre l’ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="55925-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="55925-109">Cette rubrique montre comment résoudre une heure ambiguë en supposant qu’elle représente l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="55925-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="55925-110">Pour mapper une heure ambiguë à l’heure d’hiver d’un fuseau horaire</span><span class="sxs-lookup"><span data-stu-id="55925-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="55925-111">Appelez la <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> méthode pour déterminer si l’heure est ambiguë.</span><span class="sxs-lookup"><span data-stu-id="55925-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="55925-112">Si l’heure est ambiguë, soustraire l’heure de l' <xref:System.TimeSpan> objet retourné par la propriété du fuseau horaire <xref:System.TimeZoneInfo.BaseUtcOffset%2A> .</span><span class="sxs-lookup"><span data-stu-id="55925-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="55925-113">Appelez la `static` `Shared` méthode (en Visual Basic .net) <xref:System.DateTime.SpecifyKind%2A> pour affecter à la propriété de la valeur de date et d’heure UTC la valeur <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="55925-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="55925-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="55925-114">Example</span></span>

<span data-ttu-id="55925-115">L’exemple suivant montre comment convertir une heure ambiguë en heure UTC en supposant qu’elle représente l’heure d’hiver du fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="55925-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="55925-116">L’exemple se compose d’une méthode nommée `ResolveAmbiguousTime` qui détermine si la <xref:System.DateTime> valeur qui lui est passée est ambiguë.</span><span class="sxs-lookup"><span data-stu-id="55925-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="55925-117">Si la valeur est ambiguë, la méthode retourne une <xref:System.DateTime> valeur qui représente l’heure UTC correspondante.</span><span class="sxs-lookup"><span data-stu-id="55925-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="55925-118">La méthode gère cette conversion en soustrayant la valeur de la propriété du fuseau horaire local <xref:System.TimeZoneInfo.BaseUtcOffset%2A> de l’heure locale.</span><span class="sxs-lookup"><span data-stu-id="55925-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="55925-119">En règle générale, une heure ambiguë est gérée en appelant la <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> méthode pour récupérer un tableau d' <xref:System.TimeSpan> objets qui contiennent les décalages UTC possibles de l’heure ambiguë.</span><span class="sxs-lookup"><span data-stu-id="55925-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="55925-120">Toutefois, cet exemple émet l’hypothèse arbitraire qu’une heure ambiguë devrait toujours être mappée à l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="55925-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="55925-121">La <xref:System.TimeZoneInfo.BaseUtcOffset%2A> propriété retourne le décalage entre l’heure UTC et l’heure d’hiver d’un fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="55925-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="55925-122">Dans cet exemple, toutes les références au fuseau horaire local sont effectuées par le biais de la <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété ; le fuseau horaire local n’est jamais assigné à une variable objet.</span><span class="sxs-lookup"><span data-stu-id="55925-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="55925-123">Il s’agit d’une pratique recommandée, car un appel à la <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> méthode invalide tous les objets auxquels le fuseau horaire local est assigné.</span><span class="sxs-lookup"><span data-stu-id="55925-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="55925-124">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="55925-124">Compiling the code</span></span>

<span data-ttu-id="55925-125">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="55925-125">This example requires:</span></span>

- <span data-ttu-id="55925-126">Que l' <xref:System> espace de noms soit importé avec l' `using` instruction (obligatoire dans le code C#).</span><span class="sxs-lookup"><span data-stu-id="55925-126">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="55925-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55925-127">See also</span></span>

- [<span data-ttu-id="55925-128">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="55925-128">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="55925-129">Comment : permettre aux utilisateurs de résoudre des heures ambiguës</span><span class="sxs-lookup"><span data-stu-id="55925-129">How to: Let users resolve ambiguous times</span></span>](let-users-resolve-ambiguous-times.md)
