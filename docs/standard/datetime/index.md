---
title: Dates, heures et fuseaux horaires
ms.date: 04/10/2017
helpviewer_keywords:
- time zone objects [.NET]
- date and time data [.NET]
- time zones [.NET]
- times [.NET], time zones
- time [.NET], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
ms.openlocfilehash: b9dbbfa30c3398a984432fb0ecb8d0052c425f51
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817898"
---
# <a name="dates-times-and-time-zones"></a>Dates, heures et fuseaux horaires

En plus de la structure <xref:System.DateTime> élémentaire, .NET fournit les classes suivantes qui prennent en charge l’utilisation des fuseaux horaires :

* <xref:System.TimeZone>

  Utilisez cette classe pour travailler avec le fuseau horaire local du système et le fuseau horaire UTC. Les fonctionnalités de la <xref:System.TimeZone> classe sont en grande partie remplacées par la <xref:System.TimeZoneInfo> classe.

* <xref:System.TimeZoneInfo>

  Utilisez cette classe pour travailler avec tout fuseau horaire prédéfini sur un système, créer des fuseaux horaires et convertir facilement des dates et des heures d'un fuseau horaire à un autre. Pour tout nouveau développement, utilisez la classe <xref:System.TimeZoneInfo> plutôt que la classe <xref:System.TimeZone>.

* <xref:System.DateTimeOffset>

  Utilisez cette structure pour travailler avec des dates et heures dont le décalage (ou différence) par rapport à l'heure UTC est connu. La structure <xref:System.DateTimeOffset> associe une valeur de date et d’heure au décalage de cette heure par rapport à l’heure UTC. En raison de sa relation avec l’heure UTC, une valeur individuelle de date et d’heure identifie de façon univoque un point unique dans le temps. Cela rend une valeur <xref:System.DateTimeOffset> plus portable d’un ordinateur à un autre par rapport à une valeur <xref:System.DateTime>.

Cette section de la documentation fournit les informations dont vous avez besoin pour travailler avec les fuseaux horaires et pour créer des applications prenant en charge les fuseaux horaires, qui peuvent convertir des dates et des heures d’un fuseau horaire à un autre.

## <a name="in-this-section"></a>Dans cette section

[Vue d’ensemble des fuseaux horaires](time-zone-overview.md) Décrit la terminologie, les concepts et les problèmes impliqués dans la création d’applications prenant en charge les fuseaux horaires.

[Choix entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](choosing-between-datetime.md) Explique quand utiliser les <xref:System.DateTime> <xref:System.DateTimeOffset> types, et <xref:System.TimeZoneInfo> lors de l’utilisation de données de date et d’heure.

[Recherche des fuseaux horaires définis sur un système local](finding-the-time-zones-on-local-system.md) Décrit comment énumérer les fuseaux horaires trouvés sur un système local.

[Guide pratique pour énumérer les fuseaux horaires d’un ordinateur](enumerate-time-zones.md) Fournit des exemples qui énumèrent les fuseaux horaires définis dans le Registre d’un ordinateur et qui permettent aux utilisateurs de sélectionner un fuseau horaire prédéfini dans une liste.

[Guide pratique pour accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](access-utc-and-local.md) Décrit comment accéder au temps universel coordonné et au fuseau horaire local.

[Guide pratique : instancier un objet TimeZoneInfo](instantiate-time-zone-info.md) Décrit comment instancier un objet <xref:System.TimeZoneInfo> à partir du Registre système local.

[Instanciation d’un objet DateTimeOffset](instantiating-a-datetimeoffset-object.md) Décrit comment un objet <xref:System.DateTimeOffset> peut être instancié et comment une valeur <xref:System.DateTime> peut être convertie en valeur <xref:System.DateTimeOffset>.

[Guide pratique pour créer des fuseaux horaires sans règles d’ajustement](create-time-zones-without-adjustment-rules.md) Explique comment créer un fuseau horaire personnalisé qui ne prend pas en charge la transition vers et depuis l’heure d’été.

[Guide pratique pour créer des fuseaux horaires avec des règles d’ajustement](create-time-zones-with-adjustment-rules.md) Explique comment créer un fuseau horaire personnalisé qui prend en charge une ou plusieurs transitions vers et depuis l’heure d’été.

[Enregistrement et restauration de fuseaux horaires](saving-and-restoring-time-zones.md) Décrit la prise en charge de <xref:System.TimeZoneInfo> pour la sérialisation et la désérialisation des données de fuseau horaire et présente certains des scénarios dans lesquels ces fonctionnalités peuvent être utilisées.

[Guide pratique pour enregistrer des fuseaux horaires dans une ressource incorporée](save-time-zones-to-an-embedded-resource.md) Explique comment créer un fuseau horaire personnalisé et enregistrer ses informations dans un fichier de ressources.

[Guide pratique pour restaurer des fuseaux horaires dans une ressource incorporée](restore-time-zones-from-an-embedded-resource.md) Explique comment instancier des fuseaux horaires personnalisés qui ont été enregistrés dans un fichier de ressources incorporées.

[Exécution d’opérations arithmétiques avec des dates et heures](performing-arithmetic-operations.md) Traite les problèmes liés à l’ajout, la soustraction et la comparaison de valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset>.

[Guide pratique pour utiliser des fuseaux horaires dans des opérations arithmétiques de date et d’heure](use-time-zones-in-arithmetic.md) Explique comment effectuer des opérations arithmétiques de date et d’heure qui reflètent les règles d’ajustement d’un fuseau horaire.

[Conversion entre DateTime et DateTimeOffset](converting-between-datetime-and-offset.md) Décrit comment effectuer une conversion entre des valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset>.

[Conversion d’heures entre fuseaux horaires](converting-between-time-zones.md) Décrit comment convertir les heures d’un fuseau horaire dans un autre fuseau horaire.

[Guide pratique pour résoudre des heures ambiguës](resolve-ambiguous-times.md) Décrit comment résoudre une heure ambiguë en la mappant à l’heure d’hiver du fuseau horaire.

[Guide pratique pour permettre aux utilisateurs de résoudre des heures ambiguës](let-users-resolve-ambiguous-times.md) Décrit comment permettre à un utilisateur de déterminer le mappage entre une heure locale ambiguë et le temps universel coordonné.

## <a name="reference"></a>Référence

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
