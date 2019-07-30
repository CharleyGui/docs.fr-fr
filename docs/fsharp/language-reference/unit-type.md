---
title: Unit, type
description: Découvrez comment le F# type «unité» est souvent utilisé pour conserver l’emplacement où une valeur est requise par la syntaxe du langage quand aucune valeur n’est requise ou souhaitée.
ms.date: 05/16/2016
ms.openlocfilehash: 4e586702324565b8dcd4f6c7e11a0e1754f89c58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630178"
---
# <a name="unit-type"></a>Unit, type

Le `unit` type est un type qui indique l’absence d’une valeur spécifique; le `unit` type n’a qu’une seule valeur, qui joue le rôle d’espace réservé quand aucune autre valeur n’existe ou n’est nécessaire.

## <a name="syntax"></a>Syntaxe

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Notes

Chaque F# expression doit être évaluée à une valeur. Pour les expressions qui ne génèrent pas une valeur intéressante, la valeur de type `unit` est utilisée. Le `unit` type ressemble au `void` type dans des langages tels C# que C++et.

Le `unit` type a une valeur unique, et cette valeur est indiquée par le jeton `()`.

La valeur du `unit` type est souvent utilisée en F# programmation pour conserver l’emplacement où une valeur est requise par la syntaxe du langage, mais quand aucune valeur n’est requise ou souhaitée. Par exemple, il peut s’agir de la `printf` valeur de retour d’une fonction. Étant donné que les actions importantes `printf` de l’opération se produisent dans la fonction, la fonction n’a pas besoin de retourner une valeur réelle. Par conséquent, la valeur de retour est `unit`de type.

Certaines constructions attendent une `unit` valeur. Par exemple, une `do` liaison ou un code au niveau supérieur d’un module est supposé correspondre à une `unit` valeur. Le compilateur signale un avertissement quand `do` une liaison ou du code au niveau supérieur d’un module produit un résultat autre que `unit` la valeur qui n’est pas utilisée, comme indiqué dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

Cet avertissement est une caractéristique de la programmation fonctionnelle. Il n’apparaît pas dans d’autres langages de programmation .NET. Dans un programme purement fonctionnel, dans lequel les fonctions n’ont pas d’effets secondaires, la valeur de retour finale est le seul résultat d’un appel de fonction. Par conséquent, lorsque le résultat est ignoré, il s’agit d’une erreur de programmation possible. Bien F# que ne soit pas un langage de programmation purement fonctionnel, il est recommandé de suivre le style de programmation fonctionnelle chaque fois que cela est possible.

## <a name="see-also"></a>Voir aussi

- [Primitifs](primitive-types.md)
- [Informations de référence du langage F#](index.md)
