---
title: Comparer DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo
description: Découvrez les différences entre les types DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo pour représenter les informations de date et d’heure dans .NET.
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTimeOffset structure
- TimeZoneInfo class
- time zones [.NET], common uses
- date and time classes [.NET]
- time zones [.NET], type options
- DateTime structure
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
ms.openlocfilehash: 5d6173642e88165bb52d5d9cfc85c8889ce763a5
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063870"
---
# <a name="choose-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a>Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo

Les applications .NET peuvent utiliser les informations de date et d’heure de plusieurs façons. Les utilisations les plus courantes des informations de date et d’heure sont les suivantes :

- Pour refléter seulement une date, les informations d'heure n'étant pas importantes.

- Pour refléter seulement une heure, les informations de date n'étant pas importantes.

- Pour refléter une date et une heure abstraites, qui ne sont pas liées à un moment et un endroit spécifiques (par exemple, la plupart des magasins d'une chaîne internationale ouvrent en semaine à 9h00).

- Pour récupérer des informations de date et d’heure à partir de sources en dehors de .NET, en général, où les informations de date et d’heure sont stockées dans un type de données simple.

- Pour identifier de façon univoque et non ambiguë un point unique dans le temps. Certaines applications requièrent qu’une date et une heure ne soient pas ambiguës sur le système hôte. D’autres applications requièrent une non-ambiguïté entre les systèmes (autrement dit, une date sérialisée sur un système peut être désérialisée de manière significative et utilisée sur un autre système n’importe où dans le monde).

- Pour conserver plusieurs dates/heures ayant un lien les unes avec les autres (comme la date/heure locale du demandeur et la date/heure de réception par le serveur d'une demande web).

- Pour effectuer des calculs de date et d'heure, éventuellement avec un résultat qui identifie de façon univoque et non ambiguë un point unique dans le temps.

.Net comprend les <xref:System.DateTime> <xref:System.DateTimeOffset> types,, <xref:System.TimeSpan> et <xref:System.TimeZoneInfo> , qui peuvent tous être utilisés pour créer des applications qui fonctionnent avec des dates et des heures.

> [!NOTE]
> Cette rubrique ne traite pas <xref:System.TimeZone> du fait que sa fonctionnalité est presque entièrement incorporée dans la <xref:System.TimeZoneInfo> classe. Dans la mesure du possible, utilisez la <xref:System.TimeZoneInfo> classe au lieu de la <xref:System.TimeZone> classe.

## <a name="the-datetimeoffset-structure"></a>La structure DateTimeOffset

La structure <xref:System.DateTimeOffset> représente une valeur de date et d'heure, ainsi qu'un décalage qui indique de combien cette valeur diffère du temps UTC. Ainsi, la valeur toujours identifie toujours de façon non ambiguë un point unique dans le temps.

Le type <xref:System.DateTimeOffset> comprend toutes les fonctionnalités du type <xref:System.DateTime> , ainsi que la gestion des fuseaux horaires. Cela le rend approprié pour les applications qui :

- Identifient de façon univoque et non ambiguë un point unique dans le temps. Le type <xref:System.DateTimeOffset> peut être utilisé pour définir de façon non ambiguë la signification de "maintenant", pour consigner les dates/heures des transactions, pour consigner les dates/heures des événements système ou des événements d'une application, et pour enregistrer les dates/heures de création et de modification des fichiers.

- Effectuent des calculs de date et d'heure.

- Conservent plusieurs dates/heures ayant un lien entre elles, comme les dates/heures qui sont stockées sous la forme de deux valeurs distinctes ou de deux membres d'une structure.

> [!NOTE]
> Ces utilisations pour des valeurs <xref:System.DateTimeOffset> sont beaucoup plus courantes que celles pour les valeurs <xref:System.DateTime> . Par conséquent, considérez <xref:System.DateTimeOffset> comme le type de date et d’heure par défaut pour le développement d’applications.

Une <xref:System.DateTimeOffset> valeur n’est pas liée à un fuseau horaire particulier, mais peut provenir de différents fuseaux horaires. L’exemple suivant répertorie les fuseaux horaires auxquels plusieurs <xref:System.DateTimeOffset> valeurs (y compris une heure locale du Pacifique) peuvent appartenir.

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

La sortie montre que chaque valeur de date et d'heure de cet exemple peut appartenir à au moins trois fuseaux horaires différents. La <xref:System.DateTimeOffset> valeur de 6/10/2007 indique que si une valeur de date et d’heure représente une heure d’été, son décalage par rapport à l’heure UTC ne correspond pas nécessairement au décalage UTC de base du fuseau horaire d’origine ou au décalage par rapport à l’heure UTC trouvée dans son nom d’affichage. Comme une <xref:System.DateTimeOffset> valeur unique n’est pas étroitement couplée avec son fuseau horaire, elle ne peut pas refléter la transition d’un fuseau horaire vers et depuis l’heure d’été. Cela peut être problématique lorsque des opérations arithmétiques de date et d’heure sont utilisées pour manipuler une <xref:System.DateTimeOffset> valeur. Pour plus d’informations sur la façon d’effectuer des opérations arithmétiques de date et d’heure d’une manière qui prend en compte les règles d’ajustement d’un fuseau horaire, consultez [exécution d’opérations arithmétiques avec des dates et des heures](performing-arithmetic-operations.md).

## <a name="the-datetime-structure"></a>La structure DateTime

Une valeur <xref:System.DateTime> définit une date/heure spécifique. Il inclut une <xref:System.DateTime.Kind%2A> propriété qui fournit des informations limitées sur le fuseau horaire auquel cette date et cette heure appartiennent. La valeur <xref:System.DateTimeKind> retournée par la propriété <xref:System.DateTime.Kind%2A> indique si la valeur <xref:System.DateTime> représente la date/heure locale (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), la date/heure UTC (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>) ou une date/heure non spécifiée (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).

La <xref:System.DateTime> structure convient aux applications présentant une ou plusieurs des caractéristiques suivantes :

- Utilisent seulement des dates.

- Utilisent seulement des heures.

- Utilisent des dates et des heures abstraites.

- Utilisent des dates et des heures pour lesquelles les informations de fuseau horaire sont manquantes.

- Utilisent seulement des dates et des heures UTC.

- Récupérez des informations de date et d’heure à partir de sources en dehors de .NET, telles que des bases de données SQL. En règle générale, ces sources stockent les informations de date et d'heure dans un format simple qui est compatible avec la structure <xref:System.DateTime> .

- Effectuent des calculs de dates et d'heures, mais sont surtout concernées par des résultats d'ordre général. Par exemple, dans une opération d'addition qui ajoute six mois à une date/heure, il n'est souvent pas important que le résultat soit ajusté pour l'heure d'été.

Sauf si une valeur <xref:System.DateTime> particulière représente le temps UTC, cette valeur de date/heure est souvent ambiguë ou limitée en termes de portabilité. Par exemple, si une valeur <xref:System.DateTime> représente l'heure locale, elle est portable dans ce fuseau horaire local (c'est-à-dire que si la valeur est désérialisée sur un autre système dans le même fuseau horaire, cette valeur continue d'identifier de façon non ambiguë un point unique dans le temps). En dehors du fuseau horaire local, cette valeur <xref:System.DateTime> peut être interprétée de plusieurs façons. Si la propriété <xref:System.DateTime.Kind%2A> de la valeur est <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, elle est encore moins portable : elle est maintenant ambiguë dans le même fuseau horaire, voire même sur le système où elle a été sérialisée pour la première fois. Seulement dans le cas où une valeur <xref:System.DateTime> représente le temps UTC, celle-ci identifie de façon non ambiguë un point unique dans le temps, indépendamment du système ou du fuseau horaire où la valeur est utilisée.

> [!IMPORTANT]
> Lors de l'enregistrement ou du partage de données <xref:System.DateTime> , le temps UTC doit être utilisé et la propriété <xref:System.DateTime> de la valeur <xref:System.DateTime.Kind%2A> doit être définie à <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="the-timespan-structure"></a>La structure TimeSpan

La structure <xref:System.TimeSpan> représente un intervalle de temps. Ses deux utilisations courantes sont :

- Refléter un intervalle de temps entre deux valeurs de date/heure. Par exemple, la soustraction d'une valeur <xref:System.DateTime> d'une autre retourne une valeur <xref:System.TimeSpan> .

- Mesurer un temps écoulé. Par exemple, la <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> propriété retourne une <xref:System.TimeSpan> valeur qui reflète l’intervalle de temps qui s’est écoulé depuis l’appel à l’une des <xref:System.Diagnostics.Stopwatch> méthodes qui commence à mesurer le temps écoulé.

Une <xref:System.TimeSpan> valeur peut également être utilisée en remplacement d’une <xref:System.DateTime> valeur quand cette valeur reflète une heure sans référence à un jour particulier. Cette utilisation est similaire aux <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> Propriétés et <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> , qui retournent une <xref:System.TimeSpan> valeur qui représente l’heure sans référence à une date. Par exemple, la structure <xref:System.TimeSpan> peut être utilisée pour refléter les heures d'ouverture ou de fermeture quotidiennes d'un magasin, ou elle peut être utilisée pour représenter l'heure où se produit un événement régulier.

L'exemple suivant définit une structure `StoreInfo` qui inclut des objets <xref:System.TimeSpan> pour les heures d'ouverture et de fermeture d'un magasin, ainsi qu'un objet <xref:System.TimeZoneInfo> qui représente le fuseau horaire du magasin. La structure comprend également deux méthodes, `IsOpenNow` et `IsOpenAt`, qui indiquent si le magasin est ouvert à une heure spécifiée par l'utilisateur, qui est supposé être dans le fuseau horaire local.

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

La structure `StoreInfo` peut ensuite être utilisée par le code du client comme ce qui suit.

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a>La classe TimeZoneInfo

La classe <xref:System.TimeZoneInfo> class represents any of the Earth's time zones, and enables the conversion of any date and time in one time zone to its equivalent in another time zone. La classe <xref:System.TimeZoneInfo> permet de travailler avec des dates et des heures de façon à ce qu'une valeur de date/heure identifie d'une manière non ambiguë un point unique dans le temps. La classe <xref:System.TimeZoneInfo> est également extensible. Bien que dépendante des informations de fuseau horaire fournies pour les systèmes Windows et définies dans le Registre, elle prend en charge la création de fuseaux horaires personnalisés. Elle prend également en charge la sérialisation et la désérialisation des informations de fuseau horaire.

Dans certains cas, tirer parti de la classe <xref:System.TimeZoneInfo> peut nécessiter du travail de développement supplémentaire. Si les valeurs de date et d’heure ne sont pas étroitement couplées avec les fuseaux horaires auxquels elles appartiennent, un travail supplémentaire est nécessaire. À moins que votre application ne fournisse un mécanisme de liaison d’une date et d’une heure avec son fuseau horaire associé, il est facile pour une valeur de date et d’heure particulière de se dissocier de son fuseau horaire. Une méthode pour lier ces informations consiste à définir une classe ou une structure qui contient à la fois la date/heure et son objet de fuseau horaire associé.

Pour tirer parti de la prise en charge des fuseaux horaires dans .NET, vous devez connaître le fuseau horaire auquel une valeur de date et d’heure appartient quand cet objet de date et d’heure est instancié. Le fuseau horaire est souvent inconnu, en particulier dans les applications Web ou réseau.

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](index.md)
