---
title: Introduction aux requêtes LINQ (C#)
description: LINQ offre un modèle cohérent pour les requêtes sur des données de différents types de sources et de formats de données. Dans une requête LINQ, vous travaillez toujours avec des objets.
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: f81c3f4e355215f1a750a764c617ad47430adc31
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170569"
---
# <a name="introduction-to-linq-queries-c"></a>Introduction aux requêtes LINQ (C#)

Une *requête* est une expression qui récupère des données à partir d’une source de données. Les requêtes sont généralement exprimées dans un langage de requête spécialisé. Les différents langages ont été développés au fil du temps pour les différents types de sources de données, par exemple, SQL pour les bases de données relationnelles et XQuery pour XML. Les développeurs devaient donc apprendre un nouveau langage de requête pour chaque nouveau type de source de données ou format de données qu’ils devaient prendre en charge. LINQ simplifie cette situation en proposant un modèle cohérent pour travailler avec des données dans différents types de sources et de formats de données. Dans une requête LINQ, vous travaillez toujours avec des objets. Vous utilisez les mêmes modèles de codage de base pour interroger et transformer des données dans des documents XML, des bases de données SQL, des jeux de données ADO.NET, des collections .NET et tout autre format pour lequel un fournisseur LINQ est disponible.  
  
## <a name="three-parts-of-a-query-operation"></a>Les trois parties d’une opération de requête  

 Toutes les opérations de requête LINQ se composent de trois actions distinctes :  
  
1. Obtention de la source de données  
  
2. Création de la requête  
  
3. exécutez la requête.  
  
 L’exemple suivant montre comment les trois parties d’une opération de requête sont exprimées dans le code source. Cet exemple utilise un tableau d’entiers comme source de données pour des raisons pratiques. Toutefois, ces mêmes concepts s’appliquent également aux autres sources de données. Le reste de la rubrique fait référence à cet exemple.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 L’illustration suivante montre l’intégralité de l’opération de requête. Dans LINQ, l’exécution de la requête est distincte de la requête elle-même. En d’autres termes, vous n’avez récupéré aucune donnée en créant simplement une variable de requête.  
  
 ![Diagramme de l’opération de requête LINQ complète.](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Source de données  

 Dans l’exemple précédent, comme la source de données est un tableau, elle prend en charge implicitement l’interface générique <xref:System.Collections.Generic.IEnumerable%601>. Cela signifie qu’elle peut être interrogée avec LINQ. Une requête est exécutée dans une instruction `foreach`, et `foreach` nécessite <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>. Les types qui prennent en charge <xref:System.Collections.Generic.IEnumerable%601> ou une interface dérivée, comme l’interface générique <xref:System.Linq.IQueryable%601>, sont appelés des *types requêtables*.  
  
 Un type interrogeable ne nécessite aucune modification ni traitement spécial pour servir de source de données LINQ. Si les données sources ne sont pas déjà en mémoire en tant que type interrogeable, le fournisseur LINQ doit le représenter comme tel. Par exemple, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] charge un document XML dans un type <xref:System.Xml.Linq.XElement> requêtable :  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 Avec [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] , vous créez tout d’abord un mappage objet/relationnel au moment du design, soit manuellement, soit à l’aide des [outils de LINQ to SQL dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2). Vous écrivez vos requêtes pour des objets. Ensuite, au moment de l’exécution, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] gère la communication avec la base de données. Dans l’exemple suivant, `Customers` représente une table spécifique de la base de données et le type du résultat de la requête, <xref:System.Linq.IQueryable%601>, dérive de <xref:System.Collections.Generic.IEnumerable%601>.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Pour plus d’informations sur la création de types spécifiques de sources de données, consultez la documentation relative aux différents fournisseurs LINQ. Toutefois, la règle de base est très simple : une source de données LINQ est un objet qui prend en charge l' <xref:System.Collections.Generic.IEnumerable%601> interface générique ou une interface qui hérite de celui-ci.  
  
> [!NOTE]
> Les types tels que <xref:System.Collections.ArrayList> qui prennent en charge l' <xref:System.Collections.IEnumerable> interface non générique peuvent également être utilisés comme source de données Linq. Pour plus d’informations, consultez [Comment interroger un ArrayList avec LINQ (C#)](./how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a><a name="query"></a> La requête  

 La requête spécifie les informations à récupérer à partir de la ou des sources de données. Si vous le souhaitez, une requête peut également spécifier la manière dont ces informations doivent être triées, regroupées et mises en forme avant d’être retournées. Une requête est stockée dans une variable de requête et initialisée avec une expression de requête. Pour faciliter l’écriture de requêtes, le langage C# propose désormais une nouvelle syntaxe de requête.  
  
 La requête de l’exemple précédent retourne tous les nombres pairs du tableau d’entiers. L’expression de requête contient trois clauses : `from`, `where` et `select`. (Si vous êtes familiarisé avec SQL, vous aurez remarqué que l’ordre des clauses est inversé par rapport à l’ordre dans SQL.) La `from` clause spécifie la source de données, la `where` clause applique le filtre et la `select` clause spécifie le type des éléments retournés. Celles-ci et les autres clauses de requête sont abordées en détail dans la section [Language Integrated Query (LINQ)](../../../linq/index.md) . Pour le moment, le point important est que dans LINQ, la variable de requête elle-même n’effectue aucune action et ne retourne aucune donnée. Elle stocke simplement les informations qui seront nécessaires pour produire des résultats lors de l’exécution ultérieure de la requête. Pour plus d’informations sur la construction des requêtes en arrière-plan, consultez [Vue d’ensemble des opérateurs de requête standard (C#)](./standard-query-operators-overview.md).  
  
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

- [Mise en route de LINQ en C#](index.md)
- [Procédure pas à pas : écriture de requêtes en C#](./walkthrough-writing-queries-linq.md)
- [LINQ (Language-Integrated Query)](../../../linq/index.md)
- [foreach, in](../../../language-reference/keywords/foreach-in.md)
- [Mots clés de requête (LINQ)](../../../language-reference/keywords/query-keywords.md)
