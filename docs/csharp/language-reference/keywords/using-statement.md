---
title: using, instruction - Référence C#
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 52cde99fd029ce50f159b2a87fbfbf47fc79dccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712960"
---
# <a name="using-statement-c-reference"></a>using, instruction (référence C#)

Fournit une syntaxe pratique qui garantit l’utilisation correcte d’objets <xref:System.IDisposable>.

## <a name="example"></a> Exemple

L’exemple suivant montre comment utiliser l’instruction `using`.

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

En commençant par C 8.0, vous pouvez utiliser `using` la syntaxe alternative suivante pour l’énoncé qui ne nécessite pas d’accolades :

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a>Notes 

<xref:System.IO.File> et <xref:System.Drawing.Font> sont des exemples de types managés qui accèdent à des ressources non managées (dans le cas présent, des handles de fichiers et des contextes d’appareil). Beaucoup d’autres types de ressources non managées et de bibliothèques de classes peuvent les encapsuler. Tous les types de cette sorte doivent implémentent l’interface <xref:System.IDisposable>.

Quand la durée de vie d’un objet `IDisposable` est limitée à une seule méthode, vous devez le déclarer et l’instancier dans l’instruction `using`. L’instruction `using` appelle la méthode <xref:System.IDisposable.Dispose%2A> correctement sur l’objet et, quand vous l’utilisez comme indiqué précédemment, elle met également l’objet lui-même hors de portée dès que <xref:System.IDisposable.Dispose%2A> est appelée. Dans le bloc `using`, l’objet est en lecture seule et ne peut être ni modifié ni réassigné.

L’instruction `using` garantit que <xref:System.IDisposable.Dispose%2A> est appelée même si une exception se produit dans le bloc `using`. Vous pouvez obtenir le même résultat en plaçant l’objet dans un bloc `try`, puis en appelant <xref:System.IDisposable.Dispose%2A> dans un bloc `finally` ; c’est d’ailleurs ainsi que l’instruction `using` est traduite par le compilateur. L’exemple de code précédent se développe pour donner le code suivant au moment de la compilation (notez les accolades supplémentaires pour créer la portée limitée de l’objet) :

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

La syntaxe de déclaration plus nouvelle `using` se traduit par un code très similaire. Le `try` bloc s’ouvre là où la variable est déclarée. Le `finally` bloc est ajouté à la fin du bloc d’enceinte, généralement à la fin d’une méthode.

Pour plus d’informations sur l’instruction `try`-`finally`, consultez la rubrique [try-finally](try-finally.md).

Vous pouvez déclarer plusieurs instances d’un type dans l’instruction `using`, comme indiqué dans l’exemple suivant :

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

Vous pouvez combiner plusieurs déclarations du même type à l’aide de la nouvelle syntaxe introduite avec C 8 ainsi. Ceci est illustré dans l'exemple suivant :

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

Il n’est pas recommandé d’instancier l’objet de ressource, puis de passer la variable à l’instruction `using`. Dans ce cas, une fois que le contrôle a quitté le bloc `using`, l’objet reste dans la portée mais n’a probablement pas accès à ses ressources non managées. En d’autres termes, il n’est plus complètement initialisé. Si vous essayez d’utiliser l’objet à l’extérieur du bloc `using`, vous risquez de provoquer la levée d’une exception. C’est pourquoi il est généralement préférable d’instancier l’objet dans l’instruction `using` et de limiter sa portée au bloc `using`.

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

Pour plus d’informations sur la suppression d’objets `IDisposable`, consultez [Utilisation d’objets qui implémentent IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez [Instruction using](~/_csharplang/spec/statements.md#the-using-statement) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [en utilisant la directive](using-directive.md)
- [Garbage collection](../../../standard/garbage-collection/index.md)
- [Utilisation d’objets implémentant IDisposable](../../../standard/garbage-collection/using-objects.md)
- [Interface IDisposable](xref:System.IDisposable)
- [à l’aide de l’énoncé dans C 8.0](~/_csharplang/proposals/csharp-8.0/using.md)
