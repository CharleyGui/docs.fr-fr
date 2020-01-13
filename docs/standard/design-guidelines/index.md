---
title: Règles de conception de .NET Framework
titleSuffix: ''
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 8abe64476a5d3d1319dfa30dd7a06dc2bb541a0f
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904615"
---
# <a name="framework-design-guidelines"></a>Règles de conception de .NET Framework
Cette section fournit des instructions pour concevoir des bibliothèques qui étendent et interagissent avec l' .NET Framework. L’objectif est d’aider les concepteurs de bibliothèques à garantir la cohérence et la facilité d’utilisation des API en fournissant un modèle de programmation unifié qui est indépendant du langage de programmation utilisé pour le développement. Nous vous recommandons de suivre ces instructions de conception lors du développement de classes et de composants qui étendent les .NET Framework. Une conception incohérente de la bibliothèque affecte la productivité des développeurs et déconseille l’adoption.  
  
 Les instructions sont organisées en tant que recommandations simples précédées des termes `Do`, `Consider`, `Avoid`et `Do not`. Ces instructions sont destinées à aider les concepteurs de bibliothèques de classes à comprendre les compromis entre les différentes solutions. Il peut y avoir des situations où une bonne conception de bibliothèque exige que vous violiez ces règles de conception. Ce cas de figure doit être rare et il est important que vous ayez une raison claire et attrayante pour votre décision.  
  
 Ces instructions sont extraites des règles de *conception de la structure Book : conventions, idiomes et modèles pour les bibliothèques .net réutilisables, 2e édition*, par Krzysztof Cwalina et Brad Abrams.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Fournit des instructions pour nommer les assemblys, les espaces de noms, les types et les membres dans les bibliothèques de classes.  
  
 [Instructions pour la conception des types](../../../docs/standard/design-guidelines/type.md)  
 Fournit des instructions pour l’utilisation des classes, des interfaces, des énumérations, des structures et des types statiques et abstraits.  
  
 [Instructions de conception des membres](../../../docs/standard/design-guidelines/member.md)  
 Fournit des indications sur la conception et l’utilisation des propriétés, des méthodes, des constructeurs, des champs, des événements, des opérateurs et des paramètres.  
  
 [Conception en vue de l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Traite des mécanismes d’extensibilité tels que le sous-classing, l’utilisation d’événements, de membres virtuels et de rappels, et explique comment choisir les mécanismes qui répondent le mieux aux besoins de votre infrastructure.  
  
 [Instructions de conception pour les exceptions](../../../docs/standard/design-guidelines/exceptions.md)  
 Décrit les instructions de conception pour la conception, la levée et l’interception des exceptions.  
  
 [Indications relatives à l’utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Fournit des instructions pour l’utilisation de types communs tels que des tableaux, des attributs et des collections, la prise en charge de la sérialisation et la surcharge des opérateurs d’égalité.  
  
 [Modèles de design courants](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Fournit des instructions pour le choix et l’implémentation des propriétés de dépendance.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble](../../../docs/framework/get-started/overview.md)
- [Guide de développement](../../../docs/framework/development-guide.md)
