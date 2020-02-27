---
title: Mémoires tampons de taille fixe - Guide de programmation C#
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 9005c425badc5a4ed74e6af3447e563daf61229e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627797"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Mémoires tampons de taille fixe (Guide de programmation C#)

En C#, vous pouvez utiliser l’instruction [fixed](../../language-reference/keywords/fixed-statement.md) pour créer une mémoire tampon avec un tableau de taille fixe dans une structure de données. Les mémoires tampons de taille fixe sont utiles quand vous écrivez des méthodes qui sont interopérables avec les sources de données d’autres langages ou plateformes. Le tableau fixe peut accepter tous les attributs ou modificateurs qui sont autorisés pour les membres de structures régulières. La seule restriction est que le tableau doit être de type `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Notes

Dans du code safe, un struct C# qui contient un tableau ne contient pas les éléments du tableau. Le struct contient une référence aux éléments du tableau. Vous pouvez incorporer un tableau de taille fixe dans un [struct](../../language-reference/builtin-types/struct.md) quand il est utilisé dans un bloc de code [unsafe](../../language-reference/keywords/unsafe.md).

Le `struct` suivant a une taille de 8 octets. Le tableau `pathName` est une référence :

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

Un `struct` peut contenir un tableau incorporé dans du code unsafe. Dans l’exemple suivant, le tableau `fixedBuffer` a une taille fixe. Utilisez une instruction `fixed` pour établir un pointeur vers le premier élément. Accédez aux éléments du tableau par le biais de ce pointeur. L’instruction `fixed` épingle le champ de l’instance `fixedBuffer` à un emplacement spécifique de la mémoire.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

La taille du tableau `char` de 128 éléments est de 256 octets. Les mémoires tampons [char](../../language-reference/builtin-types/char.md) de taille fixe acceptent toujours deux octets par caractère, quel que soit l’encodage. Ceci est vrai même lorsque les mémoires tampons char sont marshalées vers des méthodes ou des structs d’API avec `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`. Pour plus d’informations, consultez <xref:System.Runtime.InteropServices.CharSet>.

L’exemple précédent montre comment accéder aux champs `fixed` sans épinglage, ce qui est possible à compter de C# 7.3.

Un autre tableau courant de taille fixe est le tableau [bool](../../language-reference/builtin-types/bool.md). La taille des éléments d’un tableau `bool` est toujours d’un octet. Les tableaux `bool` ne conviennent pas à la création de tableaux d’octets ou de mémoires tampons.

> [!NOTE]
> Le compilateur C# et le common language runtime (CLR) ne contrôlent pas le dépassement de la mémoire tampon de sécurité, sauf pour la mémoire créée à l’aide de [stackalloc](../../language-reference/operators/stackalloc.md). Comme toujours pour le code unsafe, la prudence est recommandée.

Les mémoires tampons unsafe diffèrent des tableaux normaux à différents niveaux :

- Les mémoires tampons unsafe peuvent uniquement être utilisées dans un contexte unsafe.
- Les mémoires tampons unsafe sont toujours des vecteurs ou des tableaux unidimensionnels.
- La déclaration du tableau doit inclure un nombre, tel que `char id[8]`. Vous ne pouvez pas utiliser `char id[]`.
- Les mémoires tampons unsafe peuvent uniquement être des champs d’instance de structs dans un contexte unsafe.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Pointeurs et code unsafe](index.md)
- [fixed, instruction](../../language-reference/keywords/fixed-statement.md)
- [Interopérabilité](../interop/index.md)
