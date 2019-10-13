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
ms.openlocfilehash: 9e26fb36b77e38c81273ccda370a203dd3388e5c
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291738"
---
# <a name="systemiopipelines-in-net"></a>System. IO. pipelines dans .NET

<xref:System.IO.Pipelines> est une nouvelle bibliothèque conçue pour faciliter l’exécution d’e/s hautes performances dans .NET. Il s’agit d’une bibliothèque ciblant .NET Standard qui fonctionne sur toutes les implémentations .NET.

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a>Quel est le problème résolu par System. IO. pipelines ?
<!-- corner case doesn't MT (machine translate)   -->
Les applications qui analysent les données de streaming sont composées de code réutilisable avec de nombreux flux de code spécialisés et inhabituels. Le code réutilisable et cas particulier est complexe et difficile à gérer.

`System.IO.Pipelines` a été conçu pour :

* Ont des données de diffusion en continu d’analyse hautes performances.
* Réduisez la complexité du code.

Le code suivant est courant pour un serveur TCP qui reçoit des messages délimités par des lignes (délimités par `'\n'`) d’un client :

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);
    
    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

Le code précédent présente plusieurs problèmes :

* Le message entier (fin de ligne) ne peut pas être reçu dans un appel unique à `ReadAsync`.
* Il ignore le résultat de `stream.ReadAsync`. `stream.ReadAsync` retourne la quantité de données lues.
* Elle ne gère pas le cas où plusieurs lignes sont lues dans un seul appel `ReadAsync`.
* Elle alloue un tableau `byte` à chaque lecture.

Pour résoudre les problèmes précédents, les modifications suivantes sont requises :

* Met en mémoire tampon les données entrantes jusqu’à ce qu’une nouvelle ligne soit trouvée.
* Analyse toutes les lignes retournées dans la mémoire tampon.
* Il est possible que la ligne dépasse 1 Ko (1024 octets). Le code doit redimensionner la mémoire tampon d’entrée. une ligne complète est trouvée.

  * Si la mémoire tampon est redimensionnée, davantage de copies de mémoire tampon sont effectuées à mesure que des lignes plus longues apparaissent dans l’entrée.
  * Pour réduire l’espace gaspillé, compactez la mémoire tampon utilisée pour la lecture des lignes.

* Envisagez d’utiliser le regroupement de mémoires tampons pour éviter d’allouer de la mémoire à plusieurs reprises.
* Le code suivant présente certains de ces problèmes :

[!code-csharp[](~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs?name=snippet)]

Le code précédent est complexe et ne traite pas tous les problèmes identifiés. La mise en réseau hautes performances implique généralement l’écriture de code très complexe pour optimiser les performances. `System.IO.Pipelines` a été conçu pour faciliter l’écriture de ce type de code.

## <a name="pipe"></a>nommé

La classe <xref:System.IO.Pipelines.Pipe> peut être utilisée pour créer une paire `PipeWriter/PipeReader`. Toutes les données écrites dans le `PipeWriter` sont disponibles dans la `PipeReader` :

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet2)]

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a>Utilisation de base du canal

[!code-csharp[](~/samples/snippets/csharp/pipelines/Pipe.cs?name=snippet)]

Il existe deux boucles :

* `FillPipeAsync` lit à partir du `Socket` et écrit dans le `PipeWriter`.
* `ReadPipeAsync` lit à partir du `PipeReader` et analyse les lignes entrantes.

Aucune mémoire tampon explicite n’est allouée. La gestion de la mémoire tampon est déléguée aux implémentations `PipeReader` et `PipeWriter`. La délégation de la gestion des tampons facilite la consommation du code pour se concentrer uniquement sur la logique métier.

Dans la première boucle :

* <xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> est appelé pour récupérer la mémoire à partir du writer sous-jacent.
* <xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> est appelé pour indiquer à la `PipeWriter` la quantité de données qui a été écrite dans la mémoire tampon.
* <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> est appelé pour rendre les données disponibles pour la `PipeReader`.

Dans la deuxième boucle, le `PipeReader` consomme les tampons écrits par `PipeWriter`. Les mémoires tampons proviennent du Socket. L’appel à `PipeReader.ReadAsync` :

* Retourne un <xref:System.IO.Pipelines.ReadResult> qui contient deux informations importantes :

  * Données lues sous la forme `ReadOnlySequence<byte>`.
  * Valeur booléenne `IsCompleted` qui indique si la fin de données (EOF) a été atteinte. 

Après avoir trouvé le délimiteur de fin de ligne (EOL) et l’analyse de la ligne :

* La logique traite la mémoire tampon pour ignorer ce qui est déjà traité.
* `PipeReader.AdvanceTo` est appelé pour indiquer à la `PipeReader` la quantité de données consommées et examinées.

Les boucles de lecteur et d’enregistreur se terminent en appelant `Complete`. `Complete` permet au canal sous-jacent de libérer la mémoire qu’il a allouée.

### <a name="backpressure-and-flow-control"></a>Contrôle de la contre-pression et du fluide

Dans l’idéal, la lecture et l’analyse fonctionnent ensemble :

* Le thread d’écriture consomme des données à partir du réseau et les place dans des tampons.
* Le thread d’analyse est chargé de construire les structures de données appropriées.

En règle générale, l’analyse prend plus de temps que la simple copie des blocs de données à partir du réseau :

* Le thread de lecture avance le thread d’analyse.
* Le thread de lecture doit ralentir ou allouer davantage de mémoire pour stocker les données du thread d’analyse.

Pour des performances optimales, il existe un équilibre entre les pauses fréquentes et l’allocation de mémoire supplémentaire.

Pour résoudre le problème précédent, le `Pipe` a deux paramètres pour contrôler le workflow de données :

* <xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Détermine la quantité de données qui doit être mise en mémoire tampon avant les appels à <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.
* <xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Détermine la quantité de données que le lecteur doit observer avant les appels à `PipeWriter.FlushAsync` reprendre.

![Diagramme avec ResumeWriterThreshold et PauseWriterThreshold](./media/pipelines/resume-pause.png)

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:

* Retourne un @no__t incomplet-0 lorsque la quantité de données dans la `Pipe` traverse `PauseWriterThreshold`.
* Termine `ValueTask<FlushResult>` lorsqu’il est inférieur à `ResumeWriterThreshold`.

Deux valeurs sont utilisées pour empêcher un cycle rapide, ce qui peut se produire si une valeur est utilisée.

### <a name="examples"></a>Exemples

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a>PipeScheduler

En général, lors de l’utilisation de `async` et `await`, le code asynchrone reprend sur un <xref:System.Threading.Tasks.TaskScheduler> ou sur le @no__t actuel-3.

Lors des e/s, il est important de contrôler précisément l’emplacement d’exécution des e/s. Ce contrôle permet de tirer efficacement parti des caches de l’UC. Une mise en cache efficace est essentielle pour les applications hautes performances, comme les serveurs Web. <xref:System.IO.Pipelines.PipeScheduler> permet de contrôler l’emplacement d’exécution des rappels asynchrones. Par défaut :

* Le @no__t actuel-0 est utilisé.
* S’il n’existe aucun `SynchronizationContext`, il utilise le pool de threads pour exécuter les rappels.

[!code-csharp[](~/samples/snippets/csharp/pipelines/Program.cs?name=snippet)]

[PipeScheduler. ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) est l’implémentation <xref:System.IO.Pipelines.PipeScheduler> qui met en file d’attente les rappels dans le pool de threads. `PipeScheduler.ThreadPool` est la valeur par défaut et généralement le meilleur choix. [PipeScheduler. Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) peut entraîner des conséquences inattendues, telles que les blocages.

### <a name="pipe-reset"></a>Réinitialisation du canal

Il est souvent efficace de réutiliser l’objet `Pipe`. Pour réinitialiser le canal, appelez <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> lorsque les `PipeReader` et `PipeWriter` sont terminés.

## <a name="pipereader"></a>PipeReader

<xref:System.IO.Pipelines.PipeReader> gère la mémoire au nom de l’appelant. Appelez **toujours** <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> après avoir appelé <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>. Cela permet à l' `PipeReader` de savoir quand l’appelant est en mesure de faire en sorte qu’il puisse être suivi. La `ReadOnlySequence<byte>` retournée à partir de `PipeReader.ReadAsync` est valide uniquement jusqu’à ce que l’appel de la `PipeReader.AdvanceTo`. L’utilisation de `ReadOnlySequence<byte>` est illégale après l’appel de `PipeReader.AdvanceTo`.

`PipeReader.AdvanceTo` accepte deux arguments <xref:System.SequencePosition> :

* Le premier argument détermine la quantité de mémoire consommée.
* Le deuxième argument détermine la quantité de mémoire tampon observée.

Le marquage des données comme consommées signifie que le canal peut retourner la mémoire au pool de mémoires tampons sous-jacent. Le marquage des données comme observées détermine ce que fait l’appel suivant à `PipeReader.ReadAsync`. Le fait de marquer tout comme observé signifie que l’appel suivant à `PipeReader.ReadAsync` ne retourne pas jusqu’à ce qu’il y ait plus de données écrites dans le canal. Toute autre valeur fera passer l’appel suivant à `PipeReader.ReadAsync` à retourner immédiatement avec les données observées *et* non observées, mais les données qui ont déjà été consommées.

### <a name="read-streaming-data-scenarios"></a>Lire les scénarios de données de streaming

Il existe deux modèles typiques qui émergent lorsque vous tentez de lire des données de streaming :

* En fonction d’un flux de données, analysez un message unique.
* À partir d’un flux de données, analysez tous les messages disponibles.

Les exemples suivants utilisent la méthode `TryParseMessage` pour analyser les messages d’une `ReadOnlySequence<byte>`. `TryParseMessage` analyse un message unique et met à jour la mémoire tampon d’entrée pour supprimer le message analysé de la mémoire tampon. `TryParseMessage` ne fait pas partie de .NET, il s’agit d’une méthode écrite par l’utilisateur, utilisée dans les sections suivantes.

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a>Lire un seul message

Le code suivant lit un message unique à partir d’un `PipeReader` et le retourne à l’appelant.

[!code-csharp[ReadSingleMsg](~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs?name=snippet)]

Le code précédent :

* Analyse un message unique.
* Met à jour le @no__t utilisé-0 et examine `SequencePosition` pour pointer vers le début de la mémoire tampon d’entrée tronquée.

Les deux arguments `SequencePosition` sont mis à jour, car `TryParseMessage` supprime le message analysé de la mémoire tampon d’entrée. En général, lors de l’analyse d’un message unique à partir de la mémoire tampon, la position examinée doit être l’une des suivantes :

* Fin du message.
* Fin de la mémoire tampon reçue si aucun message n’a été trouvé.

Le cas de message unique présente le risque d’erreurs. Le passage des valeurs incorrectes à l' *examen* peut entraîner une exception de mémoire insuffisante ou une boucle infinie. Pour plus d’informations, consultez la section [problèmes courants PipeReader](#gotchas) dans cet article.

### <a name="reading-multiple-messages"></a>Lecture de plusieurs messages

Le code suivant lit tous les messages d’un `PipeReader` et appelle `ProcessMessageAsync` sur chacun d’eux.

[!code-csharp[MyConnection1](~/samples/snippets/csharp/pipelines/MyConnection1.cs?name=snippet)]

### <a name="cancellation"></a>Annulation

`PipeReader.ReadAsync`:

* Prend en charge le passage d’un <xref:System.Threading.CancellationToken>.
* Lève une <xref:System.OperationCanceledException> si la `CancellationToken` est annulée alors qu’une lecture est en attente.
* Prend en charge un moyen d’annuler l’opération de lecture en cours via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, ce qui évite de déclencher une exception. L’appel de `PipeReader.CancelPendingRead` provoque l’appel actuel ou suivant à `PipeReader.ReadAsync` pour retourner un <xref:System.IO.Pipelines.ReadResult> avec `IsCanceled` défini sur `true`. Cela peut être utile pour arrêter la boucle de lecture existante de manière non destructrice et non exceptionnelle.

[!code-csharp[MyConnection](~/samples/snippets/csharp/pipelines/MyConnection.cs?name=snippet)]

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a>Problèmes courants liés à PipeReader

* Le passage des valeurs incorrectes à `consumed` ou `examined` peut entraîner la lecture des données déjà lues.
* Le passage de `buffer.End` comme examiné peut aboutir à :

  * Données bloquées
  * Une exception éventuelle de mémoire insuffisante (insuffisance) si les données ne sont pas consommées. Par exemple, `PipeReader.AdvanceTo(position, buffer.End)` lors du traitement d’un seul message à la fois à partir de la mémoire tampon.

* Le passage des valeurs incorrectes à `consumed` ou `examined` peut entraîner une boucle infinie. Par exemple, `PipeReader.AdvanceTo(buffer.Start)` si `buffer.Start` n’a pas changé entraîne l’appel suivant à `PipeReader.ReadAsync` pour retourner immédiatement avant l’arrivée de nouvelles données.
* Le passage des valeurs incorrectes à `consumed` ou `examined` peut entraîner une mise en mémoire tampon infinie (éventuellement insuffisance).
* L’utilisation de la `ReadOnlySequence<byte>` après l’appel de `PipeReader.AdvanceTo` peut entraîner une altération de la mémoire (utilisez après Free).
* L’échec de l’appel de `PipeReader.Complete/CompleteAsync` peut entraîner une fuite de mémoire.
* La vérification de <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> et la sortie de la logique de lecture avant le traitement de la mémoire tampon entraînent une perte de données. La condition de sortie de boucle doit être basée sur `ReadResult.Buffer.IsEmpty` et `ReadResult.IsCompleted`. Une telle erreur peut entraîner une boucle infinie.

#### <a name="problematic-code"></a>Code problématique

**perte de données** ❌

La `ReadResult` peut retourner le segment final des données lorsque `IsCompleted` a la valeur `true`. Le fait de ne pas lire ces données avant de quitter la boucle de lecture entraînera une perte de données.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#1](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **boucle infinie**

La logique suivante peut entraîner une boucle infinie si le `Result.IsCompleted` est `true`, mais qu’il n’y a jamais de message complet dans la mémoire tampon.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#2](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet2)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

Voici un autre morceau de code avec le même problème. Il recherche une mémoire tampon non vide avant de vérifier `ReadResult.IsCompleted`. Dans la mesure où elle se trouve dans un `else if`, elle est en boucle infinie s’il n’y a jamais de message complet dans la mémoire tampon.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#3](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet3)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **blocage inattendu**

L’appel sans condition de `PipeReader.AdvanceTo` avec `buffer.End` dans la position `examined` peut entraîner des blocages lors de l’analyse d’un message unique. L’appel suivant à `PipeReader.AdvanceTo` ne retourne pas tant que :

* Il y a plus de données écrites dans le canal.
* Et les nouvelles données n’ont pas été examinées précédemment.

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#4](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet4)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **mémoire insuffisante (insuffisance)**

Dans les conditions suivantes, le code suivant assure la mise en mémoire tampon jusqu’à ce qu’une <xref:System.OutOfMemoryException> se produise :

* Il n’y a aucune taille de message maximale.
* Les données retournées par le `PipeReader` ne constituent pas un message complet. Par exemple, il ne fait pas de message complet, car l’autre côté écrit un message volumineux (par exemple, un message de 4 Go).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#5](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet5)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

❌ **endommagement** de la mémoire

Lors de l’écriture d’applications auxiliaires qui lisent la mémoire tampon, toute charge utile retournée doit être copiée avant l’appel de `Advance`. L’exemple suivant retourne la mémoire que le `Pipe` a ignoré et peut le réutiliser pour l’opération suivante (lecture/écriture).

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

[!code-csharp[DoNotUse#Message](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippetMessage)]

[!code-csharp[DoNotUse#6](~/samples/snippets/csharp/pipelines/DoNotUse.cs?name=snippet6)]

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a>PipeWriter

La <xref:System.IO.Pipelines.PipeWriter> gère les tampons pour l’écriture au nom de l’appelant. `PipeWriter` implémente [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter`1). `IBufferWriter<byte>` permet d’obtenir l’accès aux mémoires tampons pour effectuer des opérations d’écriture sans copie supplémentaire des mémoires tampons.

[!code-csharp[MyPipeWriter](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet)]

Le code précédent :

* Demande une mémoire tampon d’au moins 5 octets à partir du `PipeWriter` à l’aide de <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A>.
* Écrit les octets de la chaîne ASCII `"Hello"` dans la `Span<byte>` retournée.
* Appelle <xref:System.IO.Pipelines.PipeWriter.Advance%2A> pour indiquer le nombre d’octets qui ont été écrits dans la mémoire tampon.
* Vide la `PipeWriter`, qui envoie les octets à l’appareil sous-jacent.

La méthode d’écriture précédente utilise les mémoires tampons fournies par le `PipeWriter`. Vous pouvez également <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType> :

* Copie la mémoire tampon existante sur le `PipeWriter`.
* Appelle `GetSpan`, `Advance` selon le cas et appelle <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.

[!code-csharp[MyPipeWriter#2](~/samples/snippets/csharp/pipelines/MyPipeWriter.cs?name=snippet2)]

### <a name="cancellation"></a>Annulation

<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> prend en charge le passage d’une <xref:System.Threading.CancellationToken>. Le passage d’un `CancellationToken` entraîne une `OperationCanceledException` si le jeton est annulé alors qu’il y a un vidage en attente. `PipeWriter.FlushAsync` permet d’annuler l’opération de vidage en cours via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> sans lever d’exception. L’appel de `PipeWriter.CancelPendingFlush` provoque l’appel actuel ou suivant à `PipeWriter.FlushAsync` ou `PipeWriter.WriteAsync` pour retourner un <xref:System.IO.Pipelines.FlushResult> avec `IsCanceled` défini sur `true`. Cela peut être utile pour stopper le vidage à l’arrêt d’une façon non destructrice et non exceptionnelle.

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a>Problèmes courants liés à PipeWriter

* <xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> et <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> retournent une mémoire tampon avec au moins la quantité de mémoire demandée. **Ne** supposez pas des tailles de mémoire tampon exactes.
* Il n’y a aucune garantie que les appels successifs retourneront la même mémoire tampon ou la même mémoire tampon de taille.
* Une nouvelle mémoire tampon doit être demandée après l’appel de <xref:System.IO.Pipelines.PipeWriter.Advance%2A> pour poursuivre l’écriture de données supplémentaires. Impossible d’écrire dans la mémoire tampon acquise précédemment.
* L’appel de `GetMemory` ou `GetSpan` alors qu’il existe un appel incomplet à `FlushAsync` n’est pas sécurisé.
* L’appel de `Complete` ou `CompleteAsync` pendant qu’il y a des données non vidées peut entraîner une altération de la mémoire.

## <a name="iduplexpipe"></a>IDuplexPipe

Le <xref:System.IO.Pipelines.IDuplexPipe> est un contrat pour les types qui prennent en charge la lecture et l’écriture. Par exemple, une connexion réseau est représentée par un `IDuplexPipe`.

 Contrairement à `Pipe` qui contient un `PipeReader` et un `PipeWriter`, `IDuplexPipe` représente un côté unique d’une connexion duplex intégral. Cela signifie ce qui est écrit dans le `PipeWriter` ne sera pas lu à partir du `PipeReader`.

## <a name="streams"></a>Flux

Lors de la lecture ou de l’écriture de données de flux, vous lisez généralement les données à l’aide d’un désérialiseur et écrivez des données à l’aide d’un sérialiseur. La plupart de ces API de flux de lecture et d’écriture ont un paramètre `Stream`. Pour faciliter l’intégration avec ces API existantes, `PipeReader` et `PipeWriter` exposent un <xref:System.IO.Pipelines.PipeReader.AsStream%2A>.  <xref:System.IO.Pipelines.PipeWriter.AsStream%2A> retourne une implémentation de `Stream` autour du `PipeReader` ou de `PipeWriter`.
