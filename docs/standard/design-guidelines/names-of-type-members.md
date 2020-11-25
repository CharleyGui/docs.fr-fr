---
title: Noms de membres de type
description: Découvrez les instructions pour nommer des membres de type dans .NET, tels que les méthodes, les propriétés, les événements et les champs.
ms.date: 10/22/2008
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: 409e881198a359fa28356e22ea73d5b724742a0d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706474"
---
# <a name="names-of-type-members"></a>Noms de membres de type

Les types se composent de membres, de méthodes, de propriétés, d’événements, de constructeurs et de champs. Les sections suivantes décrivent les règles de nommage des membres de type.

## <a name="names-of-methods"></a>Noms des méthodes

 Comme les méthodes permettent d’entreprendre des actions, les règles de conception exigent que les noms des méthodes soient des verbes ou des expressions verbales. Cette règle sert également à distinguer les noms de méthode des noms de propriété et de type, qui sont des expressions nominales ou adjectivales.

 ✔️ Donnez des noms de méthodes qui sont des verbes ou des expressions de verbe.

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a>Noms des propriétés

 Contrairement aux autres membres, les noms des propriétés doivent être des expressions nominales ou adjectivales. C’est parce que les propriétés font référence à des données, donc leur nom doivent le refléter. La casse Pascal est toujours utilisée pour les noms de propriété.

 ✔️ Nommez les propriétés à l’aide d’un nom, d’une expression nominale ou d’un adjectif.

 ❌ N’avez pas de propriétés qui correspondent au nom des méthodes « obtenir » comme dans l’exemple suivant :

 `public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`

 Ce modèle indique typiquement que la propriété doit vraiment être une méthode.

 ✔️ Nommez les propriétés de collection avec une expression pluriel décrivant les éléments de la collection au lieu d’utiliser une expression singulière suivie de « List » ou « collection ».

 ✔️ Nommez les propriétés booléennes avec une expression affirmative ( `CanSeek` au lieu de `CantSeek` ). Si vous le souhaitez, vous pouvez également préfixer les propriétés booléennes avec « is », « CAN » ou « has », mais uniquement à l’endroit où elle ajoute value.

 ✔️ envisagez de donner à une propriété le même nom que son type.

 Par exemple, la propriété suivante obtient et définit correctement une valeur enum nommée `Color`, donc la propriété est nommée `Color`:

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a>Noms des événements

 Les événements font toujours référence à une action, soit une action en cours, soit une action passée. Par conséquent, comme avec les méthodes, les événements sont nommés avec des verbes, le temps des verbes servant à indiquer l’heure où l’événement est déclenché.

 ✔️ Nommez les événements avec un verbe ou une phrase verbale.

 Par exemple, `Clicked`, `Painting`, `DroppedDown`, etc.

 ✔️ Donnez des noms d’événements avec un concept antérieur et postérieur, en utilisant les dizaines présents et précédents.

 Par exemple, un événement de fermeture déclenché avant la fermeture d’une fenêtre serait nommé `Closing`, tandis qu’un événement déclenché après la fermeture de la fenêtre serait nommé `Closed`.

 ❌ N’utilisez pas les préfixes ou les suffixes « Before » ou « after » pour indiquer les pré-et post-événements. Utilisez les temps du présent et du passé, comme nous venons de le décrire.

 ✔️ Nommez les gestionnaires d’événements (délégués utilisés comme types d’événements) avec le suffixe « EventHandler », comme indiqué dans l’exemple suivant :

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 ✔️ Utilisez deux paramètres nommés `sender` et `e` dans des gestionnaires d’événements.

 Le paramètre d’expéditeur représente l’objet qui a déclenché l’événement. Le paramètre d’expéditeur est généralement de type `object`, même s’il est possible d’employer un type plus spécifique.

 ✔️ Nommez les classes d’argument d’événement avec le suffixe « EventArgs ».

## <a name="names-of-fields"></a>Noms des champs

 Les règles de nommage des champs s’appliquent à des champs publics et protégés statiques. Les champs internes et privés ne sont pas couverts par les règles, tandis que les champs d’instance publics ou protégés ne sont pas autorisés par les [règles de conception de membres](member.md).

 ✔️ Utilisez PascalCasing dans les noms de champs.

 ✔️ Nommez les champs à l’aide d’un nom, d’une expression nominale ou d’un adjectif.

 ❌ N’utilisez pas de préfixe pour les noms de champs.

 Par exemple, n’utilisez pas « g_ » ou « s_ » pour indiquer des champs statiques.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Instructions d’affectation de noms](naming-guidelines.md)
