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
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Comment : accéder aux objets UTC et aux objets de fuseau horaire local prédéfinis

La classe <xref:System.TimeZoneInfo> fournit deux propriétés, <xref:System.TimeZoneInfo.Utc%2A> et <xref:System.TimeZoneInfo.Local%2A>, qui permettent à votre code d’accéder à des objets de fuseau horaire prédéfinis. Cette rubrique explique comment accéder aux objets <xref:System.TimeZoneInfo> retournés par ces propriétés.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Pour accéder à l’objet TimeZoneInfo de temps universel coordonné (UTC)

1. Utilisez la propriété `static` (`Shared` dans Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> pour accéder au temps universel coordonné.

2. Au lieu d’assigner l’objet <xref:System.TimeZoneInfo> retourné par la propriété à une variable objet, continuez à accéder au temps universel coordonné via la propriété <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>.

### <a name="to-access-the-local-time-zone"></a>Pour accéder au fuseau horaire local

1. Utilisez la propriété `static` (`Shared` dans Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> pour accéder au fuseau horaire du système local.

2. Au lieu d’assigner l’objet <xref:System.TimeZoneInfo> retourné par la propriété à une variable objet, continuez à accéder au fuseau horaire local via la propriété <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>.

## <a name="example"></a>Exemple

Le code suivant utilise les propriétés <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> et <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> pour convertir une heure du fuseau horaire de l’est des États-Unis et du Canada, ainsi que pour afficher le nom du fuseau horaire sur la console.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Vous devez toujours accéder au fuseau horaire local via la propriété <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> plutôt que d’attribuer le fuseau horaire local à une variable objet <xref:System.TimeZoneInfo>. De même, vous devez toujours accéder au temps universel coordonné via la propriété <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> plutôt que d’affecter la zone UTC à une variable objet <xref:System.TimeZoneInfo>. Cela empêche la variable d’objet <xref:System.TimeZoneInfo> d’être invalidée par un appel à la méthode <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- L’importation de l’espace de noms <xref:System> avec l’instruction `using` ( C# obligatoire dans le code).

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Guide pratique pour instancier un objet TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
