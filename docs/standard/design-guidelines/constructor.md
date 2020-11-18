---
title: Conception de constructeurs
ms.date: 10/22/2008
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
ms.openlocfilehash: 27fb73aa01adf31117d1b82724873db3a03fd269
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821396"
---
# <a name="constructor-design"></a>Conception de constructeurs

Il existe deux genres de constructeurs : des constructeurs de type et des constructeurs d’instance.

Les constructeurs de type sont statiques et sont exécutés par le CLR avant l’utilisation du type. Les constructeurs d’instance s’exécutent lors de la création d’une instance d’un type.

Les constructeurs de type ne peuvent pas accepter de paramètres. Les constructeurs d’instance peuvent. Les constructeurs d’instance qui ne prennent pas de paramètres sont souvent appelés constructeurs sans paramètre.

Les constructeurs sont le moyen le plus naturel de créer des instances d’un type. La plupart des développeurs recherchent et essaient d’utiliser un constructeur avant qu’ils n’envisagent d’autres façons de créer des instances (comme les méthodes de fabrique).

✔️ envisagez de fournir des constructeurs simples, idéalement par défaut.

Un constructeur simple possède un très petit nombre de paramètres, et tous les paramètres sont des primitives ou des enums. Ces constructeurs simples augmentent l’utilisation de l’infrastructure.

✔️ envisagez d’utiliser une méthode de fabrique statique à la place d’un constructeur si la sémantique de l’opération souhaitée ne mappe pas directement à la construction d’une nouvelle instance, ou si les règles de conception de constructeur se présentent comme non naturelles.

✔️ Utilisez des paramètres de constructeur comme raccourcis pour définir des propriétés principales.

Il ne doit y avoir aucune différence de sémantique entre l’utilisation du constructeur vide suivi par certains jeux de propriétés et l’utilisation d’un constructeur avec plusieurs arguments.

✔️ Utilisez le même nom pour les paramètres du constructeur et une propriété si les paramètres du constructeur sont utilisés pour définir simplement la propriété.

La seule différence entre ces paramètres et les propriétés doit être la casse.

✔️ EFFECTUER un travail minimal dans le constructeur.

Les constructeurs ne doivent pas effectuer de nombreuses tâches autres que la capture des paramètres de constructeur. Le coût d’un autre traitement doit être retardé jusqu’à ce qu’il soit nécessaire.

✔️ lever des exceptions à partir de constructeurs d’instance, le cas échéant.

✔️ déclarer explicitement le constructeur sans paramètre public dans les classes, si un tel constructeur est requis.

Si vous ne déclarez pas explicitement de constructeurs sur un type, de nombreux langages (tels que C#) ajouteront automatiquement un constructeur sans paramètre public. (Les classes abstraites obtiennent un constructeur protégé.)

L’ajout d’un constructeur paramétrable à une classe empêche le compilateur d’ajouter le constructeur sans paramètre. Cela provoque souvent des modifications avec rupture accidentelles.

❌ Évitez de définir explicitement des constructeurs sans paramètre sur des structs.

La création de tableau est ainsi plus rapide, car si le constructeur sans paramètre n’est pas défini, il n’est pas nécessaire qu’il soit exécuté sur chaque emplacement du tableau. Notez que de nombreux compilateurs, y compris C#, n’autorisent pas les structs à avoir des constructeurs sans paramètre pour cette raison.

❌ Évitez d’appeler des membres virtuels sur un objet à l’intérieur de son constructeur.

L’appel d’un membre virtuel entraîne l’appel de la substitution la plus dérivée, même si le constructeur du type le plus dérivé n’a pas encore été complètement exécuté.

## <a name="type-constructor-guidelines"></a>Directives de constructeur de type

✔️ rendent les constructeurs statiques privés.

Un constructeur statique, également appelé constructeur de classe, est utilisé pour initialiser un type. Le CLR appelle le constructeur statique avant la création de la première instance du type ou l’appel de tous les membres statiques de ce type. L’utilisateur n’a aucun contrôle sur le moment où le constructeur statique est appelé. Si un constructeur statique n’est pas privé, il peut être appelé par un code autre que le CLR. Selon les opérations effectuées dans le constructeur, cela peut provoquer un comportement inattendu. Le compilateur C# force la confidentialité des constructeurs statiques.

❌ NE levez pas d’exceptions à partir de constructeurs statiques.

Si une exception est levée à partir d’un constructeur de type, le type n’est pas utilisable dans le domaine d’application actuel.

✔️ envisagez d’initialiser des champs statiques inline plutôt que d’utiliser explicitement des constructeurs statiques, car le runtime est en mesure d’optimiser les performances des types qui n’ont pas de constructeur statique défini explicitement.

*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Recommandations en matière de conception de membres](member.md)
- [Directives de conception d’infrastructure](index.md)
