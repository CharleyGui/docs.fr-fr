---
title: Fonctionnement de l'accélération dans PLINQ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, performance tuning
ms.assetid: 53706c7e-397d-467a-98cd-c0d1fd63ba5e
ms.openlocfilehash: 247ebb868a9256deaf59c1369e6143e15af4d6b0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829971"
---
# <a name="understanding-speedup-in-plinq"></a>Fonctionnement de l'accélération dans PLINQ
Le principal objectif de PLINQ est d’accélérer l’exécution de requêtes LINQ to Objects en exécutant parallèlement les délégués de requête sur des ordinateurs multicœurs. PLINQ accomplit les meilleures performances lorsque le traitement de chaque élément dans une collection source est indépendant, sans aucun état partagé parmi les délégués individuels. Ces opérations sont courantes dans LINQ to Objects et PLINQ et sont souvent appelées « *délicieusement parallèles* », car elles se prêtent facilement à la planification sur plusieurs threads. Toutefois, toutes les requêtes ne sont pas entièrement constituées d’opérations délicieusement parallèles ; dans la plupart des cas, une requête concerne certains opérateurs qui ne peuvent pas être parallélisés, ou qui ralentissent l’exécution parallèle. Et même dans le cas de requêtes qui sont entièrement délicieusement parallèles, PLINQ doit encore partitionner la source de données et planifier le travail sur les threads et, généralement, fusionner les résultats lorsque la requête est terminée. Toutes ces opérations ajoutent au coût de calcul de la parallélisation ; ces coûts d’ajout de parallélisation sont appelés *surcharge*. Pour optimiser les performances dans une requête PLINQ, l’objectif est d’augmenter les parties délicieusement parallèles et de réduire au minimum les parties qui nécessitent une surcharge. Cet article fournit des informations qui vous aideront à écrire des requêtes PLINQ aussi efficaces que possible, tout en produisant des résultats corrects.  
  
## <a name="factors-that-impact-plinq-query-performance"></a>Facteurs ayant un impact sur les performances des requêtes  
 Les sections suivantes répertorient certains des facteurs plus importants ayant un impact sur les performances des requêtes parallèles. Il s’agit d’instructions générales qui ne sont en soi pas suffisantes pour prédire les performances des requêtes dans tous les cas. Comme toujours, il est important de mesurer les performances réelles de requêtes spécifiques sur des ordinateurs avec une plage de configurations et de charges représentatives.  
  
1. Coût de calcul du travail global.  
  
     Pour atteindre l’accélération, une requête PLINQ doit avoir suffisamment de travail délicieusement parallèle pour compenser la surcharge. Le travail peut être exprimé comme le coût de calcul de chaque délégué multiplié par le nombre d’éléments dans la collection source. En supposant qu’une opération peut être parallélisée, plus elle est coûteuse en matière de calcul, plus la possibilité d’accélération est grande. Par exemple, si une fonction s’exécute en une milliseconde, une requête séquentielle de 1 000 éléments prendra une seconde, tandis qu’une requête parallèle sur un ordinateur doté de quatre cœurs ne prendra probablement que 250 millisecondes. Il en résulte une accélération de 750 millisecondes. Si la fonction mettait une seconde à s’exécuter pour chaque élément, l’accélération sera de 750 secondes. Si le délégué est très coûteux, PLINQ peut offrir une accélération significative avec uniquement quelques éléments dans la collection source. À l’inverse, de petites collections source avec des délégués triviaux ne sont généralement pas bons candidats pour PLINQ.  
  
     Dans l’exemple suivant, queryA est probablement un bon candidat pour PLINQ, en supposant que sa fonction Select implique de nombreuses tâches. queryB n’est probablement pas un bon candidat, car il n’y a pas suffisamment de travail dans l’instruction Select, et la surcharge de parallélisation compensera la plus grande partie ou la totalité de l’accélération.  
  
    ```vb  
    Dim queryA = From num In numberList.AsParallel()  
                 Select ExpensiveFunction(num); 'good for PLINQ  
  
    Dim queryB = From num In numberList.AsParallel()  
                 Where num Mod 2 > 0  
                 Select num; 'not as good for PLINQ  
    ```  
  
    ```csharp  
    var queryA = from num in numberList.AsParallel()  
                 select ExpensiveFunction(num); //good for PLINQ  
  
    var queryB = from num in numberList.AsParallel()  
                 where num % 2 > 0  
                 select num; //not as good for PLINQ  
    ```  
  
2. Nombre de cœurs logiques sur le système (degré de parallélisme).  
  
     Ce point est un corollaire évident de la section précédente : lLes requêtes délicieusement parallèles s’exécutent plus rapidement sur des ordinateurs au nombre de cœurs plus élevé, car le travail peut être divisé entre davantage de threads simultanés. L’accélération globale dépend du pourcentage de travail global parallèle de la requête. Toutefois, ne supposez pas que toutes les requêtes s’exécuteront deux fois plus vite sur un ordinateur à huit cœurs que sur un ordinateur à quatre cœurs. Lors du paramétrage des requêtes pour des performances optimales, il est important de mesurer les résultats réels sur des ordinateurs avec des nombres de cœurs différents. Ce point est lié au point numéro 1 : des jeux de données plus volumineux sont nécessaires pour tirer parti de ressources de calcul plus importantes.  
  
3. Le nombre et le type d’opérations.  
  
     PLINQ fournit l’opérateur AsOrdered pour les situations dans lesquelles il est nécessaire de conserver l’ordre des éléments dans la séquence source. Un coût est associé à la commande, mais il est généralement modeste. Les opérations GroupBy et Join entraînent également une surcharge. PLINQ offre les meilleures performances lorsqu’elle est autorisée à traiter les éléments de la collection source dans n’importe quel ordre et à les passer à l’opérateur suivant dès qu’ils sont prêts. Pour plus d’informations, consultez [Order Preservation in PLINQ](order-preservation-in-plinq.md) (Conservation de l’ordre dans PLINQ).  
  
4. Formulaire d'exécution des requêtes.  
  
     Si vous stockez les résultats d’une requête en appelant ToArray ou ToList, les résultats de tous les threads parallèles doivent être fusionnés dans la structure de données unique. Ceci implique un coût de calcul inévitable. De même, si vous itérez les résultats à l’aide d’une boucle foreach (For Each en Visual Basic), les résultats des threads de travail doivent être sérialisés sur le thread de l’énumérateur. Mais si vous souhaitez simplement effectuer une action en fonction du résultat de chaque thread, vous pouvez utiliser la méthode ForAll pour exécuter ce travail sur plusieurs threads.  
  
5. Le type des options de fusion.  
  
     PLINQ peut être configuré pour mettre en mémoire tampon sa sortie et en produire des segments ou la totalité après avoir produit le jeu de résultats entier, ou enfin transmettre en continu des résultats individuels à mesure qu'ils sont produits. Les anciens résultats dans le délai d'exécution général réduit et les derniers résultats dans la latence réduite entre les éléments produits.  Tandis que les options de fusion n'ont pas toujours une incidence majeure sur les performances globales de la requête, elles peuvent affecter les performances perçues dans la mesure où elles contrôlent la durée d'attente d'un utilisateur avant consultation des résultats. Pour plus d’informations, consultez l’article [Merge Options in PLINQ](merge-options-in-plinq.md) (Options de fusion de PLINQ).  
  
6. Types de partitionnement.  
  
     Dans certains cas, une requête PLINQ sur une collection source indexable peut entraîner une charge de travail déséquilibrée. Lorsque cela se produit, vous pouvez peut-être augmenter les performances des requêtes en créant un partitionneur personnalisé. Pour plus d’informations, consultez [Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)](custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="when-plinq-chooses-sequential-mode"></a>Lorsque PLINQ choisit le mode séquentiel  
 PLINQ essaiera toujours exécuter une requête au moins aussi rapidement que si elle était exécutée de manière séquentielle. Bien que PLINQ ne tienne compte ni du coût de calcul des délégués de l’utilisateur, ni de la taille la source d’entrée, il recherche certaines « formes » de requêtes. Plus précisément, il recherche des opérateurs de requêtes ou des combinaisons d’opérateurs qui font qu’une requête s’exécute plus lentement en mode parallèle. Lorsqu’il trouve de telles formes, par défaut PLINQ revient au mode séquentiel.  
  
 Toutefois, après avoir mesuré les performances d’une requête spécifique, vous pouvez déterminer qu’elle s’exécute plus rapidement en mode parallèle. Dans ce cas, vous pouvez utiliser l’indicateur <xref:System.Linq.ParallelExecutionMode.ForceParallelism?displayProperty=nameWithType> via la méthode <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> pour indiquer à PLINQ de paralléliser la requête. Pour plus d’informations, consultez [How to: Specify the Execution Mode in PLINQ](how-to-specify-the-execution-mode-in-plinq.md) (Guide pratique pour spécifier le mode d’exécution dans PLINQ).  
  
 La liste suivante décrit les formes de requêtes que PLINQ exécutera en mode séquentiel par défaut :  
  
- Requêtes qui contiennent une instruction Select, Where indexée, SelectMany indexée ou ElementAt après un opérateur de tri ou de filtrage qui a supprimé ou réorganisé les indices d’origine.  
  
- Requêtes qui contiennent un SkipWhile opérateur Take, TakeWhile, ignorer et où les index de la séquence source ne sont pas dans l’ordre d’origine.  
  
- Requêtes qui contiennent Zip ou SequenceEquals, sauf si une des sources de données a un index ordonné à l’origine et la source de données indexable (autrement dit, un tableau ou un IList(T)).  
  
- Requêtes qui contiennent Concat, sauf si elle est appliquée aux sources de données indexables.  
  
- Requêtes qui contiennent Reverse, sauf si elle est appliquée aux sources de données indexables.  
  
## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
