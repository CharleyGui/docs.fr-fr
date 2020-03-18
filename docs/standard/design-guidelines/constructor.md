---
title: Conception de constructeurs
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400602"
---
# <a name="constructor-design"></a>Conception de constructeurs

Il existe deux types de constructeurs : les constructeurs de type et les constructeurs d’instance.

Les constructeurs de type sont statiques et sont gérés par le CLR avant que le type ne soit utilisé. Les constructeurs d’instance s’exécutent lorsqu’une instance d’un type est créée.

Les constructeurs de type ne peuvent pas prendre de paramètres. Les constructeurs d’instance peuvent. Les constructeurs d’instance qui ne prennent aucun paramètre sont souvent appelés constructeurs sans paramètres.

Les constructeurs sont le moyen le plus naturel de créer des instances de type. La plupart des développeurs vont rechercher et essayer d’utiliser un constructeur avant d’envisager d’autres moyens de créer des instances (telles que les méthodes d’usine).

✔️ CONSIDER fournissant des constructeurs simples, idéalement par défaut.

Un constructeur simple a un très petit nombre de paramètres, et tous les paramètres sont primitifs ou enums. Ces constructeurs simples augmentent la convivialité du cadre.

✔️ CONSIDER en utilisant une méthode d’usine statique au lieu d’un constructeur si la sémantique de l’opération désirée ne cartographie pas directement à la construction d’une nouvelle instance, ou si suivre les directives de conception du constructeur se sent contre nature.

✔️ UTILISEZ les paramètres du constructeur comme raccourcis pour définir les propriétés principales.

Il ne devrait y avoir aucune différence dans la sémantique entre l’utilisation du constructeur vide suivi par certains ensembles de propriété et l’utilisation d’un constructeur avec de multiples arguments.

✔️ NE pas utiliser le même nom pour les paramètres constructeur et une propriété si les paramètres du constructeur sont utilisés pour simplement définir la propriété.

La seule différence entre ces paramètres et les propriétés doit être le boîtier.

✔️ FAITES un travail minimal dans le constructeur.

Les constructeurs ne doivent pas faire beaucoup de travail autre que la capture des paramètres du constructeur. Le coût de tout autre traitement doit être retardé jusqu’à ce qu’il soit nécessaire.

✔️ NE jeter des exceptions de constructeurs d’instance, le cas échéant.

✔️ NE déclarez explicitement le constructeur public sans paramètres dans les classes, si un tel constructeur est nécessaire.

Si vous ne déclarez pas explicitement les constructeurs sur un type, de nombreuses langues (comme le C) ajouteront automatiquement un constructeur public sans paramètres. (Les classes abstraites obtiennent un constructeur protégé.)

L’ajout d’un constructeur paramétré à une classe empêche le compilateur d’ajouter le constructeur sans paramètres. Cela provoque souvent des changements de rupture accidentelle.

❌AVOID définissant explicitement les constructeurs sans paramètres sur les structs.

Cela rend la création de tableau plus rapide, parce que si le constructeur sans paramètres n’est pas défini, il n’a pas à être exécuté sur chaque fente dans le tableau. Notez que de nombreux compilateurs, y compris le C, ne permettent pas aux structs d’avoir des constructeurs sans paramètres pour cette raison.

❌AVOID appelant des membres virtuels sur un objet à l’intérieur de son constructeur.

L’appel d’un membre virtuel entraînera l’appel du remplacement le plus dérivé, même si le constructeur du type le plus dérivé n’a pas encore été entièrement exécuté.

## <a name="type-constructor-guidelines"></a>Lignes directrices sur les constructeurs de types

✔️ NE rendre les constructeurs statiques privés.

Un constructeur statique, également appelé un constructeur de classe, est utilisé pour initialiser un type. Le CLR appelle le constructeur statique avant la création de la première instance du type ou que des membres statiques de ce type soient appelés. L’utilisateur n’a aucun contrôle sur quand le constructeur statique est appelé. Si un constructeur statique n’est pas privé, il peut être appelé par code autre que le CLR. Selon les opérations effectuées dans le constructeur, cela peut causer un comportement inattendu. Le compilateur CMD force les constructeurs statiques à être privés.

❌NE PAS jeter des exceptions des constructeurs statiques.

Si une exception est projetée à partir d’un constructeur type, le type n’est pas utilisable dans le domaine actuel de l’application.

✔️ CONSIDER initialisant les champs statiques en ligne plutôt que d’utiliser explicitement des constructeurs statiques, parce que le temps d’exécution est capable d’optimiser les performances des types qui n’ont pas un constructeur statique explicitement défini.

*Parts © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Instructions de conception des membres](../../../docs/standard/design-guidelines/member.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
