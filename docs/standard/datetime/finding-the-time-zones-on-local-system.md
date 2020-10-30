---
title: Recherche des fuseaux horaires définis sur un système local
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET], local
- time zones [.NET], finding local system time zones
- time zone identifiers [.NET]
- local time zone access
- time zones [.NET], retrieving
- UTC times, finding local system time zones
- time zones [.NET], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
ms.openlocfilehash: c968c7891a4fc9b77ed6224a9fc5f8f6d8f5d80b
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063688"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Recherche des fuseaux horaires définis sur un système local

La classe <xref:System.TimeZoneInfo> n'expose pas de constructeur public. En conséquence, le mot clé `new` ne peut pas être utilisé pour créer un objet <xref:System.TimeZoneInfo>. Pour instancier des objets <xref:System.TimeZoneInfo>, vous devez donc soit récupérer dans le Registre des informations sur les fuseaux horaires prédéfinis, soit créer un fuseau horaire personnalisé. Cette rubrique explique comment instancier un fuseau horaire à partir de données stockées dans le Registre. En outre, les propriétés `static` (`shared` en Visual Basic) de la classe <xref:System.TimeZoneInfo> permettent d'accéder au temps universel coordonné (UTC) et au fuseau horaire local.

> [!NOTE]
> Si les fuseaux horaires ne sont pas définis dans le Registre, vous pouvez créer des fuseaux horaires personnalisés en appelant les surcharges de la méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>. La création d’un fuseau horaire personnalisé est décrite dans les rubriques [Comment : créer des fuseaux horaires sans règles d’ajustement](create-time-zones-without-adjustment-rules.md) et [Comment : créer des fuseaux horaires avec des règles d’ajustement](create-time-zones-with-adjustment-rules.md) . Vous pouvez également instancier un objet <xref:System.TimeZoneInfo> en le restaurant à partir d'une chaîne sérialisée à l'aide de la méthode <xref:System.TimeZoneInfo.FromSerializedString%2A>. La sérialisation et la désérialisation d’un <xref:System.TimeZoneInfo> objet sont abordées dans la rubrique [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](save-time-zones-to-an-embedded-resource.md) et [Comment : restaurer des fuseaux horaires à partir d’une ressource incorporée](restore-time-zones-from-an-embedded-resource.md) .

## <a name="accessing-individual-time-zones"></a>Accès aux fuseaux horaires individuels

La classe <xref:System.TimeZoneInfo> fournit deux objets de fuseaux horaires prédéfinis qui représentent l'heure UTC et le fuseau horaire local. Ils sont disponibles dans les propriétés <xref:System.TimeZoneInfo.Utc%2A> et <xref:System.TimeZoneInfo.Local%2A>, respectivement. Pour obtenir des instructions sur l’accès aux fuseaux horaires UTC ou locaux, consultez [Comment : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](access-utc-and-local.md).

Vous pouvez également instancier un objet <xref:System.TimeZoneInfo> qui représente tout fuseau horaire défini dans le Registre. Pour obtenir des instructions sur l’instanciation d’un objet de fuseau horaire spécifique, consultez [Comment : instancier un objet TimeZoneInfo](instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Identificateurs de fuseau horaire

L'identificateur de fuseau horaire est un champ clé qui identifie le fuseau horaire de manière unique. Alors que la plupart des clés sont relativement courtes, l'identificateur de fuseau horaire est long. Dans la plupart des cas, sa valeur correspond à la propriété <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType>, utilisée pour fournir le nom de l'heure standard du fuseau horaire. Toutefois, il existe des exceptions. Pour vous assurer que l'identificateur fourni est valide, la meilleure façon consiste à énumérer les fuseaux horaires disponibles sur votre système et à noter les identificateurs associés.

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](index.md)
- [Comment : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis](access-utc-and-local.md)
- [Comment : instancier un objet TimeZoneInfo](instantiate-time-zone-info.md)
- [Conversion d’heures entre fuseaux horaires](converting-between-time-zones.md)
