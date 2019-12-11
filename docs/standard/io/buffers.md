---
title: System. buffers-.NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: e42f165bfedec3b1fa54615ee7e2a2028f40aadb
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960494"
---
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="befe4-102">Utiliser des mémoires tampons dans .NET</span><span class="sxs-lookup"><span data-stu-id="befe4-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="befe4-103">Cet article fournit une vue d’ensemble des types qui aident à lire les données qui s’exécutent sur plusieurs mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="befe4-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="befe4-104">Ils sont principalement utilisés pour prendre en charge les objets <xref:System.IO.Pipelines.PipeReader>.</span><span class="sxs-lookup"><span data-stu-id="befe4-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="befe4-105">IBufferWriter\<T\></span><span class="sxs-lookup"><span data-stu-id="befe4-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="befe4-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> est un contrat pour l’écriture en mémoire tampon synchrone.</span><span class="sxs-lookup"><span data-stu-id="befe4-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="befe4-107">Au niveau le plus bas, l’interface :</span><span class="sxs-lookup"><span data-stu-id="befe4-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="befe4-108">Est de base et n’est pas difficile à utiliser.</span><span class="sxs-lookup"><span data-stu-id="befe4-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="befe4-109">Autorise l’accès à une <xref:System.Memory%601> ou <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="befe4-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="befe4-110">La `Memory<T>` ou la `Span<T>` peut être écrite dans et vous pouvez déterminer le nombre d’éléments de `T` écrits.</span><span class="sxs-lookup"><span data-stu-id="befe4-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="befe4-111">La méthode précédente :</span><span class="sxs-lookup"><span data-stu-id="befe4-111">The preceding method:</span></span>

- <span data-ttu-id="befe4-112">Demande une mémoire tampon d’au moins 5 octets à partir du `IBufferWriter<byte>` à l’aide de `GetSpan(5)`.</span><span class="sxs-lookup"><span data-stu-id="befe4-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="befe4-113">Écrit des octets pour la chaîne ASCII « Hello » dans le `Span<byte>`retourné.</span><span class="sxs-lookup"><span data-stu-id="befe4-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="befe4-114">Appelle <xref:System.Buffers.IBufferWriter%601> pour indiquer le nombre d’octets qui ont été écrits dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="befe4-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="befe4-115">Cette méthode d’écriture utilise le `Memory<T>`/`Span<T>` mémoire tampon fournie par le `IBufferWriter<T>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="befe4-116">Vous pouvez également utiliser la méthode d’extension <xref:System.Buffers.BuffersExtensions.Write%2A> pour copier une mémoire tampon existante dans le `IBufferWriter<T>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="befe4-117">`Write` effectue le travail d’appel de `GetSpan`/`Advance` si nécessaire. il n’est donc pas nécessaire d’appeler `Advance` après l’écriture :</span><span class="sxs-lookup"><span data-stu-id="befe4-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="befe4-118"><xref:System.Buffers.ArrayBufferWriter%601> est une implémentation de `IBufferWriter<T>` dont le magasin de stockage est un tableau contigu unique.</span><span class="sxs-lookup"><span data-stu-id="befe4-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="befe4-119">Problèmes courants liés à IBufferWriter</span><span class="sxs-lookup"><span data-stu-id="befe4-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="befe4-120">`GetSpan` et `GetMemory` retournent une mémoire tampon avec au moins la quantité de mémoire demandée.</span><span class="sxs-lookup"><span data-stu-id="befe4-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="befe4-121">Ne supposez pas des tailles de mémoire tampon exactes.</span><span class="sxs-lookup"><span data-stu-id="befe4-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="befe4-122">Il n’y a aucune garantie que les appels successifs retourneront la même mémoire tampon ou la même mémoire tampon de taille.</span><span class="sxs-lookup"><span data-stu-id="befe4-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="befe4-123">Une nouvelle mémoire tampon doit être demandée après l’appel de `Advance` pour continuer à écrire davantage de données.</span><span class="sxs-lookup"><span data-stu-id="befe4-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="befe4-124">Impossible d’écrire dans une mémoire tampon acquise précédemment après l’appel de `Advance`.</span><span class="sxs-lookup"><span data-stu-id="befe4-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="befe4-125">ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="befe4-125">ReadOnlySequence\<T\></span></span>

![ReadOnlySequence indiquant la mémoire dans le canal et en dessous de la position de séquence de la mémoire en lecture seule](media/buffers/ro-sequence.png)

<span data-ttu-id="befe4-127"><xref:System.Buffers.ReadOnlySequence%601> est un struct qui peut représenter une séquence contiguë ou non contiguë de `T`.</span><span class="sxs-lookup"><span data-stu-id="befe4-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="befe4-128">Il peut être construit à partir de :</span><span class="sxs-lookup"><span data-stu-id="befe4-128">It can be constructed from:</span></span>

1. <span data-ttu-id="befe4-129">`T[]`</span><span class="sxs-lookup"><span data-stu-id="befe4-129">A `T[]`</span></span>
1. <span data-ttu-id="befe4-130">`ReadOnlyMemory<T>`</span><span class="sxs-lookup"><span data-stu-id="befe4-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="befe4-131">Paire de nœuds de liste liés <xref:System.Buffers.ReadOnlySequenceSegment%601> et index pour représenter la position de début et de fin de la séquence.</span><span class="sxs-lookup"><span data-stu-id="befe4-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="befe4-132">La troisième représentation est la plus intéressante, car elle a une incidence sur les performances de diverses opérations sur le `ReadOnlySequence<T>`:</span><span class="sxs-lookup"><span data-stu-id="befe4-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="befe4-133">Représentation</span><span class="sxs-lookup"><span data-stu-id="befe4-133">Representation</span></span>|<span data-ttu-id="befe4-134">Opération</span><span class="sxs-lookup"><span data-stu-id="befe4-134">Operation</span></span>|<span data-ttu-id="befe4-135">Complexité</span><span class="sxs-lookup"><span data-stu-id="befe4-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="befe4-136">En raison de cette représentation mixte, le `ReadOnlySequence<T>` expose les index comme `SequencePosition` au lieu d’un entier.</span><span class="sxs-lookup"><span data-stu-id="befe4-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="befe4-137">`SequencePosition`:</span><span class="sxs-lookup"><span data-stu-id="befe4-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="befe4-138">Est une valeur opaque qui représente un index dans le `ReadOnlySequence<T>` à son origine.</span><span class="sxs-lookup"><span data-stu-id="befe4-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="befe4-139">Se compose de deux parties : un entier et un objet.</span><span class="sxs-lookup"><span data-stu-id="befe4-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="befe4-140">Ce que représentent ces deux valeurs sont liées à l’implémentation de `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="befe4-141">Accéder aux données</span><span class="sxs-lookup"><span data-stu-id="befe4-141">Access data</span></span>

<span data-ttu-id="befe4-142">Le `ReadOnlySequence<T>` expose les données sous la forme d’un énumérable de `ReadOnlyMemory<T>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="befe4-143">L’énumération de chacun des segments peut être effectuée à l’aide d’une instruction foreach de base :</span><span class="sxs-lookup"><span data-stu-id="befe4-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="befe4-144">La méthode précédente recherche un octet spécifique dans chaque segment.</span><span class="sxs-lookup"><span data-stu-id="befe4-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="befe4-145">Si vous devez effectuer le suivi de la `SequencePosition`de chaque segment, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> est plus approprié.</span><span class="sxs-lookup"><span data-stu-id="befe4-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="befe4-146">L’exemple suivant modifie le code précédent pour retourner un `SequencePosition` au lieu d’un entier.</span><span class="sxs-lookup"><span data-stu-id="befe4-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="befe4-147">Le retour d’un `SequencePosition` présente l’avantage de permettre à l’appelant d’éviter une deuxième analyse pour obtenir les données à un index spécifique.</span><span class="sxs-lookup"><span data-stu-id="befe4-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="befe4-148">La combinaison de `SequencePosition` et `TryGet` agit comme un énumérateur.</span><span class="sxs-lookup"><span data-stu-id="befe4-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="befe4-149">Le champ position est modifié au début de chaque itération pour démarrer chaque segment dans le `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="befe4-150">La méthode précédente existe en tant que méthode d’extension sur `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="befe4-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> peut être utilisé pour simplifier le code précédent :</span><span class="sxs-lookup"><span data-stu-id="befe4-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="befe4-152">Traiter un ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="befe4-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="befe4-153">Le traitement d’un `ReadOnlySequence<T>` peut être difficile, car les données peuvent être réparties entre plusieurs segments au sein de la séquence.</span><span class="sxs-lookup"><span data-stu-id="befe4-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="befe4-154">Pour des performances optimales, fractionnez le code en deux chemins d’accès :</span><span class="sxs-lookup"><span data-stu-id="befe4-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="befe4-155">Un chemin d’accès rapide qui gère le cas de segment unique.</span><span class="sxs-lookup"><span data-stu-id="befe4-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="befe4-156">Chemin d’accès lent qui traite les données fractionnées entre les segments.</span><span class="sxs-lookup"><span data-stu-id="befe4-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="befe4-157">Il existe plusieurs approches qui peuvent être utilisées pour traiter les données dans des séquences multisegment :</span><span class="sxs-lookup"><span data-stu-id="befe4-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="befe4-158">Utilisez l' [`SequenceReader<T>`](#sequencereadert).</span><span class="sxs-lookup"><span data-stu-id="befe4-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="befe4-159">Analyser le segment de données par segment, en effectuant le suivi de la `SequencePosition` et de l’index dans le segment analysé.</span><span class="sxs-lookup"><span data-stu-id="befe4-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="befe4-160">Cela évite les allocations inutiles, mais peut s’avérer inefficace, en particulier pour les mémoires tampons de petite taille.</span><span class="sxs-lookup"><span data-stu-id="befe4-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="befe4-161">Copiez le `ReadOnlySequence<T>` dans un tableau contigu et traitez-le comme une mémoire tampon unique :</span><span class="sxs-lookup"><span data-stu-id="befe4-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="befe4-162">Si la taille du `ReadOnlySequence<T>` est faible, il peut être raisonnable de copier les données dans une mémoire tampon allouée par la pile à l’aide de l’opérateur [stackalloc](../../csharp/language-reference/operators/stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="befe4-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="befe4-163">Copiez le `ReadOnlySequence<T>` dans un tableau mis en pool à l’aide de <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="befe4-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="befe4-164">Utilisez [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span><span class="sxs-lookup"><span data-stu-id="befe4-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="befe4-165">Cela n’est pas recommandé dans les chemins d’accès à chaud, car il alloue une nouvelle `T[]` sur le tas.</span><span class="sxs-lookup"><span data-stu-id="befe4-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="befe4-166">Les exemples suivants illustrent des cas courants de traitement de `ReadOnlySequence<byte>`:</span><span class="sxs-lookup"><span data-stu-id="befe4-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="befe4-167">Traiter des données binaires</span><span class="sxs-lookup"><span data-stu-id="befe4-167">Process binary data</span></span>

<span data-ttu-id="befe4-168">L’exemple suivant analyse une longueur d’entier Big-endian de 4 octets à partir du début de l' `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

##### <a name="process-text-data"></a><span data-ttu-id="befe4-169">Traiter des données texte</span><span class="sxs-lookup"><span data-stu-id="befe4-169">Process text data</span></span>

<span data-ttu-id="befe4-170">L’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="befe4-170">The following example:</span></span>

- <span data-ttu-id="befe4-171">Recherche le premier saut de ligne (`\r\n`) dans le `ReadOnlySequence<byte>` et le retourne via le paramètre out’line'.</span><span class="sxs-lookup"><span data-stu-id="befe4-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="befe4-172">Supprime cette ligne, à l’exclusion de la `\r\n` de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="befe4-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="befe4-173">Segments vides</span><span class="sxs-lookup"><span data-stu-id="befe4-173">Empty segments</span></span>

<span data-ttu-id="befe4-174">Il est valide de stocker des segments vides à l’intérieur d’un `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="befe4-175">Des segments vides peuvent se produire lors de l’énumération des segments de manière explicite :</span><span class="sxs-lookup"><span data-stu-id="befe4-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="befe4-176">Le code précédent crée un `ReadOnlySequence<byte>` avec des segments vides et montre comment ces segments vides affectent les différentes API :</span><span class="sxs-lookup"><span data-stu-id="befe4-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="befe4-177">`ReadOnlySequence<T>.Slice` avec un `SequencePosition` pointant vers un segment vide préserve ce segment.</span><span class="sxs-lookup"><span data-stu-id="befe4-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="befe4-178">`ReadOnlySequence<T>.Slice` avec un entier ignore les segments vides.</span><span class="sxs-lookup"><span data-stu-id="befe4-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="befe4-179">L’énumération du `ReadOnlySequence<T>` énumère les segments vides.</span><span class="sxs-lookup"><span data-stu-id="befe4-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="befe4-180">Problèmes potentiels avec ReadOnlySequence\<T > et SequencePosition</span><span class="sxs-lookup"><span data-stu-id="befe4-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="befe4-181">Il existe plusieurs résultats inhabituels lors du traitement d’un `ReadOnlySequence<T>`/`SequencePosition` par rapport à un `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span><span class="sxs-lookup"><span data-stu-id="befe4-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="befe4-182">`SequencePosition` est un marqueur de position pour un `ReadOnlySequence<T>`spécifique, et non une position absolue.</span><span class="sxs-lookup"><span data-stu-id="befe4-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="befe4-183">Étant donné qu’il est relatif à un `ReadOnlySequence<T>`spécifique, il n’a pas de sens s’il est utilisé en dehors du `ReadOnlySequence<T>` d’où il provient.</span><span class="sxs-lookup"><span data-stu-id="befe4-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="befe4-184">L’arithmétique ne peut pas être exécutée sur `SequencePosition` sans le `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="befe4-185">Cela signifie que les opérations de base comme `position++` sont écrites `ReadOnlySequence<T>.GetPosition(position, 1)`.</span><span class="sxs-lookup"><span data-stu-id="befe4-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="befe4-186">`GetPosition(long)` ne prend **pas** en charge les index négatifs.</span><span class="sxs-lookup"><span data-stu-id="befe4-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="befe4-187">Cela signifie qu’il est impossible d’extraire l’avant-dernier caractère sans parcourir tous les segments.</span><span class="sxs-lookup"><span data-stu-id="befe4-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="befe4-188">Deux `SequencePosition` ne peuvent pas être comparés, ce qui complique la tâche :</span><span class="sxs-lookup"><span data-stu-id="befe4-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="befe4-189">Savoir si une position est supérieure ou inférieure à une autre position.</span><span class="sxs-lookup"><span data-stu-id="befe4-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="befe4-190">Écrivez des algorithmes d’analyse.</span><span class="sxs-lookup"><span data-stu-id="befe4-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="befe4-191">`ReadOnlySequence<T>` est plus grand qu’une référence d’objet et doit être passé par in ou [ref](../../csharp/language-reference/keywords/ref.md) dans la mesure [du](../../csharp/language-reference/keywords/in-parameter-modifier.md) possible.</span><span class="sxs-lookup"><span data-stu-id="befe4-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="befe4-192">Le passage de `ReadOnlySequence<T>` par `in` ou `ref` réduit les copies du [struct](../../csharp/language-reference/keywords/struct.md).</span><span class="sxs-lookup"><span data-stu-id="befe4-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/keywords/struct.md).</span></span>
- <span data-ttu-id="befe4-193">Segments vides :</span><span class="sxs-lookup"><span data-stu-id="befe4-193">Empty segments:</span></span>
  - <span data-ttu-id="befe4-194">Sont valides dans un `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="befe4-195">Peut apparaître lors de l’itération à l’aide de la méthode `ReadOnlySequence<T>.TryGet`.</span><span class="sxs-lookup"><span data-stu-id="befe4-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="befe4-196">Peut apparaître le découpage de la séquence à l’aide de la méthode `ReadOnlySequence<T>.Slice()` avec des objets `SequencePosition`.</span><span class="sxs-lookup"><span data-stu-id="befe4-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="befe4-197">SequenceReader\<T\></span><span class="sxs-lookup"><span data-stu-id="befe4-197">SequenceReader\<T\></span></span>

<span data-ttu-id="befe4-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="befe4-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="befe4-199">Est un nouveau type qui a été introduit dans .NET Core 3,0 pour simplifier le traitement d’un `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="befe4-200">Unifie les différences entre un segment unique `ReadOnlySequence<T>` et des `ReadOnlySequence<T>`à plusieurs segments.</span><span class="sxs-lookup"><span data-stu-id="befe4-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="befe4-201">Fournit des assistances pour la lecture de données binaires et textuelles (`byte` et `char`) qui peuvent ou ne peuvent pas être fractionnées entre les segments.</span><span class="sxs-lookup"><span data-stu-id="befe4-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="befe4-202">Il existe des méthodes intégrées pour traiter le traitement des données binaires et délimitées.</span><span class="sxs-lookup"><span data-stu-id="befe4-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="befe4-203">La section suivante montre à quoi ressemblent ces mêmes méthodes avec l' `SequenceReader<T>`:</span><span class="sxs-lookup"><span data-stu-id="befe4-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="befe4-204">Accéder aux données</span><span class="sxs-lookup"><span data-stu-id="befe4-204">Access data</span></span>

<span data-ttu-id="befe4-205">`SequenceReader<T>` a des méthodes pour énumérer directement des données à l’intérieur du `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="befe4-206">Le code suivant est un exemple de traitement d’un `ReadOnlySequence<byte>` un `byte` à la fois :</span><span class="sxs-lookup"><span data-stu-id="befe4-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="befe4-207">L' `CurrentSpan` expose le `Span`du segment actuel, ce qui est similaire à ce qui a été fait manuellement dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="befe4-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="befe4-208">Utiliser la position</span><span class="sxs-lookup"><span data-stu-id="befe4-208">Use position</span></span>

<span data-ttu-id="befe4-209">Le code suivant est un exemple d’implémentation de `FindIndexOf` à l’aide de la `SequenceReader<T>`:</span><span class="sxs-lookup"><span data-stu-id="befe4-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="befe4-210">Traiter des données binaires</span><span class="sxs-lookup"><span data-stu-id="befe4-210">Process binary data</span></span>

<span data-ttu-id="befe4-211">L’exemple suivant analyse une longueur d’entier Big-endian de 4 octets à partir du début de l' `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="befe4-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="befe4-212">Traiter des données texte</span><span class="sxs-lookup"><span data-stu-id="befe4-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="befe4-213">SequenceReader\<T\> problèmes courants</span><span class="sxs-lookup"><span data-stu-id="befe4-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="befe4-214">Étant donné que `SequenceReader<T>` est un struct mutable, il doit toujours être passé par [référence](../../csharp/language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="befe4-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="befe4-215">`SequenceReader<T>` est un [struct de référence](../../csharp/language-reference/keywords/ref.md#ref-struct-types) , il ne peut donc être utilisé que dans des méthodes synchrones et ne peut pas être stocké dans des champs.</span><span class="sxs-lookup"><span data-stu-id="befe4-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/keywords/ref.md#ref-struct-types) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="befe4-216">Pour plus d’informations, consultez [écrire du code C# sécurisé et efficace](../../csharp/write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="befe4-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="befe4-217">`SequenceReader<T>` est optimisé pour une utilisation en tant que lecteur avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="befe4-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="befe4-218">`Rewind` est destiné aux petites sauvegardes qui ne peuvent pas être traitées à l’aide d’autres API de `Read`, `Peek`et `IsNext`.</span><span class="sxs-lookup"><span data-stu-id="befe4-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
