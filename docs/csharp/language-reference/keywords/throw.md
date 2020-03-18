---
title: throw - Référence C#
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 04d3138e3390627355b4b2d4e25c6b00248cec1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399335"
---
# <a name="throw-c-reference"></a>throw (référence C#)

Signale l’occurrence d’une exception pendant l’exécution du programme.  
  
## <a name="remarks"></a>Notes 

La syntaxe de `throw` est :

```csharp
throw [e];
```

où `e` est une instance d’une classe dérivée de <xref:System.Exception?displayProperty=nameWithType>. L’exemple suivant utilise l’instruction `throw` pour lever une exception <xref:System.IndexOutOfRangeException> si l’argument passé à une méthode nommée `GetNumber` ne correspond pas à un index valide d’un tableau interne.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

Les appelants de méthode utilisent alors un bloc `try-catch` ou `try-catch-finally` pour gérer l’exception levée. L’exemple suivant gère l’exception levée par la méthode `GetNumber`.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a>Génération répétée d’une exception

`throw` peut également être utilisé dans un bloc `catch` pour lever de nouveau une exception gérée dans un bloc `catch`.  Dans ce cas, `throw` n’accepte pas d’opérande d’exception. Cela est très utile lorsqu’une méthode passe un argument d’un appelant à une autre méthode de bibliothèque, et que la méthode de bibliothèque lève une exception qui doit être passée à l’appelant. Par exemple, l’exemple suivant lève de nouveau une exception <xref:System.NullReferenceException> qui est levée lorsque vous tentez de récupérer le premier caractère d’une chaîne non initialisée.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> Vous pouvez également utiliser la syntaxe `throw e` dans un bloc `catch` pour instancier une nouvelle exception que vous passez à l’appelant. Dans ce cas, la trace de la pile de l’exception d’origine, qui est disponible à partir de la propriété <xref:System.Exception.StackTrace>, n’est pas conservée.

## <a name="the-throw-expression"></a>Expression `throw`

À compter de C# 7.0, `throw` peut être utilisé comme expression et comme instruction. Ainsi, une exception peut être levée dans des contextes qui n’étaient précédemment pas pris en charge. notamment :

- [l’opérateur conditionnel](../operators/conditional-operator.md). l’exemple suivant utilise une expression `throw` pour lever une exception <xref:System.ArgumentException> si une méthode reçoit un tableau de chaînes vide. Avant C# 7.0, cette logique devait figurer dans une instruction `if`/`else`.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- [l’opérateur de fusion de Null](../operators/null-coalescing-operator.md) : dans l’exemple suivant, une expression `throw` est utilisée avec un opérateur de fusion de Null pour lever une exception si la chaîne assignée à une propriété `Name` est `null`.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- un [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ou une méthode expression-bodied : l’exemple suivant illustre une méthode expression-bodied qui lève une exception <xref:System.InvalidCastException>, car une conversion vers une valeur <xref:System.DateTime> n’est pas prise en charge.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [Mots clés C#](index.md)
- [Comment : Jeter explicitement des exceptions](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
