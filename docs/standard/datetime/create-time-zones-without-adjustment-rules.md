---
title: 'Procédure : créer des fuseaux horaires sans règles d’ajustement'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], adjustment rule
- time zones [.NET], creating
- adjustment rule [.NET]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
ms.openlocfilehash: e3bce4d915a8d979f043b5c4a49b20ce3e0596c9
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063792"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="3dc66-102">Procédure : créer des fuseaux horaires sans règles d’ajustement</span><span class="sxs-lookup"><span data-stu-id="3dc66-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="3dc66-103">Les informations de fuseau horaire précises requises par une application peuvent ne pas être présentes sur un système particulier pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="3dc66-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="3dc66-104">Le fuseau horaire n’a jamais été défini dans le Registre du système local.</span><span class="sxs-lookup"><span data-stu-id="3dc66-104">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="3dc66-105">Les données relatives au fuseau horaire ont été modifiées ou supprimées du Registre.</span><span class="sxs-lookup"><span data-stu-id="3dc66-105">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="3dc66-106">Le fuseau horaire existe mais il ne contient pas d’informations exactes sur les ajustements de fuseau horaire pour une période historique particulière.</span><span class="sxs-lookup"><span data-stu-id="3dc66-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="3dc66-107">Dans ce cas, vous pouvez appeler la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode pour définir le fuseau horaire requis par votre application.</span><span class="sxs-lookup"><span data-stu-id="3dc66-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="3dc66-108">Vous pouvez utiliser les surcharges de cette méthode pour créer un fuseau horaire avec ou sans règles d’ajustement.</span><span class="sxs-lookup"><span data-stu-id="3dc66-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="3dc66-109">Si le fuseau horaire prend en charge l’heure d’été, vous pouvez définir des ajustements à l’aide de règles d’ajustement fixes ou flottantes.</span><span class="sxs-lookup"><span data-stu-id="3dc66-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="3dc66-110">(Pour obtenir les définitions de ces termes, consultez la section « Terminologie relative aux fuseaux horaires » dans [vue d’ensemble des fuseaux horaires](time-zone-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="3dc66-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3dc66-111">Les fuseaux horaires personnalisés créés en appelant la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode ne sont pas ajoutés au registre.</span><span class="sxs-lookup"><span data-stu-id="3dc66-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="3dc66-112">Au lieu de cela, ils sont accessibles uniquement par le biais de la référence d’objet retournée par l' <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="3dc66-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="3dc66-113">Cette rubrique montre comment créer un fuseau horaire sans règle d’ajustement.</span><span class="sxs-lookup"><span data-stu-id="3dc66-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="3dc66-114">Pour créer un fuseau horaire qui prend en charge les règles d’ajustement à l’heure d’été, consultez [Comment : créer des fuseaux horaires avec des règles d’ajustement](create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="3dc66-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="3dc66-115">Pour créer un fuseau horaire sans règles d’ajustement</span><span class="sxs-lookup"><span data-stu-id="3dc66-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="3dc66-116">Définissez le nom d’affichage du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3dc66-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="3dc66-117">Le nom d’affichage suit un format relativement standard dans lequel le décalage du fuseau horaire par rapport au temps universel coordonné (UTC, Universal Time Coordinated) est placé entre parenthèses et est suivi d’une chaîne qui identifie le fuseau horaire, une ou plusieurs des villes du fuseau horaire, ou un ou plusieurs des pays ou régions du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3dc66-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="3dc66-118">Définissez le nom de l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3dc66-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="3dc66-119">En règle générale, cette chaîne est également utilisée comme identificateur du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3dc66-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="3dc66-120">Si vous souhaitez utiliser un identificateur différent du nom standard du fuseau horaire, définissez l’identificateur de fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3dc66-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="3dc66-121">Instanciez un <xref:System.TimeSpan> objet qui définit le décalage du fuseau horaire par rapport à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="3dc66-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="3dc66-122">Les fuseaux horaires dont les heures sont postérieures à l’heure UTC ont un décalage positif.</span><span class="sxs-lookup"><span data-stu-id="3dc66-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="3dc66-123">Les fuseaux horaires dont les heures sont antérieures à l’heure UTC ont un décalage négatif.</span><span class="sxs-lookup"><span data-stu-id="3dc66-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="3dc66-124">Appelez la <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> méthode pour instancier le nouveau fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3dc66-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="3dc66-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="3dc66-125">Example</span></span>

<span data-ttu-id="3dc66-126">L’exemple suivant définit un fuseau horaire personnalisé pour Mawson, Antarctique, qui n’a aucune règle d’ajustement.</span><span class="sxs-lookup"><span data-stu-id="3dc66-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="3dc66-127">La chaîne assignée à la <xref:System.TimeZoneInfo.DisplayName%2A> propriété suit un format standard dans lequel le décalage du fuseau horaire par rapport à l’heure UTC est suivi d’une description conviviale du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3dc66-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="3dc66-128">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3dc66-128">Compiling the code</span></span>

<span data-ttu-id="3dc66-129">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="3dc66-129">This example requires:</span></span>

- <span data-ttu-id="3dc66-130">Que les espaces de noms suivants soient importés :</span><span class="sxs-lookup"><span data-stu-id="3dc66-130">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="3dc66-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dc66-131">See also</span></span>

- [<span data-ttu-id="3dc66-132">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="3dc66-132">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="3dc66-133">Vue d’ensemble des fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="3dc66-133">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="3dc66-134">Comment : créer des fuseaux horaires avec des règles d’ajustement</span><span class="sxs-lookup"><span data-stu-id="3dc66-134">How to: Create time zones with adjustment rules</span></span>](create-time-zones-with-adjustment-rules.md)
