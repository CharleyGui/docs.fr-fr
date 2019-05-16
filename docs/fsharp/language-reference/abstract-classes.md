---
title: Classes abstraites
description: En savoir plus sur F# abstraite des classes qui laissent certains ou tous les membres non implémentés et représentent les fonctionnalités communes d’une grande diversité de types d’objets.
ms.date: 05/16/2016
ms.openlocfilehash: 8251d481c9056d40a0b13ae3c89353406986c116
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645540"
---
# <a name="abstract-classes"></a>Classes abstraites

*Les classes abstraites* sont des classes qui laissent une partie ou la totalité des membres non implémentés, afin que les implémentations puissent être fournies par les classes dérivées.

## <a name="syntax"></a>Syntaxe

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a>Notes

Dans la programmation orientée objet, une classe abstraite est utilisée comme classe de base d’une hiérarchie et représente les fonctionnalités communes d’une grande diversité de types d’objets. Comme le « abstrait » nom l’indique, les classes abstraites ne correspondent pas souvent directement à des entités concrètes dans le domaine du problème. Toutefois, ils ne représentent que nombreuses entités concrètes ont en commun.

Classes abstraites doivent avoir le `AbstractClass` attribut. Qu’ils peuvent avoir implémentés et non implémentés de membres. L’utilisation du terme *abstraite* lorsqu’il est appliqué à une classe est le même que dans d’autres langages .NET ; Toutefois, l’utilisation du terme *abstraite* lorsqu’il est appliqué aux méthodes (et propriétés) est un peu différent dans F# à partir de son utilisation dans d’autres langages .NET. Dans F#, lorsqu’une méthode est marquée avec le `abstract` mot clé, cela indique qu’un membre a une entrée, appelée un *emplacement de dispatch virtuel*, dans la table interne des fonctions virtuelles pour ce type. En d’autres termes, la méthode est virtuelle, bien que le `virtual` mot clé n’est pas utilisé dans le F# langage. Le mot clé `abstract` est utilisé sur les méthodes virtuelles, quel que soit la méthode est implémentée ou non. La déclaration d’un emplacement de dispatch virtuel est séparée de la définition d’une méthode pour cet emplacement de dispatch. Par conséquent, le F# équivalent d’une déclaration de méthode virtuelle et une définition dans un autre langage .NET est une combinaison d’une déclaration de méthode abstraite et une définition séparée, avec soit le `default` mot clé ou le `override` mot clé. Pour plus d’informations et des exemples, consultez [méthodes](members/methods.md).

Une classe est considérée comme abstraite uniquement s’il existe des méthodes abstraites qui sont déclarés mais non définis. Par conséquent, les classes qui ont des méthodes abstraites ne sont pas nécessairement des classes abstraites. Si une classe a des méthodes abstraites non définies, n’utilisez pas le **AbstractClass** attribut.

Dans la syntaxe précédente, *-modificateur d’accessibilité* peut être `public`, `private` ou `internal`. Pour plus d’informations, consultez [Contrôle d’accès](access-control.md).

Comme avec d’autres types, les classes abstraites peuvent avoir une classe de base et un ou plusieurs interfaces de base. Chaque classe de base ou l’interface apparaît sur une ligne distincte avec le `inherit` mot clé.

La définition du type d’une classe abstraite peut contenir des membres entièrement définis, mais il peut également contenir des membres abstraits. La syntaxe pour les membres abstraits est affichée séparément dans la syntaxe précédente. Dans cette syntaxe, la *signature de type* d’un membre est une liste qui contient les types de paramètre dans l’ordre et les types de retour, séparés par des `->` jetons et/ou `*` des jetons comme approprié pour curryfiées et basée sur des tuples paramètres. La syntaxe pour les signatures de type de membre abstrait est identique à utilisés dans les fichiers de signature et celle indiquée par IntelliSense dans l’éditeur de Code Visual Studio.

Le code suivant illustre une classe abstraite forme, qui dispose de deux classes dérivées non abstraite, carré et un cercle. L’exemple montre comment utiliser les propriétés, méthodes et classes abstraites. Dans l’exemple, la forme de classe abstraite représente les éléments communs des entités concrètes circle et square. Les fonctionnalités communes de toutes les formes (dans un système de coordonnées à deux dimensions) sont abstraites dans la classe Shape : la position sur la grille, un angle de rotation et les propriétés de l’aire et périmètre. Celles-ci peuvent être remplacées, à l’exception de position, le comportement qui ne peut pas modifier des formes.

La méthode de rotation peut être substituée, comme dans la classe de cercle, qui est indifférente à la rotation en raison de sa symétrie. Par conséquent, dans la classe de cercle, la méthode de rotation est remplacée par une méthode qui ne fait rien.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Sortie :**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Voir aussi

- [Classes](classes.md)
- [Membres](members/index.md)
- [Méthodes](members/methods.md)
- [Propriétés](members/Properties.md)
