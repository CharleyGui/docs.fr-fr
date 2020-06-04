---
title: Guide pratique pour utiliser des pointeurs pour copier un tableau d’octets-Guide de programmation C#
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 8c1afc06fb567a923d604ad53dc26f94178a8d60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397413"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Comment utiliser des pointeurs pour copier un tableau d’octets (Guide de programmation C#)

L’exemple suivant utilise des pointeurs pour copier des octets d’un tableau à un autre.

Cet exemple utilise le mot clé [unsafe](../../language-reference/keywords/unsafe.md), qui vous permet d’utiliser des pointeurs dans la méthode `Copy`. L’instruction [fixed](../../language-reference/keywords/fixed-statement.md) permet de déclarer des pointeurs vers les tableaux source et de destination. L’instruction `fixed`*épingle* l’emplacement des tableaux source et de destination en mémoire pour que ceux-ci ne soient pas déplacés par l’opération de garbage collection. Les blocs de mémoire des tableaux sont libérés quand le bloc `fixed` est effectué. Comme la méthode `Copy` dans cet exemple utilise le mot clé `unsafe`, elle doit être compilée avec l’option de compilateur [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).

Cet exemple accède aux éléments des deux tableaux au moyen d’index et non au moyen d’un second pointeur non managé. La déclaration des pointeurs `pSource` et `pTarget` épingle les tableaux. Cette fonctionnalité est disponible à compter de C# 7.3.

## <a name="example"></a>Exemple

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Pointeurs et code unsafe](index.md)
- [-unsafe (Options du compilateur C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Garbage collection](../../../standard/garbage-collection/index.md)
