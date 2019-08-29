---
title: 'Procédure : accéder aux objets de fuseau horaire UTC et local prédéfinis'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aa19118ce0837b9ce0eb523f3e086fcbcecb9e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106563"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Procédure : accéder aux objets de fuseau horaire UTC et local prédéfinis

La <xref:System.TimeZoneInfo> classe fournit deux propriétés, <xref:System.TimeZoneInfo.Utc%2A> et <xref:System.TimeZoneInfo.Local%2A>, qui permettent à votre code d’accéder à des objets de fuseau horaire prédéfinis. Cette rubrique explique comment accéder aux objets <xref:System.TimeZoneInfo> retournés par ces propriétés.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Pour accéder à l’objet TimeZoneInfo de temps universel coordonné (UTC)

1. Utilisez la `static` propriété`Shared` (dans Visual Basic <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> ) pour accéder au temps universel coordonné.

2. Au lieu d’assigner l' <xref:System.TimeZoneInfo> objet retourné par la propriété à une variable objet, continuez à accéder au temps universel coordonné via la <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> propriété.

### <a name="to-access-the-local-time-zone"></a>Pour accéder au fuseau horaire local

1. Utilisez la `static` propriété`Shared` (dans Visual Basic <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ) pour accéder au fuseau horaire du système local.

2. Au lieu d’assigner l' <xref:System.TimeZoneInfo> objet retourné par la propriété à une variable objet, continuez à accéder au fuseau horaire local via la <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété.

## <a name="example"></a>Exemples

Le code suivant utilise les <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriétés <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> et pour convertir une heure du fuseau horaire de l’est des États-Unis et du Canada, ainsi que pour afficher le nom du fuseau horaire sur la console.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Vous devez toujours accéder au fuseau horaire local via la <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> propriété plutôt que d’attribuer le fuseau horaire local à une <xref:System.TimeZoneInfo> variable objet. De même, vous devez toujours accéder au temps universel coordonné via <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> la propriété plutôt que d’affecter la zone UTC à <xref:System.TimeZoneInfo> une variable objet. Cela empêche la <xref:System.TimeZoneInfo> variable d’objet d’être invalidée par un appel à <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> la méthode.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Que l'espace de noms <xref:System> soit importé avec l'instruction `using` (obligatoire en C#).

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Guide pratique pour Instancier un objet TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
