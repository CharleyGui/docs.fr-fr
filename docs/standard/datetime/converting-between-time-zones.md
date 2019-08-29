---
title: Conversion d’heures entre fuseaux horaires
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], converting
- time zones [.NET Framework], conversions
- UTC times, converting
- converting times
- local time conversions
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5b78e3985169954d71b479aa2e8a034f61afc01
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106978"
---
# <a name="converting-times-between-time-zones"></a>Conversion d’heures entre fuseaux horaires

Il devient de plus en plus important pour une application qui fonctionne avec des dates et des heures de gérer les différences entre les fuseaux horaires. Une application ne peut plus supposer que toutes les heures peuvent être exprimées dans l’heure locale, qui est l’heure disponible <xref:System.DateTime> à partir de la structure. Par exemple, une page web qui affiche l’heure actuelle dans la partie Est des États-Unis ne sera pas crédible pour un client d’Asie orientale. Cette rubrique explique comment convertir des heures d’un fuseau horaire vers un autre, et comment convertir <xref:System.DateTimeOffset> des valeurs qui ont une prise en forme limitée des fuseaux horaires.

## <a name="converting-to-coordinated-universal-time"></a>Conversion en heure UTC

Le temps universel coordonné (UTC) est une norme d’heure atomique de haute précision. Les fuseaux horaires du monde sont exprimés comme décalages positifs ou négatifs par rapport à l’heure UTC. Par conséquent, l’heure UTC fournit une sorte d’heure neutre du point de vue des fuseaux horaires. L’utilisation de l’heure UTC est recommandée lorsque la portabilité de la date et de l’heure entre les ordinateurs est importante. (Pour plus d’informations et pour connaître les meilleures pratiques utilisant des dates et des heures, consultez [codage des meilleures pratiques à l’aide de DateTime dans le .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973825(v=msdn.10)).) La conversion de fuseaux horaires individuels en heure UTC facilite les comparaisons d’heures.

> [!NOTE]
> Vous pouvez également sérialiser une <xref:System.DateTimeOffset> structure pour représenter de façon non ambiguë un point unique dans le temps. Étant <xref:System.DateTimeOffset> donné que les objets stockent une valeur de date et d’heure avec son décalage par rapport à l’heure UTC, ils représentent toujours un point particulier dans le temps par rapport à l’heure UTC.

Le moyen le plus simple de convertir une heure en heure UTC consiste `static` à`Shared` appeler la méthode <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> (en Visual Basic). La conversion exacte effectuée par la méthode dépend de la valeur de la `dateTime` propriété du <xref:System.DateTime.Kind%2A> paramètre, comme le montre le tableau suivant.

| `DateTime.Kind`            | Conversion                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | Convertit l’heure locale en heure UTC.                                                    |
| `DateTimeKind.Unspecified` | Suppose que le paramètre `dateTime` est l’heure locale et convertit l’heure locale en heure UTC. |
| `DateTimeKind.Utc`         | Retourne le paramètre `dateTime` inchangé.                                    |

Le code suivant convertit l’heure locale actuelle en heure UTC et affiche le résultat dans la console.

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

Si la valeur de date et d’heure ne représente ni l’heure locale, ni l' <xref:System.DateTime.ToUniversalTime%2A> heure UTC, la méthode retournera probablement un résultat erroné. Toutefois, vous pouvez utiliser la <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> méthode pour convertir la date et l’heure d’un fuseau horaire spécifié. (Pour plus d’informations sur la <xref:System.TimeZoneInfo> récupération d’un objet qui représente le fuseau horaire de destination, consultez [recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md).) Le code suivant utilise la <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> méthode pour convertir l’heure de l’est en heure UTC.

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

Notez que cette méthode lève une <xref:System.ArgumentException> si la <xref:System.DateTime> propriété de <xref:System.DateTime.Kind%2A> l’objet et le fuseau horaire ne correspondent pas. Une incompatibilité se produit <xref:System.DateTime.Kind%2A> si la <xref:System.DateTimeKind.Local?displayProperty=nameWithType> propriété est <xref:System.TimeZoneInfo> , mais que l’objet ne représente pas le fuseau horaire local <xref:System.DateTime.Kind%2A> , ou <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> si la <xref:System.TimeZoneInfo> propriété est, mais <xref:System.TimeZoneInfo.Utc?displayProperty=nameWithType>que l’objet n’est pas égal à.

Toutes ces méthodes prennent <xref:System.DateTime> des valeurs en tant que paramètres et retournent une <xref:System.DateTime> valeur. Pour <xref:System.DateTimeOffset> les valeurs, <xref:System.DateTimeOffset> la structure a <xref:System.DateTimeOffset.ToUniversalTime%2A> une méthode d’instance qui convertit la date et l’heure de l’instance actuelle en heure UTC. L’exemple suivant appelle la <xref:System.DateTimeOffset.ToUniversalTime%2A> méthode pour convertir une heure locale et plusieurs autres heures en temps universel coordonné (UTC, Universal Time Coordinated).

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a>Conversion de l’heure UTC dans un fuseau horaire désigné

Pour convertir l’heure UTC en heure locale, consultez la section «conversion de l’heure UTC en heure locale» qui suit. Pour convertir l’heure UTC et l’heure dans n’importe quel fuseau horaire que vous <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> désignez, appelez la méthode. Cette méthode accepte deux paramètres :

- L’heure UTC à convertir. Il doit s’agir <xref:System.DateTime> d’une <xref:System.DateTime.Kind%2A> valeur dont la propriété `Unspecified` a `Utc`la valeur ou.

- Le fuseau horaire vers lequel convertir l’heure UTC.

Le code suivant convertit l’heure UTC en heure propre au fuseau horaire Centre.

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a>Conversion de l’heure UTC en heure locale

Pour convertir l’heure UTC en heure locale, <xref:System.DateTime.ToLocalTime%2A> appelez la méthode <xref:System.DateTime> de l’objet dont vous souhaitez convertir l’heure. Le comportement exact de la méthode dépend de la valeur de la <xref:System.DateTime.Kind%2A> propriété de l’objet, comme le montre le tableau suivant.

| `DateTime.Kind`            | Conversion                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | Retourne la <xref:System.DateTime> valeur inchangée.                                      |
| `DateTimeKind.Unspecified` | Suppose que la <xref:System.DateTime> valeur est UTC et convertit l’heure UTC en heure locale. |
| `DateTimeKind.Utc`         | Convertit <xref:System.DateTime> la valeur en heure locale.                                 |

> [!NOTE]
> La <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> méthode se comporte de la même façon que `DateTime.ToLocalTime` la méthode. Il accepte un seul paramètre, qui est la valeur de date et d’heure à convertir.

Vous pouvez également convertir l’heure d’un fuseau horaire désigné en heure locale à l’aide `static` de`Shared` la méthode ( <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> en Visual Basic). Cette technique est décrite dans la section suivante.

## <a name="converting-between-any-two-time-zones"></a>Conversion entre deux fuseaux horaires quelconques

Vous pouvez effectuer une conversion entre deux fuseaux horaires quelconques à l’aide `static` de`Shared` l’une des deux méthodes suivantes <xref:System.TimeZoneInfo> (dans Visual Basic) de la classe:

- <xref:System.TimeZoneInfo.ConvertTime%2A>

  Les paramètres de cette méthode sont la valeur de date et d’heure à `TimeZoneInfo` convertir, un objet qui représente le fuseau horaire de la valeur de date et `TimeZoneInfo` d’heure et un objet qui représente le fuseau horaire vers lequel convertir la valeur de date et d’heure.

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  Les paramètres de cette méthode sont la valeur de date et d’heure à convertir, l’identificateur du fuseau horaire de la valeur de date et d’heure et l’identificateur du fuseau horaire vers lequel convertir la valeur de date et d’heure.

Les deux méthodes requièrent <xref:System.DateTime.Kind%2A> que la propriété de la valeur de date et d’heure <xref:System.TimeZoneInfo> à convertir et l’objet ou l’identificateur de fuseau horaire qui représente son fuseau horaire correspondent l’un à l’autre. Sinon, une exception <xref:System.ArgumentException> est levée. Par exemple, si la `Kind` propriété de la valeur de date et d' `DateTimeKind.Local`heure est, une exception est levée `TimeZoneInfo` si l’objet passé en tant que paramètre à la méthode n' `TimeZoneInfo.Local`est pas égal à. Une exception est également levée si l’identificateur passé comme paramètre à la méthode n’est pas égal à `TimeZoneInfo.Local.Id`.

L’exemple suivant utilise la <xref:System.TimeZoneInfo.ConvertTime%2A> méthode pour convertir l’heure standard d’Hawaii en heure locale.

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a>Conversion de valeurs DateTimeOffset

Les valeurs de date et d' <xref:System.DateTimeOffset> heure représentées par les objets ne prennent pas complètement en charge les fuseaux horaires, car l’objet est dissocié de son fuseau horaire au moment où il est instancié. Toutefois, dans de nombreux cas, une application doit simplement convertir une date et une heure en fonction de deux décalages différents par rapport à l’heure UTC plutôt qu’en fonction de l’heure dans des fuseaux horaires particuliers. Pour effectuer cette conversion, vous pouvez appeler la méthode de <xref:System.DateTimeOffset.ToOffset%2A> l’instance actuelle. Le paramètre unique de la méthode est le décalage de la nouvelle valeur de date et d’heure que la méthode doit retourner.

Par exemple, si la date et l’heure d’une demande de page web de l’utilisateur sont connues et sont sérialisées comme chaîne au format MM/jj/aaaa hh:mm:ss zzzz, la méthode `ReturnTimeOnServer` qui suit convertit cette valeur de date et d’heure en date et heure sur le serveur web.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

Si la chaîne « 1/9/2007 5:32:07 -05:00 » est transmise à la méthode, représentant la date et l’heure dans un fuseau horaire en retard de cinq heures par rapport à l’heure UTC, elle retourne 1/9/2007 3:32:07 AM -07:00 pour un serveur situé dans le fuseau horaire horaire Pacifique (É.-U.).

La <xref:System.TimeZoneInfo> classe comprend également une surcharge de la <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> méthode qui effectue des conversions de fuseau <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> horaire avec des valeurs. Les paramètres de la méthode sont <xref:System.DateTimeOffset> une valeur et une référence au fuseau horaire vers lequel l’heure doit être convertie. L’appel de méthode retourne <xref:System.DateTimeOffset> une valeur. Par exemple, la `ReturnTimeOnServer` méthode de l’exemple précédent peut être réécrite comme suit pour appeler <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> la méthode.

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a>Voir aussi

- <xref:System.TimeZoneInfo>
- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
