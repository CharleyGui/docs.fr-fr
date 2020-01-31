---
title: Conception d'interfaces
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 544035180a5004bfe2f4c75c680116e52bf25f98
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744150"
---
# <a name="interface-design"></a>Conception d'interfaces
Bien que la plupart des API soient mieux modélisées à l’aide de classes et de structs, il existe des cas dans lesquels les interfaces sont plus appropriées ou sont la seule option.

 Le CLR ne prend pas en charge l’héritage multiple (autrement dit, les classes CLR ne peuvent pas hériter de plusieurs classes de base), mais autorisent les types à implémenter une ou plusieurs interfaces en plus de l’héritage d’une classe de base. Par conséquent, les interfaces sont souvent utilisées pour obtenir l’effet de plusieurs héritages. Par exemple, <xref:System.IDisposable> est une interface qui permet aux types de prendre en charge disposability indépendamment de toute autre hiérarchie d’héritage dans laquelle ils souhaitent participer.

 L’autre situation dans laquelle la définition d’une interface est appropriée est la création d’une interface commune qui peut être prise en charge par plusieurs types, y compris certains types valeur. Les types valeur ne peuvent pas hériter de types autres que <xref:System.ValueType>, mais ils peuvent implémenter des interfaces. par conséquent, l’utilisation d’une interface est la seule option pour fournir un type de base commun.

 ✔️ définir une interface si vous avez besoin d’une API commune prise en charge par un ensemble de types incluant des types valeur.

 ✔️ envisagez de définir une interface si vous devez prendre en charge ses fonctionnalités sur les types qui héritent déjà d’un autre type.

 ❌ Évitez d’utiliser des interfaces de marqueur (interfaces sans membres).

 Si vous avez besoin de marquer une classe comme ayant une caractéristique spécifique (marqueur), en général, utilisez un attribut personnalisé plutôt qu’une interface.

 ✔️ fournissez au moins un type qui est une implémentation d’une interface.

 Cela permet de valider la conception de l’interface. Par exemple, <xref:System.Collections.Generic.List%601> est une implémentation de l’interface <xref:System.Collections.Generic.IList%601>.

 ✔️ fournissez au moins une API qui utilise chaque interface que vous définissez (une méthode qui prend l’interface en tant que paramètre ou une propriété de type interface).

 Cela permet de valider la conception de l’interface. Par exemple, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consomme l’interface <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>.

 ❌ n’ajoutez pas de membres à une interface qui a déjà été expédiée.

 Cela entraînerait l’arrêt des implémentations de l’interface. Vous devez créer une nouvelle interface afin d’éviter les problèmes de Versioning.

 À l’exception des situations décrites dans ces instructions, vous devez, en général, choisir des classes plutôt que des interfaces pour concevoir des bibliothèques réutilisables de code managé.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Instructions pour la conception des types](../../../docs/standard/design-guidelines/type.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
