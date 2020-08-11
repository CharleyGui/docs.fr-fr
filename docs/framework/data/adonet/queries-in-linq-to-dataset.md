---
title: Requêtes dans LINQ to DataSet
description: Apprenez à composer des requêtes dans LINQ to DataSet en obtenant la ou les sources de données, en créant la requête et en exécutant la requête.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
ms.openlocfilehash: eee04959493914018904b61b0e5a289f172f2f18
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063716"
---
# <a name="queries-in-linq-to-dataset"></a>Requêtes dans LINQ to DataSet
Une requête est une expression qui récupère des données d'une source de données. En général, les requêtes sont exprimées dans un langage de requête spécialisé, tel que SQL pour les bases de données relationnelles et Xquery pour XML. Par conséquent, les développeurs ont dû apprendre un nouveau langage de requête pour chaque type de source de données ou format de données qu'ils interrogent. LINQ (Language-Integrated Query) propose un modèle cohérent plus simple qui permet d'utiliser des données de types de sources et de formats divers. Dans une requête LINQ, vous travaillez toujours avec des objets de programmation.  
  
 Une opération de requête LINQ se compose de trois actions : obtenir la ou les sources de données, créer la requête, puis exécuter cette dernière.  
  
 Les sources de données qui implémentent l' <xref:System.Collections.Generic.IEnumerable%601> interface générique peuvent être interrogées à l’aide de Linq. <xref:System.Data.DataTableExtensions.AsEnumerable%2A>L’appel de sur un <xref:System.Data.DataTable> retourne un objet qui implémente l' <xref:System.Collections.Generic.IEnumerable%601> interface générique, qui sert de source de données pour les requêtes de LINQ to DataSet.  
  
 Dans la requête, vous spécifiez exactement les informations que vous voulez récupérer à partir de la source de données. Une requête peut également spécifier la manière dont ces informations doivent être triées, regroupées et mises en forme avant d'être retournées. Dans LINQ, une requête est stockée dans une variable. Si la requête est conçue pour retourner une séquence de valeurs, la variable de requête doit elle-même être de type dénombrable. Cette variable de requête n'effectue aucune action et ne retourne aucune donnée ; elle stocke uniquement les informations de requête. Une fois que vous avez créé une requête, vous devez l'exécuter pour extraire des données.  
  
 Dans une requête qui retourne une séquence, la variable de requête elle-même ne contient jamais les résultats de la requête et stocke uniquement les commandes de requête. L'exécution de la requête est différée jusqu'à ce que la variable de requête soit itérée au sein d'une boucle `foreach` ou `For Each`. C’est ce que l’on appelle *l’exécution différée*; autrement dit, l’exécution de la requête a lieu un certain temps après la construction de la requête. Vous pouvez ainsi exécuter une requête aussi souvent que vous le souhaitez. Cela est utile lorsque, par exemple, l'une de vos bases de données est en cours de mise à jour par d'autres applications. Dans votre application, vous pouvez créer une requête pour récupérer les informations les plus récentes et l'exécuter à plusieurs reprises, pour retourner chaque fois les informations à jour.  
  
 Contrairement aux requêtes différées qui retournent une séquence de valeurs, les requêtes qui retournent une valeur singleton sont exécutées immédiatement. Les requêtes <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A> et <xref:System.Linq.Enumerable.First%2A> en sont quelques exemples. Elles s'exécutent immédiatement parce que les résultats de la requête sont nécessaires pour calculer le résultat singleton. Par exemple, pour trouver la moyenne des résultats, la requête doit être exécutée pour que la fonction de moyenne dispose de données sur lesquelles effectuer ses calculs. Vous pouvez également utiliser les méthodes <xref:System.Linq.Enumerable.ToList%2A> ou <xref:System.Linq.Enumerable.ToArray%2A> sur une requête pour forcer l'exécution immédiate d'une requête qui ne produit pas de valeur singleton. Ces techniques peuvent être utiles lorsque vous souhaitez mettre en cache les résultats d'une requête.
  
## <a name="queries"></a>Requêtes  
 LINQ to DataSet requêtes peuvent être formulées dans deux syntaxes différentes : la syntaxe d’expression de requête et la syntaxe de requête fondée sur une méthode.  
  
### <a name="query-expression-syntax"></a>Syntaxe d’expression de requête  
 Les expressions de requête utilisent une syntaxe de requête déclarative. Cette syntaxe permet au développeur d'écrire des requêtes en C# ou Visual Basic dans un format similaire à SQL. En utilisant la syntaxe d'expression de requête, vous pouvez même effectuer des opérations de filtrage, de classement et de regroupement complexes sur des sources de données avec un minimum de code. Pour plus d’informations, consultez [expressions de requête LINQ](../../../csharp/linq/index.md#query-expression-overview) et [opérations de requête de base (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).
  
 Le .NET Framework common language runtime (CLR) ne peut pas lire la syntaxe de l’expression de requête proprement dite. Par conséquent, au moment de la compilation, les expressions de requête sont traduites en appels de méthodes pour que le CLR puisse les comprendre. Ces méthodes sont appelées opérateurs de *requête standard*. En tant que développeur, vous pouvez les appeler directement en utilisant la syntaxe de méthode plutôt que la syntaxe de requête. Pour plus d’informations, consultez [Syntaxe de requête et syntaxe de méthode dans LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md). Pour plus d’informations sur les opérateurs de requête standard, consultez [vue d’ensemble des opérateurs de requête standard](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 L'exemple ci-dessous utilise <xref:System.Linq.Enumerable.Select%2A> pour retourner toutes les lignes de la table `Product` et afficher les noms de produits.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>Syntaxe de requête fondée sur une méthode  
 L’autre façon de formuler des requêtes de LINQ to DataSet consiste à utiliser des requêtes basées sur une méthode. La syntaxe de requête fondée sur une méthode est une séquence d'appels directs de méthodes d'opérateur LINQ passant des expressions lambda comme paramètres. Pour plus d’informations, consultez [expressions lambda](../../../csharp/language-reference/operators/lambda-expressions.md).  
  
 Cet exemple utilise <xref:System.Linq.Enumerable.Select%2A> pour retourner toutes les lignes de `Product` et afficher les noms de produits.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>Composition de requêtes  
 Comme mentionné précédemment dans cette rubrique, la variable de requête elle-même ne stocke les commandes de requête que lorsque la requête est conçue pour retourner une séquence de valeurs. Si la requête ne contient pas de méthode qui déclenche une exécution immédiate, l'exécution effective de la requête est différée jusqu'à ce que vous itériez au sein de la variable de requête dans une boucle `foreach` ou `For Each`. L'exécution différée permet de combiner plusieurs requêtes ou d'étendre une requête. Lorsqu'une requête est étendue, elle est modifiée de manière à inclure les nouvelles opérations, et l'exécution finale reflète les modifications. Dans l'exemple suivant, la première requête retourne tous les produits. La deuxième requête étend la première en utilisant `Where` pour retourner tous les produits de taille « L » :  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Une fois qu’une requête a été exécutée, aucune requête supplémentaire ne peut être composée, et toutes les requêtes suivantes utilisent les opérateurs LINQ en mémoire. L’exécution de la requête se produit lorsque vous itérez au sein de la variable de requête dans une `foreach` `For Each` instruction ou, ou par un appel à l’un des opérateurs de conversion LINQ qui provoquent une exécution immédiate. Ces opérateurs sont notamment : <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A> et <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
 Dans l'exemple suivant, la première requête retourne tous les produits triés par tarif. La méthode <xref:System.Linq.Enumerable.ToArray%2A> est utilisée pour forcer l'exécution immédiate de la requête :  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation](programming-guide-linq-to-dataset.md)
- [Interrogation de DataSets](querying-datasets-linq-to-dataset.md)
- [Mise en route de LINQ en C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Mise en route de LINQ dans Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
