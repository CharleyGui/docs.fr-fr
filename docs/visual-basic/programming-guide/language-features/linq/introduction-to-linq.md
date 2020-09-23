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
ms.openlocfilehash: 00022fc7790548dbc0ed8018f202e136bdbcc033
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075250"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Introduction à LINQ dans Visual Basic

LINQ (Language-Integrated Query) ajoute des fonctionnalités de requête à Visual Basic et fournit des fonctionnalités simples et puissantes quand vous travaillez avec tous les types de données. Plutôt que d’envoyer une requête à une base de données à traiter, ou d’utiliser une syntaxe de requête différente pour chaque type de données que vous recherchez, LINQ introduit des requêtes dans le cadre du langage de Visual Basic. Il utilise une syntaxe unifiée indépendamment du type de données.  
  
 LINQ vous permet d’interroger des données à partir d’une base de données SQL Server, d’un fichier XML, de tableaux et de collections en mémoire, de jeux de données ADO.NET ou de toute autre source de données distante ou locale qui prend en charge LINQ. Vous pouvez effectuer toutes ces tâches avec les éléments de langage d’Visual Basic courants. Étant donné que vos requêtes sont écrites en Visual Basic langage, les résultats de votre requête sont retournés en tant qu’objets fortement typés. Ces objets prennent en charge IntelliSense, qui vous permet d'écrire du code plus rapidement et d'intercepter les erreurs dans vos requêtes au moment de la compilation plutôt qu'au moment de l'exécution. Les requêtes LINQ peuvent être utilisées comme source de requêtes supplémentaires pour affiner les résultats. Elles peuvent également être liées à des contrôles pour que les utilisateurs puissent afficher et modifier facilement vos résultats de requête.  
  
 Par exemple, l'exemple de code suivant affiche une requête LINQ qui retourne une liste de clients à partir d'une collection et les regroupe en fonction de leur emplacement.  
  
 [!code-vb[VbVbalrIntroToLINQ#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#1)]  
  
## <a name="running-the-examples"></a>Exécution des exemples  

 Pour exécuter les exemples de l’introduction et de la section [structure d’une requête LINQ](#structure-of-a-linq-query) , incluez le code suivant, qui retourne les listes Customers et Orders.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#31)]  
  
## <a name="linq-providers"></a>Fournisseurs LINQ  

 Un *fournisseur LINQ* mappe vos requêtes LINQ Visual Basic à la source de données interrogée. Quand vous écrivez une requête LINQ, le fournisseur prend cette requête et la traduit en commandes que la source de données sera en mesure d'exécuter. Le fournisseur convertit également des données de la source en objets qui composent votre résultat de la requête. Enfin, il convertit des objets en données quand vous envoyez des mises à jour à la source de données.  
  
 Visual Basic comprend les fournisseurs LINQ suivants.  
  
|Fournisseur|Description|  
|---|---|  
|LINQ to Objects|Le fournisseur LINQ to Objects vous permet d'interroger des collections et des tableaux en mémoire. Si un objet prend en charge l'interface <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>, le fournisseur LINQ to Objects vous permet de l'interroger.<br /><br /> Vous pouvez activer le fournisseur LINQ to Objects en important l' <xref:System.Linq> espace de noms, qui est importé par défaut pour tous les projets Visual Basic.<br /><br /> Pour plus d’informations sur le fournisseur de LINQ to Objects, consultez [LINQ to Objects](../../concepts/linq/linq-to-objects.md).|  
|LINQ to SQL|Le fournisseur LINQ to SQL vous permet d'interroger et de modifier des données dans une base de données SQL Server. Cela facilite le mappage du modèle objet d'une application aux tables et objets d'une base de données.<br /><br /> Visual Basic simplifie l’utilisation de LINQ to SQL en incluant le Concepteur Objet Relationnel (Concepteur O/R). Ce concepteur est utilisé pour créer un modèle objet dans une application qui effectue un mappage aux objets d'une base de données. Le Concepteur O/R fournit également des fonctionnalités permettant de mapper des procédures stockées et des fonctions à l' <xref:System.Data.Linq.DataContext> objet, qui gère la communication avec la base de données et stocke l’état des contrôles d’accès concurrentiel optimiste.<br /><br /> Pour plus d’informations sur le fournisseur de LINQ to SQL, consultez [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md). Pour plus d’informations sur la Concepteur Objet Relationnel, consultez [LINQ to SQL Tools dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ to XML|Le fournisseur LINQ to XML vous permet d'interroger et de modifier du code XML. Vous pouvez modifier du code XML en mémoire ou le charger à partir d'un fichier, mais également l'enregistrer dans un fichier.<br /><br /> En outre, le fournisseur LINQ to XML active des littéraux XML et des propriétés d’axe XML qui vous permettent d’écrire du code XML directement dans votre code Visual Basic. Pour plus d’informations, consultez [XML](../xml/index.md).|  
|LINQ to DataSet|Le fournisseur LINQ to DataSet vous permet d’interroger et de mettre à jour des données dans un jeu de données ADO.NET. Vous pouvez ajouter la puissance de LINQ aux applications qui utilisent des groupes de données afin de simplifier et d'étendre vos capacités de requête, d'agrégation et de mise à jour des données dans votre dataset.<br /><br /> Pour plus d’informations, [consultez LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).|  
  
## <a name="structure-of-a-linq-query"></a>Structure d’une requête LINQ  

 Une requête LINQ, souvent appelée *expression de requête*, se compose d’une combinaison de clauses de requête qui identifient les sources de données et les variables d’itération pour la requête. Une expression de requête peut également inclure des instructions de tri, de filtrage, de regroupement et de jonction ou des calculs applicables aux données sources. La syntaxe de l'expression de requête ressemble à la syntaxe de SQL ; par conséquent, une grande partie de cette syntaxe vous semblera familière.  
  
 Une expression de requête commence par une clause `From`. Cette clause identifie les données sources d'une requête et les variables utilisées pour faire individuellement référence à chaque élément des données sources. Ces variables sont des variables de *plages* nommées ou des *variables d’itération*. La clause `From` est nécessaire pour une requête, à l'exception des requêtes `Aggregate`, où la clause `From` est facultative. Après avoir identifié la portée et la source de la requête dans les clauses `From` ou `Aggregate`, vous pouvez inclure toute combinaison de clauses de requête pour affiner la requête. Pour plus d’informations sur les clauses de requête, consultez Visual Basic opérateurs de requête LINQ plus loin dans cette rubrique. Par exemple, la requête suivante identifie une collection de sources de données client comme variable `customers` et une variable d’itération appelée `cust`.  
  
 [!code-vb[VbVbalrIntroToLINQ#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#2)]  
  
 Cet exemple représente une requête valide en elle-même ; toutefois, la requête gagne en puissance quand vous ajoutez davantage de clauses de requête pour affiner le résultat. Par exemple, vous pouvez ajouter une clause `Where` pour filtrer le résultat en fonction d'une ou plusieurs valeurs. Les expressions de requête forment une ligne unique de code ; il vous suffit d'ajouter des clauses de requête supplémentaires à la fin de la requête. Vous pouvez décomposer une requête sur plusieurs lignes de texte pour améliorer la lisibilité en utilisant le caractère de continuation de ligne de soulignement ( \_ ). L'exemple de code suivant illustre une requête qui inclut une clause `Where`.  
  
 [!code-vb[VbVbalrIntroToLINQ#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#3)]  
  
 Autre clause de requête performante, la clause `Select` vous permet de retourner uniquement des champs sélectionnés de la source de données. Les requêtes LINQ retournent des collections énumérables d'objets fortement typés. Une requête peut retourner une collection de types anonymes ou nommés. Vous pouvez utiliser la clause `Select` pour retourner uniquement un champ de la source de données. Dans ce cas, le type de la collection retournée est le type de ce champ unique. Vous pouvez également utiliser la clause `Select` pour retourner plusieurs champs de la source de données. Dans ce cas, le type de la collection retournée est un nouveau type anonyme. Vous pouvez également faire correspondre les champs retournés par la requête aux champs d'un type nommé spécifié. L’exemple de code suivant affiche une expression de requête qui retourne une collection de types anonymes dont les membres sont remplis des données des champs sélectionnés de la source de données.  
  
 [!code-vb[VbVbalrIntroToLINQ#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#4)]  
  
 Les requêtes LINQ peuvent également être utilisées pour combiner plusieurs sources de données et retourner un résultat unique. Cette opération peut être effectuée à l'aide d'une ou plusieurs clauses `From` ou en utilisant les clauses de requête `Join` ou `Group Join`. L'exemple de code suivant illustre une expression de requête qui combine des données de client et de commande et retourne une collection de types anonymes contenant ces deux types de données.  
  
 [!code-vb[VbVbalrIntroToLINQ#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#5)]  
  
 Vous pouvez utiliser la clause `Group Join` pour créer un résultat de requête hiérarchique contenant une collection d'objets customer. Chaque objet customer possède une propriété contenant une collection de toutes les commandes de ce client. L'exemple de code suivant affiche une expression de requête qui combine des données client/commande sous forme de résultat hiérarchique et retourne une collection de types anonymes. La requête retourne un type qui inclut une propriété `CustomerOrders` contenant une collection de données de commande pour le client. Il inclut également une propriété `OrderTotal` qui contient la somme des totaux pour toutes les commandes de ce client. (Cette requête est équivalente à une JOINTURE EXTERNE GAUCHE.)  
  
 [!code-vb[VbVbalrIntroToLINQ#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#6)]  
  
 Il existe plusieurs opérateurs de requête LINQ supplémentaires qui vous permettent de créer des expressions de requête puissantes. La section suivante de cette rubrique présente les différentes clauses de requête que vous pouvez inclure dans une expression de requête. Pour plus d’informations sur Visual Basic clauses de requête, consultez [requêtes](../../../language-reference/queries/index.md).  
  
## <a name="visual-basic-linq-query-operators"></a>Visual Basic opérateurs de requête LINQ  

Les classes de l'espace de noms <xref:System.Linq> et des autres espaces de noms qui prennent en charge les requêtes LINQ incluent des méthodes que vous pouvez appeler pour créer et affiner les requêtes en fonction des besoins de votre application. Visual Basic comprend des mots clés pour les clauses de requête communes suivantes. Pour plus d’informations sur Visual Basic clauses de requête, consultez [requêtes](../../../language-reference/queries/index.md).

### <a name="from-clause"></a>Clause From

Une [ `From` clause](../../../language-reference/queries/from-clause.md) ou une `Aggregate` clause est nécessaire pour commencer une requête. Une clause `From` spécifie une collection de sources et une variable d'itération pour une requête. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#7)]

### <a name="select-clause"></a>Select (clause)

Optionnel. Une [ `Select` clause](../../../language-reference/queries/select-clause.md) déclare un ensemble de variables d’itération pour une requête. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#8)]

Si une clause `Select` n'est pas spécifiée, les variables d'itération de la requête se composent des variables d'itération spécifiées par la clause `From` ou `Aggregate`.

### <a name="where-clause"></a>Clause Where

Optionnel. Une [ `Where` clause](../../../language-reference/queries/where-clause.md) spécifie une condition de filtrage pour une requête. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#9)]

### <a name="order-by-clause"></a>Order By (clause)

Optionnel. Une [ `Order By` clause](../../../language-reference/queries/order-by-clause.md) spécifie l’ordre de tri des colonnes dans une requête. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#10)]

### <a name="join-clause"></a>Join (clause)

Optionnel. Une [ `Join` clause](../../../language-reference/queries/join-clause.md) combine deux collections en une collection unique. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#11)]

### <a name="group-by-clause"></a>Group By (clause)

Optionnel. Une [ `Group By` clause](../../../language-reference/queries/group-by-clause.md) regroupe les éléments d’un résultat de requête. Elle peut être utilisée pour appliquer des fonctions d’agrégation à chaque groupe. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#12)]

### <a name="group-join-clause"></a>Group Join (clause)

Optionnel. Une [ `Group Join` clause](../../../language-reference/queries/group-join-clause.md) combine deux collections en une collection hiérarchique unique. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#13)]

### <a name="aggregate-clause"></a>Aggregate (clause)

Une [ `Aggregate` clause](../../../language-reference/queries/aggregate-clause.md) ou une `From` clause est nécessaire pour commencer une requête. Une clause `Aggregate` applique une ou plusieurs fonctions d’agrégation à une collection. Par exemple, vous pouvez utiliser la `Aggregate` clause pour calculer une somme pour tous les éléments retournés par une requête, comme l’illustre l’exemple suivant.

 [!code-vb[VbVbalrIntroToLINQ#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#14)]

Vous pouvez également utiliser la clause `Aggregate` pour modifier une requête. Par exemple, vous pouvez utiliser la clause `Aggregate` pour effectuer un calcul sur une collection de requêtes connexe. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#15)]

### <a name="let-clause"></a>Let (clause)

Optionnel. Une [ `Let` clause](../../../language-reference/queries/let-clause.md) calcule une valeur et l’assigne à une nouvelle variable dans la requête. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#16)]

### <a name="distinct-clause"></a>Distinct (clause)

Optionnel. Une `Distinct` clause restreint les valeurs de la variable d’itération actuelle pour éliminer les valeurs en double dans les résultats de la requête. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#17)]

### <a name="skip-clause"></a>Skip (clause)

Optionnel. Une [ `Skip` clause](../../../language-reference/queries/skip-clause.md) ignore un nombre spécifié d’éléments dans une collection, puis retourne les éléments restants. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#18)]

### <a name="skip-while-clause"></a>SkipWhile (clause)

Optionnel. Une [ `Skip While` clause](../../../language-reference/queries/skip-while-clause.md) ignore les éléments d’une collection tant qu’une condition spécifiée a `true` la valeur, puis retourne les éléments restants. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#19)]

### <a name="take-clause"></a>Take (clause)

Optionnel. Une [ `Take` clause](../../../language-reference/queries/take-clause.md) retourne un nombre spécifié d’éléments contigus à partir du début d’une collection. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#20)]

### <a name="take-while-clause"></a>Take While (clause)

Optionnel. Une [ `Take While` clause](../../../language-reference/queries/take-while-clause.md) comprend des éléments dans une collection tant qu’une condition spécifiée a `true` la valeur et ignore les éléments restants. Par exemple :

 [!code-vb[VbVbalrIntroToLINQ#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#21)]
  
## <a name="use-additional-linq-query-features"></a>Utiliser des fonctionnalités de requête LINQ supplémentaires  
  
Vous pouvez utiliser des fonctionnalités de requête LINQ supplémentaires en appelant des membres des types énumérables et requêtables fournis par LINQ. Vous pouvez utiliser ces fonctions supplémentaires en appelant un opérateur de requête particulier sur le résultat d'une expression de requête. Par exemple, l’exemple suivant utilise la <xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType> méthode pour combiner les résultats de deux requêtes en un seul résultat de requête. Il utilise la méthode <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> pour retourner le résultat de la requête sous forme de liste générique.
  
 [!code-vb[VbVbalrIntroToLINQ#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#22)]  
  
 Pour plus d’informations sur les fonctionnalités LINQ supplémentaires, consultez [vue d’ensemble des opérateurs de requête standard](../../concepts/linq/standard-query-operators-overview.md).  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>Se connecter à une base de données à l’aide de LINQ to SQL  

 Dans Visual Basic, vous identifiez les objets de base de données SQL Server, tels que les tables, les vues et les procédures stockées, auxquels vous souhaitez accéder à l’aide d’un fichier de LINQ to SQL. Un fichier LINQ to SQL possède une extension .dbml.  
  
 Lorsque vous disposez d’une connexion valide à une base de données SQL Server, vous pouvez ajouter un modèle d’élément de **Classes LINQ to SQL** à votre projet. Le Concepteur Objet Relationnel (Concepteur O/R) s'affiche alors. Le Concepteur O/R vous permet de faire glisser les éléments auxquels vous souhaitez accéder dans votre code à partir de la **Explorateur de serveurs** / **Explorateur de base de données** sur l’aire du concepteur. Le fichier LINQ to SQL ajoute un objet <xref:System.Data.Linq.DataContext> à votre projet. Cet objet inclut des propriétés et des collections pour les tables et vues auxquelles vous souhaitez accéder, et aux méthodes des procédures stockées que vous souhaitez appeler. Après avoir enregistré vos modifications dans le fichier LINQ to SQL (.dbml), vous pouvez accéder à ces objets dans votre code en référençant l'objet <xref:System.Data.Linq.DataContext> défini par le Concepteur O/R. L'objet <xref:System.Data.Linq.DataContext> de votre projet est nommé d'après le nom de votre fichier LINQ to SQL. Par exemple, un fichier LINQ to SQL nommé Northwind.dbml créera un objet <xref:System.Data.Linq.DataContext> nommé `NorthwindDataContext`.  
  
 Pour obtenir des exemples d’instructions pas à pas, consultez [Comment : interroger une base de données](how-to-query-a-database-by-using-linq.md) et [Comment : appeler une procédure stockée](how-to-call-a-stored-procedure-by-using-linq.md).  
  
## <a name="visual-basic-features-that-support-linq"></a>Fonctionnalités Visual Basic qui prennent en charge LINQ  

 Visual Basic comprend d’autres fonctionnalités notables qui facilitent l’utilisation de LINQ et réduisent la quantité de code que vous devez écrire pour effectuer des requêtes LINQ. Elles sont associées aux limitations suivantes :  
  
- Les **types anonymes**, qui vous permettent de créer un nouveau type basé sur un résultat de requête.  
  
- Les **variables implicitement typées**, qui vous permettent de différer la spécification d’un type et de laisser le compilateur déduire le type en fonction du résultat de la requête.  
  
- Les **méthodes d’extension**, qui vous permettent d’étendre un type existant avec vos propres méthodes sans modifier le type lui-même.  
  
 Pour plus d’informations, consultez [Visual Basic fonctionnalités qui prennent en charge LINQ](../../concepts/linq/features-that-support-linq.md).  
  
## <a name="deferred-and-immediate-query-execution"></a>Exécution de requête différée et immédiate

 L'exécution d'une requête est distincte de sa création. Après avoir créé une requête, son exécution est déclenchée par un mécanisme distinct. Une requête peut être exécutée dès qu’elle est définie (*exécution immédiate*), ou la définition peut être stockée et la requête peut être exécutée ultérieurement (*exécution différée*).  
  
 Par défaut, quand vous créez une requête, cette dernière ne s'exécute pas immédiatement. À la place, la définition de la requête est stockée dans la variable utilisée pour référencer le résultat de la requête. Quand vous accédez à la variable de résultat de la requête ultérieurement dans le code, par exemple, dans une boucle `For…Next`, la requête est exécutée. Ce processus est appelé « *exécution différée*».  
  
 Les requêtes peuvent également être exécutées quand elles sont définies, ce qui est appelé *exécution immédiate*. Vous pouvez déclencher l'exécution immédiate en appliquant une méthode qui requiert l'accès aux éléments individuels du résultat de la requête. L'inclusion d'une fonction d'agrégation, telle que `Count`, `Sum`, `Average`, `Min` ou `Max` peut engendrer un tel résultat. Pour plus d’informations sur les fonctions d’agrégation, consultez [Aggregate, clause](../../../language-reference/queries/aggregate-clause.md).  
  
 L'utilisation de la méthode `ToList` ou `ToArray` force également l'exécution immédiate. Cela peut être utile quand vous souhaitez exécuter immédiatement la requête et mettre en cache les résultats. Pour plus d’informations sur ces méthodes, consultez [conversion des types de données](../../concepts/linq/converting-data-types.md).  
  
 Pour plus d’informations sur l’exécution des requêtes, consultez [écriture de votre première requête LINQ](../../concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="xml-in-visual-basic"></a>XML en Visual Basic  

 Les fonctionnalités XML de Visual Basic incluent des littéraux XML et des propriétés d’axe XML, qui vous permettent de créer, d’accéder, d’interroger et de modifier facilement du code XML dans votre code. Les littéraux XML vous permettent d'écrire directement en XML dans votre code. Le compilateur Visual Basic traite le XML comme un objet de donnée de première classe.  
  
 L'exemple de code suivant montre comment créer un élément XML, accéder à ses sous-éléments et attributs, et interroger son contenu à l'aide de LINQ.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Pour plus d’informations, consultez [XML](../xml/index.md).  
  
## <a name="related-resources"></a>Ressources associées  
  
|Rubrique|Description|  
|---|---|  
|[XML](../xml/index.md)|Décrit les fonctionnalités XML de Visual Basic qui peuvent être interrogées et qui vous permettent d’inclure du XML en tant qu’objets de données de première classe dans votre code Visual Basic.|  
|[Requêtes](../../../language-reference/queries/index.md)|Fournit des informations de référence sur les clauses de requête qui sont disponibles dans Visual Basic.|  
|[LINQ (Language Integrated Query)](../../concepts/linq/index.md)|Inclut des informations générales, un guide de programmation et des exemples de requêtes LINQ.|  
|[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)|Inclut des informations générales, un guide de programmation et des exemples de LINQ to SQL.|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|Inclut des informations générales, un guide de programmation et des exemples de LINQ to Objects.|  
|[LINQ to ADO.NET (page de portail)](../../concepts/linq/linq-to-adonet-portal-page.md)|Contient des liens vers des informations générales, des conseils de programmation et des exemples pour LINQ to ADO.NET.|  
|[LINQ to XML](../../../../standard/linq/linq-xml-overview.md)|Inclut des informations générales, un guide de programmation et des exemples de LINQ to XML.|  
  
## <a name="how-to-and-walkthrough-topics"></a>Rubriques de procédures et procédures pas à pas

 [Guide pratique : interroger une base de données](how-to-query-a-database-by-using-linq.md)  
  
 [Guide pratique : appeler une procédure stockée](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [Guide pratique : modifier des données dans une base de données](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [Guide pratique : combiner des données avec des jointures](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [Guide pratique : trier les résultats d’une requête](how-to-sort-query-results-by-using-linq.md)  
  
 [Guide pratique : filtrer les résultats d’une requête](how-to-filter-query-results-by-using-linq.md)  
  
 [Guide pratique : compter, additionner ou faire la moyenne de données](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [Guide pratique : rechercher la valeur minimale ou maximale dans un résultat de requête](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
  
## <a name="featured-book-chapters"></a>Chapitres de livres proposés  

 [Chapitre 17 : LINQ](/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) en [programmation Visual Basic 2008](/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>Voir aussi

- [LINQ (Language Integrated Query)](../../concepts/linq/index.md)
- [Vue d’ensemble de LINQ to XML en Visual Basic](../xml/overview-of-linq-to-xml.md)
- [Vue d'ensemble de LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset-overview.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [LINQ to SQL Tools dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [DataContext, méthodes (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
