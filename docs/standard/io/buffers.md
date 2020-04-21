---
title: System.Buffers - .NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: d113def0182dc6a5bcea6c18b2d0e4b475946e31
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739626"
---
# <a name="work-with-buffers-in-net"></a>Travailler avec Buffers en .NET

Cet article fournit un aperçu des types qui aident à lire les données qui s’exécutent à travers plusieurs tampons. Ils sont principalement utilisés <xref:System.IO.Pipelines.PipeReader> pour soutenir les objets.

## <a name="ibufferwritert"></a>IBufferWriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>est un contrat pour l’écriture tampon synchrone. Au niveau le plus bas, l’interface:

- Est basique et pas difficile à utiliser.
- Permet l’accès à un <xref:System.Memory%601> ou <xref:System.Span%601>. Le `Memory<T>` `Span<T>` ou peut être écrit à `T` et vous pouvez déterminer combien d’articles ont été écrits.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

La méthode précédente :

- Demande un tampon d’au moins `IBufferWriter<byte>` 5 octets de l’utilisation `GetSpan(5)`.
- Écrit octets pour la chaîne ASCII `Span<byte>`"Bonjour" à l’retourné .
- Appels <xref:System.Buffers.IBufferWriter%601> pour indiquer combien d’octets ont été écrits au tampon.

Cette méthode d’écriture utilise `Memory<T>` / `Span<T>` `IBufferWriter<T>`le tampon fourni par le . Alternativement, <xref:System.Buffers.BuffersExtensions.Write%2A> la méthode d’extension peut être `IBufferWriter<T>`utilisée pour copier un tampon existant à la . `Write`fait le travail `GetSpan` / `Advance` d’appel le cas échéant, `Advance` il n’est donc pas nécessaire d’appeler après l’écriture:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601>est une `IBufferWriter<T>` mise en œuvre de dont le magasin de soutien est un tableau contigus unique.

### <a name="ibufferwriter-common-problems"></a>Problèmes communs iBufferWriter

- `GetSpan`et `GetMemory` retourner un tampon avec au moins la quantité demandée de mémoire. N’assumez pas les tailles exactes de tampon.
- Il n’y a aucune garantie que les appels successifs retourneront le même tampon ou le même tampon de taille.
- Un nouveau tampon doit `Advance` être demandé après avoir appelé pour continuer à écrire plus de données. Un tampon acquis précédemment ne `Advance` peut pas être écrit après a été appelé.

## <a name="readonlysequencet"></a>LireOnlySequence\<T\>

![LireOnlySequence montrant la mémoire dans le tuyau et en dessous de cette position de séquence de la mémoire lue seulement](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601>est une struct qui peut représenter une séquence contigu ou non contigue de `T`. Il peut être construit à partir de:

1. Une variable de type `T[]`.
1. Une variable de type `ReadOnlyMemory<T>`.
1. Une paire de nœuds <xref:System.Buffers.ReadOnlySequenceSegment%601> de liste et d’index liés pour représenter le début et la position de fin de la séquence.

La troisième représentation est la plus intéressante car elle `ReadOnlySequence<T>`a des implications de performance sur diverses opérations sur le :

|Représentation|Opération|Complexité|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

En raison de cette `ReadOnlySequence<T>` représentation mixte, `SequencePosition` les indices expose comme au lieu d’un intégrant. A `SequencePosition`:

- Est une valeur opaque qui `ReadOnlySequence<T>` représente un indice dans l’endroit où il est originaire.
- Se compose de deux parties, un intégreur et un objet. Ce que ces deux valeurs représentent `ReadOnlySequence<T>`sont liés à la mise en œuvre de .

### <a name="access-data"></a>Accéder aux données

Le `ReadOnlySequence<T>` expose les données comme un `ReadOnlyMemory<T>`enumerable de . L’énumération de chacun des segments peut être faite à l’aide d’un avant-plan de base :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

La méthode précédente recherche chaque segment pour un byte spécifique. Si vous avez besoin de garder `SequencePosition` <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> une trace de chaque segment , est plus approprié. L’échantillon suivant modifie le `SequencePosition` code précédent pour retourner un au lieu d’un intégrant. Le `SequencePosition` retour d’un a l’avantage de permettre à l’appelant d’éviter une deuxième analyse pour obtenir les données à un index spécifique.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

La combinaison `SequencePosition` `TryGet` et agit comme un enumérateur. Le champ de position est modifié au début de chaque itération pour être le début de chaque segment dans le `ReadOnlySequence<T>`.

La méthode précédente existe comme `ReadOnlySequence<T>`méthode d’extension sur . <xref:System.Buffers.BuffersExtensions.PositionOf%2A>peut être utilisé pour simplifier le code précédent :

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>Traiter un ReadOnlySequence\<T\>

Le `ReadOnlySequence<T>` traitement d’un peut être difficile puisque les données peuvent être divisées entre plusieurs segments de la séquence. Pour la meilleure performance, diviser le code en deux chemins :

- Un chemin rapide qui traite du cas du segment unique.
- Un chemin lent qui traite des données réparties entre les segments.

Il existe quelques approches qui peuvent être utilisées pour traiter les données dans des séquences multi-segmentées :

- Utilisez [`SequenceReader<T>`](#sequencereadert)le .
- Segment de données par segment de `SequencePosition` par segment, en gardant une trace de l’indice et de l’indice dans le segment analysé. Cela évite les allocations inutiles, mais peut être inefficace, en particulier pour les petits tampons.
- Copiez `ReadOnlySequence<T>` le à un tableau contigus et le traiter comme un seul tampon:
  - Si la taille `ReadOnlySequence<T>` de la est petite, il peut être raisonnable de copier les données dans un tampon de pile alloué à l’aide de [l’opérateur stackalloc.](../../csharp/language-reference/operators/stackalloc.md)
  - Copiez-le `ReadOnlySequence<T>` dans un <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>tableau mis en commun à l’aide de .
  - Utilisez [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A). Ce n’est pas recommandé dans les `T[]` sentiers chauds car il alloue un nouveau sur le tas.

Les exemples suivants démontrent `ReadOnlySequence<byte>`quelques cas courants pour le traitement :

##### <a name="process-binary-data"></a>Traiter les données binaires

L’exemple suivant analyse une longueur d’intégriste big-endian 4-bytete depuis le début de la `ReadOnlySequence<byte>`.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>Traiter les données textuelles

L’exemple suivant :

- Trouve la première`\r\n`nouvelle ligne `ReadOnlySequence<byte>` ( ) dans le et la renvoie via le paramètre «ligne» out.
- Coupe cette ligne, `\r\n` à l’exclusion du tampon d’entrée.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>Segments vides

Il est valable de stocker des `ReadOnlySequence<T>`segments vides à l’intérieur d’un . Les segments vides peuvent se produire lors de l’énumération explicite des segments :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

Le code précédent `ReadOnlySequence<byte>` crée un avec des segments vides et montre comment ces segments vides affectent les différentes API:

- `ReadOnlySequence<T>.Slice`avec `SequencePosition` un pointage vers un segment vide conserve ce segment.
- `ReadOnlySequence<T>.Slice`avec un int saute sur les segments vides.
- Énumérer les `ReadOnlySequence<T>` énumérations des segments vides.

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>Problèmes potentiels avec ReadOnlySequence\<T> et SequencePosition

Il ya plusieurs résultats inhabituels `ReadOnlySequence<T>` / `SequencePosition` lors de `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int`la gestion d’un vs.

- `SequencePosition`est un marqueur de `ReadOnlySequence<T>`position pour une position spécifique, et non absolue. Parce qu’il est `ReadOnlySequence<T>`relatif à un spécifique, il n’a pas de sens s’il est utilisé en dehors de l’endroit `ReadOnlySequence<T>` où il est originaire.
- Arithmetic ne peut pas `SequencePosition` être `ReadOnlySequence<T>`effectuée sans le . Cela signifie faire `position++` des `ReadOnlySequence<T>.GetPosition(position, 1)`choses de base comme est écrit .
- `GetPosition(long)`ne prend **pas** en charge les indices négatifs. Cela signifie qu’il est impossible d’obtenir l’avant-dernier personnage sans marcher tous les segments.
- Deux `SequencePosition` ne peuvent pas être comparés, ce qui rend difficile de :
  - Sachez si une position est supérieure ou inférieure à celle d’une autre.
  - Écrivez des algorithmes d’analyse.
- `ReadOnlySequence<T>`est plus grand qu’une référence d’objet et doit être passé [par ou](../../csharp/language-reference/keywords/in-parameter-modifier.md) [arbitre](../../csharp/language-reference/keywords/ref.md) dans la mesure du possible. Passer `ReadOnlySequence<T>` `in` ou `ref` réduire des copies de la [struct](../../csharp/language-reference/builtin-types/struct.md).
- Segments vides :
  - Sont valides `ReadOnlySequence<T>`dans un .
  - Peut apparaître lors de `ReadOnlySequence<T>.TryGet` l’itération en utilisant la méthode.
  - Peut apparaître trancher la `ReadOnlySequence<T>.Slice()` séquence `SequencePosition` en utilisant la méthode avec des objets.

## <a name="sequencereadert"></a>SéquenceLire\<T\>

<xref:System.Buffers.SequenceReader%601>:

- Est un nouveau type qui a été introduit dans .NET Core `ReadOnlySequence<T>`3.0 pour simplifier le traitement d’un .
- Unifie les différences entre `ReadOnlySequence<T>` un segment `ReadOnlySequence<T>`unique et un segment multi-segment.
- Fournit des aides pour la`byte` lecture `char`de données binaires et textuelles ( et ) qui peuvent ou ne peuvent pas être divisées entre les segments.

Il existe des méthodes intégrées pour traiter les données binaires et délimitées. La section suivante montre à quoi ressemblent `SequenceReader<T>`ces mêmes méthodes avec le :

### <a name="access-data"></a>Accéder aux données

`SequenceReader<T>`a des méthodes pour énumérer `ReadOnlySequence<T>` les données à l’intérieur du direct. Le code suivant est un `ReadOnlySequence<byte>` `byte` exemple de traitement d’un à la fois :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

Le `CurrentSpan` expose le segment `Span`actuel , qui est similaire à ce qui a été fait dans la méthode manuellement.

### <a name="use-position"></a>Position d’utilisation

Le code suivant est `FindIndexOf` un `SequenceReader<T>`exemple d’implémentation de l’utilisation de la :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>Traiter les données binaires

L’exemple suivant analyse une longueur d’intégriste big-endian 4-bytete depuis le début de la `ReadOnlySequence<byte>`.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>Traiter les données textuelles

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>SéquenceLire\<\> T problèmes communs

- Parce `SequenceReader<T>` que c’est une structable mutable, elle doit toujours être transmise par [référence](../../csharp/language-reference/keywords/ref.md).
- `SequenceReader<T>`est une [structif de ref](../../csharp/language-reference/builtin-types/struct.md#ref-struct) de sorte qu’il ne peut être utilisé que dans des méthodes synchrones et ne peut pas être stocké dans les champs. Pour plus d’informations, voir [Écrire un code Cmd sûr et efficace](../../csharp/write-safe-efficient-code.md).
- `SequenceReader<T>`est optimisé pour une utilisation en tant que lecteur avant-seulement. `Rewind`est destiné à de petites sauvegardes qui `Read`ne `Peek`peuvent `IsNext` pas être traitées en utilisant d’autres , , et API.
