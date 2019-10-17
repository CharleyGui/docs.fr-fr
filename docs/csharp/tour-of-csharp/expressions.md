---
title: Expressions C# - Visite guidée du langage C#
description: Les expressions, opérandes et opérateurs sont des blocs de construction du langage C#
ms.date: 04/25/2019
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 4866d12118518827c1f7032ac09933927f0f3c52
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395676"
---
# <a name="expressions"></a>Expressions

Les *expressions* sont construites à partir de *d’opérandes* et *d’opérateurs*. Les opérateurs d’une expression indiquent les opérations à appliquer aux opérandes. Parmi les exemples d’opérateurs figurent `+`, `-`, `*`, `/` et `new`. Les littéraux, les champs, les variables locales et les expressions sont des exemples d’opérandes.

Quand une expression contient plusieurs opérateurs, la *priorité* des opérateurs contrôle l'ordre dans lequel les opérateurs individuels sont évalués. Par exemple, l’expression `x + y * z` est évaluée comme `x + (y * z)`, car l’opérateur `*` a une priorité plus élevée que `+`.

Lorsqu’un opérande se produit entre deux opérateurs de même priorité, *l’associativité* des opérateurs détermine l’ordre dans lequel les opérations sont effectuées :

* À l’exception des opérateurs d’assignation et de fusion Null, tous les opérateurs binaires sont *associatifs à gauche*, ce qui signifie que les opérations sont effectuées de gauche à droite. Par exemple, `x + y + z` est évalué comme étant `(x + y) + z`.
* Les opérateurs d’assignation, les opérateurs de fusion Null `??` et `??=`, et l’opérateur conditionnel `?:` sont *associatifs à droite*, ce qui signifie que les opérations sont exécutées de droite à gauche. Par exemple, `x = y = z` est évalué comme étant `x = (y = z)`.

La priorité et l’associativité peuvent être contrôlées à l’aide de parenthèses. Par exemple, `x + y * z` multiplie d’abord `y` par `z`, puis ajoute le résultat à `x`, mais `(x + y) * z` ajoute d’abord `x` et `y`, puis multiplie le résultat par `z`.

La plupart des opérateurs peuvent être [*surchargés*](../language-reference/operators/operator-overloading.md). La surcharge d’opérateur autorise la spécification d’implémentations d’opérateurs définies par l’utilisateur pour les opérations où l’un des deux opérandes ou les deux sont d’un type classe ou struct défini par l’utilisateur.

C# met à votre disposition de nombreux opérateurs pour effectuer des opérations [arithmétiques](../language-reference/operators/arithmetic-operators.md), [logiques](../language-reference/operators/boolean-logical-operators.md), [au niveau du bit et de décalage](../language-reference/operators/bitwise-and-shift-operators.md) et des comparaisons d’[égalité](../language-reference/operators/equality-operators.md) et d’[ordre](../language-reference/operators/comparison-operators.md) .

Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez [Opérateurs C#](../language-reference/operators/index.md).

> [!div class="step-by-step"]
> [Précédent](types-and-variables.md)
> [Suivant](statements.md)
