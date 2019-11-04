---
title: Unit, type
description: Découvrez comment le F# type « unité » est souvent utilisé pour conserver l’emplacement où une valeur est requise par la syntaxe du langage quand aucune valeur n’est requise ou souhaitée.
ms.date: 05/16/2016
ms.openlocfilehash: a5960fb05af50486a78345d10a5ad913e65729e3
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424029"
---
# <a name="unit-type"></a>Unit, type

Le type de `unit` est un type qui indique l’absence d’une valeur spécifique ; le type de `unit` n’a qu’une seule valeur, qui joue le rôle d’espace réservé quand aucune autre valeur n’existe ou n’est nécessaire.

## <a name="syntax"></a>Syntaxe

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Notes

Chaque F# expression doit être évaluée à une valeur. Pour les expressions qui ne génèrent pas une valeur intéressante, la valeur de type `unit` est utilisée. Le type de `unit` ressemble au type de `void` dans des langages tels que C# et C++.

Le type de `unit` a une valeur unique, et cette valeur est indiquée par le jeton `()`.

La valeur du type de `unit` est souvent utilisée en F# programmation pour conserver l’emplacement où une valeur est requise par la syntaxe de langage, mais quand aucune valeur n’est requise ou souhaitée. Par exemple, il peut s’agir de la valeur de retour d’une fonction `printf`. Étant donné que les actions importantes de l’opération `printf` se produisent dans la fonction, la fonction n’a pas besoin de retourner une valeur réelle. Par conséquent, la valeur de retour est de type `unit`.

Certaines constructions attendent une valeur `unit`. Par exemple, une liaison de `do` ou tout code au niveau supérieur d’un module est supposé correspondre à une valeur de `unit`. Le compilateur signale un avertissement quand une liaison ou un code `do` au niveau supérieur d’un module produit un résultat autre que la valeur `unit` qui n’est pas utilisée, comme indiqué dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Cet avertissement est une caractéristique de la programmation fonctionnelle. Il n’apparaît pas dans d’autres langages de programmation .NET. Dans un programme purement fonctionnel, dans lequel les fonctions n’ont pas d’effets secondaires, la valeur de retour finale est le seul résultat d’un appel de fonction. Par conséquent, lorsque le résultat est ignoré, il s’agit d’une erreur de programmation possible. Bien F# que ne soit pas un langage de programmation purement fonctionnel, il est recommandé de suivre le style de programmation fonctionnelle chaque fois que cela est possible.

## <a name="see-also"></a>Voir aussi

- [Primitifs](basic-types.md)
- [Informations de référence sur le langage F#](index.md)
