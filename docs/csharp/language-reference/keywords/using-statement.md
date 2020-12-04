---
description: using, instruction - Référence C#
title: using, instruction - Référence C#
ms.date: 05/29/2020
f1_keywords:
- using-statement_CSharpKeyword
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 451235d9d41565c35369700eeec75cfd2f5bfc06
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599328"
---
# <a name="using-statement-c-reference"></a>using, instruction (référence C#)

Fournit une syntaxe pratique qui garantit l’utilisation correcte d’objets <xref:System.IDisposable>. À compter de C# 8,0, l' `using` instruction garantit l’utilisation correcte des <xref:System.IAsyncDisposable> objets.

## <a name="example"></a> Exemple

L’exemple suivant montre comment utiliser l’instruction `using`.

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

À compter de C# 8,0, vous pouvez utiliser la syntaxe alternative suivante pour l' `using` instruction qui ne requiert pas d’accolades :

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a>Remarques

<xref:System.IO.File> et <xref:System.Drawing.Font> sont des exemples de types managés qui accèdent à des ressources non managées (dans le cas présent, des handles de fichiers et des contextes d’appareil). Beaucoup d’autres types de ressources non managées et de bibliothèques de classes peuvent les encapsuler. Tous ces types doivent implémenter l' <xref:System.IDisposable> interface ou l' <xref:System.IAsyncDisposable> interface.

Quand la durée de vie d’un objet `IDisposable` est limitée à une seule méthode, vous devez le déclarer et l’instancier dans l’instruction `using`. L’instruction `using` appelle la méthode <xref:System.IDisposable.Dispose%2A> correctement sur l’objet et, quand vous l’utilisez comme indiqué précédemment, elle met également l’objet lui-même hors de portée dès que <xref:System.IDisposable.Dispose%2A> est appelée. Dans le `using` bloc, l’objet est en lecture seule et ne peut pas être modifié ou réassigné. Si l’objet implémente `IAsyncDisposable` au lieu de `IDisposable` , l' `using` instruction appelle <xref:System.IAsyncDisposable.DisposeAsync%2A> et `awaits` le retourné <xref:System.Threading.Tasks.ValueTask> . Pour plus d’informations sur <xref:System.IAsyncDisposable> , consultez [implémenter une méthode DisposeAsync](../../../standard/garbage-collection/implementing-disposeasync.md).

L' `using` instruction garantit que <xref:System.IDisposable.Dispose%2A> (ou <xref:System.IAsyncDisposable.DisposeAsync%2A> ) est appelé même si une exception se produit dans le `using` bloc. Vous pouvez obtenir le même résultat en plaçant l’objet à l’intérieur d’un `try` bloc, puis <xref:System.IDisposable.Dispose%2A> en appelant (ou <xref:System.IAsyncDisposable.DisposeAsync%2A> ) dans un `finally` bloc. en fait, il s’agit de la façon dont l' `using` instruction est traduite par le compilateur. L’exemple de code précédent se développe pour donner le code suivant au moment de la compilation (notez les accolades supplémentaires pour créer la portée limitée de l’objet) :

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

La `using` syntaxe d’instruction la plus récente traduit en code similaire. Le `try` bloc s’ouvre à l’emplacement où la variable est déclarée. Le `finally` bloc est ajouté à la fermeture du bloc englobant, en général à la fin d’une méthode.

Pour plus d’informations sur l' `try` - `finally` instruction, consultez l’article [try-finally](try-finally.md) .

Plusieurs instances d’un type peuvent être déclarées dans une même `using` instruction, comme illustré dans l’exemple suivant. Notez que vous ne pouvez pas utiliser de variables implicitement typées ( `var` ) lorsque vous déclarez plusieurs variables dans une même instruction :

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

Vous pouvez combiner plusieurs déclarations du même type à l’aide de la nouvelle syntaxe introduite avec C# 8, comme indiqué dans l’exemple suivant :

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

Vous pouvez instancier l’objet de ressource, puis passer la variable à l' `using` instruction, mais ce n’est pas une meilleure pratique. Dans ce cas, une fois que le contrôle a quitté le bloc `using`, l’objet reste dans la portée mais n’a probablement pas accès à ses ressources non managées. En d’autres termes, il n’est plus complètement initialisé. Si vous essayez d’utiliser l’objet à l’extérieur du bloc `using`, vous risquez de provoquer la levée d’une exception. Pour cette raison, il est préférable d’instancier l’objet dans l' `using` instruction et de limiter son étendue au `using` bloc.

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

Pour plus d’informations sur la suppression d’objets `IDisposable`, consultez [Utilisation d’objets qui implémentent IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez [Instruction using](~/_csharplang/spec/statements.md#the-using-statement) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [using, directive](using-directive.md)
- [Garbage collection](../../../standard/garbage-collection/index.md)
- [Utilisation d’objets implémentant IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Interface IDisposable](xref:System.IDisposable)
- [instruction using en C# 8,0](~/_csharplang/proposals/csharp-8.0/using.md)
