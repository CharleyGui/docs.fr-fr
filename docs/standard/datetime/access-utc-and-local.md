---
title: 'Procédure : accéder aux objets de fuseau horaire UTC et local prédéfinis'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET], retrieving
- time zones [.NET], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
ms.openlocfilehash: 598cd631fab1ddc115bc6153580351b1dc14d5bf
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063883"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="3b6cd-102">Procédure : accéder aux objets de fuseau horaire UTC et local prédéfinis</span><span class="sxs-lookup"><span data-stu-id="3b6cd-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="3b6cd-103">La <xref:System.TimeZoneInfo> classe fournit deux propriétés, <xref:System.TimeZoneInfo.Utc%2A> et <xref:System.TimeZoneInfo.Local%2A> , qui permettent à votre code d’accéder à des objets de fuseau horaire prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="3b6cd-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="3b6cd-104">Cette rubrique explique comment accéder aux objets <xref:System.TimeZoneInfo> retournés par ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="3b6cd-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="3b6cd-105">Pour accéder à l’objet TimeZoneInfo de temps universel coordonné (UTC)</span><span class="sxs-lookup"><span data-stu-id="3b6cd-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="3b6cd-106">Utilisez la `static` `Shared` propriété (dans Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> pour accéder au temps universel coordonné.</span><span class="sxs-lookup"><span data-stu-id="3b6cd-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="3b6cd-107">Au lieu d’assigner l' <xref:System.TimeZoneInfo> objet retourné par la propriété à une variable objet, continuez à accéder au temps universel coordonné via la <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="3b6cd-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="3b6cd-108">Pour accéder au fuseau horaire local</span><span class="sxs-lookup"><span data-stu-id="3b6cd-108">To access the local time zone</span></span>

1. <span data-ttu-id="3b6cd-109">Utilisez la `static` `Shared` propriété (dans Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> pour accéder au fuseau horaire du système local.</span><span class="sxs-lookup"><span data-stu-id="3b6cd-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="3b6cd-110">Au lieu d’assigner l' <xref:System.TimeZoneInfo> objet retourné par la propriété à une variable objet, continuez à accéder au fuseau horaire local via la <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="3b6cd-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="3b6cd-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b6cd-111">Example</span></span>

<span data-ttu-id="3b6cd-112">Le code suivant utilise les <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Propriétés et pour convertir une heure du fuseau horaire de l’est des États-Unis et du Canada, ainsi que pour afficher le nom du fuseau horaire sur la console.</span><span class="sxs-lookup"><span data-stu-id="3b6cd-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="3b6cd-113">Vous devez toujours accéder au fuseau horaire local via la <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété plutôt que d’attribuer le fuseau horaire local à une <xref:System.TimeZoneInfo> variable objet.</span><span class="sxs-lookup"><span data-stu-id="3b6cd-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="3b6cd-114">De même, vous devez toujours accéder au temps universel coordonné via la <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriété plutôt que d’affecter la zone UTC à une <xref:System.TimeZoneInfo> variable objet.</span><span class="sxs-lookup"><span data-stu-id="3b6cd-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="3b6cd-115">Cela empêche la <xref:System.TimeZoneInfo> variable d’objet d’être invalidée par un appel à la <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="3b6cd-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="3b6cd-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3b6cd-116">Compiling the code</span></span>

<span data-ttu-id="3b6cd-117">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="3b6cd-117">This example requires:</span></span>

- <span data-ttu-id="3b6cd-118">Que l' <xref:System> espace de noms soit importé avec l' `using` instruction (obligatoire dans le code C#).</span><span class="sxs-lookup"><span data-stu-id="3b6cd-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="3b6cd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b6cd-119">See also</span></span>

- [<span data-ttu-id="3b6cd-120">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="3b6cd-120">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="3b6cd-121">Recherche des fuseaux horaires définis sur un système local</span><span class="sxs-lookup"><span data-stu-id="3b6cd-121">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="3b6cd-122">Comment : instancier un objet TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="3b6cd-122">How to: Instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)
