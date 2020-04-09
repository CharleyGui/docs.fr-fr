---
title: using, instruction - Référence C#
ms.date: 04/07/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: a237a90b4782e0460857c3d5d887771bcc8ccaaf
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989179"
---
# <a name="using-statement-c-reference"></a>using, instruction (référence C#)

Fournit une syntaxe pratique qui garantit l’utilisation correcte d’objets <xref:System.IDisposable>. À partir de C 8.0, `using` l’instruction <xref:System.IAsyncDisposable> assure l’utilisation correcte des objets.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser l’instruction `using`.

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

En commençant par C 8.0, vous pouvez utiliser `using` la syntaxe alternative suivante pour l’énoncé qui ne nécessite pas d’accolades :

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a>Notes

<xref:System.IO.File> et <xref:System.Drawing.Font> sont des exemples de types managés qui accèdent à des ressources non managées (dans le cas présent, des handles de fichiers et des contextes d’appareil). Beaucoup d’autres types de ressources non managées et de bibliothèques de classes peuvent les encapsuler. Tous ces types <xref:System.IDisposable> doivent implémenter l’interface, ou l’interface. <xref:System.IAsyncDisposable>

Quand la durée de vie d’un objet `IDisposable` est limitée à une seule méthode, vous devez le déclarer et l’instancier dans l’instruction `using`. L’instruction `using` appelle la méthode <xref:System.IDisposable.Dispose%2A> correctement sur l’objet et, quand vous l’utilisez comme indiqué précédemment, elle met également l’objet lui-même hors de portée dès que <xref:System.IDisposable.Dispose%2A> est appelée. Dans `using` le bloc, l’objet est lu uniquement et ne peut pas être modifié ou réaffecté. Si l’objet `IAsyncDisposable` implémente au <xref:System.IAsyncDisposable.DisposeAsync%2A> `awaits` lieu <xref:System.Threading.Tasks.Task>de `IDisposable`, la `using` déclaration appelle le et le retourné .

L’instruction `using` garantit <xref:System.IDisposable.Dispose%2A> que <xref:System.IAsyncDisposable.DisposeAsync%2A>(ou) est appelé même `using` si une exception se produit dans le bloc. Vous pouvez obtenir le même résultat `try` en mettant <xref:System.IDisposable.Dispose%2A> l’objet à l’intérieur d’un bloc, puis en appelant (ou <xref:System.IAsyncDisposable.DisposeAsync%2A> dans un `finally` bloc; en fait, c’est ainsi que la `using` déclaration est traduite par le compilateur. L’exemple de code précédent se développe pour donner le code suivant au moment de la compilation (notez les accolades supplémentaires pour créer la portée limitée de l’objet) :

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

La syntaxe de déclaration plus nouvelle `using` se traduit par un code similaire. Le `try` bloc s’ouvre là où la variable est déclarée. Le `finally` bloc est ajouté à la fin du bloc d’enceinte, généralement à la fin d’une méthode.

Pour plus d’informations sur `try` - `finally` la déclaration, voir [l’article try-finally.](try-finally.md)

Plusieurs cas d’un type peuvent `using` être déclarés dans une seule déclaration, comme le montre l’exemple suivant. Notez que vous ne pouvez pas`var`utiliser des variables implicitement typées ( ) lorsque vous déclarez plusieurs variables dans une seule instruction :

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

Vous pouvez combiner plusieurs déclarations du même type à l’aide de la nouvelle syntaxe introduite avec C 8 ainsi, comme indiqué dans l’exemple suivant:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

Vous pouvez instantané l’objet de ressources, puis `using` passer la variable à l’instruction, mais ce n’est pas une pratique exemplaire. Dans ce cas, une fois que le contrôle a quitté le bloc `using`, l’objet reste dans la portée mais n’a probablement pas accès à ses ressources non managées. En d’autres termes, il n’est plus complètement initialisé. Si vous essayez d’utiliser l’objet à l’extérieur du bloc `using`, vous risquez de provoquer la levée d’une exception. Pour cette raison, il est préférable d’instantané `using` l’objet dans `using` l’instruction et de limiter sa portée au bloc.

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

Pour plus d’informations sur la suppression d’objets `IDisposable`, consultez [Utilisation d’objets qui implémentent IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez [Instruction using](~/_csharplang/spec/statements.md#the-using-statement) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation CMD](../../programming-guide/index.md)
- [Mots-clés C](index.md)
- [using, directive](using-directive.md)
- [Garbage collection](../../../standard/garbage-collection/index.md)
- [Utilisation d’objets implémentant IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Interface IDisposable](xref:System.IDisposable)
- [à l’aide de l’énoncé dans C 8.0](~/_csharplang/proposals/csharp-8.0/using.md)
