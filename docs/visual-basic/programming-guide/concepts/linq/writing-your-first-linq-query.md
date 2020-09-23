---
title: Écriture de votre première requête LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: c7d0595b991bdad6ef05b567f95ead8c7fccdbc2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077278"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Écriture de votre première requête LINQ (Visual Basic)

Une *requête* est une expression qui récupère des données à partir d’une source de données. Les requêtes sont exprimées dans un langage de requête dédié. Au fil du temps, des langages différents ont été développés pour différents types de sources de données, par exemple, SQL pour les bases de données relationnelles et XQuery pour XML. Cela oblige le développeur d’applications à apprendre un nouveau langage de requête pour chaque type de source de données ou format de données pris en charge.  
  
 LINQ (Language-Integrated Query) simplifie la situation en offrant un modèle cohérent pour l’utilisation des données dans différents types de sources et de formats de données. Dans une requête LINQ, vous travaillez toujours avec des objets. Vous utilisez les mêmes modèles de codage de base pour interroger et transformer des données dans des documents XML, des bases de données SQL, des jeux de données ADO.NET et des entités, des collections .NET Framework et toute autre source ou format pour lequel un fournisseur LINQ est disponible. Ce document décrit les trois phases de création et d’utilisation de requêtes LINQ de base.  
  
## <a name="three-stages-of-a-query-operation"></a>Trois étapes d’une opération de requête  

 Les opérations de requête LINQ consistent en trois actions :  
  
1. Obtenez la ou les sources de données.  
  
2. Création de la requête  
  
3. exécutez la requête.  
  
 Dans LINQ, l’exécution d’une requête est distincte de la création de la requête. Vous ne récupérez pas de données simplement en créant une requête. Ce point est abordé en détail plus loin dans cette rubrique.  
  
 L’exemple suivant illustre les trois parties d’une opération de requête. L’exemple utilise un tableau d’entiers comme source de données pratique à des fins de démonstration. Toutefois, les mêmes concepts s’appliquent également à d’autres sources de données.  
  
> [!NOTE]
> Sur la [page compiler, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), vérifiez que **Option Infer** a la valeur **on**.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Sortie :  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Source de données  

 Étant donné que la source de données dans l’exemple précédent est un tableau, elle prend en charge implicitement l' <xref:System.Collections.Generic.IEnumerable%601> interface générique. C’est ce fait qui vous permet d’utiliser un tableau comme source de données pour une requête LINQ. Les types qui prennent en charge <xref:System.Collections.Generic.IEnumerable%601> ou une interface dérivée, comme l’interface générique <xref:System.Linq.IQueryable%601>, sont appelés des *types requêtables*.  
  
 En tant que type implicitement interrogeable, le tableau ne nécessite aucune modification ni traitement spécial pour servir de source de données LINQ. Il en va de même pour tout type de collection qui prend en charge <xref:System.Collections.Generic.IEnumerable%601> , y compris les <xref:System.Collections.Generic.List%601> classes génériques, <xref:System.Collections.Generic.Dictionary%602> , et autres dans la bibliothèque de classes .NET Framework.  
  
 Si les données sources ne sont pas encore implémentées <xref:System.Collections.Generic.IEnumerable%601> , un fournisseur LINQ est nécessaire pour implémenter les fonctionnalités des *opérateurs de requête standard* pour cette source de données. Par exemple, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gère le travail de chargement d’un document XML dans un type interrogeable <xref:System.Xml.Linq.XElement> , comme indiqué dans l’exemple suivant. Pour plus d’informations sur les opérateurs de requête standard, consultez [vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 Avec [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] , vous créez tout d’abord un mappage objet/relationnel au moment du design, soit manuellement, soit à l’aide des [outils de LINQ to SQL dans](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) Visual Studio dans Visual Studio. Vous écrivez vos requêtes pour des objets. Ensuite, au moment de l’exécution, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] gère la communication avec la base de données. Dans l’exemple suivant, `customers` représente une table spécifique dans la base de données et <xref:System.Data.Linq.Table%601> prend en charge le générique <xref:System.Linq.IQueryable%601> .  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Pour plus d’informations sur la création de types spécifiques de sources de données, consultez la documentation relative aux différents fournisseurs LINQ. (Pour obtenir la liste de ces fournisseurs, consultez [LINQ (Language-Integrated Query)](index.md).) La règle de base est simple : une source de données LINQ est un objet qui prend en charge l' <xref:System.Collections.Generic.IEnumerable%601> interface générique ou une interface qui hérite de celui-ci.  
  
> [!NOTE]
> Les types tels que <xref:System.Collections.ArrayList> qui prennent en charge l' <xref:System.Collections.IEnumerable> interface non générique peuvent également être utilisés en tant que sources de données Linq. Pour obtenir un exemple qui utilise un <xref:System.Collections.ArrayList> , consultez [Comment : interroger un ARRAYLIST avec LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>La requête  

 Dans la requête, vous spécifiez les informations que vous souhaitez récupérer à partir de la ou des sources de données. Vous avez également la possibilité de spécifier la façon dont ces informations doivent être triées, regroupées ou structurées avant d’être retournées. Pour permettre la création de requêtes, Visual Basic a incorporé une nouvelle syntaxe de requête dans le langage.  
  
 Lorsqu’elle est exécutée, la requête de l’exemple suivant retourne tous les nombres pairs d’un tableau d’entiers, `numbers` .  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 L’expression de requête contient trois clauses : `From` , `Where` et `Select` . La fonction et l’objectif spécifiques de chaque clause d’expression de requête sont décrits dans [opérations de requête de base (Visual Basic)](basic-query-operations.md). Pour plus d’informations, consultez [requêtes](../../../language-reference/queries/index.md). Notez que dans LINQ, une définition de requête est souvent stockée dans une variable et exécutée ultérieurement. La variable de requête, telle que `evensQuery` dans l’exemple précédent, doit être un type interrogeable. Le type de `evensQuery` est `IEnumerable(Of Integer)` , assigné par le compilateur à l’aide de l’inférence de type local.  
  
 Il est important de se souvenir que la variable de requête elle-même n’effectue aucune action et ne retourne aucune donnée. Il stocke uniquement la définition de la requête. Dans l’exemple précédent, il s’agit de la `For Each` boucle qui exécute la requête.  
  
## <a name="query-execution"></a>Exécution des requêtes  

 L’exécution de la requête est distincte de la création de la requête. La création de requête définit la requête, mais l’exécution est déclenchée par un mécanisme différent. Une requête peut être exécutée dès qu’elle est définie (*exécution immédiate*), ou la définition peut être stockée et la requête peut être exécutée ultérieurement (*exécution différée*).  
  
### <a name="deferred-execution"></a>Exécution différée  

 Une requête LINQ classique ressemble à celle de l’exemple précédent, dans laquelle `evensQuery` est défini. Elle crée la requête, mais ne l’exécute pas immédiatement. Au lieu de cela, la définition de la requête est stockée dans la variable de requête `evensQuery` . Vous exécutez la requête ultérieurement, en général à l’aide d’une `For Each` boucle, qui retourne une séquence de valeurs, ou en appliquant un opérateur de requête standard, tel que `Count` ou `Max` . Ce processus est appelé « *exécution différée*».  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 Pour une séquence de valeurs, vous accédez aux données récupérées à l’aide de la variable d’itération dans la `For Each` boucle ( `number` dans l’exemple précédent). Étant donné que la variable de requête, `evensQuery` , contient la définition de la requête plutôt que les résultats de la requête, vous pouvez exécuter une requête aussi souvent que vous le souhaitez en utilisant plusieurs fois la variable de requête. Par exemple, vous pouvez avoir une base de données dans votre application en cours de mise à jour en continu par une application distincte. Une fois que vous avez créé une requête qui extrait les données de cette base de données, vous pouvez utiliser une `For Each` boucle pour exécuter la requête à plusieurs reprises, en extrayant les données les plus récentes à chaque fois.  
  
 L’exemple suivant montre comment fonctionne l’exécution différée. Une fois que `evensQuery2` est défini et exécuté avec une `For Each` boucle, comme dans les exemples précédents, certains éléments de la source de données `numbers` sont modifiés. Ensuite, une deuxième `For Each` boucle s’exécute `evensQuery2` à nouveau. Les résultats sont différents la deuxième fois, car la `For Each` boucle exécute à nouveau la requête, en utilisant les nouvelles valeurs de `numbers` .  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Sortie :  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Exécution immédiate  

 Dans l’exécution différée des requêtes, la définition de la requête est stockée dans une variable de requête pour une exécution ultérieure. En cours d’exécution, la requête est exécutée au moment de sa définition. L’exécution est déclenchée lorsque vous appliquez une méthode qui requiert l’accès à des éléments individuels du résultat de la requête. L’exécution immédiate est souvent forcée à l’aide de l’un des opérateurs de requête standard qui retournent des valeurs uniques. Les exemples sont `Count` ,, `Max` `Average` et `First` . Ces opérateurs de requête standard exécutent la requête dès qu’ils sont appliqués pour calculer et retourner un résultat Singleton. Pour plus d’informations sur les opérateurs de requête standard qui retournent des valeurs uniques, consultez opérations d' [agrégation](aggregation-operations.md), [opérations d’élément](element-operations.md)et [opérations de quantificateur](quantifier-operations.md).  
  
 La requête suivante retourne le nombre de nombres pairs dans un tableau d’entiers. La définition de la requête n’est pas enregistrée et `numEvens` est un simple `Integer` .  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 Vous pouvez obtenir le même résultat à l’aide de la `Aggregate` méthode.  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 Vous pouvez également forcer l’exécution d’une requête en appelant `ToList` la `ToArray` méthode ou sur une requête (immédiate) ou une variable de requête (différée), comme indiqué dans le code suivant.  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 Dans les exemples précédents, `evensQuery3` est une variable de requête, mais `evensList` est une liste et `evensArray` est un tableau.  
  
 L’utilisation de `ToList` ou `ToArray` pour forcer l’exécution immédiate est particulièrement utile dans les scénarios où vous souhaitez exécuter immédiatement la requête et mettre en cache les résultats dans un objet de collection unique. Pour plus d’informations sur ces méthodes, consultez [conversion des types de données](converting-data-types.md).  
  
 Vous pouvez également faire en sorte qu’une requête soit exécutée à l’aide d’une `IEnumerable` méthode telle que la <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> méthode.  
  
## <a name="see-also"></a>Voir aussi

- [Mise en route de LINQ dans Visual Basic](getting-started-with-linq.md)
- [Inférence de type local](../../language-features/variables/local-type-inference.md)
- [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md)
- [Introduction à LINQ en Visual Basic](../../language-features/linq/introduction-to-linq.md)
- [LINQ](../../language-features/linq/index.md)
- [Requêtes](../../../language-reference/queries/index.md)
