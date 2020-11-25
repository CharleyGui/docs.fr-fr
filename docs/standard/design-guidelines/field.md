---
title: Conception de champs
ms.date: 10/22/2008
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 4329ca9e74fa02411bd39755a432fc7d4858597d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706695"
---
# <a name="field-design"></a>Conception de champs

Le principe de l’encapsulation est l’une des notions les plus importantes en matière de conception orientée objet. Ce principe stipule que les données stockées dans un objet ne doivent être accessibles qu’à cet objet.

 Une méthode utile pour interpréter le principe consiste à indiquer qu’un type doit être conçu de manière à ce que les modifications apportées aux champs de ce type (modification de nom ou de type) puissent être effectuées sans interrompre le code autre que pour les membres du type. Cette interprétation implique immédiatement que tous les champs doivent être privés.

 Nous excluons les champs constants et statiques en lecture seule de cette restriction stricte, car ces champs, presque par définition, ne sont jamais requis pour la modification.

 ❌ NE fournissez pas de champs d’instance publics ou protégés.

 Vous devez fournir des propriétés pour accéder aux champs au lieu de les rendre publics ou protégés.

 ✔️ Utilisez des champs constants pour les constantes qui ne changeront jamais.

 Le compilateur grave les valeurs des champs const directement dans le code appelant. Par conséquent, les valeurs const ne peuvent jamais être modifiées sans risque d’interruption de la compatibilité.

 ✔️ Utilisez des champs statiques publics `readonly` pour les instances d’objet prédéfinies.

 S’il existe des instances prédéfinies du type, déclarez-les en tant que champs statiques publics en lecture seule du type lui-même.

 ❌ N’assignez pas d’instances de types mutables à des `readonly` champs.

 Un type mutable est un type dont les instances peuvent être modifiées une fois qu’elles ont été instanciées. Par exemple, les tableaux, la plupart des collections et des flux sont des types mutables, mais <xref:System.Int32?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType> et <xref:System.String?displayProperty=nameWithType> sont tous immuables. Le modificateur en lecture seule sur un champ de type référence empêche le remplacement de l’instance stockée dans le champ, mais n’empêche pas la modification des données d’instance du champ en appelant des membres qui modifient l’instance.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Recommandations en matière de conception de membres](member.md)
- [Directives de conception d’infrastructure](index.md)
