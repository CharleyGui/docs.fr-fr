---
title: Accès asynchrone aux fichiers (C#)
description: Découvrez comment utiliser la fonctionnalité Async pour accéder aux fichiers en C#. Vous pouvez appeler des méthodes asynchrones sans utiliser de rappels ni fractionner votre code entre les méthodes.
ms.date: 08/19/2020
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 9a8db6004e8fff2cb39f0c350b403b56ea619e54
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812040"
---
# <a name="asynchronous-file-access-c"></a>Accès asynchrone aux fichiers (C#)

Vous pouvez utiliser la fonctionnalité Async pour accéder à des fichiers. La fonctionnalité async vous permet d’appeler des méthodes asynchrones sans utiliser de rappels ni fractionner votre code entre plusieurs méthodes ou expressions lambda. Pour rendre le code synchrone asynchrone, il vous suffit d’appeler une méthode asynchrone au lieu d’une méthode synchrone, puis d’ajouter quelques mots clés au code.

Vous pouvez considérer les raisons suivantes pour ajouter de l'asynchrone aux appels d'accès aux fichiers :

> [!div class="checklist"]
>
> - L'asynchronisme rend les applications d'interface utilisateur plus réactives parce que le thread d'interface utilisateur qui lance l'exécution peut effectuer d'autres tâches. Si le thread d’interface utilisateur doit exécuter du code qui prend du temps (par exemple, plus de 50 millisecondes), l’interface utilisateur peut figer jusqu’à ce que l’E/S soit terminée et que le thread d’interface utilisateur puisse traiter à nouveau des entrées au clavier et à la souris et d’autres événements.
> - L'asynchronisme améliore l'extensibilité d'ASP.NET et d'autres applications serveur en réduisant le besoin de threads. Si l'application utilise un thread dédié par réponse et que mille demandes sont traitées simultanément, mille threads sont nécessaires. Les opérations asynchrones n’ont souvent pas besoin d’utiliser un thread pendant l’attente. Elles utilisent le thread de terminaison d’E/S existant brièvement à la fin.
> - La latence d'une opération d'accès à un fichier peut être très basse sous les conditions actuelles, mais la latence peut considérablement augmenter à l'avenir. Par exemple, un fichier peut être déplacé vers un serveur qui se trouve à travers le monde.
> - La charge mémoire supplémentaire pour l'utilisation de la fonctionnalité Async est faible.
> - Les tâches asynchrones peuvent facilement être exécutées en parallèle.

## <a name="use-appropriate-classes"></a>Utiliser les classes appropriées

Les exemples simples de cette rubrique illustrent <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> et <xref:System.IO.File.ReadAllTextAsync%2A?displayProperty=nameWithType> . Pour un contrôle fini sur les opérations d’e/s de fichier, utilisez la <xref:System.IO.FileStream> classe, qui a une option qui provoque l’exécution d’e/s asynchrones au niveau du système d’exploitation. En utilisant cette option, vous pouvez éviter de bloquer un thread de pool de threads dans de nombreux cas. Pour l’activer, spécifiez l’argument `useAsync=true` ou `options=FileOptions.Asynchronous` dans l’appel de constructeur.

Vous ne pouvez pas utiliser cette option avec <xref:System.IO.StreamReader> et <xref:System.IO.StreamWriter> si vous les ouvrez directement en spécifiant un chemin d’accès de fichier. Toutefois, vous pouvez utiliser cette option si vous leur fournissez un <xref:System.IO.Stream> ouvert par la classe <xref:System.IO.FileStream>. Les appels asynchrones sont plus rapides dans les applications d’interface utilisateur même si un thread de pool de threads est bloqué, car le thread d’interface utilisateur n’est pas bloqué pendant l’attente.

## <a name="write-text"></a>Écrire du texte

Les exemples suivants écrivent du texte dans un fichier. À chaque instruction await, la méthode s'arrête immédiatement. Quand l’E/S de fichier est terminée, la méthode reprend à l’instruction qui suit l’instruction await. Le modificateur Async est dans la définition des méthodes qui utilisent l’instruction await.

### <a name="simple-example"></a>Exemple simple

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleWrite":::

### <a name="finite-control-example"></a>Exemple de contrôle fini

:::code language="csharp" source="snippets/file-access/Program.cs" id="WriteText":::

L’exemple d’origine comprend l’instruction `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, qui est une contraction des deux instructions suivantes :

```csharp
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);
await theTask;
```

La première instruction retourne une tâche et provoque le début du traitement du fichier. La deuxième instruction avec await provoque la fin immédiate de la méthode et retourne une tâche différente. Quand le traitement du fichier se termine plus loin, l’exécution retourne à l’instruction qui suit l’attente.

## <a name="read-text"></a>Lire le texte

Les exemples suivants lisent du texte à partir d’un fichier.

### <a name="simple-example"></a>Exemple simple

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleRead":::

### <a name="finite-control-example"></a>Exemple de contrôle fini

Le texte est mis en mémoire tampon et, dans cet exemple, est placé dans un <xref:System.Text.StringBuilder>. Contrairement à l’exemple précédent, l’évaluation de l’instruction await génère une valeur. La <xref:System.IO.Stream.ReadAsync%2A> méthode retourne un <xref:System.Threading.Tasks.Task> \<<xref:System.Int32>>, donc l’évaluation de l’expression await produit une `Int32` valeur `numRead` une fois l’opération terminée. Pour plus d’informations, consultez [Types de retour Async (C#)](async-return-types.md).

:::code language="csharp" source="snippets/file-access/Program.cs" id="ReadText":::

## <a name="parallel-asynchronous-io"></a>E/s asynchrones parallèles

Les exemples suivants illustrent le traitement en parallèle en écrivant 10 fichiers texte.

### <a name="simple-example"></a>Exemple simple

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleParallelWrite":::

### <a name="finite-control-example"></a>Exemple de contrôle fini

Pour chaque fichier, la méthode <xref:System.IO.Stream.WriteAsync%2A> retourne une tâche qui est ensuite ajoutée à une liste des tâches. L’instruction `await Task.WhenAll(tasks);` quitte la méthode et reprend dans cette dernière quand le traitement du fichier est terminé pour toutes les tâches.

L’exemple ferme toutes les instances de <xref:System.IO.FileStream> dans un bloc `finally` une fois les tâches effectuées. Si chaque `FileStream` était plutôt créé dans une instruction `using`, `FileStream` pourrait être libéré avant que la tâche ne soit terminée.

Toute amélioration des performances est presque entièrement issue du traitement parallèle et non du traitement asynchrone. L’asynchronie présente l’avantage de ne pas bloquer plusieurs threads et de ne pas bloquer le thread d’interface utilisateur.

:::code language="csharp" source="snippets/file-access/Program.cs" id="ParallelWriteText":::

Quand vous utilisez les méthodes <xref:System.IO.Stream.WriteAsync%2A> et <xref:System.IO.Stream.ReadAsync%2A>, vous pouvez spécifier un <xref:System.Threading.CancellationToken>, qui vous permet d’annuler l’opération en cours de route. Pour plus d’informations, consultez [Annulation dans les threads managés](../../../../standard/threading/cancellation-in-managed-threads.md).

## <a name="see-also"></a>Voir aussi

- [Programmation asynchrone avec Async et await (C#)](index.md)
- [Types de retour Async (C#)](async-return-types.md)
