---
title: 'Comment : itérer les répertoires de fichiers avec PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: de33561e2ef8e8fe62e8179272abe8adfffecd6f
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587758"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Comment : itérer les répertoires de fichiers avec PLINQ
Cet exemple montre comment paralléliser des opérations sur des répertoires de fichiers de deux manières différentes. La première requête utilise la méthode <xref:System.IO.Directory.GetFiles%2A> pour renseigner un tableau de noms de fichiers dans un répertoire et tous ses sous-répertoires. Cette méthode ne retourne de résultats qu’une fois le tableau entièrement renseigné. Par conséquent, elle peut introduire une latence au début de l’opération. Mais une fois le tableau renseigné, PLINQ est capable de le traiter en parallèle très rapidement.  
  
 La seconde requête utilise les méthodes statiques <xref:System.IO.Directory.EnumerateDirectories%2A> et <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> qui commencent à retourner des résultats immédiatement. Cette approche peut être plus rapide quand vous itérez au sein d’arborescences de répertoires importantes, bien que le temps de traitement par rapport au premier exemple puisse varier en fonction de nombreux facteurs.  
  
> [!WARNING]
> Ces exemples, destinés à illustrer l'utilisation, peuvent ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment itérer au sein de répertoires de fichiers dans des scénarios simples où vous avez accès à tous les répertoires de l’arborescence, où les tailles de fichier ne sont pas très grandes et où les temps d’accès ne sont pas significatifs. Cette approche implique une période de latence au début, le temps que le tableau de noms de fichiers soit créé.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment itérer au sein de répertoires de fichiers dans des scénarios simples où vous avez accès à tous les répertoires de l’arborescence, où les tailles de fichier ne sont pas très grandes et où les temps d’accès ne sont pas significatifs. Cette méthode commence à générer des résultats plus rapidement que l’exemple précédent.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Si vous utilisez <xref:System.IO.Directory.GetFiles%2A>, assurez-vous de disposer des autorisations suffisantes sur tous les répertoires de l’arborescence. Dans le cas contraire, une exception sera levée et aucun résultat ne sera retourné. Quand vous utilisez la méthode <xref:System.IO.Directory.EnumerateDirectories%2A> dans une requête PLINQ, la gestion des exceptions d’E/S de façon normale permettant de poursuivre l’itération devient problématique. Si votre code doit gérer les E/S ou les exceptions d’accès non autorisé, vous devez envisager l’approche décrite dans [Comment : itérer les répertoires de fichiers avec la classe parallèle](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Si la latence des E/S s’avère un problème, par exemple avec des E/S de fichiers sur un réseau, optez plutôt pour l’une des techniques d’E/S asynchrones décrites dans [Bibliothèque parallèle de tâches et programmation asynchrone .NET traditionnelle](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) et dans ce [billet de blog](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
