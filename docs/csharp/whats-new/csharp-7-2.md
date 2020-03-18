---
title: Nouveautés de C# 7.2
description: Vue d’ensemble des nouvelles fonctionnalités de C# 7.2.
ms.date: 08/16/2017
ms.openlocfilehash: 7febefb81bbea6f24690adb05488ad6a18bbf552
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75694593"
---
# <a name="whats-new-in-c-72"></a>Nouveautés de C# 7.2

C# 7.2 est une autre version intermédiaire qui ajoute un certain nombre de fonctionnalités utiles.
Cette version a notamment pour but d’utiliser plus efficacement les types valeur en évitant des copies ou allocations inutiles.

Les fonctionnalités restantes sont des fonctionnalités réduites, mais pratiques.

C# 7.2 utilise l’élément de configuration de [sélection de la version du langage](../language-reference/configure-language-version.md) pour sélectionner la version du langage du compilateur.

Les nouvelles fonctionnalités de langage de cette version sont :

- [Techniques d’écriture de code safe et efficace](#safe-efficient-code-enhancements)
  - Une combinaison des améliorations de la syntaxe qui permettent d’utiliser les types valeur avec la sémantique de référence.
- [Arguments nommés non placés en position de fin](#non-trailing-named-arguments)
  - Les arguments nommés peuvent être suivis par des arguments de position.
- [Traits de soulignement de début dans les littéraux numériques](#leading-underscores-in-numeric-literals)
  - Les littéraux numériques peuvent maintenant comporter des traits de soulignement de début avant tout chiffre affiché.
- [`private protected`modifier d’accès](#private-protected-access-modifier)
  - Le modificateur d’accès `private protected` active l’accès pour les classes dérivées dans le même assembly.
- [Expressions `ref` conditionnelles](#conditional-ref-expressions)
  - Le résultat d’une expression conditionnelle (`?:`) peut maintenant être une référence.

Le reste de cet article présente une vue d’ensemble de chaque fonctionnalité. Vous découvrirez la logique de chacune d’elles. Vous allez apprendre leur syntaxe. Vous pouvez explorer ces fonctionnalités dans votre environnement à l’aide de l’outil global `dotnet try` :

1. Installez l’outil global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).
1. Clonez le référentiel [dotnet/try-samples](https://github.com/dotnet/try-samples).
1. Définissez le répertoire actuel sur le sous-répertoire *csharp7* pour le référentiel *try-samples*.
1. Exécutez `dotnet try`.

## <a name="safe-efficient-code-enhancements"></a>Amélioration du code safe et efficace

Les fonctionnalités de langage introduites dans 7.2 vous permettent de travailler avec les types valeur tout en utilisant la sémantique de référence. Elles sont conçues pour améliorer les performances en réduisant la copie des types valeur sans impliquer les allocations de mémoire associées à l’utilisation des types référence. Cette API offre les fonctionnalités suivantes :

- Le modificateur `in` sur les paramètres pour spécifier qu’un argument est passé par référence, mais pas modifié par la méthode appelée. L’ajout du modificateur `in` à un argument est une [modification compatible avec la source](version-update-considerations.md#source-compatible-changes).
- Le modificateur `ref readonly` sur les retours de méthode pour indiquer qu’une méthode retourne sa valeur par référence, mais n’autorise pas les écritures sur cet objet. L’ajout du modificateur `ref readonly` est une [modification compatible avec la source](version-update-considerations.md#source-compatible-changes), si une valeur est assignée au retour. Le fait d’ajouter le modificateur `readonly` à une instruction de retour `ref` existante représente une [modification incompatible](version-update-considerations.md#incompatible-changes). Cela nécessite que les appelants mettent à jour de la déclaration de variables locales `ref` pour inclure le modificateur `readonly`.
- La déclaration `readonly struct` pour indiquer qu’un struct est immuable et doit être passé comme un paramètre `in` aux méthodes de ses membres. L’ajout du modificateur `readonly` à une déclaration struct existante est une [modification compatible binaire](version-update-considerations.md#binary-compatible-changes).
- La déclaration `ref struct` pour indiquer qu’un type struct accède directement à la mémoire managée et doit toujours être alloué par la pile. L’ajout du modificateur `ref` à une déclaration `struct` existante est une [modification incompatible](version-update-considerations.md#incompatible-changes). Un `ref struct` ne peut pas être membre d’une classe ou utilisé dans d’autres emplacements où il pourrait être alloué sur le tas.

Pour plus d’informations sur toutes ces modifications, voir [Écrire du code safe et efficace](../write-safe-efficient-code.md).

## <a name="non-trailing-named-arguments"></a>Arguments nommés non placés en position de fin

Les appels de méthode peuvent désormais utiliser des arguments nommés qui précèdent les arguments de position quand ces arguments nommés se trouvent dans les positions appropriées. Pour plus d’informations, consultez [Arguments nommés et facultatifs](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Traits de soulignement de début dans les littéraux numériques

L’implémentation de la prise en charge des séparateurs numériques dans C# 7.0 n’autorisait pas `_` comme premier caractère de la valeur littérale. Les littéraux numériques binaires et hexadécimaux peuvent maintenant commencer par un caractère `_`.

Par exemple :

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>*private protected* (modificateur d’accès)

Enfin, un nouveau modificateur d’accès composé, `private protected`, indique qu’un membre est accessible à la classe globale ou aux classes dérivées déclarées dans le même assembly. Alors que `protected internal` autorise l’accès par des classes dérivées ou qui se trouvent dans le même assembly, `private protected` limite l’accès aux types dérivés déclarés dans le même assembly.

Pour plus d’informations, consultez [Modificateurs d’accès](../language-reference/keywords/access-modifiers.md) dans Informations de référence sur le langage.

## <a name="conditional-ref-expressions"></a>Expressions `ref` conditionnelles

Enfin, l’expression conditionnelle peut produire comme résultat une référence plutôt qu’une valeur. Prenons par exemple la ligne suivante, qui récupère une référence au premier élément dans un des deux tableaux :

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

La variable `r` est une référence à la première valeur de `arr` ou `otherArr`.

Pour plus d’informations, voir [Opérateur conditionnel (?:)](../language-reference/operators/conditional-operator.md) dans la référence sur le langage.
