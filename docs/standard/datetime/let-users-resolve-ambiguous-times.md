---
title: 'Procédure : permettre aux utilisateurs de résoudre des heures ambiguës'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf97f1a08c6df13ce639466fc07472926c63987f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106621"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="612fa-102">Procédure : permettre aux utilisateurs de résoudre des heures ambiguës</span><span class="sxs-lookup"><span data-stu-id="612fa-102">How to: Let users resolve ambiguous times</span></span>

<span data-ttu-id="612fa-103">Une heure ambiguë est une heure qui correspond à plusieurs heures UTC.</span><span class="sxs-lookup"><span data-stu-id="612fa-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="612fa-104">Cela se produit quand l’heure de l’horloge est retardée, comme lors du passage de l’heure d’été à l'heure d'hiver dans un fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="612fa-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="612fa-105">Quand vous gérez une heure ambiguë, vous pouvez procéder de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="612fa-105">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="612fa-106">Si l’heure ambiguë est un élément de données entré par l’utilisateur, vous pouvez laisser l’utilisateur résoudre l’ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="612fa-106">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

- <span data-ttu-id="612fa-107">Proposez une méthode de mappage à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="612fa-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="612fa-108">Par exemple, vous pouvez supposer qu’une heure ambiguë est toujours exprimée à l'heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="612fa-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="612fa-109">Cette rubrique montre comment permettre à un utilisateur de résoudre une heure ambiguë.</span><span class="sxs-lookup"><span data-stu-id="612fa-109">This topic shows how to let a user resolve an ambiguous time.</span></span>

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="612fa-110">Pour permettre à un utilisateur de résoudre une heure ambiguë</span><span class="sxs-lookup"><span data-stu-id="612fa-110">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="612fa-111">Obtenez la date et l’heure entrées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="612fa-111">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="612fa-112">Appelez la <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> méthode pour déterminer si l’heure est ambiguë.</span><span class="sxs-lookup"><span data-stu-id="612fa-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="612fa-113">Si l’heure est ambiguë, appelez la méthode <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> pour récupérer un tableau d'objets <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="612fa-113">If the time is ambiguous, call the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects.</span></span> <span data-ttu-id="612fa-114">Chaque élément du tableau contient un décalage UTC auquel l’heure ambiguë peut être mappée.</span><span class="sxs-lookup"><span data-stu-id="612fa-114">Each element in the array contains a UTC offset that the ambiguous time can map to.</span></span>

4. <span data-ttu-id="612fa-115">Laissez l’utilisateur sélectionner le décalage souhaité.</span><span class="sxs-lookup"><span data-stu-id="612fa-115">Let the user select the desired offset.</span></span>

5. <span data-ttu-id="612fa-116">Obtenez la date et l’heure UTC en soustrayant de l’heure locale le décalage sélectionné par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="612fa-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

6. <span data-ttu-id="612fa-117">Appelez la `static` méthode`Shared` (en Visual Basic .NET <xref:System.DateTime.SpecifyKind%2A> ) pour affecter à <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>la propriété de <xref:System.DateTime.Kind%2A> la valeur de date et d’heure UTC la valeur.</span><span class="sxs-lookup"><span data-stu-id="612fa-117">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="612fa-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="612fa-118">Example</span></span>

<span data-ttu-id="612fa-119">L’exemple suivant invite l’utilisateur à entrer une date et une heure et, si cette dernière est ambiguë, permet à l’utilisateur de sélectionner l’heure UTC à laquelle l’heure ambiguë correspond.</span><span class="sxs-lookup"><span data-stu-id="612fa-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span>

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

<span data-ttu-id="612fa-120">Le cœur de l’exemple de code utilise un tableau d'objets <xref:System.TimeSpan> pour indiquer les décalages possibles de l’heure ambiguë par rapport à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="612fa-120">The core of the example code uses an array of <xref:System.TimeSpan> objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="612fa-121">Toutefois, ces décalages n’ont probablement aucune signification pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="612fa-121">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="612fa-122">Pour clarifier les choses, le code note également si un décalage représente l’heure d’hiver du fuseau horaire local ou son heure d’été.</span><span class="sxs-lookup"><span data-stu-id="612fa-122">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="612fa-123">Le code détermine l'heure qui correspond à l'heure d'hiver et celle qui correspond à l’heure d’été en comparant le décalage avec la valeur de la propriété <xref:System.TimeZoneInfo.BaseUtcOffset%2A>.</span><span class="sxs-lookup"><span data-stu-id="612fa-123">The code determines which time is standard and which time is daylight by comparing the offset with the value of the <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span> <span data-ttu-id="612fa-124">Cette propriété indique la différence entre l’heure UTC et l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="612fa-124">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="612fa-125">Dans cet exemple, toutes les références au fuseau horaire local sont faites par le biais de la propriété <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ; le fuseau horaire local n’est jamais affecté à une variable objet.</span><span class="sxs-lookup"><span data-stu-id="612fa-125">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="612fa-126">Cette pratique est recommandée, car un appel à la méthode <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> invalide tous les objets auxquels le fuseau horaire est affecté.</span><span class="sxs-lookup"><span data-stu-id="612fa-126">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="612fa-127">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="612fa-127">Compiling the code</span></span>

<span data-ttu-id="612fa-128">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="612fa-128">This example requires:</span></span>

- <span data-ttu-id="612fa-129">Que l'espace de noms <xref:System> soit importé avec l'instruction `using` (obligatoire en C#).</span><span class="sxs-lookup"><span data-stu-id="612fa-129">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="612fa-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="612fa-130">See also</span></span>

- [<span data-ttu-id="612fa-131">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="612fa-131">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="612fa-132">Guide pratique pour Résoudre les heures ambiguës</span><span class="sxs-lookup"><span data-stu-id="612fa-132">How to: Resolve ambiguous times</span></span>](../../../docs/standard/datetime/resolve-ambiguous-times.md)
