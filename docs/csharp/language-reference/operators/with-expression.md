---
title: avec expression-référence C#
description: En savoir plus sur une expression with qui effectue une mutation non destructrice d’enregistrements C#
ms.date: 11/12/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: d7d3758c8c5da7859974b5b50b63d2a5ca16b24d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702223"
---
# <a name="with-expression-c-reference"></a>with, expression (référence C#)

Disponible en C# 9,0 et versions ultérieures, une `with` expression génère une copie de son opérande [Record](../../whats-new/csharp-9.md#record-types) avec les propriétés et les champs spécifiés modifiés :

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

Comme le montre l’exemple précédent, vous utilisez la syntaxe de l' [initialiseur d’objet](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) pour spécifier les membres à modifier et leurs nouvelles valeurs. Dans une `with` expression, un opérande de gauche doit être d’un type d’enregistrement.

Le résultat d’une `with` expression a le même type au moment de l’exécution que l’opérande de l’expression, comme le montre l’exemple suivant :

:::code language="csharp" source="snippets/with-expression/InheritanceExample.cs" :::

Dans le cas d’un membre de type référence, seule la référence à une instance est copiée lors de la copie d’un enregistrement. La copie et l’enregistrement d’origine ont accès à la même instance de type référence. L’exemple suivant illustre ce comportement :

:::code language="csharp" source="snippets/with-expression/ExampleWithReferenceType.cs" :::

Tout type d’enregistrement a le *constructeur de copie*. Il s’agit d’un constructeur avec un paramètre unique du type d’enregistrement contenant. Elle copie l’état de son argument dans une nouvelle instance d’enregistrement. Lors de l’évaluation d’une `with` expression, le constructeur de copie est appelé pour instancier une nouvelle instance d’enregistrement basée sur un enregistrement d’origine. Après cela, la nouvelle instance est mise à jour selon les modifications spécifiées. Par défaut, le constructeur de copie est implicite, c’est-à-dire qu’il est généré par le compilateur. Si vous devez personnaliser la sémantique de copie des enregistrements, déclarez explicitement un constructeur de copie avec le comportement souhaité. L’exemple suivant met à jour l’exemple précédent avec un constructeur de copie explicite. Le nouveau comportement de copie consiste à copier des éléments de liste au lieu d’une référence de liste lorsqu’un enregistrement est copié :

:::code language="csharp" source="snippets/with-expression/UserDefinedCopyConstructor.cs" :::

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [proposition de fonctionnalité d’enregistrements note](~/_csharplang/proposals/csharp-9.0/records.md):

- [`with` formule](~/_csharplang/proposals/csharp-9.0/records.md#with-expression)
- [Copier et cloner des membres](~/_csharplang/proposals/csharp-9.0/records.md#copy-and-clone-members)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
