---
title: Pipelines d’e/s-.NET
description: Apprenez à utiliser efficacement des pipelines d’e/s dans .NET et évitez les problèmes dans votre code.
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 54b5f97aca131f52b9b5d9f54d7fa5ec00ba3d5b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423673"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="78a7c-103">System. IO. pipelines dans .NET</span><span class="sxs-lookup"><span data-stu-id="78a7c-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="78a7c-104"><xref:System.IO.Pipelines> est une nouvelle bibliothèque conçue pour faciliter l’exécution d’e/s hautes performances dans .NET.</span><span class="sxs-lookup"><span data-stu-id="78a7c-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="78a7c-105">Il s’agit d’une bibliothèque ciblant .NET Standard qui fonctionne sur toutes les implémentations .NET.</span><span class="sxs-lookup"><span data-stu-id="78a7c-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="78a7c-106">Quel est le problème résolu par System. IO. pipelines ?</span><span class="sxs-lookup"><span data-stu-id="78a7c-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="78a7c-107">Les applications qui analysent les données de streaming sont composées de code réutilisable avec de nombreux flux de code spécialisés et inhabituels.</span><span class="sxs-lookup"><span data-stu-id="78a7c-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="78a7c-108">Le code réutilisable et cas particulier est complexe et difficile à gérer.</span><span class="sxs-lookup"><span data-stu-id="78a7c-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="78a7c-109">`System.IO.Pipelines` a été conçu pour :</span><span class="sxs-lookup"><span data-stu-id="78a7c-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="78a7c-110">Ont des données de diffusion en continu d’analyse hautes performances.</span><span class="sxs-lookup"><span data-stu-id="78a7c-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="78a7c-111">Réduisez la complexité du code.</span><span class="sxs-lookup"><span data-stu-id="78a7c-111">Reduce code complexity.</span></span>

<span data-ttu-id="78a7c-112">Le code suivant est courant pour un serveur TCP qui reçoit des messages délimités par des lignes (délimités par `'\n'`) d’un client :</span><span class="sxs-lookup"><span data-stu-id="78a7c-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="78a7c-113">Le code précédent présente plusieurs problèmes :</span><span class="sxs-lookup"><span data-stu-id="78a7c-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="78a7c-114">Le message entier (fin de ligne) ne peut pas être reçu dans un appel unique à `ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="78a7c-115">Il ignore le résultat de `stream.ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="78a7c-116">`stream.ReadAsync` retourne la quantité de données lues.</span><span class="sxs-lookup"><span data-stu-id="78a7c-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="78a7c-117">Elle ne gère pas le cas où plusieurs lignes sont lues dans un seul appel `ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="78a7c-118">Elle alloue un tableau `byte` à chaque lecture.</span><span class="sxs-lookup"><span data-stu-id="78a7c-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="78a7c-119">Pour résoudre les problèmes précédents, les modifications suivantes sont requises :</span><span class="sxs-lookup"><span data-stu-id="78a7c-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="78a7c-120">Met en mémoire tampon les données entrantes jusqu’à ce qu’une nouvelle ligne soit trouvée.</span><span class="sxs-lookup"><span data-stu-id="78a7c-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="78a7c-121">Analyse toutes les lignes retournées dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="78a7c-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="78a7c-122">Il est possible que la ligne dépasse 1 Ko (1024 octets).</span><span class="sxs-lookup"><span data-stu-id="78a7c-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="78a7c-123">Le code doit redimensionner la mémoire tampon d’entrée jusqu’à ce que le délimiteur soit trouvé afin d’ajuster la ligne complète à l’intérieur de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="78a7c-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="78a7c-124">Si la mémoire tampon est redimensionnée, davantage de copies de mémoire tampon sont effectuées à mesure que des lignes plus longues apparaissent dans l’entrée.</span><span class="sxs-lookup"><span data-stu-id="78a7c-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="78a7c-125">Pour réduire l’espace gaspillé, compactez la mémoire tampon utilisée pour la lecture des lignes.</span><span class="sxs-lookup"><span data-stu-id="78a7c-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="78a7c-126">Envisagez d’utiliser le regroupement de mémoires tampons pour éviter d’allouer de la mémoire à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="78a7c-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="78a7c-127">Le code suivant résout certains de ces problèmes :</span><span class="sxs-lookup"><span data-stu-id="78a7c-127">The following code addresses some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="78a7c-128">Le code précédent est complexe et ne traite pas tous les problèmes identifiés.</span><span class="sxs-lookup"><span data-stu-id="78a7c-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="78a7c-129">La mise en réseau hautes performances implique généralement l’écriture de code très complexe pour optimiser les performances.</span><span class="sxs-lookup"><span data-stu-id="78a7c-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="78a7c-130">`System.IO.Pipelines` a été conçu pour faciliter l’écriture de ce type de code.</span><span class="sxs-lookup"><span data-stu-id="78a7c-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

## <a name="pipe"></a><span data-ttu-id="78a7c-131">nommé</span><span class="sxs-lookup"><span data-stu-id="78a7c-131">Pipe</span></span>

<span data-ttu-id="78a7c-132">La classe <xref:System.IO.Pipelines.Pipe> peut être utilisée pour créer une paire `PipeWriter/PipeReader`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="78a7c-133">Toutes les données écrites dans le `PipeWriter` sont disponibles dans la `PipeReader` :</span><span class="sxs-lookup"><span data-stu-id="78a7c-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="78a7c-134">Utilisation de base du canal</span><span class="sxs-lookup"><span data-stu-id="78a7c-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="78a7c-135">Il existe deux boucles :</span><span class="sxs-lookup"><span data-stu-id="78a7c-135">There are two loops:</span></span>

* <span data-ttu-id="78a7c-136">`FillPipeAsync` lit à partir du `Socket` et écrit dans le `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="78a7c-137">`ReadPipeAsync` lit à partir du `PipeReader` et analyse les lignes entrantes.</span><span class="sxs-lookup"><span data-stu-id="78a7c-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="78a7c-138">Aucune mémoire tampon explicite n’est allouée.</span><span class="sxs-lookup"><span data-stu-id="78a7c-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="78a7c-139">La gestion de la mémoire tampon est déléguée aux implémentations `PipeReader` et `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="78a7c-140">La délégation de la gestion des tampons facilite la consommation du code pour se concentrer uniquement sur la logique métier.</span><span class="sxs-lookup"><span data-stu-id="78a7c-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="78a7c-141">Dans la première boucle :</span><span class="sxs-lookup"><span data-stu-id="78a7c-141">In the first loop:</span></span>

* <span data-ttu-id="78a7c-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> est appelé pour récupérer la mémoire à partir du writer sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="78a7c-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="78a7c-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> est appelé pour indiquer à la `PipeWriter` la quantité de données qui a été écrite dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="78a7c-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="78a7c-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> est appelé pour mettre les données à la disposition du `PipeReader`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="78a7c-145">Dans la deuxième boucle, le `PipeReader` consomme les tampons écrits par `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="78a7c-146">Les mémoires tampons proviennent du Socket.</span><span class="sxs-lookup"><span data-stu-id="78a7c-146">The buffers come from the socket.</span></span> <span data-ttu-id="78a7c-147">L’appel à `PipeReader.ReadAsync` :</span><span class="sxs-lookup"><span data-stu-id="78a7c-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="78a7c-148">Retourne un <xref:System.IO.Pipelines.ReadResult> qui contient deux informations importantes :</span><span class="sxs-lookup"><span data-stu-id="78a7c-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="78a7c-149">Données lues sous la forme `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="78a7c-150">Valeur booléenne `IsCompleted` qui indique si la fin de données (EOF) a été atteinte.</span><span class="sxs-lookup"><span data-stu-id="78a7c-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="78a7c-151">Après avoir trouvé le délimiteur de fin de ligne (EOL) et l’analyse de la ligne :</span><span class="sxs-lookup"><span data-stu-id="78a7c-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="78a7c-152">La logique traite la mémoire tampon pour ignorer ce qui est déjà traité.</span><span class="sxs-lookup"><span data-stu-id="78a7c-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="78a7c-153">`PipeReader.AdvanceTo` est appelé pour indiquer à la `PipeReader` la quantité de données consommées et examinées.</span><span class="sxs-lookup"><span data-stu-id="78a7c-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="78a7c-154">Les boucles de lecteur et d’enregistreur se terminent en appelant `Complete`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="78a7c-155">`Complete` permet au canal sous-jacent de libérer la mémoire qu’il a allouée.</span><span class="sxs-lookup"><span data-stu-id="78a7c-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="78a7c-156">Contrôle de la contre-pression et du fluide</span><span class="sxs-lookup"><span data-stu-id="78a7c-156">Backpressure and flow control</span></span>

<span data-ttu-id="78a7c-157">Dans l’idéal, la lecture et l’analyse fonctionnent ensemble :</span><span class="sxs-lookup"><span data-stu-id="78a7c-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="78a7c-158">Le thread d’écriture consomme des données à partir du réseau et les place dans des tampons.</span><span class="sxs-lookup"><span data-stu-id="78a7c-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="78a7c-159">Le thread d’analyse est chargé de construire les structures de données appropriées.</span><span class="sxs-lookup"><span data-stu-id="78a7c-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="78a7c-160">En règle générale, l’analyse prend plus de temps que la simple copie des blocs de données à partir du réseau :</span><span class="sxs-lookup"><span data-stu-id="78a7c-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="78a7c-161">Le thread de lecture avance le thread d’analyse.</span><span class="sxs-lookup"><span data-stu-id="78a7c-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="78a7c-162">Le thread de lecture doit ralentir ou allouer davantage de mémoire pour stocker les données du thread d’analyse.</span><span class="sxs-lookup"><span data-stu-id="78a7c-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="78a7c-163">Pour des performances optimales, il existe un équilibre entre les pauses fréquentes et l’allocation de mémoire supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="78a7c-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="78a7c-164">Pour résoudre le problème précédent, le `Pipe` a deux paramètres pour contrôler le workflow de données :</span><span class="sxs-lookup"><span data-stu-id="78a7c-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="78a7c-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: détermine la quantité de données qui doit être mise en mémoire tampon avant les appels à <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> suspendre.</span><span class="sxs-lookup"><span data-stu-id="78a7c-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="78a7c-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold> : détermine la quantité de données que le lecteur doit observer avant les appels à la reprise de `PipeWriter.FlushAsync`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![Diagramme avec ResumeWriterThreshold et PauseWriterThreshold](./media/pipelines/resume-pause.png)

<span data-ttu-id="78a7c-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="78a7c-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="78a7c-169">Retourne un `ValueTask<FlushResult>` incomplet lorsque la quantité de données du `Pipe` traverse `PauseWriterThreshold`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="78a7c-170">Termine `ValueTask<FlushResult>` lorsqu’il est inférieur à `ResumeWriterThreshold`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="78a7c-171">Deux valeurs sont utilisées pour empêcher un cycle rapide, ce qui peut se produire si une valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="78a7c-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="78a7c-172">Exemples</span><span class="sxs-lookup"><span data-stu-id="78a7c-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="78a7c-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="78a7c-173">PipeScheduler</span></span>

<span data-ttu-id="78a7c-174">En général, lorsque vous utilisez `async` et `await`, le code asynchrone reprend sur un <xref:System.Threading.Tasks.TaskScheduler> ou sur le <xref:System.Threading.SynchronizationContext>actuel.</span><span class="sxs-lookup"><span data-stu-id="78a7c-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="78a7c-175">Lors des e/s, il est important de contrôler précisément l’emplacement d’exécution des e/s.</span><span class="sxs-lookup"><span data-stu-id="78a7c-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="78a7c-176">Ce contrôle permet de tirer efficacement parti des caches de l’UC.</span><span class="sxs-lookup"><span data-stu-id="78a7c-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="78a7c-177">Une mise en cache efficace est essentielle pour les applications hautes performances, comme les serveurs Web.</span><span class="sxs-lookup"><span data-stu-id="78a7c-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="78a7c-178"><xref:System.IO.Pipelines.PipeScheduler> permet de contrôler l’emplacement d’exécution des rappels asynchrones.</span><span class="sxs-lookup"><span data-stu-id="78a7c-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="78a7c-179">Par défaut :</span><span class="sxs-lookup"><span data-stu-id="78a7c-179">By default:</span></span>

* <span data-ttu-id="78a7c-180">Le <xref:System.Threading.SynchronizationContext> actuel est utilisé.</span><span class="sxs-lookup"><span data-stu-id="78a7c-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="78a7c-181">S’il n’existe aucun `SynchronizationContext`, il utilise le pool de threads pour exécuter les rappels.</span><span class="sxs-lookup"><span data-stu-id="78a7c-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="78a7c-182">[PipeScheduler. ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) est l’implémentation <xref:System.IO.Pipelines.PipeScheduler> qui met en file d’attente les rappels dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="78a7c-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="78a7c-183">`PipeScheduler.ThreadPool` est la valeur par défaut et généralement le meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="78a7c-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="78a7c-184">[PipeScheduler. Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) peut entraîner des conséquences inattendues, telles que les blocages.</span><span class="sxs-lookup"><span data-stu-id="78a7c-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="78a7c-185">Réinitialisation du canal</span><span class="sxs-lookup"><span data-stu-id="78a7c-185">Pipe reset</span></span>

<span data-ttu-id="78a7c-186">Il est souvent efficace de réutiliser l’objet `Pipe`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="78a7c-187">Pour réinitialiser le canal, appelez <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> lorsque le `PipeReader` et le `PipeWriter` sont terminés.</span><span class="sxs-lookup"><span data-stu-id="78a7c-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="78a7c-188">PipeReader</span><span class="sxs-lookup"><span data-stu-id="78a7c-188">PipeReader</span></span>

<span data-ttu-id="78a7c-189"><xref:System.IO.Pipelines.PipeReader> gère la mémoire au nom de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="78a7c-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="78a7c-190">Appelez **toujours** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> après l’appel de <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="78a7c-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="78a7c-191">Cela permet à l' `PipeReader` de savoir quand l’appelant est en mesure de faire en sorte qu’il puisse être suivi.</span><span class="sxs-lookup"><span data-stu-id="78a7c-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="78a7c-192">La `ReadOnlySequence<byte>` retournée à partir de `PipeReader.ReadAsync` est valide uniquement jusqu’à ce que l’appel de la `PipeReader.AdvanceTo`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="78a7c-193">L’utilisation de `ReadOnlySequence<byte>` est illégale après l’appel de `PipeReader.AdvanceTo`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="78a7c-194">`PipeReader.AdvanceTo` accepte deux arguments <xref:System.SequencePosition> :</span><span class="sxs-lookup"><span data-stu-id="78a7c-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="78a7c-195">Le premier argument détermine la quantité de mémoire consommée.</span><span class="sxs-lookup"><span data-stu-id="78a7c-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="78a7c-196">Le deuxième argument détermine la quantité de mémoire tampon observée.</span><span class="sxs-lookup"><span data-stu-id="78a7c-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="78a7c-197">Le marquage des données comme consommées signifie que le canal peut retourner la mémoire au pool de mémoires tampons sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="78a7c-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="78a7c-198">Le marquage des données comme observées détermine ce que fait l’appel suivant à `PipeReader.ReadAsync`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="78a7c-199">Le fait de marquer tout comme observé signifie que l’appel suivant à `PipeReader.ReadAsync` ne retourne pas jusqu’à ce qu’il y ait plus de données écrites dans le canal.</span><span class="sxs-lookup"><span data-stu-id="78a7c-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="78a7c-200">Toute autre valeur fera passer l’appel suivant à `PipeReader.ReadAsync` à retourner immédiatement avec les données observées *et* non observées, mais les données qui ont déjà été consommées.</span><span class="sxs-lookup"><span data-stu-id="78a7c-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="78a7c-201">Lire les scénarios de données de streaming</span><span class="sxs-lookup"><span data-stu-id="78a7c-201">Read streaming data scenarios</span></span>

<span data-ttu-id="78a7c-202">Il existe deux modèles typiques qui émergent lorsque vous tentez de lire des données de streaming :</span><span class="sxs-lookup"><span data-stu-id="78a7c-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="78a7c-203">En fonction d’un flux de données, analysez un message unique.</span><span class="sxs-lookup"><span data-stu-id="78a7c-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="78a7c-204">À partir d’un flux de données, analysez tous les messages disponibles.</span><span class="sxs-lookup"><span data-stu-id="78a7c-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="78a7c-205">Les exemples suivants utilisent la méthode `TryParseMessage` pour analyser les messages d’une `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="78a7c-206">`TryParseMessage` analyse un message unique et met à jour la mémoire tampon d’entrée pour supprimer le message analysé de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="78a7c-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="78a7c-207">`TryParseMessage` ne fait pas partie de .NET, il s’agit d’une méthode écrite par l’utilisateur, utilisée dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="78a7c-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="78a7c-208">Lire un seul message</span><span class="sxs-lookup"><span data-stu-id="78a7c-208">Read a single message</span></span>

<span data-ttu-id="78a7c-209">Le code suivant lit un message unique à partir d’un `PipeReader` et le retourne à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="78a7c-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="78a7c-210">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="78a7c-210">The preceding code:</span></span>

* <span data-ttu-id="78a7c-211">Analyse un message unique.</span><span class="sxs-lookup"><span data-stu-id="78a7c-211">Parses a single message.</span></span>
* <span data-ttu-id="78a7c-212">Met à jour le `SequencePosition` consommé et examine `SequencePosition` pour pointer vers le début de la mémoire tampon d’entrée tronquée.</span><span class="sxs-lookup"><span data-stu-id="78a7c-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="78a7c-213">Les deux arguments `SequencePosition` sont mis à jour, car `TryParseMessage` supprime le message analysé de la mémoire tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="78a7c-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="78a7c-214">En général, lors de l’analyse d’un message unique à partir de la mémoire tampon, la position examinée doit être l’une des suivantes :</span><span class="sxs-lookup"><span data-stu-id="78a7c-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="78a7c-215">Fin du message.</span><span class="sxs-lookup"><span data-stu-id="78a7c-215">The end of the message.</span></span>
* <span data-ttu-id="78a7c-216">Fin de la mémoire tampon reçue si aucun message n’a été trouvé.</span><span class="sxs-lookup"><span data-stu-id="78a7c-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="78a7c-217">Le cas de message unique présente le risque d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="78a7c-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="78a7c-218">Le passage des valeurs incorrectes à l' *examen* peut entraîner une exception de mémoire insuffisante ou une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="78a7c-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="78a7c-219">Pour plus d’informations, consultez la section [problèmes courants PipeReader](#gotchas) dans cet article.</span><span class="sxs-lookup"><span data-stu-id="78a7c-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="78a7c-220">Lecture de plusieurs messages</span><span class="sxs-lookup"><span data-stu-id="78a7c-220">Reading multiple messages</span></span>

<span data-ttu-id="78a7c-221">Le code suivant lit tous les messages d’un `PipeReader` et appelle `ProcessMessageAsync` sur chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="78a7c-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="78a7c-222">Annulation</span><span class="sxs-lookup"><span data-stu-id="78a7c-222">Cancellation</span></span>

<span data-ttu-id="78a7c-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="78a7c-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="78a7c-224">Prend en charge le passage d’un <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="78a7c-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="78a7c-225">Lève une <xref:System.OperationCanceledException> si la `CancellationToken` est annulée alors qu’une lecture est en attente.</span><span class="sxs-lookup"><span data-stu-id="78a7c-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="78a7c-226">Prend en charge un moyen d’annuler l’opération de lecture en cours via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, ce qui évite de déclencher une exception.</span><span class="sxs-lookup"><span data-stu-id="78a7c-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="78a7c-227">L’appel de `PipeReader.CancelPendingRead` provoque l’appel actuel ou suivant à `PipeReader.ReadAsync` pour retourner un <xref:System.IO.Pipelines.ReadResult> avec `IsCanceled` défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="78a7c-228">Cela peut être utile pour arrêter la boucle de lecture existante de manière non destructrice et non exceptionnelle.</span><span class="sxs-lookup"><span data-stu-id="78a7c-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="78a7c-229">Problèmes courants liés à PipeReader</span><span class="sxs-lookup"><span data-stu-id="78a7c-229">PipeReader common problems</span></span>

* <span data-ttu-id="78a7c-230">Le passage des valeurs incorrectes à `consumed` ou `examined` peut entraîner la lecture des données déjà lues.</span><span class="sxs-lookup"><span data-stu-id="78a7c-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="78a7c-231">Le passage de `buffer.End` comme examiné peut aboutir à :</span><span class="sxs-lookup"><span data-stu-id="78a7c-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="78a7c-232">Données bloquées</span><span class="sxs-lookup"><span data-stu-id="78a7c-232">Stalled data</span></span>
  * <span data-ttu-id="78a7c-233">Une exception éventuelle de mémoire insuffisante (insuffisance) si les données ne sont pas consommées.</span><span class="sxs-lookup"><span data-stu-id="78a7c-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="78a7c-234">Par exemple, `PipeReader.AdvanceTo(position, buffer.End)` lors du traitement d’un seul message à la fois à partir de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="78a7c-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="78a7c-235">Le passage des valeurs incorrectes à `consumed` ou `examined` peut entraîner une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="78a7c-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="78a7c-236">Par exemple, `PipeReader.AdvanceTo(buffer.Start)` si `buffer.Start` n’a pas changé entraîne l’appel suivant à `PipeReader.ReadAsync` pour retourner immédiatement avant l’arrivée de nouvelles données.</span><span class="sxs-lookup"><span data-stu-id="78a7c-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="78a7c-237">Le passage des valeurs incorrectes à `consumed` ou `examined` peut entraîner une mise en mémoire tampon infinie (éventuellement insuffisance).</span><span class="sxs-lookup"><span data-stu-id="78a7c-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="78a7c-238">L’utilisation de la `ReadOnlySequence<byte>` après l’appel de `PipeReader.AdvanceTo` peut entraîner une altération de la mémoire (utilisez après Free).</span><span class="sxs-lookup"><span data-stu-id="78a7c-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="78a7c-239">L’échec de l’appel de `PipeReader.Complete/CompleteAsync` peut entraîner une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="78a7c-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="78a7c-240">La vérification de <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> et la sortie de la logique de lecture avant le traitement de la mémoire tampon entraînent une perte de données.</span><span class="sxs-lookup"><span data-stu-id="78a7c-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="78a7c-241">La condition de sortie de boucle doit être basée sur `ReadResult.Buffer.IsEmpty` et `ReadResult.IsCompleted`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="78a7c-242">Une telle erreur peut entraîner une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="78a7c-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="78a7c-243">Code problématique</span><span class="sxs-lookup"><span data-stu-id="78a7c-243">Problematic code</span></span>

<span data-ttu-id="78a7c-244">**perte de données** ❌</span><span class="sxs-lookup"><span data-stu-id="78a7c-244">❌ **Data loss**</span></span>

<span data-ttu-id="78a7c-245">La `ReadResult` peut retourner le segment final des données lorsque `IsCompleted` a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="78a7c-246">Le fait de ne pas lire ces données avant de quitter la boucle de lecture entraînera une perte de données.</span><span class="sxs-lookup"><span data-stu-id="78a7c-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="78a7c-247">❌ **boucle infinie**</span><span class="sxs-lookup"><span data-stu-id="78a7c-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="78a7c-248">La logique suivante peut entraîner une boucle infinie si le `Result.IsCompleted` est `true`, mais qu’il n’y a jamais de message complet dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="78a7c-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="78a7c-249">Voici un autre morceau de code avec le même problème.</span><span class="sxs-lookup"><span data-stu-id="78a7c-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="78a7c-250">Il recherche une mémoire tampon non vide avant de vérifier `ReadResult.IsCompleted`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="78a7c-251">Dans la mesure où elle se trouve dans un `else if`, elle est en boucle infinie s’il n’y a jamais de message complet dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="78a7c-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="78a7c-252">❌ **blocage inattendu**</span><span class="sxs-lookup"><span data-stu-id="78a7c-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="78a7c-253">L’appel sans condition de `PipeReader.AdvanceTo` avec `buffer.End` dans la position `examined` peut entraîner des blocages lors de l’analyse d’un message unique.</span><span class="sxs-lookup"><span data-stu-id="78a7c-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="78a7c-254">L’appel suivant à `PipeReader.AdvanceTo` ne retourne pas tant que :</span><span class="sxs-lookup"><span data-stu-id="78a7c-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="78a7c-255">Il y a plus de données écrites dans le canal.</span><span class="sxs-lookup"><span data-stu-id="78a7c-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="78a7c-256">Et les nouvelles données n’ont pas été examinées précédemment.</span><span class="sxs-lookup"><span data-stu-id="78a7c-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="78a7c-257">❌ **mémoire insuffisante (insuffisance)**</span><span class="sxs-lookup"><span data-stu-id="78a7c-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="78a7c-258">Dans les conditions suivantes, le code suivant assure la mise en mémoire tampon jusqu’à ce qu’une <xref:System.OutOfMemoryException> se produise :</span><span class="sxs-lookup"><span data-stu-id="78a7c-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="78a7c-259">Il n’y a aucune taille de message maximale.</span><span class="sxs-lookup"><span data-stu-id="78a7c-259">There's no maximum message size.</span></span>
* <span data-ttu-id="78a7c-260">Les données retournées par le `PipeReader` ne constituent pas un message complet.</span><span class="sxs-lookup"><span data-stu-id="78a7c-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="78a7c-261">Par exemple, il ne fait pas de message complet, car l’autre côté écrit un message volumineux (par exemple, un message de 4 Go).</span><span class="sxs-lookup"><span data-stu-id="78a7c-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="78a7c-262">❌ **endommagement** de la mémoire</span><span class="sxs-lookup"><span data-stu-id="78a7c-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="78a7c-263">Lors de l’écriture d’applications auxiliaires qui lisent la mémoire tampon, toute charge utile retournée doit être copiée avant l’appel de `Advance`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="78a7c-264">L’exemple suivant retourne la mémoire que le `Pipe` a ignoré et peut le réutiliser pour l’opération suivante (lecture/écriture).</span><span class="sxs-lookup"><span data-stu-id="78a7c-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="78a7c-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="78a7c-265">PipeWriter</span></span>

<span data-ttu-id="78a7c-266">La <xref:System.IO.Pipelines.PipeWriter> gère les tampons pour l’écriture au nom de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="78a7c-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="78a7c-267">`PipeWriter` implémente [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span><span class="sxs-lookup"><span data-stu-id="78a7c-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="78a7c-268">`IBufferWriter<byte>` permet d’obtenir l’accès aux mémoires tampons pour effectuer des opérations d’écriture sans copie supplémentaire des mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="78a7c-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="78a7c-269">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="78a7c-269">The previous code:</span></span>

* <span data-ttu-id="78a7c-270">Demande une mémoire tampon d’au moins 5 octets à partir du `PipeWriter` à l’aide de <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span><span class="sxs-lookup"><span data-stu-id="78a7c-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="78a7c-271">Écrit les octets de la chaîne ASCII `"Hello"` dans le `Memory<byte>`retourné.</span><span class="sxs-lookup"><span data-stu-id="78a7c-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="78a7c-272">Appelle <xref:System.IO.Pipelines.PipeWriter.Advance%2A> pour indiquer le nombre d’octets qui ont été écrits dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="78a7c-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="78a7c-273">Vide la `PipeWriter`, qui envoie les octets à l’appareil sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="78a7c-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="78a7c-274">La méthode d’écriture précédente utilise les mémoires tampons fournies par le `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="78a7c-275">Vous pouvez également <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="78a7c-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="78a7c-276">Copie la mémoire tampon existante sur le `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="78a7c-277">Appelle `GetSpan`, `Advance` en fonction des besoins et appelle <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="78a7c-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="78a7c-278">Annulation</span><span class="sxs-lookup"><span data-stu-id="78a7c-278">Cancellation</span></span>

<span data-ttu-id="78a7c-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> prend en charge le passage d’une <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="78a7c-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="78a7c-280">Le passage d’un `CancellationToken` entraîne une `OperationCanceledException` si le jeton est annulé alors qu’il y a un vidage en attente.</span><span class="sxs-lookup"><span data-stu-id="78a7c-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="78a7c-281">`PipeWriter.FlushAsync` prend en charge un moyen d’annuler l’opération de vidage en cours via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> sans lever d’exception.</span><span class="sxs-lookup"><span data-stu-id="78a7c-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="78a7c-282">L’appel de `PipeWriter.CancelPendingFlush` provoque l’appel actuel ou suivant à `PipeWriter.FlushAsync` ou `PipeWriter.WriteAsync` pour retourner un <xref:System.IO.Pipelines.FlushResult> avec `IsCanceled` défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="78a7c-283">Cela peut être utile pour stopper le vidage à l’arrêt d’une façon non destructrice et non exceptionnelle.</span><span class="sxs-lookup"><span data-stu-id="78a7c-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="78a7c-284">Problèmes courants liés à PipeWriter</span><span class="sxs-lookup"><span data-stu-id="78a7c-284">PipeWriter common problems</span></span>

* <span data-ttu-id="78a7c-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> et <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> retournent une mémoire tampon avec au moins la quantité de mémoire demandée.</span><span class="sxs-lookup"><span data-stu-id="78a7c-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="78a7c-286">**Ne** supposez pas des tailles de mémoire tampon exactes.</span><span class="sxs-lookup"><span data-stu-id="78a7c-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="78a7c-287">Il n’y a aucune garantie que les appels successifs retourneront la même mémoire tampon ou la même mémoire tampon de taille.</span><span class="sxs-lookup"><span data-stu-id="78a7c-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="78a7c-288">Une nouvelle mémoire tampon doit être demandée après l’appel de <xref:System.IO.Pipelines.PipeWriter.Advance%2A> pour continuer à écrire davantage de données.</span><span class="sxs-lookup"><span data-stu-id="78a7c-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="78a7c-289">Impossible d’écrire dans la mémoire tampon acquise précédemment.</span><span class="sxs-lookup"><span data-stu-id="78a7c-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="78a7c-290">L’appel de `GetMemory` ou `GetSpan` alors qu’il existe un appel incomplet à `FlushAsync` n’est pas sécurisé.</span><span class="sxs-lookup"><span data-stu-id="78a7c-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="78a7c-291">L’appel de `Complete` ou `CompleteAsync` pendant qu’il y a des données non vidées peut entraîner une altération de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="78a7c-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="78a7c-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="78a7c-292">IDuplexPipe</span></span>

<span data-ttu-id="78a7c-293">Le <xref:System.IO.Pipelines.IDuplexPipe> est un contrat pour les types qui prennent en charge la lecture et l’écriture.</span><span class="sxs-lookup"><span data-stu-id="78a7c-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="78a7c-294">Par exemple, une connexion réseau est représentée par un `IDuplexPipe`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="78a7c-295">Contrairement à `Pipe` qui contient un `PipeReader` et un `PipeWriter`, `IDuplexPipe` représente un côté unique d’une connexion duplex intégral.</span><span class="sxs-lookup"><span data-stu-id="78a7c-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="78a7c-296">Cela signifie ce qui est écrit dans le `PipeWriter` ne sera pas lu à partir du `PipeReader`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="78a7c-297">Flux</span><span class="sxs-lookup"><span data-stu-id="78a7c-297">Streams</span></span>

<span data-ttu-id="78a7c-298">Lors de la lecture ou de l’écriture de données de flux, vous lisez généralement les données à l’aide d’un désérialiseur et écrivez des données à l’aide d’un sérialiseur.</span><span class="sxs-lookup"><span data-stu-id="78a7c-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="78a7c-299">La plupart de ces API de flux de lecture et d’écriture ont un paramètre `Stream`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="78a7c-300">Pour faciliter l’intégration avec ces API existantes, `PipeReader` et `PipeWriter` exposer un <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="78a7c-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="78a7c-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> retourne une implémentation de `Stream` autour du `PipeReader` ou `PipeWriter`.</span><span class="sxs-lookup"><span data-stu-id="78a7c-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
