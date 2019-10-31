---
title: 'Comment : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
ms.openlocfilehash: ef22753d9934a52d955412a4493b608f265519aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132602"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="7ad65-102">Comment : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis</span><span class="sxs-lookup"><span data-stu-id="7ad65-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="7ad65-103">La classe <xref:System.TimeZoneInfo> fournit deux propriétés, <xref:System.TimeZoneInfo.Utc%2A> et <xref:System.TimeZoneInfo.Local%2A>, qui permettent à votre code d’accéder à des objets de fuseau horaire prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="7ad65-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="7ad65-104">Cette rubrique explique comment accéder aux objets <xref:System.TimeZoneInfo> retournés par ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="7ad65-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="7ad65-105">Pour accéder à l’objet TimeZoneInfo de temps universel coordonné (UTC)</span><span class="sxs-lookup"><span data-stu-id="7ad65-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="7ad65-106">Utilisez la propriété `static` (`Shared` dans Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> pour accéder au temps universel coordonné.</span><span class="sxs-lookup"><span data-stu-id="7ad65-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="7ad65-107">Au lieu d’assigner l’objet <xref:System.TimeZoneInfo> retourné par la propriété à une variable objet, continuez à accéder au temps universel coordonné via la propriété <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ad65-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="7ad65-108">Pour accéder au fuseau horaire local</span><span class="sxs-lookup"><span data-stu-id="7ad65-108">To access the local time zone</span></span>

1. <span data-ttu-id="7ad65-109">Utilisez la propriété `static` (`Shared` dans Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> pour accéder au fuseau horaire du système local.</span><span class="sxs-lookup"><span data-stu-id="7ad65-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="7ad65-110">Au lieu d’assigner l’objet <xref:System.TimeZoneInfo> retourné par la propriété à une variable objet, continuez à accéder au fuseau horaire local via la propriété <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ad65-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="7ad65-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="7ad65-111">Example</span></span>

<span data-ttu-id="7ad65-112">Le code suivant utilise les propriétés <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> et <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> pour convertir une heure du fuseau horaire de l’est des États-Unis et du Canada, ainsi que pour afficher le nom du fuseau horaire sur la console.</span><span class="sxs-lookup"><span data-stu-id="7ad65-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="7ad65-113">Vous devez toujours accéder au fuseau horaire local via la propriété <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> plutôt que d’attribuer le fuseau horaire local à une variable objet <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="7ad65-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="7ad65-114">De même, vous devez toujours accéder au temps universel coordonné via la propriété <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> plutôt que d’affecter la zone UTC à une variable objet <xref:System.TimeZoneInfo>.</span><span class="sxs-lookup"><span data-stu-id="7ad65-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="7ad65-115">Cela empêche la variable d’objet <xref:System.TimeZoneInfo> d’être invalidée par un appel à la méthode <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ad65-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="7ad65-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="7ad65-116">Compiling the code</span></span>

<span data-ttu-id="7ad65-117">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="7ad65-117">This example requires:</span></span>

- <span data-ttu-id="7ad65-118">L’importation de l’espace de noms <xref:System> avec l’instruction `using` ( C# obligatoire dans le code).</span><span class="sxs-lookup"><span data-stu-id="7ad65-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ad65-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ad65-119">See also</span></span>

- [<span data-ttu-id="7ad65-120">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="7ad65-120">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="7ad65-121">Recherche des fuseaux horaires définis sur un système local</span><span class="sxs-lookup"><span data-stu-id="7ad65-121">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="7ad65-122">Guide pratique pour instancier un objet TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="7ad65-122">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)
