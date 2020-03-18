---
title: System.Buffers - .NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: f939164cd56b2fb2feeeb171236b0e1171327e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160116"
---
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="cd2e9-102">Travailler avec Buffers en .NET</span><span class="sxs-lookup"><span data-stu-id="cd2e9-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="cd2e9-103">Cet article fournit un aperçu des types qui aident à lire les données qui s’exécutent à travers plusieurs tampons.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="cd2e9-104">Ils sont principalement utilisés <xref:System.IO.Pipelines.PipeReader> pour soutenir les objets.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="cd2e9-105">IBufferWriter\<T\></span><span class="sxs-lookup"><span data-stu-id="cd2e9-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="cd2e9-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>est un contrat pour l’écriture tampon synchrone.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="cd2e9-107">Au niveau le plus bas, l’interface:</span><span class="sxs-lookup"><span data-stu-id="cd2e9-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="cd2e9-108">Est basique et pas difficile à utiliser.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="cd2e9-109">Permet l’accès à un <xref:System.Memory%601> ou <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="cd2e9-110">Le `Memory<T>` `Span<T>` ou peut être écrit à `T` et vous pouvez déterminer combien d’articles ont été écrits.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="cd2e9-111">La méthode précédente :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-111">The preceding method:</span></span>

- <span data-ttu-id="cd2e9-112">Demande un tampon d’au moins `IBufferWriter<byte>` 5 octets de l’utilisation `GetSpan(5)`.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="cd2e9-113">Écrit octets pour la chaîne ASCII `Span<byte>`"Bonjour" à l’retourné .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="cd2e9-114">Appels <xref:System.Buffers.IBufferWriter%601> pour indiquer combien d’octets ont été écrits au tampon.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="cd2e9-115">Cette méthode d’écriture utilise `Memory<T>` / `Span<T>` `IBufferWriter<T>`le tampon fourni par le .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="cd2e9-116">Alternativement, <xref:System.Buffers.BuffersExtensions.Write%2A> la méthode d’extension peut être `IBufferWriter<T>`utilisée pour copier un tampon existant à la .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="cd2e9-117">`Write`fait le travail `GetSpan` / `Advance` d’appel le cas échéant, `Advance` il n’est donc pas nécessaire d’appeler après l’écriture:</span><span class="sxs-lookup"><span data-stu-id="cd2e9-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="cd2e9-118"><xref:System.Buffers.ArrayBufferWriter%601>est une `IBufferWriter<T>` mise en œuvre de dont le magasin de soutien est un tableau contigus unique.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="cd2e9-119">Problèmes communs iBufferWriter</span><span class="sxs-lookup"><span data-stu-id="cd2e9-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="cd2e9-120">`GetSpan`et `GetMemory` retourner un tampon avec au moins la quantité demandée de mémoire.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="cd2e9-121">N’assumez pas les tailles exactes de tampon.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="cd2e9-122">Il n’y a aucune garantie que les appels successifs retourneront le même tampon ou le même tampon de taille.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="cd2e9-123">Un nouveau tampon doit `Advance` être demandé après avoir appelé pour continuer à écrire plus de données.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="cd2e9-124">Un tampon acquis précédemment ne `Advance` peut pas être écrit après a été appelé.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="cd2e9-125">LireOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="cd2e9-125">ReadOnlySequence\<T\></span></span>

![LireOnlySequence montrant la mémoire dans le tuyau et en dessous de cette position de séquence de la mémoire lue seulement](media/buffers/ro-sequence.png)

<span data-ttu-id="cd2e9-127"><xref:System.Buffers.ReadOnlySequence%601>est une struct qui peut représenter une séquence contigu ou non contigue de `T`.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="cd2e9-128">Il peut être construit à partir de:</span><span class="sxs-lookup"><span data-stu-id="cd2e9-128">It can be constructed from:</span></span>

1. <span data-ttu-id="cd2e9-129">Une variable de type `T[]`.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-129">A `T[]`</span></span>
1. <span data-ttu-id="cd2e9-130">Une variable de type `ReadOnlyMemory<T>`.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="cd2e9-131">Une paire de nœuds <xref:System.Buffers.ReadOnlySequenceSegment%601> de liste et d’index liés pour représenter le début et la position de fin de la séquence.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="cd2e9-132">La troisième représentation est la plus intéressante car elle `ReadOnlySequence<T>`a des implications de performance sur diverses opérations sur le :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="cd2e9-133">Représentation</span><span class="sxs-lookup"><span data-stu-id="cd2e9-133">Representation</span></span>|<span data-ttu-id="cd2e9-134">Opération</span><span class="sxs-lookup"><span data-stu-id="cd2e9-134">Operation</span></span>|<span data-ttu-id="cd2e9-135">Complexité</span><span class="sxs-lookup"><span data-stu-id="cd2e9-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="cd2e9-136">En raison de cette `ReadOnlySequence<T>` représentation mixte, `SequencePosition` les indices expose comme au lieu d’un intégrant.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="cd2e9-137">A `SequencePosition`:</span><span class="sxs-lookup"><span data-stu-id="cd2e9-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="cd2e9-138">Est une valeur opaque qui `ReadOnlySequence<T>` représente un indice dans l’endroit où il est originaire.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="cd2e9-139">Se compose de deux parties, un intégreur et un objet.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="cd2e9-140">Ce que ces deux valeurs représentent `ReadOnlySequence<T>`sont liés à la mise en œuvre de .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="cd2e9-141">Accéder aux données</span><span class="sxs-lookup"><span data-stu-id="cd2e9-141">Access data</span></span>

<span data-ttu-id="cd2e9-142">Le `ReadOnlySequence<T>` expose les données comme un `ReadOnlyMemory<T>`enumerable de .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="cd2e9-143">L’énumération de chacun des segments peut être faite à l’aide d’un avant-plan de base :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="cd2e9-144">La méthode précédente recherche chaque segment pour un byte spécifique.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="cd2e9-145">Si vous avez besoin de garder `SequencePosition` <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> une trace de chaque segment , est plus approprié.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="cd2e9-146">L’échantillon suivant modifie le `SequencePosition` code précédent pour retourner un au lieu d’un intégrant.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="cd2e9-147">Le `SequencePosition` retour d’un a l’avantage de permettre à l’appelant d’éviter une deuxième analyse pour obtenir les données à un index spécifique.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="cd2e9-148">La combinaison `SequencePosition` `TryGet` et agit comme un enumérateur.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="cd2e9-149">Le champ de position est modifié au début de chaque itération pour être le début de chaque segment dans le `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="cd2e9-150">La méthode précédente existe comme `ReadOnlySequence<T>`méthode d’extension sur .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="cd2e9-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A>peut être utilisé pour simplifier le code précédent :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="cd2e9-152">Traiter un ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="cd2e9-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="cd2e9-153">Le `ReadOnlySequence<T>` traitement d’un peut être difficile puisque les données peuvent être divisées entre plusieurs segments de la séquence.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="cd2e9-154">Pour la meilleure performance, diviser le code en deux chemins :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="cd2e9-155">Un chemin rapide qui traite du cas du segment unique.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="cd2e9-156">Un chemin lent qui traite des données réparties entre les segments.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="cd2e9-157">Il existe quelques approches qui peuvent être utilisées pour traiter les données dans des séquences multi-segmentées :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="cd2e9-158">Utilisez [`SequenceReader<T>`](#sequencereadert)le .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="cd2e9-159">Segment de données par segment de `SequencePosition` par segment, en gardant une trace de l’indice et de l’indice dans le segment analysé.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="cd2e9-160">Cela évite les allocations inutiles, mais peut être inefficace, en particulier pour les petits tampons.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="cd2e9-161">Copiez `ReadOnlySequence<T>` le à un tableau contigus et le traiter comme un seul tampon:</span><span class="sxs-lookup"><span data-stu-id="cd2e9-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="cd2e9-162">Si la taille `ReadOnlySequence<T>` de la est petite, il peut être raisonnable de copier les données dans un tampon de pile alloué à l’aide de [l’opérateur stackalloc.](../../csharp/language-reference/operators/stackalloc.md)</span><span class="sxs-lookup"><span data-stu-id="cd2e9-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="cd2e9-163">Copiez-le `ReadOnlySequence<T>` dans un <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>tableau mis en commun à l’aide de .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="cd2e9-164">Utilisation [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span><span class="sxs-lookup"><span data-stu-id="cd2e9-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="cd2e9-165">Ce n’est pas recommandé dans les `T[]` sentiers chauds car il alloue un nouveau sur le tas.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="cd2e9-166">Les exemples suivants démontrent `ReadOnlySequence<byte>`quelques cas courants pour le traitement :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="cd2e9-167">Traiter les données binaires</span><span class="sxs-lookup"><span data-stu-id="cd2e9-167">Process binary data</span></span>

<span data-ttu-id="cd2e9-168">L’exemple suivant analyse une longueur d’intégriste big-endian 4-bytete depuis le début de la `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="cd2e9-169">Traiter les données textuelles</span><span class="sxs-lookup"><span data-stu-id="cd2e9-169">Process text data</span></span>

<span data-ttu-id="cd2e9-170">L’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-170">The following example:</span></span>

- <span data-ttu-id="cd2e9-171">Trouve la première`\r\n`nouvelle ligne `ReadOnlySequence<byte>` ( ) dans le et la renvoie via le paramètre «ligne» out.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="cd2e9-172">Coupe cette ligne, `\r\n` à l’exclusion du tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="cd2e9-173">Segments vides</span><span class="sxs-lookup"><span data-stu-id="cd2e9-173">Empty segments</span></span>

<span data-ttu-id="cd2e9-174">Il est valable de stocker des `ReadOnlySequence<T>`segments vides à l’intérieur d’un .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="cd2e9-175">Les segments vides peuvent se produire lors de l’énumération explicite des segments :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="cd2e9-176">Le code précédent `ReadOnlySequence<byte>` crée un avec des segments vides et montre comment ces segments vides affectent les différentes API:</span><span class="sxs-lookup"><span data-stu-id="cd2e9-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="cd2e9-177">`ReadOnlySequence<T>.Slice`avec `SequencePosition` un pointage vers un segment vide conserve ce segment.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="cd2e9-178">`ReadOnlySequence<T>.Slice`avec un int saute sur les segments vides.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="cd2e9-179">Énumérer les `ReadOnlySequence<T>` énumérations des segments vides.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="cd2e9-180">Problèmes potentiels avec ReadOnlySequence\<T> et SequencePosition</span><span class="sxs-lookup"><span data-stu-id="cd2e9-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="cd2e9-181">Il ya plusieurs résultats inhabituels `ReadOnlySequence<T>` / `SequencePosition` lors de `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int`la gestion d’un vs.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="cd2e9-182">`SequencePosition`est un marqueur de `ReadOnlySequence<T>`position pour une position spécifique, et non absolue.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="cd2e9-183">Parce qu’il est `ReadOnlySequence<T>`relatif à un spécifique, il n’a pas de sens s’il est utilisé en dehors de l’endroit `ReadOnlySequence<T>` où il est originaire.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="cd2e9-184">Arithmetic ne peut pas `SequencePosition` être `ReadOnlySequence<T>`effectuée sans le .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="cd2e9-185">Cela signifie faire `position++` des `ReadOnlySequence<T>.GetPosition(position, 1)`choses de base comme est écrit .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="cd2e9-186">`GetPosition(long)`ne prend **pas** en charge les indices négatifs.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="cd2e9-187">Cela signifie qu’il est impossible d’obtenir l’avant-dernier personnage sans marcher tous les segments.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="cd2e9-188">Deux `SequencePosition` ne peuvent pas être comparés, ce qui rend difficile de :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="cd2e9-189">Sachez si une position est supérieure ou inférieure à celle d’une autre.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="cd2e9-190">Écrivez des algorithmes d’analyse.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="cd2e9-191">`ReadOnlySequence<T>`est plus grand qu’une référence d’objet et doit être passé [par ou](../../csharp/language-reference/keywords/in-parameter-modifier.md) [arbitre](../../csharp/language-reference/keywords/ref.md) dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="cd2e9-192">Passer `ReadOnlySequence<T>` `in` ou `ref` réduire des copies de la [struct](../../csharp/language-reference/builtin-types/struct.md).</span><span class="sxs-lookup"><span data-stu-id="cd2e9-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="cd2e9-193">Segments vides :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-193">Empty segments:</span></span>
  - <span data-ttu-id="cd2e9-194">Sont valides `ReadOnlySequence<T>`dans un .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="cd2e9-195">Peut apparaître lors de `ReadOnlySequence<T>.TryGet` l’itération en utilisant la méthode.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="cd2e9-196">Peut apparaître trancher la `ReadOnlySequence<T>.Slice()` séquence `SequencePosition` en utilisant la méthode avec des objets.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="cd2e9-197">SéquenceLire\<T\></span><span class="sxs-lookup"><span data-stu-id="cd2e9-197">SequenceReader\<T\></span></span>

<span data-ttu-id="cd2e9-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="cd2e9-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="cd2e9-199">Est un nouveau type qui a été introduit dans .NET Core `ReadOnlySequence<T>`3.0 pour simplifier le traitement d’un .</span><span class="sxs-lookup"><span data-stu-id="cd2e9-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="cd2e9-200">Unifie les différences entre `ReadOnlySequence<T>` un segment `ReadOnlySequence<T>`unique et un segment multi-segment.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="cd2e9-201">Fournit des aides pour la`byte` lecture `char`de données binaires et textuelles ( et ) qui peuvent ou ne peuvent pas être divisées entre les segments.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="cd2e9-202">Il existe des méthodes intégrées pour traiter les données binaires et délimitées.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="cd2e9-203">La section suivante montre à quoi ressemblent `SequenceReader<T>`ces mêmes méthodes avec le :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="cd2e9-204">Accéder aux données</span><span class="sxs-lookup"><span data-stu-id="cd2e9-204">Access data</span></span>

<span data-ttu-id="cd2e9-205">`SequenceReader<T>`a des méthodes pour énumérer `ReadOnlySequence<T>` les données à l’intérieur du direct.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="cd2e9-206">Le code suivant est un `ReadOnlySequence<byte>` `byte` exemple de traitement d’un à la fois :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="cd2e9-207">Le `CurrentSpan` expose le segment `Span`actuel , qui est similaire à ce qui a été fait dans la méthode manuellement.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="cd2e9-208">Position d’utilisation</span><span class="sxs-lookup"><span data-stu-id="cd2e9-208">Use position</span></span>

<span data-ttu-id="cd2e9-209">Le code suivant est `FindIndexOf` un `SequenceReader<T>`exemple d’implémentation de l’utilisation de la :</span><span class="sxs-lookup"><span data-stu-id="cd2e9-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="cd2e9-210">Traiter les données binaires</span><span class="sxs-lookup"><span data-stu-id="cd2e9-210">Process binary data</span></span>

<span data-ttu-id="cd2e9-211">L’exemple suivant analyse une longueur d’intégriste big-endian 4-bytete depuis le début de la `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="cd2e9-212">Traiter les données textuelles</span><span class="sxs-lookup"><span data-stu-id="cd2e9-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="cd2e9-213">SéquenceLire\<\> T problèmes communs</span><span class="sxs-lookup"><span data-stu-id="cd2e9-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="cd2e9-214">Parce `SequenceReader<T>` que c’est une structable mutable, elle doit toujours être transmise par [référence](../../csharp/language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="cd2e9-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="cd2e9-215">`SequenceReader<T>`est une [structif de ref](../../csharp/language-reference/keywords/ref.md#ref-struct-types) de sorte qu’il ne peut être utilisé que dans des méthodes synchrones et ne peut pas être stocké dans les champs.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/keywords/ref.md#ref-struct-types) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="cd2e9-216">Pour plus d’informations, voir [Écrire un code Cmd sûr et efficace](../../csharp/write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="cd2e9-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="cd2e9-217">`SequenceReader<T>`est optimisé pour une utilisation en tant que lecteur avant-seulement.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="cd2e9-218">`Rewind`est destiné à de petites sauvegardes qui `Read`ne `Peek`peuvent `IsNext` pas être traitées en utilisant d’autres , , et API.</span><span class="sxs-lookup"><span data-stu-id="cd2e9-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
