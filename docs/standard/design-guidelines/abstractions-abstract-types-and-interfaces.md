---
title: Abstractions (Types et interfaces abstraits)
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
ms.openlocfilehash: 014144764609c8a7faa87f3d080900824f9189eb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709580"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Abstractions (Types et interfaces abstraits)
Une abstraction est un type qui décrit un contrat, mais qui ne fournit pas une implémentation complète du contrat. Les abstractions sont généralement implémentées en tant que classes abstraites ou interfaces, et elles sont fournies avec un ensemble bien défini de documentation de référence décrivant la sémantique requise des types qui implémentent le contrat. Voici quelques-unes des abstractions les plus importantes du .NET Framework : <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>et <xref:System.Object>.  
  
 Vous pouvez étendre des frameworks en implémentant un type concret qui prend en charge le contrat d’une abstraction et à l’aide de ce type concret avec les API d’infrastructure consommant (fonctionnant sur) l’abstraction.  
  
 Une abstraction significative et utile qui peut résister au test de temps est très difficile à concevoir. La difficulté principale est l’obtention du jeu de membres approprié, et pas plus ou moins. Si une abstraction a trop de membres, elle devient difficile, voire impossible à implémenter. S’il a trop peu de membres pour la fonctionnalité promis, il devient inutile dans de nombreux scénarios intéressants.  
  
 Un trop grand nombre d’abstractions dans une infrastructure affecte également la convivialité de l’infrastructure. Il est souvent assez difficile de comprendre une abstraction sans comprendre comment elle s’intègre à la plus grande image des implémentations concrètes et aux API opérant sur l’abstraction. En outre, les noms des abstractions et de leurs membres sont nécessairement abstraits, ce qui les rend souvent énigmatiques et incompréhensibles sans avoir d’abord à comprendre le contexte plus large de leur utilisation.  
  
 Toutefois, les abstractions offrent une extensibilité extrêmement puissante que les autres mécanismes d’extensibilité ne correspondent pas souvent. Ils sont au cœur de nombreux modèles architecturaux, tels que les plug-ins, l’inversion de contrôle (IoC), les pipelines, etc. Ils sont également extrêmement importants pour la testabilité des frameworks. De bonnes abstractions permettent de remplacer les dépendances lourdes dans le cadre des tests unitaires. En résumé, les abstractions sont responsables de la richesse recherchée des frameworks orientés objet modernes.  
  
 **X DO NOT** fournissent des abstractions, sauf si elles sont testées par le développement de plusieurs implémentations concrètes et consomme les abstractions des API.  
  
 **✓ DO** choisir entre une classe abstraite et une interface avec soin lors de la conception d’une abstraction.  
  
 **✓ CONSIDER** fournissant des tests de référence pour les implémentations concrètes d’abstractions. Ces tests doivent permettre aux utilisateurs de tester si leurs implémentations implémentent correctement le contrat.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Conception en vue de l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
