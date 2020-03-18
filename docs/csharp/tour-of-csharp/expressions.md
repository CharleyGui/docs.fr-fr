---
title: Expressions C# - Visite guidée du langage C#
description: Les expressions, opérandes et opérateurs sont des blocs de construction du langage C#
ms.date: 02/27/2020
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 209b5da01cd7539f2bd97023f40fd149910b6f1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159154"
---
# <a name="expressions"></a>Expressions

Les *expressions* sont construites à partir de *d’opérandes* et *d’opérateurs*. Les opérateurs d’une expression indiquent les opérations à appliquer aux opérandes. Parmi les exemples d’opérateurs figurent `+`, `-`, `*`, `/` et `new`. Les littéraux, les champs, les variables locales et les expressions sont des exemples d’opérandes.

Quand une expression contient plusieurs opérateurs, la *priorité* des opérateurs contrôle l'ordre dans lequel les opérateurs individuels sont évalués. Par exemple, l’expression `x + y * z` est évaluée comme `x + (y * z)`, car l’opérateur `*` a une priorité plus élevée que `+`.

Lorsqu’un opérande se produit entre deux opérateurs de même priorité, *l’associativité* des opérateurs détermine l’ordre dans lequel les opérations sont effectuées :

* À l’exception des opérateurs d’affectation et de fusion nulle, tous les opérateurs binaires sont *de gauche-associative,* ce qui signifie que les opérations sont effectuées de gauche à droite. Par exemple, `x + y + z` est évalué comme étant `(x + y) + z`.
* Les opérateurs d’affectation, les `??` opérateurs `??=` de fusion nulle `?:` et les opérateurs, et l’opérateur conditionnel sont *à droite-associative,* ce qui signifie que les opérations sont effectuées de droite à gauche. Par exemple, `x = y = z` est évalué comme étant `x = (y = z)`.

La priorité et l’associativité peuvent être contrôlées à l’aide de parenthèses. Par exemple, `x + y * z` multiplie d’abord `y` par `z`, puis ajoute le résultat à `x`, mais `(x + y) * z` ajoute d’abord `x` et `y`, puis multiplie le résultat par `z`.

La plupart des opérateurs peuvent être [*surchargés*](../language-reference/operators/operator-overloading.md). La surcharge d’opérateur autorise la spécification d’implémentations d’opérateurs définies par l’utilisateur pour les opérations où l’un des deux opérandes ou les deux sont d’un type classe ou struct défini par l’utilisateur.

C# met à votre disposition de nombreux opérateurs pour effectuer des opérations [arithmétiques](../language-reference/operators/arithmetic-operators.md), [logiques](../language-reference/operators/boolean-logical-operators.md), [au niveau du bit et de décalage](../language-reference/operators/bitwise-and-shift-operators.md) et des comparaisons d’[égalité](../language-reference/operators/equality-operators.md) et d’[ordre](../language-reference/operators/comparison-operators.md) .

Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez [Opérateurs C#](../language-reference/operators/index.md).

> [!div class="step-by-step"]
> [Suivant précédent](types-and-variables.md)
> [Next](statements.md)
