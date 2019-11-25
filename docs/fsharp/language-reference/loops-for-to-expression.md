---
title: 'Boucles : expression for...to'
description: Voir comment le F# ... to expression est utilisé pour effectuer une itération dans une boucle sur une plage de valeurs d’une variable de boucle.
ms.date: 05/16/2016
ms.openlocfilehash: 882b6e48dd09efcb57f7ef2f419e68a6c43393a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283901"
---
# <a name="loops-forto-expression"></a>Boucles : expression for...to

L’expression `for...to` est utilisée pour effectuer une itération dans une boucle sur une plage de valeurs d’une variable de boucle.

## <a name="syntax"></a>Syntaxe

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>Notes

Le type de l’identificateur est déduit à partir du type des expressions de *début* et de *fin* . Les types pour ces expressions doivent être des entiers 32 bits.

Bien qu’il s’agisse techniquement d’une expression, `for...to` ressemble davantage à une instruction traditionnelle dans un langage de programmation impératif. Le type de retour de l' *expression de corps* doit être `unit`. Les exemples suivants illustrent différentes utilisations de l’expression `for...to`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

La sortie du code précédent est la suivante.

```console
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Boucles : expression `for...in`](loops-for-in-expression.md)
- [Boucles : expression `while...do`](loops-while-do-expression.md)
