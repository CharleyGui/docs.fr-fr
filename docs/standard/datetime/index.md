---
title: Dates, heures et fuseaux horaires
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zone objects [.NET]
- date and time data [.NET]
- time zones [.NET]
- times [.NET], time zones
- time [.NET], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
ms.openlocfilehash: 1200f7edc3ac40a67ecfa2f554c5c721877e755a
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063675"
---
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="941e2-102">Dates, heures et fuseaux horaires</span><span class="sxs-lookup"><span data-stu-id="941e2-102">Dates, times, and time zones</span></span>

<span data-ttu-id="941e2-103">En plus de la structure <xref:System.DateTime> élémentaire, .NET fournit les classes suivantes qui prennent en charge l’utilisation des fuseaux horaires :</span><span class="sxs-lookup"><span data-stu-id="941e2-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="941e2-104">Utilisez cette classe pour travailler avec le fuseau horaire local du système et le fuseau horaire UTC.</span><span class="sxs-lookup"><span data-stu-id="941e2-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.</span></span> <span data-ttu-id="941e2-105">Les fonctionnalités de la <xref:System.TimeZone> classe sont en grande partie remplacées par la <xref:System.TimeZoneInfo> classe.</span><span class="sxs-lookup"><span data-stu-id="941e2-105">The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="941e2-106">Utilisez cette classe pour travailler avec tout fuseau horaire prédéfini sur un système, créer des fuseaux horaires et convertir facilement des dates et des heures d'un fuseau horaire à un autre.</span><span class="sxs-lookup"><span data-stu-id="941e2-106">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="941e2-107">Pour tout nouveau développement, utilisez la classe <xref:System.TimeZoneInfo> plutôt que la classe <xref:System.TimeZone>.</span><span class="sxs-lookup"><span data-stu-id="941e2-107">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="941e2-108">Utilisez cette structure pour travailler avec des dates et heures dont le décalage (ou différence) par rapport à l'heure UTC est connu.</span><span class="sxs-lookup"><span data-stu-id="941e2-108">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="941e2-109">La structure <xref:System.DateTimeOffset> associe une valeur de date et d’heure au décalage de cette heure par rapport à l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="941e2-109">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="941e2-110">En raison de sa relation avec l’heure UTC, une valeur individuelle de date et d’heure identifie de façon univoque un point unique dans le temps.</span><span class="sxs-lookup"><span data-stu-id="941e2-110">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="941e2-111">Cela rend une valeur <xref:System.DateTimeOffset> plus portable d’un ordinateur à un autre par rapport à une valeur <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="941e2-111">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="941e2-112">Cette section de la documentation fournit les informations dont vous avez besoin pour travailler avec les fuseaux horaires et pour créer des applications prenant en charge les fuseaux horaires, qui peuvent convertir des dates et des heures d’un fuseau horaire à un autre.</span><span class="sxs-lookup"><span data-stu-id="941e2-112">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="941e2-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="941e2-113">In this section</span></span>

<span data-ttu-id="941e2-114">[Vue d’ensemble des fuseaux horaires](time-zone-overview.md) Décrit la terminologie, les concepts et les problèmes impliqués dans la création d’applications prenant en charge les fuseaux horaires.</span><span class="sxs-lookup"><span data-stu-id="941e2-114">[Time zone overview](time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="941e2-115">[Choix entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](choosing-between-datetime.md) Explique quand utiliser les <xref:System.DateTime> <xref:System.DateTimeOffset> types, et <xref:System.TimeZoneInfo> lors de l’utilisation de données de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="941e2-115">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="941e2-116">[Recherche des fuseaux horaires définis sur un système local](finding-the-time-zones-on-local-system.md) Décrit comment énumérer les fuseaux horaires trouvés sur un système local.</span><span class="sxs-lookup"><span data-stu-id="941e2-116">[Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="941e2-117">[Guide pratique pour énumérer les fuseaux horaires d’un ordinateur](enumerate-time-zones.md) Fournit des exemples qui énumèrent les fuseaux horaires définis dans le Registre d’un ordinateur et qui permettent aux utilisateurs de sélectionner un fuseau horaire prédéfini dans une liste.</span><span class="sxs-lookup"><span data-stu-id="941e2-117">[How to: Enumerate time zones present on a computer](enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="941e2-118">[Guide pratique pour accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](access-utc-and-local.md) Décrit comment accéder au temps universel coordonné et au fuseau horaire local.</span><span class="sxs-lookup"><span data-stu-id="941e2-118">[How to: Access the predefined UTC and local time zone objects](access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="941e2-119">[Guide pratique : instancier un objet TimeZoneInfo](instantiate-time-zone-info.md) Décrit comment instancier un objet <xref:System.TimeZoneInfo> à partir du Registre système local.</span><span class="sxs-lookup"><span data-stu-id="941e2-119">[How to: Instantiate a TimeZoneInfo object](instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="941e2-120">[Instanciation d’un objet DateTimeOffset](instantiating-a-datetimeoffset-object.md) Décrit comment un objet <xref:System.DateTimeOffset> peut être instancié et comment une valeur <xref:System.DateTime> peut être convertie en valeur <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="941e2-120">[Instantiating a DateTimeOffset object](instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="941e2-121">[Guide pratique pour créer des fuseaux horaires sans règles d’ajustement](create-time-zones-without-adjustment-rules.md) Explique comment créer un fuseau horaire personnalisé qui ne prend pas en charge la transition vers et depuis l’heure d’été.</span><span class="sxs-lookup"><span data-stu-id="941e2-121">[How to: Create time zones without adjustment rules](create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="941e2-122">[Guide pratique pour créer des fuseaux horaires avec des règles d’ajustement](create-time-zones-with-adjustment-rules.md) Explique comment créer un fuseau horaire personnalisé qui prend en charge une ou plusieurs transitions vers et depuis l’heure d’été.</span><span class="sxs-lookup"><span data-stu-id="941e2-122">[How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="941e2-123">[Enregistrement et restauration de fuseaux horaires](saving-and-restoring-time-zones.md) Décrit la prise en charge de <xref:System.TimeZoneInfo> pour la sérialisation et la désérialisation des données de fuseau horaire et présente certains des scénarios dans lesquels ces fonctionnalités peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="941e2-123">[Saving and restoring time zones](saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="941e2-124">[Guide pratique pour enregistrer des fuseaux horaires dans une ressource incorporée](save-time-zones-to-an-embedded-resource.md) Explique comment créer un fuseau horaire personnalisé et enregistrer ses informations dans un fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="941e2-124">[How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="941e2-125">[Guide pratique pour restaurer des fuseaux horaires dans une ressource incorporée](restore-time-zones-from-an-embedded-resource.md) Explique comment instancier des fuseaux horaires personnalisés qui ont été enregistrés dans un fichier de ressources incorporées.</span><span class="sxs-lookup"><span data-stu-id="941e2-125">[How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="941e2-126">[Exécution d’opérations arithmétiques avec des dates et heures](performing-arithmetic-operations.md) Traite les problèmes liés à l’ajout, la soustraction et la comparaison de valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="941e2-126">[Performing arithmetic operations with dates and times](performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="941e2-127">[Guide pratique pour utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure](use-time-zones-in-arithmetic.md) Explique comment effectuer des opérations arithmétiques de date et d’heure qui reflètent les règles d’ajustement d’un fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="941e2-127">[How to: Use time zones in date and time arithmetic](use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="941e2-128">[Conversion entre DateTime et DateTimeOffset](converting-between-datetime-and-offset.md) Décrit comment effectuer une conversion entre des valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="941e2-128">[Converting between DateTime and DateTimeOffset](converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="941e2-129">[Conversion d’heures entre fuseaux horaires](converting-between-time-zones.md) Décrit comment convertir les heures d’un fuseau horaire dans un autre fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="941e2-129">[Converting times between time zones](converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="941e2-130">[Guide pratique pour résoudre des heures ambiguës](resolve-ambiguous-times.md) Décrit comment résoudre une heure ambiguë en la mappant à l’heure d’hiver du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="941e2-130">[How to: Resolve ambiguous times](resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="941e2-131">[Guide pratique pour permettre aux utilisateurs de résoudre des heures ambiguës](let-users-resolve-ambiguous-times.md) Décrit comment permettre à un utilisateur de déterminer le mappage entre une heure locale ambiguë et le temps universel coordonné.</span><span class="sxs-lookup"><span data-stu-id="941e2-131">[How to: Let users resolve ambiguous times](let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="941e2-132">Référence</span><span class="sxs-lookup"><span data-stu-id="941e2-132">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
