---
title: 'Procédure : itérer les répertoires de fichiers avec PLINQ'
ms.date: 03/30/2017
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: 4e9e8e646594ce3cd8b8861cb270170bafc9afb8
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826916"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Procédure : itérer les répertoires de fichiers avec PLINQ

Cet article présente deux façons de paralléliser les opérations sur les répertoires de fichiers. La première requête utilise la méthode <xref:System.IO.Directory.GetFiles%2A> pour renseigner un tableau de noms de fichiers dans un répertoire et tous ses sous-répertoires. Cette méthode peut introduire une latence au début de l’opération, car elle ne retourne pas jusqu’à ce que l’intégralité du tableau soit remplie. Toutefois, une fois que le tableau est rempli, PLINQ peut rapidement le traiter en parallèle.  
  
La deuxième requête utilise les <xref:System.IO.Directory.EnumerateDirectories%2A> méthodes et statiques <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> , qui commencent à retourner immédiatement les résultats. Cette approche peut être plus rapide lorsque vous effectuez une itération sur de grandes arborescences de répertoires, mais le temps de traitement comparé au premier exemple dépend de nombreux facteurs.  
  
> [!NOTE]
> Ces exemples sont destinés à illustrer l’utilisation et peuvent ne pas s’exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).  
  
## <a name="getfiles-example"></a>Exemple GetFiles

 Cet exemple montre comment itérer au sein des répertoires de fichiers dans des scénarios simples lorsque vous avez accès à tous les répertoires de l’arborescence, que les tailles de fichier ne sont pas volumineuses et que les délais d’accès ne sont pas significatifs. Cette approche implique une période de latence au début, le temps que le tableau de noms de fichiers soit créé.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="enumeratefiles-example"></a>Exemple EnumerateFiles

 Cet exemple montre comment itérer au sein des répertoires de fichiers dans des scénarios simples lorsque vous avez accès à tous les répertoires de l’arborescence, que les tailles de fichier ne sont pas volumineuses et que les délais d’accès ne sont pas significatifs. Cette méthode commence à générer des résultats plus rapidement que l’exemple précédent.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Si vous utilisez <xref:System.IO.Directory.GetFiles%2A>, assurez-vous de disposer des autorisations suffisantes sur tous les répertoires de l’arborescence. Dans le cas contraire, une exception est levée et aucun résultat n’est retourné. Quand vous utilisez la méthode <xref:System.IO.Directory.EnumerateDirectories%2A> dans une requête PLINQ, la gestion des exceptions d’E/S de façon normale permettant de poursuivre l’itération devient problématique. Si votre code doit gérer les E/S ou les exceptions d’accès non autorisé, vous devez envisager l’approche décrite dans [Comment : itérer les répertoires de fichiers avec la classe parallèle](how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Si la latence des e/s est un problème, par exemple avec les e/s de fichier sur un réseau, envisagez d’utiliser l’une des techniques d’e/s asynchrones décrites dans la [bibliothèque parallèle de tâches et la programmation asynchrone .net traditionnelle](tpl-and-traditional-async-programming.md) et dans ce billet de [blog](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
