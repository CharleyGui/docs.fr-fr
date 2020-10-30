---
title: Vue d’ensemble des fuseaux horaires
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET], about time zones
- transition time [.NET]
- TimeZoneInfo class, about TimeZoneInfo class
- time zones [.NET], creating
- invalid time [.NET]
- fixed rule [.NET]
- ambiguous time [.NET]
- floating rule [.NET]
- daylight saving time [.NET]
- adjustment rule [.NET]
- time zones [.NET], terminology
ms.assetid: c4b7ed01-5e38-4959-a3b6-ef9765d6ccf1
ms.openlocfilehash: 0f0fdbe4b63ddc9d55f7397fa71198d72e60e669
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93064104"
---
# <a name="time-zone-overview"></a>Vue d’ensemble des fuseaux horaires

La <xref:System.TimeZoneInfo> classe simplifie la création d’applications prenant en charge les fuseaux horaires. La <xref:System.TimeZone> classe prend en charge l’utilisation du fuseau horaire local et du temps universel coordonné (UTC, Universal Time Coordinated). La <xref:System.TimeZoneInfo> classe prend en charge ces deux zones ainsi que tout fuseau horaire sur lequel des informations sont prédéfinies dans le registre. Vous pouvez également utiliser <xref:System.TimeZoneInfo> pour définir des fuseaux horaires personnalisés sur lesquels le système ne dispose d’aucune information.

## <a name="time-zone-essentials"></a>Notions fondamentales sur les fuseaux horaires

Un fuseau horaire est une région géographique dans laquelle la même heure est utilisée. En général, mais pas toujours, des fuseaux horaires adjacents ont une heure d’écart. L’heure dans n’importe quel fuseau horaire du monde peut être exprimée comme un décalage par rapport au temps universel coordonné (UTC).

La plupart des fuseaux horaires du monde prennent en charge l’heure d’été. L’heure d’été essaie d’optimiser les heures de clarté en avançant l’heure d’une heure au printemps ou au début de l’été, puis en rétablissant l’heure normale (ou standard) à la fin de l’été ou en automne. Ces variations par rapport à l’heure d’hiver sont appelées règles d’ajustement.

Le passage à l’heure d’été ou à l’heure d’hiver dans un fuseau horaire particulier peut être défini par une règle d’ajustement fixe ou flottante. Une règle d’ajustement fixe définit une date particulière à laquelle le passage à l’heure d’été ou à l’heure d’hiver se produit chaque année. Par exemple, le passage à l’heure d’hiver qui se produit chaque année le 25 octobre suit une règle d’ajustement fixe. Les règles d’ajustement flottantes sont beaucoup plus courantes. Elles définissent un jour particulier d’une semaine particulière d’un mois particulier pour le passage à l’heure d’été ou à l’heure d’hiver. Par exemple, le passage à l’heure d’été qui se produit le troisième dimanche de mars suit une règle d’ajustement flottante.

Pour les fuseaux horaires qui prennent en charge des règles d’ajustement, le passage à l’heure d’hiver et à l’heure d’été crée deux types d’heures anormales : des heures non valides et des heures ambiguës. Une heure non valide est une heure inexistante, créée par le passage à l’heure d’été. Par exemple, si ce passage a lieu un jour particulier à 2:00 et fait que l’heure devient 3:00, tout intervalle de temps compris entre 2:00 et 2:59:59 est non valide. Une heure ambiguë est une heure qui peut correspondre à deux heures différentes dans un même fuseau horaire. Elle est créée par le passage à l’heure d’hiver. Par exemple, si ce passage a lieu un jour particulier à 2:00 et fait que l’heure devient 1:00, tout intervalle de temps compris entre 1:00 et 1:59:59 peut être interprété comme une heure d’hiver ou une heure d’été.

## <a name="time-zone-terminology"></a>Terminologie des fuseaux horaires

Le tableau suivant définit les termes couramment utilisés lors de l’utilisation de fuseaux horaires et du développement d’applications prenant en charge les fuseaux horaires.

| Terme            | Définition |
| --------------- | ---------- |
| Règle d’ajustement | Règle qui définit les dates de passage à l’heure d’été et de retour à l’heure d’hiver. Chaque règle d’ajustement a une date de début et de fin qui définit le moment où la règle est en place (par exemple, la règle d’ajustement est en vigueur à partir du 1er janvier 1986 au 31 décembre 2006), d’un Delta (durée pendant laquelle l’heure standard change à la suite de l’application de la règle d’ajustement) et des informations sur la date et l’heure spécifiques auxquelles les transitions doivent se produire pendant la période d’ajustement. Les transitions peuvent suivre une règle fixe ou une règle flottante. |
| Heure ambiguë  | Heure qui peut correspondre à deux heures différentes dans un même fuseau horaire. Cela se produit lorsque l’heure de l’horloge est retardée, comme lors du passage à l’heure d’hiver dans un fuseau horaire. Par exemple, si ce passage a lieu un jour particulier à 2:00 et fait que l’heure devient 1:00, tout intervalle de temps compris entre 1:00 et 1:59:59 peut être interprété comme une heure d’hiver ou une heure d’été. |
| Règle fixe      | Règle d’ajustement qui définit une date particulière pour le passage à l’heure d’été ou à l’heure d’hiver. Par exemple, le passage à l’heure d’hiver qui se produit chaque année le 25 octobre suit une règle d’ajustement fixe. |
| Règle flottante   | Règle d’ajustement qui définit un jour particulier d’une semaine particulière d’un mois particulier pour le passage à l’heure d’été ou à l’heure d’hiver. Par exemple, le passage à l’heure d’été qui se produit le troisième dimanche de mars suit une règle d’ajustement flottante. |
| Heure non valide    | Heure inexistante, créée par le passage à l’heure d’été. Elle intervient lorsque l’heure est avancée, par exemple lors du passage de l’heure d’hiver d’un fuseau horaire à son heure d’été. Par exemple, si ce passage a lieu un jour particulier à 2:00 et fait que l’heure devient 3:00, tout intervalle de temps compris entre 2:00 et 2:59:59 est non valide. |
| Durée de transition | Informations sur un changement d’heure spécifique, tel que le passage de l’heure d’été à l’heure d’hiver, ou vice versa, dans un fuseau horaire particulier. |

## <a name="time-zones-and-the-timezoneinfo-class"></a>Fuseaux horaires et classe TimeZoneInfo

Dans .NET, un <xref:System.TimeZoneInfo> objet représente un fuseau horaire. La <xref:System.TimeZoneInfo> classe comprend une <xref:System.TimeZoneInfo.GetAdjustmentRules%2A> méthode qui retourne un tableau d' <xref:System.TimeZoneInfo.AdjustmentRule> objets. Chaque élément de ce tableau fournit des informations sur la transition vers et depuis l’heure d’été pour une période particulière. (Pour les fuseaux horaires qui ne prennent pas en charge l’heure d’été, la méthode retourne un tableau vide.) Chaque <xref:System.TimeZoneInfo.AdjustmentRule> objet a un <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A> et une <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A> propriété qui définit la date et l’heure particulières de la transition vers et depuis l’heure d’été. La <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A> propriété indique si cette transition est fixe ou flottante.

.NET s’appuie sur les informations de fuseau horaire fournies par le système d’exploitation Windows et stockées dans le registre. En raison du nombre de fuseaux horaires de la terre, tous les fuseaux horaires existants ne sont pas représentés dans le registre. En outre, étant donné que le Registre est une structure dynamique, les fuseaux horaires prédéfinis peuvent être ajoutés ou supprimés de celui-ci. Enfin, le registre ne contient pas nécessairement de données de fuseau horaire historiques. Par exemple, dans Windows XP, le registre contient des données relatives à un seul ensemble d’ajustements de fuseau horaire. Windows Vista prend en charge les données de fuseau horaire dynamiques, ce qui signifie qu’un seul fuseau horaire peut avoir plusieurs règles d’ajustement qui s’appliquent à des intervalles spécifiques d’années. Toutefois, la plupart des fuseaux horaires définis dans le Registre Windows Vista et qui prennent en charge l’heure d’été ont uniquement une ou deux règles d’ajustement prédéfinies.

La dépendance de la <xref:System.TimeZoneInfo> classe sur le registre signifie qu’une application prenant en charge les fuseaux horaires ne peut pas être certain qu’un fuseau horaire particulier est défini dans le registre. Par conséquent, la tentative d’instancier un fuseau horaire spécifique (autre que le fuseau horaire local ou le fuseau horaire qui représente l’heure UTC) doit utiliser la gestion des exceptions. Elle doit également fournir une méthode permettant à l’application de continuer si un <xref:System.TimeZoneInfo> objet requis ne peut pas être instancié à partir du Registre.

Pour gérer l’absence d’un fuseau horaire requis, la <xref:System.TimeZoneInfo> classe comprend une <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode, que vous pouvez utiliser pour créer des fuseaux horaires personnalisés qui ne se trouvent pas dans le registre. Pour plus d’informations sur la création d’un fuseau horaire personnalisé, consultez [Comment : créer des fuseaux horaires sans règles d’ajustement](create-time-zones-without-adjustment-rules.md) et [Comment : créer des fuseaux horaires avec des règles d’ajustement](create-time-zones-with-adjustment-rules.md). En outre, vous pouvez utiliser la <xref:System.TimeZoneInfo.ToSerializedString%2A> méthode pour convertir un fuseau horaire nouvellement créé en une chaîne et l’enregistrer dans un magasin de données (tel qu’une base de données, un fichier texte, le registre ou une ressource d’application). Vous pouvez ensuite utiliser la <xref:System.TimeZoneInfo.FromSerializedString%2A> méthode pour reconvertir cette chaîne en <xref:System.TimeZoneInfo> objet. Pour plus d’informations, consultez [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](save-time-zones-to-an-embedded-resource.md) et [Comment : restaurer des fuseaux horaires à partir d’une ressource incorporée](restore-time-zones-from-an-embedded-resource.md).

Étant donné que chaque fuseau horaire est caractérisé par un décalage de base par rapport à l’heure UTC, ainsi que par un décalage par rapport à l’heure UTC qui reflète toutes les règles d’ajustement existantes, une heure dans un fuseau horaire peut être facilement convertie en une heure dans un autre fuseau horaire. À cet effet, l' <xref:System.TimeZoneInfo> objet inclut plusieurs méthodes de conversion, notamment :

- <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>, qui convertit le temps universel coordonné (UTC) en heure dans un fuseau horaire désigné.

- <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>, qui convertit l’heure d’un fuseau horaire désigné en heure UTC.

- <xref:System.TimeZoneInfo.ConvertTime%2A>, qui convertit l’heure d’un fuseau horaire désigné en heure d’un autre fuseau horaire désigné.

- <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>, qui utilise des identificateurs de fuseau horaire (au lieu d' <xref:System.TimeZoneInfo> objets) comme paramètres pour convertir l’heure d’un fuseau horaire désigné en heure d’un autre fuseau horaire désigné.

Pour plus d’informations sur la conversion d’heures entre fuseaux horaires, consultez [Conversion d’heures entre fuseaux horaires](converting-between-time-zones.md).

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](index.md)
