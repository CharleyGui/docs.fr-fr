---
title: 'Comment : itérer les répertoires de fichiers avec PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: 208076cb9b7b56ab13458fa0dd4d92f2023106b9
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635844"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Comment : itérer les répertoires de fichiers avec PLINQ

Cet article montre deux façons de faire le parallèle avec les opérations dans les répertoires de fichiers. La première requête utilise la méthode <xref:System.IO.Directory.GetFiles%2A> pour renseigner un tableau de noms de fichiers dans un répertoire et tous ses sous-répertoires. Cette méthode peut introduire la latence au début de l’opération, car elle ne revient pas jusqu’à ce que l’ensemble du tableau soit peuplé. Cependant, une fois le tableau peuplé, PLINQ peut le traiter en parallèle rapidement.  
  
La deuxième requête utilise <xref:System.IO.Directory.EnumerateDirectories%2A> <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> la statique et les méthodes, qui commencent à retourner les résultats immédiatement. Cette approche peut être plus rapide lorsque vous itérant sur les grands arbres d’annuaire, mais le temps de traitement par rapport au premier exemple dépend de nombreux facteurs.  
  
> [!NOTE]
> Ces exemples sont destinés à démontrer l’utilisation et pourraient ne pas courir plus vite que l’équivalent linQ séquentiel à la requête Objets. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="getfiles-example"></a>Exemple de GetFiles

 Cet exemple montre comment itérer sur les répertoires de fichiers dans des scénarios simples lorsque vous avez accès à tous les répertoires de l’arbre, que la taille des fichiers n’est pas grande et que les temps d’accès ne sont pas significatifs. Cette approche implique une période de latence au début, le temps que le tableau de noms de fichiers soit créé.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="enumeratefiles-example"></a>EnumerateFiles exemple

 Cet exemple montre comment itérer sur les répertoires de fichiers dans des scénarios simples lorsque vous avez accès à tous les répertoires de l’arbre, que la taille des fichiers n’est pas grande et que les temps d’accès ne sont pas significatifs. Cette méthode commence à générer des résultats plus rapidement que l’exemple précédent.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Si vous utilisez <xref:System.IO.Directory.GetFiles%2A>, assurez-vous de disposer des autorisations suffisantes sur tous les répertoires de l’arborescence. Dans le cas contraire, une exception sera lancée et aucun résultat ne sera retourné. Quand vous utilisez la méthode <xref:System.IO.Directory.EnumerateDirectories%2A> dans une requête PLINQ, la gestion des exceptions d’E/S de façon normale permettant de poursuivre l’itération devient problématique. Si votre code doit gérer les E/S ou les exceptions d’accès non autorisé, vous devez envisager l’approche décrite dans [Comment : itérer les répertoires de fichiers avec la classe parallèle](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Si la latence des E/S s’avère un problème, par exemple avec des E/S de fichiers sur un réseau, optez plutôt pour l’une des techniques d’E/S asynchrones décrites dans [Bibliothèque parallèle de tâches et programmation asynchrone .NET traditionnelle](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) et dans ce [billet de blog](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Voir aussi

- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
