---
title: System. buffers-.NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: f939164cd56b2fb2feeeb171236b0e1171327e19
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160116"
---
# <a name="work-with-buffers-in-net"></a>Utiliser des mémoires tampons dans .NET

Cet article fournit une vue d’ensemble des types qui aident à lire les données qui s’exécutent sur plusieurs mémoires tampons. Ils sont principalement utilisés pour prendre en charge les objets <xref:System.IO.Pipelines.PipeReader>.

## <a name="ibufferwritert"></a>IBufferWriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> est un contrat pour l’écriture en mémoire tampon synchrone. Au niveau le plus bas, l’interface :

- Est de base et n’est pas difficile à utiliser.
- Autorise l’accès à une <xref:System.Memory%601> ou <xref:System.Span%601>. La `Memory<T>` ou la `Span<T>` peut être écrite dans et vous pouvez déterminer le nombre d’éléments de `T` écrits.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

La méthode précédente :

- Demande une mémoire tampon d’au moins 5 octets à partir du `IBufferWriter<byte>` à l’aide de `GetSpan(5)`.
- Écrit des octets pour la chaîne ASCII « Hello » dans le `Span<byte>`retourné.
- Appelle <xref:System.Buffers.IBufferWriter%601> pour indiquer le nombre d’octets qui ont été écrits dans la mémoire tampon.

Cette méthode d’écriture utilise le `Memory<T>`/`Span<T>` mémoire tampon fournie par le `IBufferWriter<T>`. Vous pouvez également utiliser la méthode d’extension <xref:System.Buffers.BuffersExtensions.Write%2A> pour copier une mémoire tampon existante dans le `IBufferWriter<T>`. `Write` effectue le travail d’appel de `GetSpan`/`Advance` si nécessaire. il n’est donc pas nécessaire d’appeler `Advance` après l’écriture :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601> est une implémentation de `IBufferWriter<T>` dont le magasin de stockage est un tableau contigu unique.

### <a name="ibufferwriter-common-problems"></a>Problèmes courants liés à IBufferWriter

- `GetSpan` et `GetMemory` retournent une mémoire tampon avec au moins la quantité de mémoire demandée. Ne supposez pas des tailles de mémoire tampon exactes.
- Il n’y a aucune garantie que les appels successifs retourneront la même mémoire tampon ou la même mémoire tampon de taille.
- Une nouvelle mémoire tampon doit être demandée après l’appel de `Advance` pour continuer à écrire davantage de données. Impossible d’écrire dans une mémoire tampon acquise précédemment après l’appel de `Advance`.

## <a name="readonlysequencet"></a>ReadOnlySequence\<T\>

![ReadOnlySequence indiquant la mémoire dans le canal et en dessous de la position de séquence de la mémoire en lecture seule](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601> est un struct qui peut représenter une séquence contiguë ou non contiguë de `T`. Il peut être construit à partir de :

1. Une variable de type `T[]`.
1. Une variable de type `ReadOnlyMemory<T>`.
1. Paire de nœuds de liste liés <xref:System.Buffers.ReadOnlySequenceSegment%601> et index pour représenter la position de début et de fin de la séquence.

La troisième représentation est la plus intéressante, car elle a une incidence sur les performances de diverses opérations sur le `ReadOnlySequence<T>`:

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

En raison de cette représentation mixte, le `ReadOnlySequence<T>` expose les index comme `SequencePosition` au lieu d’un entier. `SequencePosition`:

- Est une valeur opaque qui représente un index dans le `ReadOnlySequence<T>` à son origine.
- Se compose de deux parties : un entier et un objet. Ce que représentent ces deux valeurs sont liées à l’implémentation de `ReadOnlySequence<T>`.

### <a name="access-data"></a>Accéder aux données

Le `ReadOnlySequence<T>` expose les données sous la forme d’un énumérable de `ReadOnlyMemory<T>`. L’énumération de chacun des segments peut être effectuée à l’aide d’une instruction foreach de base :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

La méthode précédente recherche un octet spécifique dans chaque segment. Si vous devez effectuer le suivi de la `SequencePosition`de chaque segment, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> est plus approprié. L’exemple suivant modifie le code précédent pour retourner un `SequencePosition` au lieu d’un entier. Le retour d’un `SequencePosition` présente l’avantage de permettre à l’appelant d’éviter une deuxième analyse pour obtenir les données à un index spécifique.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

La combinaison de `SequencePosition` et `TryGet` agit comme un énumérateur. Le champ position est modifié au début de chaque itération pour démarrer chaque segment dans le `ReadOnlySequence<T>`.

La méthode précédente existe en tant que méthode d’extension sur `ReadOnlySequence<T>`. <xref:System.Buffers.BuffersExtensions.PositionOf%2A> peut être utilisé pour simplifier le code précédent :

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>Traiter un ReadOnlySequence\<T\>

Le traitement d’un `ReadOnlySequence<T>` peut être difficile, car les données peuvent être réparties entre plusieurs segments au sein de la séquence. Pour des performances optimales, fractionnez le code en deux chemins d’accès :

- Un chemin d’accès rapide qui gère le cas de segment unique.
- Chemin d’accès lent qui traite les données fractionnées entre les segments.

Il existe plusieurs approches qui peuvent être utilisées pour traiter les données dans des séquences multisegment :

- Utilisez l' [`SequenceReader<T>`](#sequencereadert).
- Analyser le segment de données par segment, en effectuant le suivi de la `SequencePosition` et de l’index dans le segment analysé. Cela évite les allocations inutiles, mais peut s’avérer inefficace, en particulier pour les mémoires tampons de petite taille.
- Copiez le `ReadOnlySequence<T>` dans un tableau contigu et traitez-le comme une mémoire tampon unique :
  - Si la taille du `ReadOnlySequence<T>` est faible, il peut être raisonnable de copier les données dans une mémoire tampon allouée par la pile à l’aide de l’opérateur [stackalloc](../../csharp/language-reference/operators/stackalloc.md) .
  - Copiez le `ReadOnlySequence<T>` dans un tableau mis en pool à l’aide de <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.
  - Utilisez [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A). Cela n’est pas recommandé dans les chemins d’accès à chaud, car il alloue une nouvelle `T[]` sur le tas.

Les exemples suivants illustrent des cas courants de traitement de `ReadOnlySequence<byte>`:

##### <a name="process-binary-data"></a>Traiter des données binaires

L’exemple suivant analyse une longueur d’entier Big-endian de 4 octets à partir du début de l' `ReadOnlySequence<byte>`.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>Traiter des données texte

L’exemple suivant :

- Recherche le premier saut de ligne (`\r\n`) dans le `ReadOnlySequence<byte>` et le retourne via le paramètre out’line'.
- Supprime cette ligne, à l’exclusion de la `\r\n` de la mémoire tampon d’entrée.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>Segments vides

Il est valide de stocker des segments vides à l’intérieur d’un `ReadOnlySequence<T>`. Des segments vides peuvent se produire lors de l’énumération des segments de manière explicite :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

Le code précédent crée un `ReadOnlySequence<byte>` avec des segments vides et montre comment ces segments vides affectent les différentes API :

- `ReadOnlySequence<T>.Slice` avec un `SequencePosition` pointant vers un segment vide préserve ce segment.
- `ReadOnlySequence<T>.Slice` avec un entier ignore les segments vides.
- L’énumération du `ReadOnlySequence<T>` énumère les segments vides.

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>Problèmes potentiels avec ReadOnlySequence\<T > et SequencePosition

Il existe plusieurs résultats inhabituels lors du traitement d’un `ReadOnlySequence<T>`/`SequencePosition` par rapport à un `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:

- `SequencePosition` est un marqueur de position pour un `ReadOnlySequence<T>`spécifique, et non une position absolue. Étant donné qu’il est relatif à un `ReadOnlySequence<T>`spécifique, il n’a pas de sens s’il est utilisé en dehors du `ReadOnlySequence<T>` d’où il provient.
- L’arithmétique ne peut pas être exécutée sur `SequencePosition` sans le `ReadOnlySequence<T>`. Cela signifie que les opérations de base comme `position++` sont écrites `ReadOnlySequence<T>.GetPosition(position, 1)`.
- `GetPosition(long)` ne prend **pas** en charge les index négatifs. Cela signifie qu’il est impossible d’extraire l’avant-dernier caractère sans parcourir tous les segments.
- Deux `SequencePosition` ne peuvent pas être comparés, ce qui complique la tâche :
  - Savoir si une position est supérieure ou inférieure à une autre position.
  - Écrivez des algorithmes d’analyse.
- `ReadOnlySequence<T>` est plus grand qu’une référence d’objet et doit être passé par in ou [ref](../../csharp/language-reference/keywords/ref.md) dans la mesure [du](../../csharp/language-reference/keywords/in-parameter-modifier.md) possible. Le passage de `ReadOnlySequence<T>` par `in` ou `ref` réduit les copies du [struct](../../csharp/language-reference/builtin-types/struct.md).
- Segments vides :
  - Sont valides dans un `ReadOnlySequence<T>`.
  - Peut apparaître lors de l’itération à l’aide de la méthode `ReadOnlySequence<T>.TryGet`.
  - Peut apparaître le découpage de la séquence à l’aide de la méthode `ReadOnlySequence<T>.Slice()` avec des objets `SequencePosition`.

## <a name="sequencereadert"></a>SequenceReader\<T\>

<xref:System.Buffers.SequenceReader%601>:

- Est un nouveau type qui a été introduit dans .NET Core 3,0 pour simplifier le traitement d’un `ReadOnlySequence<T>`.
- Unifie les différences entre un segment unique `ReadOnlySequence<T>` et des `ReadOnlySequence<T>`à plusieurs segments.
- Fournit des assistances pour la lecture de données binaires et textuelles (`byte` et `char`) qui peuvent ou ne peuvent pas être fractionnées entre les segments.

Il existe des méthodes intégrées pour traiter le traitement des données binaires et délimitées. La section suivante montre à quoi ressemblent ces mêmes méthodes avec l' `SequenceReader<T>`:

### <a name="access-data"></a>Accéder aux données

`SequenceReader<T>` a des méthodes pour énumérer directement des données à l’intérieur du `ReadOnlySequence<T>`. Le code suivant est un exemple de traitement d’un `ReadOnlySequence<byte>` un `byte` à la fois :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

L' `CurrentSpan` expose le `Span`du segment actuel, ce qui est similaire à ce qui a été fait manuellement dans la méthode.

### <a name="use-position"></a>Utiliser la position

Le code suivant est un exemple d’implémentation de `FindIndexOf` à l’aide de la `SequenceReader<T>`:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>Traiter des données binaires

L’exemple suivant analyse une longueur d’entier Big-endian de 4 octets à partir du début de l' `ReadOnlySequence<byte>`.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>Traiter des données texte

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>SequenceReader\<T\> problèmes courants

- Étant donné que `SequenceReader<T>` est un struct mutable, il doit toujours être passé par [référence](../../csharp/language-reference/keywords/ref.md).
- `SequenceReader<T>` est un [struct de référence](../../csharp/language-reference/keywords/ref.md#ref-struct-types) , il ne peut donc être utilisé que dans des méthodes synchrones et ne peut pas être stocké dans des champs. Pour plus d’informations, consultez [écrire du code C# sécurisé et efficace](../../csharp/write-safe-efficient-code.md).
- `SequenceReader<T>` est optimisé pour une utilisation en tant que lecteur avant uniquement. `Rewind` est destiné aux petites sauvegardes qui ne peuvent pas être traitées à l’aide d’autres API de `Read`, `Peek`et `IsNext`.
