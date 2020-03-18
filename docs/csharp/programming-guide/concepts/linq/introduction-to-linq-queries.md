---
title: Introduction aux requêtes LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: 7fbdfa8656e3c4832226370dc6efe56964e14934
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168503"
---
# <a name="introduction-to-linq-queries-c"></a>Introduction aux requêtes LINQ (C#)
Une *requête* est une expression qui récupère les données d’une source de données. Les requêtes sont généralement exprimées dans un langage de requête spécialisé. Les différents langages ont été développés au fil du temps pour les différents types de sources de données, par exemple, SQL pour les bases de données relationnelles et XQuery pour XML. Les développeurs devaient donc apprendre un nouveau langage de requête pour chaque nouveau type de source de données ou format de données qu’ils devaient prendre en charge. LINQ simplifie cette situation en offrant un modèle cohérent pour travailler avec des données sur divers types de sources et de formats de données. Dans une requête LINQ, vous travaillez toujours avec des objets. Vous utilisez les mêmes modèles de codage de base pour interroger et transformer les données en documents XML, bases de données SQL, ADO.NET Datasets, collections .NET, et tout autre format pour lequel un fournisseur LINQ est disponible.  
  
## <a name="three-parts-of-a-query-operation"></a>Les trois parties d’une opération de requête  
 Toutes les opérations de requête linQ se composent de trois actions distinctes :  
  
1. Obtention de la source de données  
  
2. Création de la requête  
  
3. exécutez la requête.  
  
 L’exemple suivant montre comment les trois parties d’une opération de requête sont exprimées dans le code source. Cet exemple utilise un tableau d’entiers comme source de données pour des raisons pratiques. Toutefois, ces mêmes concepts s’appliquent également aux autres sources de données. Le reste de la rubrique fait référence à cet exemple.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 L’illustration suivante montre l’intégralité de l’opération de requête. Dans LINQ, l’exécution de la requête est distincte de la requête elle-même. En d’autres termes, vous n’avez pas récupéré de données simplement en créant une variable de requête.  
  
 ![Diagramme de l’opération de requête LINQ complète.](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Source de données  
 Dans l’exemple précédent, comme la source de données est un tableau, elle prend en charge implicitement l’interface générique <xref:System.Collections.Generic.IEnumerable%601>. Ce fait signifie qu’il peut être interrogé avec LINQ. Une requête est exécutée dans une instruction `foreach`, et `foreach` nécessite <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>. Les types qui prennent en charge <xref:System.Collections.Generic.IEnumerable%601> ou une interface dérivée, comme l’interface générique <xref:System.Linq.IQueryable%601>, sont appelés des *types requêtables*.  
  
 Un type requête ne nécessite aucune modification ou traitement spécial pour servir de source de données LINQ. Si les données sources ne sont pas déjà en mémoire comme type requête, le fournisseur linQ doit les représenter en tant que tels. Par exemple, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] charge un document XML dans un type <xref:System.Xml.Linq.XElement> requêtable :  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 Avec [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], vous commencez par créer un mappage O/R au moment du design, manuellement ou à l’aide des [Outils LINQ to SQL de Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2). Vous écrivez vos requêtes pour des objets. Ensuite, au moment de l’exécution, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] gère la communication avec la base de données. Dans l’exemple suivant, `Customers` représente une table spécifique de la base de données et le type du résultat de la requête, <xref:System.Linq.IQueryable%601>, dérive de <xref:System.Collections.Generic.IEnumerable%601>.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Pour de plus amples renseignements sur la façon de créer des types précis de sources de données, consultez la documentation des différents fournisseurs de LINQ. Cependant, la règle de base est très simple : une <xref:System.Collections.Generic.IEnumerable%601> source de données LINQ est tout objet qui prend en charge l’interface générique, ou une interface qui en hérite.  
  
> [!NOTE]
> Des types <xref:System.Collections.ArrayList> tels que ceux <xref:System.Collections.IEnumerable> qui prennent en charge l’interface non générique peuvent également être utilisés comme source de données LINQ. Pour plus d’informations, voir [Comment interroger un TableauList avec LINQ (C)](./how-to-query-an-arraylist-with-linq.md).  
  
## <a name="query"></a>La requête  
 La requête spécifie les informations à récupérer à partir de la ou des sources de données. Si vous le souhaitez, une requête peut également spécifier la manière dont ces informations doivent être triées, regroupées et mises en forme avant d’être retournées. Une requête est stockée dans une variable de requête et initialisée avec une expression de requête. Pour faciliter l’écriture de requêtes, le langage C# propose désormais une nouvelle syntaxe de requête.  
  
 La requête de l’exemple précédent retourne tous les nombres pairs du tableau d’entiers. L’expression de requête contient trois clauses : `from`, `where` et `select`. (Si vous connaissez SQL, vous aurez remarqué que la commande des clauses est inversée de l’ordre dans SQL.) La `from` clause spécifie `where` la source de données, la clause applique le filtre et la `select` clause spécifie le type d’éléments retournés. Ces clauses et les autres clauses de requête sont discutées en détail dans la section [Questions intégrées linguistiques (LINQ).](../../../linq/index.md) Pour l’instant, l’important est que dans LINQ, la variable de requête elle-même ne prend aucune mesure et ne renvoie aucune donnée. Elle stocke simplement les informations qui seront nécessaires pour produire des résultats lors de l’exécution ultérieure de la requête. Pour plus d’informations sur la construction des requêtes en arrière-plan, consultez [Vue d’ensemble des opérateurs de requête standard (C#)](./standard-query-operators-overview.md).  
  
> [!NOTE]
> Les requêtes peuvent également être exprimées à l’aide d’une syntaxe de méthode. Pour plus d’informations, consultez [Syntaxe de requête et syntaxe de méthode dans LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Exécution des requêtes  
  
### <a name="deferred-execution"></a>Exécution différée  
 Comme indiqué précédemment, la variable de requête stocke uniquement les commandes de requête. L’exécution de la requête est différée jusqu’à ce que vous itériez au sein de la variable de requête dans une instruction `foreach`. Ce concept est appelé *exécution différée* et est illustré dans l’exemple suivant :  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 C’est dans l’instruction `foreach` que les résultats de requête sont récupérés. Par exemple, dans la requête précédente, la variable d’itération `num` contient chaque valeur (une à la fois) de la séquence retournée.  
  
 Étant donné que la variable de requête ne contient jamais les résultats de requête, vous pouvez l’exécuter aussi souvent que vous le voulez. Par exemple, vous disposez peut-être d’une base de données qui est constamment mise à jour par une application distincte. Vous pouvez créer dans cette dernière une requête dans le but d’extraire les données les plus récentes, puis l’exécuter à intervalle régulier. Vous obtiendrez à chaque fois des résultats différents.  
  
### <a name="forcing-immediate-execution"></a>Forcer l’exécution immédiate  
 Les requêtes qui exécutent des fonctions d’agrégation sur une plage d’éléments sources doivent d’abord itérer au sein de ces éléments. Ces requêtes sont par exemple `Count`, `Max`, `Average` et `First`. Elles s’exécutent sans instruction `foreach` explicite, car les requêtes doivent utiliser `foreach` pour retourner un résultat. Notez également que ces types de requêtes retournent une seule valeur, et non une collection `IEnumerable`. La requête suivante retourne un nombre de chiffres pairs du tableau source :  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Pour forcer l’exécution immédiate de n’importe quelle requête et mettre en cache ses résultats, vous pouvez appeler les méthodes <xref:System.Linq.Enumerable.ToList%2A> ou <xref:System.Linq.Enumerable.ToArray%2A>.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Vous pouvez également forcer l’exécution en plaçant la boucle `foreach` immédiatement après l’expression de requête. Toutefois, en appelant `ToList` ou `ToArray`, vous mettez également en cache toutes les données dans un même objet de collection.  
  
## <a name="see-also"></a>Voir aussi

- [Démarrer avec LINQ en C #](index.md)
- [Procédure pas à pas : écriture de requêtes en C#](./walkthrough-writing-queries-linq.md)
- [Requête intégrée linguistique (LINQ)](../../../linq/index.md)
- [foreach, in](../../../language-reference/keywords/foreach-in.md)
- [Mots-clés de requête (LINQ)](../../../language-reference/keywords/query-keywords.md)
