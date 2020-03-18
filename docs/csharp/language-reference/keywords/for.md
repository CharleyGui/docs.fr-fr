---
title: pour déclaration - Référence C
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: fc6a23cabd93323cacc33dfc4388116881c1fc84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74552269"
---
# <a name="for-c-reference"></a>for (référence C#)

L’instruction `for` exécute une instruction ou un bloc d’instructions tant qu’une expression booléenne donne la valeur `true`.

À tout moment dans le bloc d’instructions `for`, vous pouvez sortir de la boucle à l’aide de l’instruction [break](break.md), ou passer à l’itération suivante de la boucle à l’aide de l’instruction [continue](continue.md). Vous pouvez également quitter une boucle `for` en utilisant les instructions [goto](goto.md), [return](return.md) ou [throw](throw.md).

## <a name="structure-of-the-for-statement"></a>Structure de l’instruction `for`

Chaque instruction `for` définit des sections *initialiseur*, *condition* et *itérateur* :

```csharp
for (initializer; condition; iterator)
    body
```

Ces trois sections sont facultatives. Le corps de la boucle est une instruction ou un bloc d’instructions.

L’exemple suivant montre l’instruction `for` avec toutes les sections définies :

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>La section *initialiseur*

Les instructions figurant dans la section *initialiseur* sont exécutées une seule fois, avant d’entrer dans la boucle. La section *initialiseur* contient au choix :

- La déclaration et l’initialisation d’une variable de boucle locale, qui n’est pas accessible à partir de l’extérieur de la boucle, ou

- Zéro, une ou plusieurs expressions d’instruction parmi celles de la liste suivante, séparées par des virgules :

  - Instruction d’[assignation](../operators/assignment-operator.md)

  - Appel d’une méthode

  - Expression d’[incrémentation](../operators/arithmetic-operators.md#increment-operator-) préfixée ou suffixée, telle que `++i` ou `i++`

  - Expression de [décrémentation](../operators/arithmetic-operators.md#decrement-operator---) préfixée ou suffixée, telle que `--i` ou `i--`

  - Création d’un objet à l’aide de l’opérateur [new](../operators/new-operator.md)

  - Expression [await](../operators/await.md)

La section *initialiseur* dans l’exemple ci-dessus déclare et initialise la variable de boucle locale `i` :

```csharp
int i = 0
```

### <a name="the-condition-section"></a>La section *condition*

La section *condition*, si elle est présente, doit être une expression booléenne. Cette expression est évaluée avant chaque itération de boucle. Si la section *condition* est absente ou que l’expression booléenne est `true`, l’itération suivante de la boucle est exécutée ; sinon, la boucle est fermée.

La section *condition* dans l’exemple ci-dessus détermine si la boucle se termine en fonction de la valeur de la variable de boucle locale :

```csharp
i < 5
```

### <a name="the-iterator-section"></a>La section *itérateur*

La section *itérateur* définit ce qui se produit après chaque itération du corps de la boucle. La section *itérateur* contient zéro, une ou plusieurs des expressions d’instruction suivantes, séparées par des virgules :

- Instruction d’[assignation](../operators/assignment-operator.md)

- Appel d’une méthode

- Expression d’[incrémentation](../operators/arithmetic-operators.md#increment-operator-) préfixée ou suffixée, telle que `++i` ou `i++`

- Expression de [décrémentation](../operators/arithmetic-operators.md#decrement-operator---) préfixée ou suffixée, telle que `--i` ou `i--`

- Création d’un objet à l’aide de l’opérateur [new](../operators/new-operator.md)

- Expression [await](../operators/await.md)

La section *itérateur* dans l’exemple ci-dessus incrémente la variable de boucle locale :

```csharp
i++
```

## <a name="examples"></a>Exemples

L’exemple suivant illustre plusieurs utilisations moins courantes des sections d’instruction `for` : l’attribution d’une valeur à une variable de boucle externe dans la section *initialiseur*, l’appel d’une méthode dans les sections *initialiseur* et *itérateur*, et la modification des valeurs de deux variables dans la section *itérateur*. Sélectionnez **Exécuter** pour exécuter l’exemple de code. Après cela, vous pouvez modifier le code et le réexécuter.

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

L’exemple suivant définit la boucle `for` infinie :

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Instruction for](~/_csharplang/spec/statements.md#the-for-statement) de la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [foreach, in](foreach-in.md)
