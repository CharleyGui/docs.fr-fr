---
title: Écriture de votre première requête LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 5c83d888f65ce5c216327e94c5d4d1267fb93c29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952008"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Écriture de votre première requête LINQ (Visual Basic)
Une *requête* est une expression qui récupère des données d’une source de données. Les requêtes sont exprimées dans un langage de requête dédié. Au fil du temps, des langages différents ont été développés pour différents types de sources de données, par exemple, SQL pour les bases de données relationnelles et XQuery pour XML. Cela oblige le développeur d’applications à apprendre un nouveau langage de requête pour chaque type de source de données ou format de données pris en charge.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]simplifie la situation en offrant un modèle cohérent pour l’utilisation des données dans différents types de sources et de formats de données. Dans une requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], vous travaillez toujours avec des objets. Vous utilisez les mêmes modèles de codage de base pour interroger et transformer des données dans des documents XML, des bases de données SQL, des jeux de données ADO.net et des entités, des collections [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] .NET Framework et toute autre source ou format pour laquelle un fournisseur est disponible. Ce document décrit les trois phases de création et d’utilisation des requêtes [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] de base.  
  
## <a name="three-stages-of-a-query-operation"></a>Trois étapes d’une opération de requête  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]les opérations de requête se composent de trois actions:  
  
1. Obtenez la ou les sources de données.  
  
2. Création de la requête  
  
3. Exécution de la requête  
  
 Dans [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], l’exécution d’une requête est distincte de la création de la requête. Vous ne récupérez pas de données simplement en créant une requête. Ce point est abordé en détail plus loin dans cette rubrique.  
  
 L’exemple suivant illustre les trois parties d’une opération de requête. L’exemple utilise un tableau d’entiers comme source de données pratique à des fins de démonstration. Toutefois, les mêmes concepts s’appliquent également à d’autres sources de données.  
  
> [!NOTE]
> Sur la [page compiler, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), vérifiez que **Option Infer** a la valeur **on**.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Sortie :  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Source de données  
 Étant donné que la source de données dans l’exemple précédent est un tableau, elle prend en <xref:System.Collections.Generic.IEnumerable%601> charge implicitement l’interface générique. C’est ce fait qui vous permet d’utiliser un tableau comme source de données pour une [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] requête. Les types qui prennent en charge <xref:System.Collections.Generic.IEnumerable%601> ou une interface dérivée, comme l’interface générique <xref:System.Linq.IQueryable%601>, sont appelés des *types requêtables*.  
  
 En tant que type implicitement interrogeable, le tableau ne nécessite aucune modification ni traitement spécial pour servir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] de source de données. Il en va de même pour tout type de collection <xref:System.Collections.Generic.IEnumerable%601>qui prend en charge <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>y compris les classes génériques,, et autres dans la bibliothèque de classes .NET Framework.  
  
 Si les données sources ne sont pas encore <xref:System.Collections.Generic.IEnumerable%601>implémentées [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] , un fournisseur est nécessaire pour implémenter les fonctionnalités des *opérateurs de requête standard* pour cette source de données. Par exemple, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gère le travail de chargement d’un document XML dans un <xref:System.Xml.Linq.XElement> type interrogeable, comme indiqué dans l’exemple suivant. Pour plus d’informations sur les opérateurs de requête standard, consultez [vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 Avec [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], vous créez tout d’abord un mappage objet/relationnel au moment du design, soit manuellement, soit à l’aide des [outils de LINQ to SQL dans](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) Visual Studio dans Visual Studio. Vous écrivez vos requêtes pour des objets. Ensuite, au moment de l’exécution, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] gère la communication avec la base de données. Dans l’exemple suivant, `customers` représente une table spécifique dans la base de données <xref:System.Data.Linq.Table%601> et prend <xref:System.Linq.IQueryable%601>en charge le générique.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Pour plus d’informations sur la création de types de sources de données spécifiques, consultez la documentation relative aux différents fournisseurs [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. (Pour obtenir la liste de ces fournisseurs, consultez [LINQ (Language-Integrated Query)](../../../../visual-basic/programming-guide/concepts/linq/index.md).) La règle de base est simple: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] une source de données est un objet qui prend <xref:System.Collections.Generic.IEnumerable%601> en charge l’interface générique ou une interface qui hérite de celui-ci.  
  
> [!NOTE]
> Les types tels <xref:System.Collections.ArrayList> que qui prennent en charge l' <xref:System.Collections.IEnumerable> interface non générique peuvent également être [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] utilisés comme sources de données. Pour obtenir un exemple qui utilise <xref:System.Collections.ArrayList>un, [consultez Procédure: Interrogez une ArrayList avec LINQ (Visual Basic](how-to-query-an-arraylist-with-linq.md)).  
  
## <a name="the-query"></a>La requête  
 Dans la requête, vous spécifiez les informations que vous souhaitez récupérer à partir de la ou des sources de données. Vous avez également la possibilité de spécifier la façon dont ces informations doivent être triées, regroupées ou structurées avant d’être retournées. Pour permettre la création de requêtes, Visual Basic a incorporé une nouvelle syntaxe de requête dans le langage.  
  
 Lorsqu’elle est exécutée, la requête de l’exemple suivant retourne tous les nombres pairs d’un tableau d' `numbers`entiers,.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 L’expression de requête contient trois clauses `From`: `Where`, et `Select`. La fonction et l’objectif spécifiques de chaque clause d’expression de requête sont décrits dans [opérations de requête de base (Visual Basic)](basic-query-operations.md). Pour plus d’informations, consultez [requêtes](../../../../visual-basic/language-reference/queries/index.md). Notez que dans [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], une définition de requête est souvent stockée dans une variable et exécutée ultérieurement. La variable de requête, telle `evensQuery` que dans l’exemple précédent, doit être un type interrogeable. Le type de `evensQuery` est `IEnumerable(Of Integer)`, assigné par le compilateur à l’aide de l’inférence de type local.  
  
 Il est important de se souvenir que la variable de requête elle-même n’effectue aucune action et ne retourne aucune donnée. Il stocke uniquement la définition de la requête. Dans l’exemple précédent, il s’agit `For Each` de la boucle qui exécute la requête.  
  
## <a name="query-execution"></a>Exécution de la requête  
 L’exécution de la requête est distincte de la création de la requête. La création de requête définit la requête, mais l’exécution est déclenchée par un mécanisme différent. Une requête peut être exécutée dès qu’elle est définie (*exécution immédiate*), ou la définition peut être stockée et la requête peut être exécutée ultérieurement (*exécution différée*).  
  
### <a name="deferred-execution"></a>Exécution différée  
 Une requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] classique ressemble à celle de l’exemple précédent, dans laquelle `evensQuery` est défini. Elle crée la requête, mais ne l’exécute pas immédiatement. Au lieu de cela, la définition de la requête est `evensQuery`stockée dans la variable de requête. Vous exécutez la requête ultérieurement, en général à l' `For Each` aide d’une boucle, qui retourne une séquence de valeurs, ou en appliquant un opérateur de `Count` requête `Max`standard, tel que ou. Ce processus est appelé « *exécution différée*».  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 Pour une séquence de valeurs, vous accédez aux données récupérées à l’aide de la variable `For Each` d’itération`number` dans la boucle (dans l’exemple précédent). Étant donné que la variable `evensQuery`de requête,, contient la définition de la requête plutôt que les résultats de la requête, vous pouvez exécuter une requête aussi souvent que vous le souhaitez en utilisant plusieurs fois la variable de requête. Par exemple, vous pouvez avoir une base de données dans votre application en cours de mise à jour en continu par une application distincte. Une fois que vous avez créé une requête qui extrait les données de cette base de données, `For Each` vous pouvez utiliser une boucle pour exécuter la requête à plusieurs reprises, en extrayant les données les plus récentes à chaque fois.  
  
 L’exemple suivant montre comment fonctionne l’exécution différée. Une `evensQuery2` fois que est défini et exécuté `For Each` avec une boucle, comme dans les exemples précédents, certains éléments de la `numbers` source de données sont modifiés. Ensuite, une `For Each` deuxième boucle `evensQuery2` s’exécute à nouveau. Les résultats sont différents la deuxième fois, car la `For Each` boucle exécute à nouveau la requête, en utilisant les nouvelles valeurs `numbers`de.  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Sortie :  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Exécution immédiate  
 Dans l’exécution différée des requêtes, la définition de la requête est stockée dans une variable de requête pour une exécution ultérieure. En cours d’exécution, la requête est exécutée au moment de sa définition. L’exécution est déclenchée lorsque vous appliquez une méthode qui requiert l’accès à des éléments individuels du résultat de la requête. L’exécution immédiate est souvent forcée à l’aide de l’un des opérateurs de requête standard qui retournent des valeurs uniques. Les exemples `Count`sont `Max` ,`Average`, et `First`. Ces opérateurs de requête standard exécutent la requête dès qu’ils sont appliqués pour calculer et retourner un résultat Singleton. Pour plus d’informations sur les opérateurs de requête standard qui retournent des valeurs uniques, consultez opérations d' [agrégation](aggregation-operations.md), [opérations d’élément](element-operations.md)et [opérations de quantificateur](quantifier-operations.md).  
  
 La requête suivante retourne le nombre de nombres pairs dans un tableau d’entiers. La définition de la requête n’est pas `numEvens` enregistrée et est `Integer`un simple.  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 Vous pouvez obtenir le même résultat à l’aide `Aggregate` de la méthode.  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 Vous pouvez également forcer l’exécution d’une requête en appelant `ToList` la `ToArray` méthode ou sur une requête (immédiate) ou une variable de requête (différée), comme indiqué dans le code suivant.  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 Dans les exemples précédents, `evensQuery3` est une variable de requête, `evensList` mais est une liste `evensArray` et est un tableau.  
  
 L' `ToList` utilisation `ToArray` de ou pour forcer l’exécution immédiate est particulièrement utile dans les scénarios où vous souhaitez exécuter immédiatement la requête et mettre en cache les résultats dans un objet de collection unique. Pour plus d’informations sur ces méthodes, consultez [conversion des types de données](converting-data-types.md).  
  
 Vous pouvez également faire en sorte qu’une requête soit exécutée `IEnumerable` à l’aide d' <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> une méthode telle que la méthode.  
  
## <a name="see-also"></a>Voir aussi

- [Bien démarrer avec LINQ en Visual Basic](getting-started-with-linq.md)
- [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md)
- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Requêtes](../../../../visual-basic/language-reference/queries/index.md)
