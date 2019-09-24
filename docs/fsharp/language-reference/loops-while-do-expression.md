---
title: 'Boucles : expression while...do'
description: Découvrez comment le... l’expression do est utilisée pour effectuer une exécution itérative (bouclage) alors qu’une condition de test spécifiée a la valeur true.
ms.date: 05/16/2016
ms.openlocfilehash: 73526279358db101f8d07721a200920f1e87f119
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216637"
---
# <a name="loops-whiledo-expression"></a>Boucles : expression while...do

L' `while...do` expression est utilisée pour effectuer une exécution itérative (bouclage) alors qu’une condition de test spécifiée a la valeur true.

## <a name="syntax"></a>Syntaxe

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Notes

L' *expression de test* est évaluée ; Si c’est `true`le cas, le *corps-expression* est exécuté et l’expression de test est de nouveau évaluée. Le *corps de l’expression* doit être `unit`de type. Si l’expression de test `false`est, l’itération se termine.

L’exemple suivant illustre l’utilisation de l' `while...do` expression.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

La sortie du code précédent est un flux de nombres aléatoires compris entre 1 et 20, le dernier étant 10.

```console
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> Vous pouvez utiliser `while...do` dans les expressions de séquence et d’autres expressions de calcul, auquel cas une version personnalisée `while...do` de l’expression est utilisée. Pour plus d’informations, consultez [séquences](sequences.md), [flux de travail asynchrones](asynchronous-workflows.md) et [expressions de calcul](computation-expressions.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Boucles `for...in`Formule](loops-for-in-expression.md)
- [Boucles `for...to`Formule](loops-for-to-expression.md)
