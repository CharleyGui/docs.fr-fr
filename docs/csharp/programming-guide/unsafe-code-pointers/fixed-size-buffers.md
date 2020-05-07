---
title: Mémoires tampons de taille fixe - Guide de programmation C#
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 5920dd125ded34969d60feb299568b56402056ab
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140552"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Mémoires tampons de taille fixe (Guide de programmation C#)

En C#, vous pouvez utiliser l’instruction [fixed](../../language-reference/keywords/fixed-statement.md) pour créer une mémoire tampon avec un tableau de taille fixe dans une structure de données. Les mémoires tampons de taille fixe sont utiles quand vous écrivez des méthodes qui sont interopérables avec les sources de données d’autres langages ou plateformes. Le tableau fixe peut accepter tous les attributs ou modificateurs qui sont autorisés pour les membres de structures régulières. La seule restriction est que le tableau doit être de type `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Notes 

Dans du code safe, un struct C# qui contient un tableau ne contient pas les éléments du tableau. Le struct contient une référence aux éléments du tableau. Vous pouvez incorporer un tableau de taille fixe dans un [struct](../../language-reference/builtin-types/struct.md) quand il est utilisé dans un bloc de code [unsafe](../../language-reference/keywords/unsafe.md).

La taille de l' `struct` élément suivant ne dépend pas du nombre d’éléments du tableau, `pathName` car est une référence :

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

Un `struct` peut contenir un tableau incorporé dans du code unsafe. Dans l’exemple suivant, le tableau `fixedBuffer` a une taille fixe. Utilisez une instruction `fixed` pour établir un pointeur vers le premier élément. Accédez aux éléments du tableau par le biais de ce pointeur. L’instruction `fixed` épingle le champ de l’instance `fixedBuffer` à un emplacement spécifique de la mémoire.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

La taille du tableau `char` de 128 éléments est de 256 octets. Les mémoires tampons [char](../../language-reference/builtin-types/char.md) de taille fixe acceptent toujours deux octets par caractère, quel que soit l’encodage. Ceci est vrai même lorsque les mémoires tampons char sont marshalées vers des méthodes ou des structs d’API avec `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`. Pour plus d’informations, consultez <xref:System.Runtime.InteropServices.CharSet>.

L’exemple précédent montre comment accéder aux champs `fixed` sans épinglage, ce qui est possible à compter de C# 7.3.

Un autre tableau courant de taille fixe est le tableau [bool](../../language-reference/builtin-types/bool.md). La taille des éléments d’un tableau `bool` est toujours d’un octet. Les tableaux `bool` ne conviennent pas à la création de tableaux d’octets ou de mémoires tampons.

Les mémoires tampons de taille fixe sont <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>compilées avec le, qui indique au Common Language Runtime (CLR) qu’un type contient un tableau non managé susceptible de provoquer un dépassement de capacité. Cela est similaire à la mémoire créée à l’aide de [stackalloc](../../language-reference/operators/stackalloc.md), qui active automatiquement les fonctionnalités de détection de dépassement de mémoire tampon dans le CLR. L’exemple précédent montre comment une mémoire tampon de taille fixe peut exister `unsafe struct`dans un.

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

Le compilateur qui a généré `Buffer`C# pour, est attribué comme suit :

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

Les mémoires tampons de taille fixe diffèrent des tableaux normaux des manières suivantes :

- Peut uniquement être utilisé dans un contexte non [sécurisé](../../language-reference/keywords/unsafe.md) .
- Peut uniquement être des champs d’instance de structs.
- Il s’agit toujours de vecteurs, ou de tableaux unidimensionnels.
- La déclaration doit inclure la longueur, telle que `fixed char id[8]`. Vous ne pouvez pas utiliser `fixed char id[]`.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Pointeurs et code unsafe](index.md)
- [fixed, instruction](../../language-reference/keywords/fixed-statement.md)
- [Interopérabilité](../interop/index.md)
