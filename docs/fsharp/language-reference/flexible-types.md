---
title: Types flexibles
description: Découvrez comment utiliser F# l’annotation de type flexible, qui indique qu’un paramètre, une variable ou une valeur a un type qui est compatible avec un type spécifié.
ms.date: 05/16/2016
ms.openlocfilehash: 43caa6cd35630df648beda5cc43cffae2ecd6f6a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630263"
---
# <a name="flexible-types"></a>Types flexibles

Une *annotation de type flexible* indique qu’un paramètre, une variable ou une valeur a un type qui est compatible avec un type spécifié, où la compatibilité est déterminée par la position dans une hiérarchie orientée objet de classes ou d’interfaces. Les types flexibles sont particulièrement utiles lorsque la conversion automatique en types plus hauts dans la hiérarchie de types ne se produit pas, mais que vous souhaitez toujours permettre à votre fonctionnalité de fonctionner avec n’importe quel type dans la hiérarchie ou dans tout type qui implémente une interface.

## <a name="syntax"></a>Syntaxe

```fsharp
#type
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, *type* représente un type de base ou une interface.

Un type flexible est équivalent à un type générique qui a une contrainte qui limite les types autorisés aux types qui sont compatibles avec le type de base ou d’interface. Autrement dit, les deux lignes de code suivantes sont équivalentes.

```fsharp
#SomeType

'T when 'T :> SomeType
```

Les types flexibles sont utiles dans plusieurs types de situations. Par exemple, lorsque vous avez une fonction d’ordre supérieur (une fonction qui prend une fonction comme argument), il est souvent utile que la fonction retourne un type flexible. Dans l’exemple suivant, l’utilisation d’un type flexible avec un argument de séquence `iterate2` dans permet à la fonction d’ordre supérieur d’utiliser des fonctions qui génèrent des séquences, des tableaux, des listes et tout autre type énumérable.

Considérez les deux fonctions suivantes, dont l’une retourne une séquence, l’autre qui retourne un type flexible.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

En guise d’autre exemple, considérez la fonction de bibliothèque [Seq. Concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) :

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Vous pouvez passer les séquences énumérables suivantes à cette fonction:

- Liste de listes
- Liste de tableaux
- Tableau de listes
- Tableau de séquences
- Toute autre combinaison de séquences énumérables

Le code suivant utilise `Seq.concat` pour illustrer les scénarios que vous pouvez prendre en charge à l’aide de types flexibles.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

La sortie est la suivante.

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

Dans F#, comme dans d’autres langages orientés objet, il existe des contextes dans lesquels les types dérivés ou les types qui implémentent les interfaces sont convertis automatiquement en type de base ou en type d’interface. Ces conversions automatiques se produisent dans les arguments directs, mais pas lorsque le type est en position subordonnée, dans le cadre d’un type plus complexe, tel qu’un type de retour d’un type de fonction, ou en tant qu’argument de type. Par conséquent, la notation de type flexible est surtout utile lorsque le type auquel vous l’appliquez fait partie d’un type plus complexe.

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Génériques](./generics/index.md)
