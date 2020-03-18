---
title: I/O pipelines - .NET
description: Apprenez à utiliser efficacement les pipelines I/O en .NET et évitez les problèmes de votre code.
ms.date: 10/01/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: b18b2bf31787fa58e614cd4f057fba9037fe8ad8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77627550"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="8e637-103">System.IO.Pipelines en .NET</span><span class="sxs-lookup"><span data-stu-id="8e637-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="8e637-104"><xref:System.IO.Pipelines>est une nouvelle bibliothèque qui est conçu pour le rendre plus facile à faire haute performance I / O en .NET.</span><span class="sxs-lookup"><span data-stu-id="8e637-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="8e637-105">C’est une bibliothèque ciblant .NET Standard qui fonctionne sur toutes les implémentations .NET.</span><span class="sxs-lookup"><span data-stu-id="8e637-105">It’s a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="8e637-106">Quel problème le problème ne System.IO.Pipelines résoudre</span><span class="sxs-lookup"><span data-stu-id="8e637-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="8e637-107">Les applications qui analysent les données de streaming sont composées de code boilerplate ayant de nombreux flux de code spécialisés et inhabituels.</span><span class="sxs-lookup"><span data-stu-id="8e637-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="8e637-108">La plaque chauffante et le code de cas spécial est complexe et difficile à entretenir.</span><span class="sxs-lookup"><span data-stu-id="8e637-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="8e637-109">`System.IO.Pipelines`a été conçu pour :</span><span class="sxs-lookup"><span data-stu-id="8e637-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="8e637-110">Avoir des données de diffusion en continu de haute performance.</span><span class="sxs-lookup"><span data-stu-id="8e637-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="8e637-111">Réduisez la complexité du code.</span><span class="sxs-lookup"><span data-stu-id="8e637-111">Reduce code complexity.</span></span>

<span data-ttu-id="8e637-112">Le code suivant est typique pour un serveur TCP qui reçoit des `'\n'`messages délimités en ligne (délimités par) d’un client :</span><span class="sxs-lookup"><span data-stu-id="8e637-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="8e637-113">Le code précédent a plusieurs problèmes :</span><span class="sxs-lookup"><span data-stu-id="8e637-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="8e637-114">L’ensemble du message (fin de ligne) pourrait `ReadAsync`ne pas être reçu en un seul appel à .</span><span class="sxs-lookup"><span data-stu-id="8e637-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="8e637-115">C’est ignorer le `stream.ReadAsync`résultat de .</span><span class="sxs-lookup"><span data-stu-id="8e637-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="8e637-116">`stream.ReadAsync`retourne la quantité de données lues.</span><span class="sxs-lookup"><span data-stu-id="8e637-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="8e637-117">Il ne gère pas le cas où `ReadAsync` plusieurs lignes sont lues en un seul appel.</span><span class="sxs-lookup"><span data-stu-id="8e637-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="8e637-118">Il alloue un `byte` tableau à chaque lecture.</span><span class="sxs-lookup"><span data-stu-id="8e637-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="8e637-119">Pour résoudre les problèmes précédents, les changements suivants sont nécessaires :</span><span class="sxs-lookup"><span data-stu-id="8e637-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="8e637-120">Tamponner les données entrantes jusqu’à ce qu’une nouvelle ligne soit trouvée.</span><span class="sxs-lookup"><span data-stu-id="8e637-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="8e637-121">Parse toutes les lignes retournées dans le tampon.</span><span class="sxs-lookup"><span data-stu-id="8e637-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="8e637-122">Il est possible que la ligne soit supérieure à 1 KB (1024 octets).</span><span class="sxs-lookup"><span data-stu-id="8e637-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="8e637-123">Le code doit resize le tampon d’entrée jusqu’à ce que le délimitateur soit trouvé afin d’adapter la ligne complète à l’intérieur du tampon.</span><span class="sxs-lookup"><span data-stu-id="8e637-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="8e637-124">Si le tampon est resized, plus de copies tampons sont faites à mesure que des lignes plus longues apparaissent dans l’entrée.</span><span class="sxs-lookup"><span data-stu-id="8e637-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="8e637-125">Pour réduire l’espace gaspillé, compactez le tampon utilisé pour les lignes de lecture.</span><span class="sxs-lookup"><span data-stu-id="8e637-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="8e637-126">Envisagez d’utiliser la mise en commun des tampons pour éviter d’allouer la mémoire à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="8e637-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="8e637-127">Le code suivant traite de certains de ces problèmes :</span><span class="sxs-lookup"><span data-stu-id="8e637-127">The following code addresses some of these problems:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

<span data-ttu-id="8e637-128">Le code précédent est complexe et ne traite pas de tous les problèmes identifiés.</span><span class="sxs-lookup"><span data-stu-id="8e637-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="8e637-129">Le réseautage haute performance signifie généralement écrire du code très complexe pour maximiser les performances.</span><span class="sxs-lookup"><span data-stu-id="8e637-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="8e637-130">`System.IO.Pipelines`a été conçu pour faciliter l’écriture de ce type de code.</span><span class="sxs-lookup"><span data-stu-id="8e637-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="8e637-131">Pipe</span><span class="sxs-lookup"><span data-stu-id="8e637-131">Pipe</span></span>

<span data-ttu-id="8e637-132">La <xref:System.IO.Pipelines.Pipe> classe peut être `PipeWriter/PipeReader` utilisée pour créer une paire.</span><span class="sxs-lookup"><span data-stu-id="8e637-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="8e637-133">Toutes les données `PipeWriter` inscrites `PipeReader`dans le est disponible dans le :</span><span class="sxs-lookup"><span data-stu-id="8e637-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="8e637-134">Utilisation de base de pipe</span><span class="sxs-lookup"><span data-stu-id="8e637-134">Pipe basic usage</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

<span data-ttu-id="8e637-135">Il y a deux boucles :</span><span class="sxs-lookup"><span data-stu-id="8e637-135">There are two loops:</span></span>

* <span data-ttu-id="8e637-136">`FillPipeAsync`lit de `Socket` la et `PipeWriter`écrit à la .</span><span class="sxs-lookup"><span data-stu-id="8e637-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="8e637-137">`ReadPipeAsync`lit à `PipeReader` partir des lignes entrantes et analyse.</span><span class="sxs-lookup"><span data-stu-id="8e637-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="8e637-138">Il n’y a pas de tampons explicites alloués.</span><span class="sxs-lookup"><span data-stu-id="8e637-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="8e637-139">Toute gestion des tampons `PipeReader` `PipeWriter` est déléguée aux mises en œuvre et aux mises en œuvre.</span><span class="sxs-lookup"><span data-stu-id="8e637-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="8e637-140">La délégation de la gestion des tampons permet de se concentrer plus facilement sur la logique métier.</span><span class="sxs-lookup"><span data-stu-id="8e637-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="8e637-141">Dans la première boucle:</span><span class="sxs-lookup"><span data-stu-id="8e637-141">In the first loop:</span></span>

* <span data-ttu-id="8e637-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType>est appelé à obtenir la mémoire de l’écrivain sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="8e637-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="8e637-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType>est appelé à `PipeWriter` dire combien de données ont été écrites au tampon.</span><span class="sxs-lookup"><span data-stu-id="8e637-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="8e637-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>est appelé à mettre les `PipeReader`données à la disposition du .</span><span class="sxs-lookup"><span data-stu-id="8e637-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="8e637-145">Dans la deuxième `PipeReader` boucle, le consomme `PipeWriter`les tampons écrits par .</span><span class="sxs-lookup"><span data-stu-id="8e637-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="8e637-146">Les tampons proviennent de la prise.</span><span class="sxs-lookup"><span data-stu-id="8e637-146">The buffers come from the socket.</span></span> <span data-ttu-id="8e637-147">L’appel `PipeReader.ReadAsync`à :</span><span class="sxs-lookup"><span data-stu-id="8e637-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="8e637-148">Renvoie <xref:System.IO.Pipelines.ReadResult> un qui contient deux éléments d’information importants :</span><span class="sxs-lookup"><span data-stu-id="8e637-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="8e637-149">Les données qui ont été `ReadOnlySequence<byte>`lues sous la forme de .</span><span class="sxs-lookup"><span data-stu-id="8e637-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="8e637-150">Un boolean `IsCompleted` qui indique si la fin des données (EOF) a été atteinte.</span><span class="sxs-lookup"><span data-stu-id="8e637-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="8e637-151">Après avoir trouvé la fin de la ligne (EOL) délimiter et d’analyser la ligne:</span><span class="sxs-lookup"><span data-stu-id="8e637-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="8e637-152">La logique traite le tampon pour sauter ce qui est déjà traité.</span><span class="sxs-lookup"><span data-stu-id="8e637-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="8e637-153">`PipeReader.AdvanceTo`est appelé à `PipeReader` dire combien de données ont été consommées et examinées.</span><span class="sxs-lookup"><span data-stu-id="8e637-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="8e637-154">Le lecteur et les boucles `Complete`d’écrivain se terminent par l’appel .</span><span class="sxs-lookup"><span data-stu-id="8e637-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="8e637-155">`Complete`permet au Tuyau sous-jacent de libérer la mémoire qu’il a allouée.</span><span class="sxs-lookup"><span data-stu-id="8e637-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="8e637-156">Rétropression et contrôle du débit</span><span class="sxs-lookup"><span data-stu-id="8e637-156">Backpressure and flow control</span></span>

<span data-ttu-id="8e637-157">Idéalement, la lecture et l’analyse travaillent ensemble :</span><span class="sxs-lookup"><span data-stu-id="8e637-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="8e637-158">Le fil d’écriture consomme les données du réseau et les met dans des tampons.</span><span class="sxs-lookup"><span data-stu-id="8e637-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="8e637-159">Le fil d’analyse est responsable de la construction des structures de données appropriées.</span><span class="sxs-lookup"><span data-stu-id="8e637-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="8e637-160">En règle générale, l’analyse prend plus de temps que de simplement copier des blocs de données du réseau :</span><span class="sxs-lookup"><span data-stu-id="8e637-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="8e637-161">Le fil de lecture prend de l’avance sur le fil d’analyse.</span><span class="sxs-lookup"><span data-stu-id="8e637-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="8e637-162">Le fil de lecture doit soit ralentir ou allouer plus de mémoire pour stocker les données pour le fil d’analyse.</span><span class="sxs-lookup"><span data-stu-id="8e637-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="8e637-163">Pour des performances optimales, il y a un équilibre entre les pauses fréquentes et l’attribution de plus de mémoire.</span><span class="sxs-lookup"><span data-stu-id="8e637-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="8e637-164">Pour résoudre le problème `Pipe` précédent, le a deux paramètres pour contrôler le flux de données:</span><span class="sxs-lookup"><span data-stu-id="8e637-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="8e637-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Détermine la quantité de données qui <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> doivent être tamponnées avant les appels à faire une pause.</span><span class="sxs-lookup"><span data-stu-id="8e637-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="8e637-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Détermine la quantité de données que `PipeWriter.FlushAsync` le lecteur doit observer avant les appels à reprendre.</span><span class="sxs-lookup"><span data-stu-id="8e637-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![Diagramme avec ResumeWriterThreshold et PauseWriterThreshold](./media/pipelines/resume-pause.png)

<span data-ttu-id="8e637-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="8e637-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="8e637-169">Retourne une `ValueTask<FlushResult>` incomplet lorsque `Pipe` la `PauseWriterThreshold`quantité de données dans les croix .</span><span class="sxs-lookup"><span data-stu-id="8e637-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="8e637-170">Se `ValueTask<FlushResult>` termine quand il `ResumeWriterThreshold`devient inférieur à .</span><span class="sxs-lookup"><span data-stu-id="8e637-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="8e637-171">Deux valeurs sont utilisées pour prévenir le cycle rapide, qui peut se produire si une valeur est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8e637-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="8e637-172">Exemples</span><span class="sxs-lookup"><span data-stu-id="8e637-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="8e637-173">PipeScheduler PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="8e637-173">PipeScheduler</span></span>

<span data-ttu-id="8e637-174">Typiquement lors `async` `await`de l’utilisation et , code asynchrone reprend sur un <xref:System.Threading.Tasks.TaskScheduler> ou sur le courant <xref:System.Threading.SynchronizationContext>.</span><span class="sxs-lookup"><span data-stu-id="8e637-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current  <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="8e637-175">Lorsque vous faites I / O, il est important d’avoir un contrôle à grain fin sur l’endroit où l’I / O est effectué.</span><span class="sxs-lookup"><span data-stu-id="8e637-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="8e637-176">Ce contrôle permet de tirer parti efficacement des caches CPU.</span><span class="sxs-lookup"><span data-stu-id="8e637-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="8e637-177">La mise en cache efficace est essentielle pour les applications haute performance comme les serveurs Web.</span><span class="sxs-lookup"><span data-stu-id="8e637-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="8e637-178"><xref:System.IO.Pipelines.PipeScheduler>donne un contrôle sur l’endroit où les rappels asynchrones s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="8e637-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="8e637-179">Par défaut :</span><span class="sxs-lookup"><span data-stu-id="8e637-179">By default:</span></span>

* <span data-ttu-id="8e637-180">Le <xref:System.Threading.SynchronizationContext> courant est utilisé.</span><span class="sxs-lookup"><span data-stu-id="8e637-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="8e637-181">S’il n’y a pas, `SynchronizationContext`il utilise le pool de thread pour exécuter des rappels.</span><span class="sxs-lookup"><span data-stu-id="8e637-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

<span data-ttu-id="8e637-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) est <xref:System.IO.Pipelines.PipeScheduler> la mise en œuvre que les files d’attente rappelle à la piscine de fil.</span><span class="sxs-lookup"><span data-stu-id="8e637-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="8e637-183">`PipeScheduler.ThreadPool`est la valeur par défaut et généralement le meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="8e637-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="8e637-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) peut causer des conséquences imprévues telles que des impasses.</span><span class="sxs-lookup"><span data-stu-id="8e637-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="8e637-185">Réinitialisation de tuyau</span><span class="sxs-lookup"><span data-stu-id="8e637-185">Pipe reset</span></span>

<span data-ttu-id="8e637-186">Il est souvent efficace de `Pipe` réutiliser l’objet.</span><span class="sxs-lookup"><span data-stu-id="8e637-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="8e637-187">Pour réinitialiser le `PipeReader` `PipeWriter` tuyau, appelez <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> lorsque le et sont terminés.</span><span class="sxs-lookup"><span data-stu-id="8e637-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="8e637-188">PipeReader PipeReader</span><span class="sxs-lookup"><span data-stu-id="8e637-188">PipeReader</span></span>

<span data-ttu-id="8e637-189"><xref:System.IO.Pipelines.PipeReader>gère la mémoire au nom de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="8e637-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="8e637-190">**Toujours** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> appeler <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>après avoir appelé .</span><span class="sxs-lookup"><span data-stu-id="8e637-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8e637-191">Cela permet `PipeReader` de savoir quand l’appelant est fait avec la mémoire afin qu’il puisse être suivi.</span><span class="sxs-lookup"><span data-stu-id="8e637-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="8e637-192">Le `ReadOnlySequence<byte>` retour `PipeReader.ReadAsync` n’est valable `PipeReader.AdvanceTo`que jusqu’à l’appel le .</span><span class="sxs-lookup"><span data-stu-id="8e637-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="8e637-193">Il est illégal `ReadOnlySequence<byte>` d’utiliser après avoir appelé `PipeReader.AdvanceTo`.</span><span class="sxs-lookup"><span data-stu-id="8e637-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="8e637-194">`PipeReader.AdvanceTo`prend <xref:System.SequencePosition> deux arguments:</span><span class="sxs-lookup"><span data-stu-id="8e637-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="8e637-195">Le premier argument détermine la quantité de mémoire consommée.</span><span class="sxs-lookup"><span data-stu-id="8e637-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="8e637-196">Le deuxième argument détermine la quantité de tampon observée.</span><span class="sxs-lookup"><span data-stu-id="8e637-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="8e637-197">Le marquage des données consommées signifie que le tuyau peut retourner la mémoire dans le pool tampon sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="8e637-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="8e637-198">Le marquage des données observées `PipeReader.ReadAsync` contrôle ce que le prochain appel à faire.</span><span class="sxs-lookup"><span data-stu-id="8e637-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="8e637-199">Marquer tout ce qui est `PipeReader.ReadAsync` observé signifie que le prochain appel à ne pas revenir jusqu’à ce qu’il y ait plus de données écrites sur le tuyau.</span><span class="sxs-lookup"><span data-stu-id="8e637-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="8e637-200">Toute autre valeur fera le `PipeReader.ReadAsync` prochain appel pour revenir immédiatement avec les données observées *et* non observées, mais les données qui ont déjà été consommées.</span><span class="sxs-lookup"><span data-stu-id="8e637-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="8e637-201">Lire les scénarios de données en streaming</span><span class="sxs-lookup"><span data-stu-id="8e637-201">Read streaming data scenarios</span></span>

<span data-ttu-id="8e637-202">Il ya un couple de modèles typiques qui émergent lorsque vous essayez de lire les données en streaming:</span><span class="sxs-lookup"><span data-stu-id="8e637-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="8e637-203">Compte tenu d’un flux de données, analysez un seul message.</span><span class="sxs-lookup"><span data-stu-id="8e637-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="8e637-204">Compte tenu d’un flux de données, analysez tous les messages disponibles.</span><span class="sxs-lookup"><span data-stu-id="8e637-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="8e637-205">Les exemples `TryParseMessage` suivants utilisent la méthode `ReadOnlySequence<byte>`pour analyser les messages à partir d’un .</span><span class="sxs-lookup"><span data-stu-id="8e637-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="8e637-206">`TryParseMessage`analyse un seul message et met à jour le tampon d’entrée pour couper le message analysé à partir du tampon.</span><span class="sxs-lookup"><span data-stu-id="8e637-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="8e637-207">`TryParseMessage`ne fait pas partie de .NET, c’est une méthode écrite par l’utilisateur utilisée dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="8e637-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="8e637-208">Lire un seul message</span><span class="sxs-lookup"><span data-stu-id="8e637-208">Read a single message</span></span>

<span data-ttu-id="8e637-209">Le code suivant lit un `PipeReader` seul message à partir d’un et le renvoie à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="8e637-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

<span data-ttu-id="8e637-210">Le code précédent :</span><span class="sxs-lookup"><span data-stu-id="8e637-210">The preceding code:</span></span>

* <span data-ttu-id="8e637-211">Parses un seul message.</span><span class="sxs-lookup"><span data-stu-id="8e637-211">Parses a single message.</span></span>
* <span data-ttu-id="8e637-212">Mises à `SequencePosition` jour `SequencePosition` de la consommation et examinée pour indiquer le début du tampon d’entrée coupé.</span><span class="sxs-lookup"><span data-stu-id="8e637-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="8e637-213">Les `SequencePosition` deux arguments `TryParseMessage` sont mis à jour parce que supprime le message analysé du tampon d’entrée.</span><span class="sxs-lookup"><span data-stu-id="8e637-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="8e637-214">En général, lors de l’analyse d’un seul message à partir du tampon, la position examinée doit être l’une des suivantes :</span><span class="sxs-lookup"><span data-stu-id="8e637-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="8e637-215">La fin du message.</span><span class="sxs-lookup"><span data-stu-id="8e637-215">The end of the message.</span></span>
* <span data-ttu-id="8e637-216">La fin du tampon reçu si aucun message n’a été trouvé.</span><span class="sxs-lookup"><span data-stu-id="8e637-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="8e637-217">Le cas de message unique a le plus de potentiel d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="8e637-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="8e637-218">Passer les mauvaises valeurs à *examiner* peut entraîner une exception hors mémoire ou une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="8e637-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="8e637-219">Pour plus d’informations, consultez la section [des problèmes courants de PipeReader](#gotchas) dans cet article.</span><span class="sxs-lookup"><span data-stu-id="8e637-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="8e637-220">Lecture de plusieurs messages</span><span class="sxs-lookup"><span data-stu-id="8e637-220">Reading multiple messages</span></span>

<span data-ttu-id="8e637-221">Le code suivant lit `PipeReader` tous `ProcessMessageAsync` les messages d’un et appelle sur chacun.</span><span class="sxs-lookup"><span data-stu-id="8e637-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a><span data-ttu-id="8e637-222">Annulation</span><span class="sxs-lookup"><span data-stu-id="8e637-222">Cancellation</span></span>

<span data-ttu-id="8e637-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="8e637-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="8e637-224">Soutient l’adoption d’un <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="8e637-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="8e637-225">Jette un <xref:System.OperationCanceledException> si `CancellationToken` le est annulé alors qu’il ya une lecture en attente.</span><span class="sxs-lookup"><span data-stu-id="8e637-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="8e637-226">Prend en charge un moyen <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>d’annuler l’opération de lecture en cours via , ce qui évite de soulever une exception.</span><span class="sxs-lookup"><span data-stu-id="8e637-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="8e637-227">L’appel `PipeReader.CancelPendingRead` provoque l’appel actuel <xref:System.IO.Pipelines.ReadResult> `IsCanceled` ou `true`suivant pour `PipeReader.ReadAsync` retourner un avec réglé à .</span><span class="sxs-lookup"><span data-stu-id="8e637-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="8e637-228">Cela peut être utile pour arrêter la boucle de lecture existante d’une manière non destructive et non exceptionnelle.</span><span class="sxs-lookup"><span data-stu-id="8e637-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="8e637-229">Problèmes courants PipeReader</span><span class="sxs-lookup"><span data-stu-id="8e637-229">PipeReader common problems</span></span>

* <span data-ttu-id="8e637-230">Passer les mauvaises `consumed` `examined` valeurs à ou peut entraîner la lecture déjà des données lues.</span><span class="sxs-lookup"><span data-stu-id="8e637-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="8e637-231">La `buffer.End` réussite examinée peut entraîner :</span><span class="sxs-lookup"><span data-stu-id="8e637-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="8e637-232">Données bloquées</span><span class="sxs-lookup"><span data-stu-id="8e637-232">Stalled data</span></span>
  * <span data-ttu-id="8e637-233">Peut-être une éventuelle exception hors mémoire (OOM) si les données ne sont pas consommées.</span><span class="sxs-lookup"><span data-stu-id="8e637-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="8e637-234">Par exemple, `PipeReader.AdvanceTo(position, buffer.End)` lors du traitement d’un seul message à la fois à partir du tampon.</span><span class="sxs-lookup"><span data-stu-id="8e637-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="8e637-235">Passer les mauvaises `consumed` `examined` valeurs à ou peut entraîner une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="8e637-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="8e637-236">Par `PipeReader.AdvanceTo(buffer.Start)` exemple, `buffer.Start` si n’a pas changé `PipeReader.ReadAsync` fera le prochain appel de revenir immédiatement avant l’arrivée de nouvelles données.</span><span class="sxs-lookup"><span data-stu-id="8e637-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="8e637-237">Passer les mauvaises `consumed` `examined` valeurs à l’OOM ou peut entraîner une mise en mémoire tampon infinie (éventuellement OOM).</span><span class="sxs-lookup"><span data-stu-id="8e637-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="8e637-238">L’utilisation `PipeReader.AdvanceTo` de l’appel `ReadOnlySequence<byte>` après peut entraîner une corruption de mémoire (utilisation après gratuit).</span><span class="sxs-lookup"><span data-stu-id="8e637-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="8e637-239">Ne pas `PipeReader.Complete/CompleteAsync` appeler peut entraîner une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="8e637-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="8e637-240">La <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> vérification et la sortie de la logique de lecture avant le traitement du tampon entraînent une perte de données.</span><span class="sxs-lookup"><span data-stu-id="8e637-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="8e637-241">L’état de sortie `ReadResult.Buffer.IsEmpty` de `ReadResult.IsCompleted`boucle doit être basé sur et .</span><span class="sxs-lookup"><span data-stu-id="8e637-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="8e637-242">Faire cela incorrectement pourrait entraîner une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="8e637-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="8e637-243">Code problématique</span><span class="sxs-lookup"><span data-stu-id="8e637-243">Problematic code</span></span>

<span data-ttu-id="8e637-244">❌**Perte de données**</span><span class="sxs-lookup"><span data-stu-id="8e637-244">❌ **Data loss**</span></span>

<span data-ttu-id="8e637-245">Le `ReadResult` peut retourner le segment `IsCompleted` final `true`de données quand est réglé à .</span><span class="sxs-lookup"><span data-stu-id="8e637-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="8e637-246">Ne pas lire ces données avant de sortir de la boucle de lecture entraînera une perte de données.</span><span class="sxs-lookup"><span data-stu-id="8e637-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="8e637-247">❌**Boucle infinie**</span><span class="sxs-lookup"><span data-stu-id="8e637-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="8e637-248">La logique suivante peut entraîner une `Result.IsCompleted` `true` boucle infinie si l’est, mais il n’y a jamais un message complet dans le tampon.</span><span class="sxs-lookup"><span data-stu-id="8e637-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="8e637-249">Voici un autre morceau de code avec le même problème.</span><span class="sxs-lookup"><span data-stu-id="8e637-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="8e637-250">Il vérifie un tampon non vide `ReadResult.IsCompleted`avant de vérifier .</span><span class="sxs-lookup"><span data-stu-id="8e637-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="8e637-251">Parce qu’il `else if`est dans un , il va boucler pour toujours s’il n’y a jamais un message complet dans le tampon.</span><span class="sxs-lookup"><span data-stu-id="8e637-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="8e637-252">❌**Hang inattendu**</span><span class="sxs-lookup"><span data-stu-id="8e637-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="8e637-253">Appeler `PipeReader.AdvanceTo` sans `buffer.End` condition `examined` dans la position peut entraîner des pendaisons lors de l’analyse d’un seul message.</span><span class="sxs-lookup"><span data-stu-id="8e637-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="8e637-254">Le prochain `PipeReader.AdvanceTo` appel à ne pas revenir jusqu’à ce que:</span><span class="sxs-lookup"><span data-stu-id="8e637-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="8e637-255">Il y a plus de données écrites sur le tuyau.</span><span class="sxs-lookup"><span data-stu-id="8e637-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="8e637-256">Et les nouvelles données n’ont pas été examinées auparavant.</span><span class="sxs-lookup"><span data-stu-id="8e637-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="8e637-257">❌**Hors mémoire (OOM)**</span><span class="sxs-lookup"><span data-stu-id="8e637-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="8e637-258">Dans les conditions suivantes, le code <xref:System.OutOfMemoryException> suivant conserve la mise en mémoire tampon jusqu’à ce qu’un se produise :</span><span class="sxs-lookup"><span data-stu-id="8e637-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="8e637-259">Il n’y a pas de taille maximale de message.</span><span class="sxs-lookup"><span data-stu-id="8e637-259">There's no maximum message size.</span></span>
* <span data-ttu-id="8e637-260">Les données retournées de la `PipeReader` ne fait pas un message complet.</span><span class="sxs-lookup"><span data-stu-id="8e637-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="8e637-261">Par exemple, il ne fait pas un message complet parce que l’autre côté écrit un grand message (par exemple, un message de 4 Go).</span><span class="sxs-lookup"><span data-stu-id="8e637-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="8e637-262">❌**Corruption de mémoire**</span><span class="sxs-lookup"><span data-stu-id="8e637-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="8e637-263">Lors de l’écriture d’aides qui lisent le `Advance`tampon, toute charge utile retournée doit être copiée avant d’appeler .</span><span class="sxs-lookup"><span data-stu-id="8e637-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="8e637-264">L’exemple suivant rendra `Pipe` la mémoire que le a jeté et peut la réutiliser pour la prochaine opération (lire/écrire).</span><span class="sxs-lookup"><span data-stu-id="8e637-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="8e637-265">PipeWriter (pipeWriter)</span><span class="sxs-lookup"><span data-stu-id="8e637-265">PipeWriter</span></span>

<span data-ttu-id="8e637-266">Le <xref:System.IO.Pipelines.PipeWriter> gère les tampons pour écrire au nom de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="8e637-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="8e637-267">`PipeWriter`met [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601)en œuvre .</span><span class="sxs-lookup"><span data-stu-id="8e637-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="8e637-268">`IBufferWriter<byte>`permet d’avoir accès à des tampons pour effectuer des écritures sans copies tampons supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="8e637-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

<span data-ttu-id="8e637-269">Le code précédent:</span><span class="sxs-lookup"><span data-stu-id="8e637-269">The previous code:</span></span>

* <span data-ttu-id="8e637-270">Demande un tampon d’au moins `PipeWriter` 5 octets de l’utilisation <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e637-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="8e637-271">Écrit des octets pour `"Hello"` la chaîne `Memory<byte>`ASCII au retour .</span><span class="sxs-lookup"><span data-stu-id="8e637-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="8e637-272">Appels <xref:System.IO.Pipelines.PipeWriter.Advance%2A> pour indiquer combien d’octets ont été écrits au tampon.</span><span class="sxs-lookup"><span data-stu-id="8e637-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="8e637-273">Flushes `PipeWriter`le , qui envoie les octets à l’appareil sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="8e637-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="8e637-274">La méthode précédente d’écriture utilise `PipeWriter`les tampons fournis par le .</span><span class="sxs-lookup"><span data-stu-id="8e637-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="8e637-275">Alternativement, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="8e637-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="8e637-276">Copie le tampon `PipeWriter`existant à la .</span><span class="sxs-lookup"><span data-stu-id="8e637-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="8e637-277">Appels `GetSpan` `Advance` , le <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>cas échéant et les appels .</span><span class="sxs-lookup"><span data-stu-id="8e637-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a><span data-ttu-id="8e637-278">Annulation</span><span class="sxs-lookup"><span data-stu-id="8e637-278">Cancellation</span></span>

<span data-ttu-id="8e637-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>soutient l’adoption d’un <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="8e637-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="8e637-280">Passer `CancellationToken` un résultat `OperationCanceledException` dans un si le jeton est annulé alors qu’il ya une chasse d’eau en attente.</span><span class="sxs-lookup"><span data-stu-id="8e637-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="8e637-281">`PipeWriter.FlushAsync`prend en charge un moyen <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> d’annuler l’opération de chasse d’eau en cours via sans soulever une exception.</span><span class="sxs-lookup"><span data-stu-id="8e637-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="8e637-282">`PipeWriter.CancelPendingFlush` L’appel provoque l’appel `PipeWriter.WriteAsync` actuel <xref:System.IO.Pipelines.FlushResult> ou `IsCanceled` suivant `true`à `PipeWriter.FlushAsync` ou de retourner un avec réglé à .</span><span class="sxs-lookup"><span data-stu-id="8e637-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="8e637-283">Cela peut être utile pour arrêter la chasse d’eau de rendement d’une manière non destructive et non exceptionnelle.</span><span class="sxs-lookup"><span data-stu-id="8e637-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="8e637-284">Problèmes courants PipeWriter</span><span class="sxs-lookup"><span data-stu-id="8e637-284">PipeWriter common problems</span></span>

* <span data-ttu-id="8e637-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>et <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> retourner un tampon avec au moins la quantité demandée de mémoire.</span><span class="sxs-lookup"><span data-stu-id="8e637-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="8e637-286">**N’assumez pas** les tailles exactes de tampon.</span><span class="sxs-lookup"><span data-stu-id="8e637-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="8e637-287">Il n’y a aucune garantie que les appels successifs retourneront le même tampon ou le même tampon de taille.</span><span class="sxs-lookup"><span data-stu-id="8e637-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="8e637-288">Un nouveau tampon doit <xref:System.IO.Pipelines.PipeWriter.Advance%2A> être demandé après avoir appelé pour continuer à écrire plus de données.</span><span class="sxs-lookup"><span data-stu-id="8e637-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="8e637-289">Le tampon précédemment acquis ne peut pas être écrit à.</span><span class="sxs-lookup"><span data-stu-id="8e637-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="8e637-290">Appeler `GetMemory` `GetSpan` ou pendant qu’il `FlushAsync` y a un appel incomplet n’est pas sûr.</span><span class="sxs-lookup"><span data-stu-id="8e637-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="8e637-291">Appeler `Complete` `CompleteAsync` ou pendant qu’il y a des données non gonflées peut entraîner une corruption de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="8e637-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="8e637-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="8e637-292">IDuplexPipe</span></span>

<span data-ttu-id="8e637-293">Il <xref:System.IO.Pipelines.IDuplexPipe> s’agit d’un contrat pour les types qui prennent en charge à la fois la lecture et l’écriture.</span><span class="sxs-lookup"><span data-stu-id="8e637-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="8e637-294">Par exemple, une connexion réseau serait `IDuplexPipe`représentée par un .</span><span class="sxs-lookup"><span data-stu-id="8e637-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="8e637-295">Contrairement `Pipe` à `PipeReader` ce `PipeWriter`qui `IDuplexPipe` contient a et a , représente un seul côté d’une connexion en duplex complet.</span><span class="sxs-lookup"><span data-stu-id="8e637-295">Unlike `Pipe` which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="8e637-296">Cela signifie que ce `PipeWriter` qui est écrit `PipeReader`à la volonté ne sera pas lu de la .</span><span class="sxs-lookup"><span data-stu-id="8e637-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="8e637-297">Flux</span><span class="sxs-lookup"><span data-stu-id="8e637-297">Streams</span></span>

<span data-ttu-id="8e637-298">Lorsque vous lisez ou écrivez des données de flux, vous lisez généralement des données à l’aide d’un dé-serializer et écrivez des données à l’aide d’un sérialisateur.</span><span class="sxs-lookup"><span data-stu-id="8e637-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="8e637-299">La plupart de ces API `Stream` de lecture et d’écriture ont un paramètre.</span><span class="sxs-lookup"><span data-stu-id="8e637-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="8e637-300">Pour faciliter l’intégration à ces `PipeReader` API existantes, et `PipeWriter` exposer un <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e637-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.</span></span>  <span data-ttu-id="8e637-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A>retourne `Stream` une mise `PipeReader` `PipeWriter`en œuvre autour de la ou .</span><span class="sxs-lookup"><span data-stu-id="8e637-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>
