---
title: 'Comment : itérer les répertoires de fichiers avec la classe parallèle'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
ms.openlocfilehash: fda8443666d1c90b31cf02c2f925d1c89243a8e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091316"
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>Comment : itérer les répertoires de fichiers avec la classe parallèle
Dans de nombreux cas, l’itération de fichiers est une opération facile à mettre en parallèle. La rubrique [Guide pratique : itérer les répertoires de fichiers avec PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) présente le moyen le plus simple d’effectuer cette tâche dans de nombreux scénarios. Toutefois, des problèmes risquent de survenir si le code doit gérer les différents types d’exceptions susceptibles de se produire avec l’accès au système de fichiers. L'exemple suivant montre une approche du problème. Il utilise une itération de type pile pour parcourir tous les fichiers et tous les dossiers situés sous un répertoire spécifié, et permet au code d’intercepter et de gérer différentes exceptions. Bien entendu, vous pouvez gérer les exceptions comme vous le souhaitez.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant itère les répertoires de manière séquentielle, mais traite les fichiers en parallèle. C’est probablement la meilleure approche en cas de rapport élevé entre les répertoires et les fichiers. Il est également possible de paralléliser l’itération des répertoires et d’accéder à chaque fichier de manière séquentielle. Il n’est probablement pas efficace de paralléliser les deux boucles, sauf si l’ordinateur ciblé comporte un grand nombre de processeurs. Toutefois, comme toujours, vous devez tester votre application de manière approfondie pour déterminer la meilleure approche.  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 Dans cet exemple, les E/S des fichiers sont effectuées de façon synchrone. En cas de fichiers volumineux ou de connexions réseau lentes, il peut être préférable d’accéder aux fichiers de façon asynchrone. Vous pouvez combiner des techniques d’E/S asynchrones avec l’itération parallèle. Pour plus d’informations, consultez [Bibliothèque parallèle de tâches (TPL) et programmation asynchrone](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
 L’exemple utilise la variable `fileCount` locale pour maintenir un décompte du nombre total de fichiers traités. Étant donné que plusieurs tâches sont susceptibles d’y accéder simultanément, la méthode <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> est utilisée pour synchroniser les accès.  
  
 Sachez que, si une exception est levée sur le thread principal, les threads lancés par la méthode <xref:System.Threading.Tasks.Parallel.ForEach%2A> risquent de continuer à s’exécuter. Pour les arrêter, vous pouvez définir une variable booléenne dans vos gestionnaires d’exceptions et vérifier sa valeur à chaque itération de la boucle parallèle. Si la valeur indique qu’une exception a été levée, utilisez la variable <xref:System.Threading.Tasks.ParallelLoopState> pour arrêter ou sortir de la boucle. Pour plus d’informations, consultez la page [Guide pratique : arrêter ou sortir d’une boucle Parallel.For](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100)).  
  
## <a name="see-also"></a>Voir aussi

- [Parallélisme de données](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
