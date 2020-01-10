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
ms.openlocfilehash: 80c16e29f1d8a0653295ebc3cf25be6fb78b7dc9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709411"
---
# <a name="events-and-callbacks"></a>Événements et rappels
Les rappels sont des points d’extensibilité qui permettent à un Framework d’effectuer un rappel dans le code utilisateur via un délégué. Ces délégués sont généralement passés à l’infrastructure par le biais d’un paramètre d’une méthode.  
  
 Les événements sont un cas spécial de rappels qui prend en charge une syntaxe pratique et cohérente pour fournir le délégué (un gestionnaire d’événements). En outre, la saisie semi-automatique des instructions de Visual Studio et les concepteurs fournissent de l’aide pour l’utilisation des API basées sur les événements. (Voir [conception des événements](../../../docs/standard/design-guidelines/event.md).)  
  
 **✓ CONSIDER** à l’aide des rappels pour permettre aux utilisateurs de fournir un code personnalisé doit être exécuté par l’infrastructure.  
  
 **✓ CONSIDER** à l’aide d’événements pour permettre aux utilisateurs de personnaliser le comportement d’une infrastructure sans avoir besoin pour comprendre la conception orientée objet.  
  
 **✓ DO** de préférence des événements via des rappels ordinaires, car ils sont plus facile pour un grand nombre de développeurs et sont intégrés à la fin de l’instruction Visual Studio.  
  
 **X AVOID** à l’aide de rappels dans les API sensibles aux performances.  
  
 **✓ DO** utiliser la nouvelle `Func<...>`, `Action<...>`, ou `Expression<...>` types à la place des délégués personnalisés lors de la définition d’API avec des rappels.  
  
 `Func<...>` et `Action<...>` représentent des délégués génériques. `Expression<...>` représente des définitions de fonction qui peuvent être compilées et appelées par la suite au moment de l’exécution, mais qui peuvent également être sérialisées et passées à des processus distants.  
  
 **✓ DO** mesurer et comprendre les implications en matière de performances de l’utilisation de `Expression<...>`, au lieu d’utiliser `Func<...>` et `Action<...>` délégués.  
  
 les types de `Expression<...>` sont dans la plupart des cas logiquement équivalents aux délégués `Func<...>` et `Action<...>`. La principale différence réside dans le fait que les délégués sont destinés à être utilisés dans les scénarios de processus local. les expressions sont prévues dans les cas où il est bénéfique et possible d’évaluer l’expression dans un processus ou un ordinateur distant.  
  
 **✓ DO** comprendre que par l’appel d’un délégué, vous exécutez du code arbitraire et qui pourraient avoir des répercussions de sécurité, d’exactitude et de compatibilité.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Conception en vue de l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
