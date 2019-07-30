---
title: 'Boucles : expression for...to'
description: Voir comment le F# ... to expression est utilisé pour effectuer une itération dans une boucle sur une plage de valeurs d’une variable de boucle.
ms.date: 05/16/2016
ms.openlocfilehash: 910c04aa4ea6b2c637dcad147347c1c317b5e0c0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626626"
---
# <a name="loops-forto-expression"></a>Boucles : expression for...to

L' `for...to` expression est utilisée pour effectuer une itération dans une boucle sur une plage de valeurs d’une variable de boucle.

## <a name="syntax"></a>Syntaxe

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Notes

Le type de l’identificateur est déduit à partir du type des expressions de *début* et de *fin* . Les types pour ces expressions doivent être des entiers 32 bits.

Bien qu’il s’agisse `for...to` techniquement d’une expression, est plus semblable à une instruction traditionnelle dans un langage de programmation impératif. Le type de retour de l' *expression de corps* doit `unit`être. Les exemples suivants illustrent différentes utilisations de `for...to` l’expression.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

La sortie du code précédent est la suivante.

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Boucles `for...in`Formule](loops-for-in-expression.md)
- [Boucles `while...do`Formule](loops-while-do-expression.md)
