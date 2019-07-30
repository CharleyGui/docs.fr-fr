---
title: Classes abstraites
description: Découvrez les F# classes abstraites, qui laissent certains ou tous les membres non implémentés et représentent les fonctionnalités communes d’un ensemble diversifié de types d’objets.
ms.date: 05/16/2016
ms.openlocfilehash: a6bbfc23b858d5f3833f3f52b6dca46753080f03
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629683"
---
# <a name="abstract-classes"></a>Classes abstraites

Les *classes abstraites* sont des classes qui laissent certains ou tous les membres non implémentés, afin que les implémentations puissent être fournies par les classes dérivées.

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

Dans la programmation orientée objet, une classe abstraite est utilisée comme classe de base d’une hiérarchie et représente les fonctionnalités communes d’un ensemble diversifié de types d’objets. Comme son nom l’indique, les classes abstraites ne correspondent souvent pas directement aux entités concrètes dans le domaine du problème. Toutefois, elles représentent ce que de nombreuses entités concrètes ont en commun.

Les classes abstraites doivent `AbstractClass` avoir l’attribut. Elles peuvent avoir des membres implémentés et non implémentés. L’utilisation du terme *abstract* quand il est appliqué à une classe est la même que dans d’autres langages .net; Toutefois, l’utilisation du terme *abstract* quand il est appliqué aux méthodes (et aux propriétés) est un peu F# différente de celle de son utilisation dans d’autres langages .net. Dans F#, lorsqu’une méthode est marquée avec le `abstract` mot clé, cela indique qu’un membre a une entrée, appelée « *emplacement de dispatch virtuel*», dans la table interne des fonctions virtuelles pour ce type. En d’autres termes, la méthode est virtuelle, bien `virtual` que le mot clé ne soit F# pas utilisé dans le langage. Le mot `abstract` clé est utilisé sur les méthodes virtuelles, que la méthode soit implémentée ou non. La déclaration d’un emplacement de dispatch virtuel est distincte de la définition d’une méthode pour cet emplacement de dispatch. Par conséquent, F# l’équivalent d’une déclaration de méthode virtuelle et d’une définition dans un autre langage .net est une combinaison d’une déclaration de méthode abstraite et d' `default` une définition distincte `override` , avec le mot clé ou le mot clé. Pour plus d’informations et d’exemples, consultez [méthodes](./members/methods.md).

Une classe est considérée comme abstraite uniquement si des méthodes abstraites sont déclarées mais pas définies. Par conséquent, les classes qui ont des méthodes abstraites ne sont pas nécessairement des classes abstraites. À moins qu’une classe ait des méthodes abstraites non définies, n’utilisez pas l’attribut **AbstractClass** .

Dans la syntaxe précédente, *accessibility-modifier* peut être `public` `private` ou `internal`. Pour plus d’informations, consultez [Contrôle d’accès](access-control.md).

Comme pour les autres types, les classes abstraites peuvent avoir une classe de base et une ou plusieurs interfaces de base. Chaque classe de base ou interface apparaît sur une ligne distincte avec le `inherit` mot clé.

La définition de type d’une classe abstraite peut contenir des membres entièrement définis, mais elle peut également contenir des membres abstraits. La syntaxe des membres abstraits est indiquée séparément dans la syntaxe précédente. Dans cette syntaxe, la *signature de type* d’un membre est une liste qui contient les types de paramètres dans l’ordre et les types de `->` retour, séparés par des `*` jetons et/ou des jetons selon les besoins des paramètres curryfiés et à l’aide de tuples. La syntaxe des signatures de type de membre abstrait est la même que celle utilisée dans les fichiers de signature et celle indiquée par IntelliSense dans l’éditeur de Visual Studio Code.

Le code suivant illustre une forme de classe abstraite, qui a deux classes dérivées non abstraites, Square et Circle. L’exemple montre comment utiliser des classes, des méthodes et des propriétés abstraites. Dans l’exemple, la forme de classe abstraite représente les éléments communs des entités concrètes Circle et Square. Les caractéristiques communes de toutes les formes (dans un système de coordonnées à deux dimensions) sont extraites dans la classe Shape: la position sur la grille, un angle de rotation et les propriétés de zone et de périmètre. Elles peuvent être substituées, à l’exception de la position, le comportement des formes individuelles qui ne peuvent pas être modifiées.

La méthode de rotation peut être substituée, comme dans la classe Circle, qui est invariant de rotation en raison de sa symétrie. Ainsi, dans la classe Circle, la méthode de rotation est remplacée par une méthode qui ne fait rien.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Output:**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Voir aussi

- [Classes](classes.md)
- [Membres](./members/index.md)
- [Méthodes](./members/methods.md)
- [Propriétés](./members/Properties.md)
