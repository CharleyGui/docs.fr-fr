---
title: Événements et rappels
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
ms.openlocfilehash: 7dab759ba48104530fc41e46f6f2bba18d6c4456
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741659"
---
# <a name="events-and-callbacks"></a>Événements et rappels
Les rappels sont des points d’extensibilité qui permettent à un Framework d’effectuer un rappel dans le code utilisateur via un délégué. Ces délégués sont généralement passés à l’infrastructure par le biais d’un paramètre d’une méthode.

 Les événements sont un cas spécial de rappels qui prend en charge une syntaxe pratique et cohérente pour fournir le délégué (un gestionnaire d’événements). En outre, la saisie semi-automatique des instructions de Visual Studio et les concepteurs fournissent de l’aide pour l’utilisation des API basées sur les événements. (Voir [conception des événements](../../../docs/standard/design-guidelines/event.md).)

 ✔️ envisagez d’utiliser des rappels pour permettre aux utilisateurs de fournir un code personnalisé à exécuter par le Framework.

 ✔️ envisagez d’utiliser des événements pour permettre aux utilisateurs de personnaliser le comportement d’une infrastructure sans avoir besoin de comprendre la conception orientée objet.

 ✔️ préférez des événements aux rappels simples, car ils sont plus familiers à un plus grand nombre de développeurs et sont intégrés à la saisie semi-automatique des instructions Visual Studio.

 ❌ Évitez d’utiliser des rappels dans les API sensibles aux performances.

 ✔️ Utilisez les nouveaux types `Func<...>`, `Action<...>`ou `Expression<...>` au lieu des délégués personnalisés, lors de la définition d’API avec des rappels.

 `Func<...>` et `Action<...>` représentent des délégués génériques. `Expression<...>` représente des définitions de fonction qui peuvent être compilées et appelées par la suite au moment de l’exécution, mais qui peuvent également être sérialisées et passées à des processus distants.

 ✔️ Mesurez et comprenez les implications en matière de performances de l’utilisation de `Expression<...>`, au lieu d’utiliser des délégués `Func<...>` et `Action<...>`.

 les types de `Expression<...>` sont dans la plupart des cas logiquement équivalents aux délégués `Func<...>` et `Action<...>`. La principale différence réside dans le fait que les délégués sont destinés à être utilisés dans les scénarios de processus local. les expressions sont prévues dans les cas où il est bénéfique et possible d’évaluer l’expression dans un processus ou un ordinateur distant.

 ✔️ comprenez qu’en appelant un délégué, vous exécutez du code arbitraire et cela peut avoir des répercussions en matière de sécurité, d’exactitude et de compatibilité.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Conception en vue de l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
