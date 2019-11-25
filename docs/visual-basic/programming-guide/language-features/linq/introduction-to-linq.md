---
title: Introduction à LINQ
ms.date: 08/28/2018
helpviewer_keywords:
- queries [LINQ in Visual Basic], about LINQ in Visual Basic queries
- query execution [LINQ in Visual Basic]
- range variables [Visual Basic]
- LINQ [Visual Basic]
- LINQ [Visual Basic], about LINQ in Visual Basic
- query expressions [LINQ in Visual Basic]
- LINQ
- deferred execution
- iteration variables [Visual Basic]
ms.assetid: 3047d86e-0d49-40e2-928b-dc02e46c7984
ms.openlocfilehash: 610f2a1020cc15f855b3ddfc0917e14aae34fb82
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344936"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Introduction à LINQ dans Visual Basic
Language-Integrated Query (LINQ) adds query capabilities to Visual Basic and provides simple and powerful capabilities when you work with all kinds of data. Rather than sending a query to a database to be processed, or working with different query syntax for each type of data that you are searching, LINQ introduces queries as part of the Visual Basic language. Il utilise une syntaxe unifiée indépendamment du type de données.  
  
 LINQ enables you to query data from a SQL Server database, XML, in-memory arrays and collections, ADO.NET datasets, or any other remote or local data source that supports LINQ. You can do all this with common Visual Basic language elements. Because your queries are written in the Visual Basic language, your query results are returned as strongly-typed objects. Ces objets prennent en charge IntelliSense, qui vous permet d'écrire du code plus rapidement et d'intercepter les erreurs dans vos requêtes au moment de la compilation plutôt qu'au moment de l'exécution. Les requêtes LINQ peuvent être utilisées comme source de requêtes supplémentaires pour affiner les résultats. Elles peuvent également être liées à des contrôles pour que les utilisateurs puissent afficher et modifier facilement vos résultats de requête.  
  
 Par exemple, l'exemple de code suivant affiche une requête LINQ qui retourne une liste de clients à partir d'une collection et les regroupe en fonction de leur emplacement.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#1)]  
  
## <a name="running-the-examples"></a>Exécution des exemples  
 To run the examples in the introduction and in the [Structure of a LINQ Query](#structure-of-a-linq-query) section, include the following code, which returns lists of customers and orders.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#31)]  
  
## <a name="linq-providers"></a>LINQ providers  
 A *LINQ provider* maps your Visual Basic LINQ queries to the data source being queried. Quand vous écrivez une requête LINQ, le fournisseur prend cette requête et la traduit en commandes que la source de données sera en mesure d'exécuter. Le fournisseur convertit également des données de la source en objets qui composent votre résultat de la requête. Enfin, il convertit des objets en données quand vous envoyez des mises à jour à la source de données.  
  
 Visual Basic includes the following LINQ providers.  
  
|Fournisseur|Description|  
|---|---|  
|LINQ to Objects|Le fournisseur LINQ to Objects vous permet d'interroger des collections et des tableaux en mémoire. Si un objet prend en charge l'interface <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, le fournisseur LINQ to Objects vous permet de l'interroger.<br /><br /> You can enable the LINQ to Objects provider by importing the <xref:System.Linq> namespace, which is imported by default for all Visual Basic projects.<br /><br /> For more information about the LINQ to Objects provider, see [LINQ to Objects](../../concepts/linq/linq-to-objects.md).|  
|LINQ to SQL|Le fournisseur LINQ to SQL vous permet d'interroger et de modifier des données dans une base de données SQL Server. Cela facilite le mappage du modèle objet d'une application aux tables et objets d'une base de données.<br /><br /> Visual Basic makes it easier to work with LINQ to SQL by including the Object Relational Designer (O/R Designer). Ce concepteur est utilisé pour créer un modèle objet dans une application qui effectue un mappage aux objets d'une base de données. The O/R Designer also provides functionality to map stored procedures and functions to the <xref:System.Data.Linq.DataContext> object, which manages communication with the database and stores state for optimistic concurrency checks.<br /><br /> For more information about the LINQ to SQL provider, see [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md). For more information about the Object Relational Designer, see [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ to XML|Le fournisseur LINQ to XML vous permet d'interroger et de modifier du code XML. Vous pouvez modifier du code XML en mémoire ou le charger à partir d'un fichier, mais également l'enregistrer dans un fichier.<br /><br /> Additionally, the LINQ to XML provider enables XML literals and XML axis properties that enable you to write XML directly in your Visual Basic code. For more information, see [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ to DataSet|The LINQ to DataSet provider enables you to query and update data in an ADO.NET dataset. Vous pouvez ajouter la puissance de LINQ aux applications qui utilisent des groupes de données afin de simplifier et d'étendre vos capacités de requête, d'agrégation et de mise à jour des données dans votre dataset.<br /><br /> Pour plus d’informations, [consultez LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
## <a name="structure-of-a-linq-query"></a>Structure of a LINQ query  
 A LINQ query, often referred to as a *query expression*, consists of a combination of query clauses that identify the data sources and iteration variables for the query. Une expression de requête peut également inclure des instructions de tri, de filtrage, de regroupement et de jonction ou des calculs applicables aux données sources. La syntaxe de l'expression de requête ressemble à la syntaxe de SQL ; par conséquent, une grande partie de cette syntaxe vous semblera familière.  
  
 Une expression de requête commence par une clause `From`. Cette clause identifie les données sources d'une requête et les variables utilisées pour faire individuellement référence à chaque élément des données sources. These variables are named *range variables* or *iteration variables*. La clause `From` est nécessaire pour une requête, à l'exception des requêtes `Aggregate`, où la clause `From` est facultative. Après avoir identifié la portée et la source de la requête dans les clauses `From` ou `Aggregate`, vous pouvez inclure toute combinaison de clauses de requête pour affiner la requête. For details about query clauses, see Visual Basic LINQ Query Operators later in this topic. Par exemple, la requête suivante identifie une collection de sources de données client comme variable `customers` et une variable d’itération appelée `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#2)]  
  
 Cet exemple représente une requête valide en elle-même ; toutefois, la requête gagne en puissance quand vous ajoutez davantage de clauses de requête pour affiner le résultat. Par exemple, vous pouvez ajouter une clause `Where` pour filtrer le résultat en fonction d'une ou plusieurs valeurs. Les expressions de requête forment une ligne unique de code ; il vous suffit d'ajouter des clauses de requête supplémentaires à la fin de la requête. You can break up a query across multiple lines of text to improve readability by using the underscore (\_) line-continuation character. L'exemple de code suivant illustre une requête qui inclut une clause `Where`.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#3)]  
  
 Autre clause de requête performante, la clause `Select` vous permet de retourner uniquement des champs sélectionnés de la source de données. Les requêtes LINQ retournent des collections énumérables d'objets fortement typés. Une requête peut retourner une collection de types anonymes ou nommés. Vous pouvez utiliser la clause `Select` pour retourner uniquement un champ de la source de données. Dans ce cas, le type de la collection retournée est le type de ce champ unique. Vous pouvez également utiliser la clause `Select` pour retourner plusieurs champs de la source de données. Dans ce cas, le type de la collection retournée est un nouveau type anonyme. Vous pouvez également faire correspondre les champs retournés par la requête aux champs d'un type nommé spécifié. L’exemple de code suivant affiche une expression de requête qui retourne une collection de types anonymes dont les membres sont remplis des données des champs sélectionnés de la source de données.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#4)]  
  
 Les requêtes LINQ peuvent également être utilisées pour combiner plusieurs sources de données et retourner un résultat unique. Cette opération peut être effectuée à l'aide d'une ou plusieurs clauses `From` ou en utilisant les clauses de requête `Join` ou `Group Join`. L'exemple de code suivant illustre une expression de requête qui combine des données de client et de commande et retourne une collection de types anonymes contenant ces deux types de données.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#5)]  
  
 Vous pouvez utiliser la clause `Group Join` pour créer un résultat de requête hiérarchique contenant une collection d'objets customer. Chaque objet customer possède une propriété contenant une collection de toutes les commandes de ce client. L'exemple de code suivant affiche une expression de requête qui combine des données client/commande sous forme de résultat hiérarchique et retourne une collection de types anonymes. La requête retourne un type qui inclut une propriété `CustomerOrders` contenant une collection de données de commande pour le client. Il inclut également une propriété `OrderTotal` qui contient la somme des totaux pour toutes les commandes de ce client. (Cette requête est équivalente à une JOINTURE EXTERNE GAUCHE.)  
  
 [!code-vb[VbVbalrIntroToLINQ#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#6)]  
  
 Il existe plusieurs opérateurs de requête LINQ supplémentaires qui vous permettent de créer des expressions de requête puissantes. La section suivante de cette rubrique présente les différentes clauses de requête que vous pouvez inclure dans une expression de requête. For details about Visual Basic query clauses, see [Queries](../../../../visual-basic/language-reference/queries/index.md).  
  
## <a name="visual-basic-linq-query-operators"></a>Visual Basic LINQ query operators  

Les classes de l'espace de noms <xref:System.Linq> et des autres espaces de noms qui prennent en charge les requêtes LINQ incluent des méthodes que vous pouvez appeler pour créer et affiner les requêtes en fonction des besoins de votre application. Visual Basic includes keywords for the following common query clauses. For details about Visual Basic query clauses, see [Queries](../../../language-reference/queries/index.md).

### <a name="from-clause"></a>Clause From

Either a [`From` clause](../../../../visual-basic/language-reference/queries/from-clause.md) or an `Aggregate` clause is required to begin a query. Une clause `From` spécifie une collection de sources et une variable d'itération pour une requête. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#7)]

### <a name="select-clause"></a>Select (clause)

Optionnel. A [`Select` clause](../../../../visual-basic/language-reference/queries/select-clause.md) declares a set of iteration variables for a query. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#8)]

Si une clause `Select` n'est pas spécifiée, les variables d'itération de la requête se composent des variables d'itération spécifiées par la clause `From` ou `Aggregate`.

### <a name="where-clause"></a>Where (clause)

Optionnel. A [`Where` clause](../../../../visual-basic/language-reference/queries/where-clause.md) specifies a filtering condition for a query. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#9)]

### <a name="order-by-clause"></a>Order By clause]

|Optional. An [`Order By` clause](../../../../visual-basic/language-reference/queries/order-by-clause.md) specifies the sort order for columns in a query. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#10)]

### <a name="join-clause"></a>Join (clause)

Optionnel. A [`Join` clause](../../../../visual-basic/language-reference/queries/join-clause.md) combines two collections into a single collection. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#11)]

### <a name="group-by-clause"></a>Group By (clause)

Optionnel. A [`Group By` clause](../../../../visual-basic/language-reference/queries/group-by-clause.md) groups the elements of a query result. It can be used to apply aggregate functions to each group. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#12)]

### <a name="group-join-clause"></a>Group Join (clause)

Optionnel. A [`Group Join` clause](../../../../visual-basic/language-reference/queries/group-join-clause.md) combines two collections into a single hierarchical collection. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#13)]

### <a name="aggregate-clause"></a>Aggregate (clause)

Either an [`Aggregate` clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) or a `From` clause is required to begin a query. Une clause `Aggregate` applique une ou plusieurs fonctions d’agrégation à une collection. For example, you can use the `Aggregate` clause to calculate a sum for all the elements returned by a query, as the following example does.

 [!code-vb[VbVbalrIntroToLINQ#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#14)]

Vous pouvez également utiliser la clause `Aggregate` pour modifier une requête. Par exemple, vous pouvez utiliser la clause `Aggregate` pour effectuer un calcul sur une collection de requêtes connexe. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#15)]

### <a name="let-clause"></a>Let (clause)

Optionnel. A [`Let` clause](../../../../visual-basic/language-reference/queries/let-clause.md) computes a value and assigns it to a new variable in the query. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#16)]

### <a name="distinct-clause"></a>Distinct (clause)

Optionnel. A `Distinct` clause restricts the values of the current iteration variable to eliminate duplicate values in query results. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#17)]

### <a name="skip-clause"></a>Skip (clause)

Optionnel. A [`Skip` clause](../../../../visual-basic/language-reference/queries/skip-clause.md) bypasses a specified number of elements in a collection and then returns the remaining elements. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#18)]

### <a name="skip-while-clause"></a>SkipWhile (clause)

Optionnel. A [`Skip While` clause](../../../../visual-basic/language-reference/queries/skip-while-clause.md) bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#19)]

### <a name="take-clause"></a>Take (clause)

Optionnel. A [`Take` clause](../../../../visual-basic/language-reference/queries/take-clause.md) returns a specified number of contiguous elements from the start of a collection. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#20)]

### <a name="take-while-clause"></a>Take While (clause)

Optionnel. A [`Take While` clause](../../../../visual-basic/language-reference/queries/take-while-clause.md) includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements. Exemple :

 [!code-vb[VbVbalrIntroToLINQ#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#21)]
  
## <a name="use-additional-linq-query-features"></a>Use additional LINQ query features  
  
Vous pouvez utiliser des fonctionnalités de requête LINQ supplémentaires en appelant des membres des types énumérables et requêtables fournis par LINQ. Vous pouvez utiliser ces fonctions supplémentaires en appelant un opérateur de requête particulier sur le résultat d'une expression de requête. For example, the following example uses the <xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType> method to combine the results of two queries into one query result. Il utilise la méthode <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> pour retourner le résultat de la requête sous forme de liste générique.
  
 [!code-vb[VbVbalrIntroToLINQ#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#22)]  
  
 For details about additional LINQ capabilities, see [Standard Query Operators Overview](../../concepts/linq/standard-query-operators-overview.md).  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>Connect to a database by using LINQ to SQL  
 In Visual Basic, you identify the SQL Server database objects, such as tables, views, and stored procedures, that you want to access by using a LINQ to SQL file. Un fichier LINQ to SQL possède une extension .dbml.  
  
 When you have a valid connection to a SQL Server database, you can add a **LINQ to SQL Classes** item template to your project. Le Concepteur Objet Relationnel (Concepteur O/R) s'affiche alors. The O/R Designer enables you to drag the items that you want to access in your code from the **Server Explorer**/**Database Explorer** onto the designer surface. Le fichier LINQ to SQL ajoute un objet <xref:System.Data.Linq.DataContext> à votre projet. Cet objet inclut des propriétés et des collections pour les tables et vues auxquelles vous souhaitez accéder, et aux méthodes des procédures stockées que vous souhaitez appeler. Après avoir enregistré vos modifications dans le fichier LINQ to SQL (.dbml), vous pouvez accéder à ces objets dans votre code en référençant l'objet <xref:System.Data.Linq.DataContext> défini par le Concepteur O/R. L'objet <xref:System.Data.Linq.DataContext> de votre projet est nommé d'après le nom de votre fichier LINQ to SQL. Par exemple, un fichier LINQ to SQL nommé Northwind.dbml créera un objet <xref:System.Data.Linq.DataContext> nommé `NorthwindDataContext`.  
  
 For examples with step-by-step instructions, see [How to: Query a Database](how-to-query-a-database-by-using-linq.md) and [How to: Call a Stored Procedure](how-to-call-a-stored-procedure-by-using-linq.md).  
  
## <a name="visual-basic-features-that-support-linq"></a>Visual Basic features that support LINQ  
 Visual Basic includes other notable features that make the use of LINQ simple and reduce the amount of code that you must write to perform LINQ queries. Notamment :  
  
- **Anonymous types**, which enable you to create a new type based on a query result.  
  
- **Implicitly typed variables**, which enable you to defer specifying a type and let the compiler infer the type based on the query result.  
  
- **Extension methods**, which enable you to extend an existing type with your own methods without modifying the type itself.  
  
 For details, see [Visual Basic Features That Support LINQ](../../concepts/linq/features-that-support-linq.md).  
  
## <a name="deferred-and-immediate-query-execution"></a>Deferred and immediate query execution

 L'exécution d'une requête est distincte de sa création. Après avoir créé une requête, son exécution est déclenchée par un mécanisme distinct. A query can be executed as soon as it is defined (*immediate execution*), or the definition can be stored and the query can be executed later (*deferred execution*).  
  
 Par défaut, quand vous créez une requête, cette dernière ne s'exécute pas immédiatement. À la place, la définition de la requête est stockée dans la variable utilisée pour référencer le résultat de la requête. Quand vous accédez à la variable de résultat de la requête ultérieurement dans le code, par exemple, dans une boucle `For…Next`, la requête est exécutée. This process is referred to as *deferred execution*.  
  
 Queries can also be executed when they are defined, which is referred to as *immediate execution*. Vous pouvez déclencher l'exécution immédiate en appliquant une méthode qui requiert l'accès aux éléments individuels du résultat de la requête. L'inclusion d'une fonction d'agrégation, telle que `Count`, `Sum`, `Average`, `Min` ou `Max` peut engendrer un tel résultat. For more information about aggregate functions, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md).  
  
 L'utilisation de la méthode `ToList` ou `ToArray` force également l'exécution immédiate. Cela peut être utile quand vous souhaitez exécuter immédiatement la requête et mettre en cache les résultats. For more information about these methods, see [Converting Data Types](../../concepts/linq/converting-data-types.md).  
  
 For more information about query execution, see [Writing Your First LINQ Query](../../concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="xml-in-visual-basic"></a>XML en Visual Basic  
 The XML features in Visual Basic include XML literals and XML axis properties, which enable you easily to create, access, query, and modify XML in your code. Les littéraux XML vous permettent d'écrire directement en XML dans votre code. Le compilateur Visual Basic traite le XML comme un objet de donnée de première classe.  
  
 L'exemple de code suivant montre comment créer un élément XML, accéder à ses sous-éléments et attributs, et interroger son contenu à l'aide de LINQ.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 For more information, see [XML](../xml/index.md).  
  
## <a name="related-resources"></a>Ressources connexes  
  
|Rubrique|Description|  
|---|---|  
|[XML](../../language-features/xml/index.md)|Describes the XML features in Visual Basic that can be queried and that enable you to include XML as first-class data objects in your Visual Basic code.|  
|[Requêtes](../../../language-reference/queries/index.md)|Provides reference information about the query clauses that are available in Visual Basic.|  
|[LINQ (Language Integrated Query)](../../concepts/linq/index.md)|Inclut des informations générales, un guide de programmation et des exemples de requêtes LINQ.|  
|[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)|Inclut des informations générales, un guide de programmation et des exemples de LINQ to SQL.|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|Inclut des informations générales, un guide de programmation et des exemples de LINQ to Objects.|  
|[LINQ to ADO.NET (page de portail)](../../concepts/linq/linq-to-adonet-portal-page.md)|Includes links to general information, programming guidance, and samples for LINQ to ADO.NET.|  
|[LINQ to XML](../../concepts/linq/linq-to-xml.md)|Inclut des informations générales, un guide de programmation et des exemples de LINQ to XML.|  
  
## <a name="how-to-and-walkthrough-topics"></a>How to and walkthrough topics
 [Guide pratique : interroger une base de données](how-to-query-a-database-by-using-linq.md)  
  
 [Guide pratique : appeler une procédure stockée](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Guide pratique : modifier des données dans une base de données](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Guide pratique : combiner des données avec des jointures](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Guide pratique : trier les résultats d’une requête](how-to-sort-query-results-by-using-linq.md)  
  
 [Guide pratique : filtrer les résultats d’une requête](how-to-filter-query-results-by-using-linq.md)  
  
 [Guide pratique : compter, additionner ou faire la moyenne de données](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Guide pratique : rechercher la valeur minimale ou maximale dans un résultat de requête](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
  
## <a name="featured-book-chapters"></a>Featured book chapters  
 [Chapter 17: LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) in [Programming Visual Basic 2008](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>Voir aussi

- [LINQ (Language Integrated Query)](../../concepts/linq/index.md)
- [Vue d’ensemble de LINQ to XML en Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md)
- [Vue d’ensemble de LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset-overview.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Outils LINQ to SQL dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [DataContext, méthodes (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
