---
description: unsafe, mot clé -Référence C#
title: unsafe, mot clé -Référence C#
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 2e047a4cff77877862c5cbbb5e49eb1a75b42499
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141957"
---
# <a name="unsafe-c-reference"></a>unsafe (référence C#)

Le mot clé `unsafe` désigne un contexte non sécurisé, qui est requis pour toute opération impliquant des pointeurs. Pour plus d’informations, consultez [Pointeurs et code unsafe](../../programming-guide/unsafe-code-pointers/index.md).

Vous pouvez utiliser le modificateur `unsafe` dans la déclaration d’un type ou d’un membre. Toute l’étendue de texte du type ou du membre est ainsi considérée comme un contexte unsafe. Par exemple, ce qui suit est une méthode déclarée avec le modificateur `unsafe` :

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

La portée du contexte unsafe s’étend de la liste de paramètres à la fin de la méthode, de sorte que les pointeurs peuvent également être utilisés dans la liste de paramètres :

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

Vous pouvez également avoir recours à un bloc unsafe pour utiliser un code unsafe dans ce bloc. Par exemple :

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Pour compiler du code unsafe, vous devez spécifier l' [`-unsafe`](../compiler-options/unsafe-compiler-option.md) option du compilateur. Le code unsafe n’est pas vérifiable par le service CLR (Common Language Runtime).

## <a name="example"></a>Exemple

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir [Code unsafe](~/_csharplang/spec/unsafe-code.md) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [fixed, instruction](fixed-statement.md)
- [Pointeurs et code unsafe](../../programming-guide/unsafe-code-pointers/index.md)
- [Mémoires tampons de taille fixe](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
