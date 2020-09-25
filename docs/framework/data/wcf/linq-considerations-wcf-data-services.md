---
title: Considérations sur LINQ (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 2523aac510516fdf19087425b10ab3f2296eb726
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194339"
---
# <a name="linq-considerations-wcf-data-services"></a>Considérations sur LINQ (WCF Data Services)

Cette rubrique fournit des informations sur la façon dont les requêtes LINQ sont composées et exécutées lorsque vous utilisez le client WCF Data Services et les limitations de l’utilisation de LINQ pour interroger un service de données qui implémente le Open Data Protocol (OData). Pour plus d’informations sur la composition et l’exécution de requêtes sur un service de données basé sur OData, consultez [interrogation du service de données](querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>Composition de requêtes LINQ  

 LINQ vous permet de composer des requêtes pour interroger une collection d'objets qui implémente <xref:System.Collections.Generic.IEnumerable%601>. La boîte de dialogue **Ajouter une référence de service** dans Visual Studio et l’outil DataSvcUtil.exe permettent de générer une représentation d’un service OData en tant que classe de conteneur d’entités qui hérite de, ainsi que des <xref:System.Data.Services.Client.DataServiceContext> objets qui représentent les entités retournées dans les flux. Ces outils génèrent également des propriétés sur la classe de conteneur d’entités des collections qui sont exposées en tant que flux par le service. Chacune de ces propriétés de classe qui encapsule le service de données retourne un <xref:System.Data.Services.Client.DataServiceQuery%601>. Étant donné que la classe <xref:System.Data.Services.Client.DataServiceQuery%601> implémente l'interface <xref:System.Linq.IQueryable%601> définie par LINQ, vous pouvez composer une requête LINQ sur des flux exposés par le service de données, qui sont convertis par la bibliothèque cliente en un URI de demande de requête envoyé au service de données lors de l'exécution.  
  
> [!IMPORTANT]
> L’ensemble de requêtes exprimables dans la syntaxe LINQ est plus large que ceux activés dans la syntaxe d’URI utilisée par les services de données OData. <xref:System.NotSupportedException> est levée lorsque la requête ne peut pas être mappée à un URI dans le service de données cible. Pour plus d’informations, consultez les [Méthodes LINQ non prises en charge](linq-considerations-wcf-data-services.md#unsupportedMethods) dans cette rubrique.  
  
 L'exemple suivant est une requête LINQ qui retourne des `Orders` ayant un coût de fret supérieur à $30 et trie les résultats par date d'expédition, en commençant par la dernière :  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]
  
 Cette requête LINQ est traduite dans l’URI de requête suivant qui est exécuté sur le service de données de [démarrage rapide](quickstart-wcf-data-services.md) basé sur Northwind :  
  
```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 Pour plus d’informations générales sur LINQ, consultez [LINQ (Language-Integrated Query)-C#](../../../csharp/programming-guide/concepts/linq/index.md) ou [LINQ (Language-Integrated query)-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).  
  
 LINQ vous permet de composer des requêtes en utilisant aussi bien la syntaxe déclarative spécifique au langage, illustrée dans l'exemple précédent, qu'un ensemble de méthodes de requête qu'on nomme opérateurs de requête standard. Une requête équivalente à l'exemple précédent peut être composée en utilisant uniquement la syntaxe reposant sur une méthode, comme illustré dans l'exemple suivant :  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpressionspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpressionspecific)]
  
 Le client WCF Data Services est en mesure de traduire les deux types de requêtes composées en un URI de requête, et vous pouvez étendre une requête LINQ en ajoutant des méthodes de requête à une expression de requête. Lorsque vous composez des requêtes LINQ en ajoutant une syntaxe de méthode à une expression de requête ou un <xref:System.Data.Services.Client.DataServiceQuery%601>, les opérations sont ajoutées à l'URI de la requête dans l'ordre suivant lequel les méthodes sont appelées. Cela équivaut à appeler la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> pour ajouter chaque option de requête à l'URI de requête.  
  
## <a name="executing-linq-queries"></a>Exécution de requêtes LINQ  

 Lorsqu'elles sont ajoutées à une requête, certaines méthodes de requête LINQ, comme <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> ou <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, provoquent son exécution. L’exécution de la requête est également déclenchée lorsque les résultats sont énumérés implicitement, comme lors d’une boucle `foreach` ou lorsque la requête est attribuée à une collection `List`. Pour plus d’informations, consultez [interrogation du service de données](querying-the-data-service-wcf-data-services.md).  
  
 Le client exécute une requête LINQ en deux parties. Lorsque cela est possible, les expressions LINQ dans une requête sont d'abord évaluées sur le client, puis une requête basée surl' URI est générée et envoyée au service de données pour être évaluée par rapport aux données dans le service. Pour plus d’informations, consultez la section relative à l' [exécution du client et du serveur](querying-the-data-service-wcf-data-services.md#executingQueries) dans [interrogation du service de données](querying-the-data-service-wcf-data-services.md).  
  
 Lorsqu’une requête LINQ ne peut pas être traduite dans un URI de requête conforme à OData, une exception est levée lors d’une tentative d’exécution. Pour plus d’informations, consultez [interrogation du service de données](querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>Exemples de requêtes LINQ  

 Les exemples des sections suivantes illustrent les types de requêtes LINQ qui peuvent être exécutés sur un service OData.  
  
<a name="filtering"></a>

### <a name="filtering"></a>Filtrage  

 Les exemples de requêtes LINQ de cette section filtrent les données dans le flux retourné par le service.  
  
 Les exemples suivants illustrent des requêtes équivalentes qui filtrent les entités `Orders` retournées afin que seules les commandes ayant un coût de fret supérieur à $30 soient retournées :  
  
- Utilisation de la syntaxe de requête LINQ :  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwhereclausespecific)]
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwhereclausespecific)]
  
- Utilisation des méthodes de requête LINQ :  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwheremethodspecific)]
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwheremethodspecific)]
  
- Option `$filter` de la chaîne de requête d'URI :  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitquerywheremethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitquerywheremethodspecific)]
  
 Tous les exemples précédents sont convertis vers l'URI de requête : `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.  
  
<a name="sorting"></a>

### <a name="sorting"></a>Tri  

 Les exemples suivants illustrent des requêtes équivalentes qui trient les données retournées par nom de société, code postal et ordre descendant :  
  
- Utilisation de la syntaxe de requête LINQ :  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbyclausespecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbyclausespecific)]
  
- Utilisation des méthodes de requête LINQ :  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbymethodspecific)]
  
- Option `$orderby` de la chaîne de requête d'URI :  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryorderbymethodspecific)]
  
 Tous les exemples précédents sont convertis vers l'URI de requête : `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>

### <a name="projection"></a>Projection  

 Les exemples suivants illustrent des requêtes équivalentes qui projettent les données retournées dans le type plus restreint `CustomerAddress`.  
  
- Utilisation de la syntaxe de requête LINQ :  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectclausespecific)]
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectclausespecific)]
  
- Utilisation des méthodes de requête LINQ :  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectmethodspecific)]

> [!NOTE]
> L'option de requête `$select` ne peut pas être ajoutée à un URI de requête à l'aide de la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>. Nous vous recommandons d'utiliser la méthode LINQ <xref:System.Linq.Enumerable.Select%2A> pour que le client génère l'option de requête `$select` dans l'URI de requête.  
  
 Les deux exemples précédents sont traduits dans l'URI de requête : `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.  
  
<a name="paging"></a>

### <a name="client-paging"></a>Pagination du client  

 Les exemples suivants illustrent des requêtes équivalentes qui génèrent une page d'entités de commande triées incluant 25 commandes, en ignorant les 50 premières commandes :  
  
- Application des méthodes de requête à une requête LINQ :  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqskiptakemethodspecific)]
  
- Options de chaîne de requête d'URI `$skip` et `$top` :  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryskiptakemethodspecific)]
  
 Les deux exemples précédents sont traduits dans l'URI de requête : `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.  
  
<a name="expand"></a>

### <a name="expand"></a>Développez  

 Lorsque vous interrogez un service de données OData, vous pouvez demander que les entités associées à l’entité ciblée par la requête soient incluses dans le flux retourné. La méthode <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> est appelée sur la <xref:System.Data.Services.Client.DataServiceQuery%601> pour l'ensemble d'entités ciblé par la requête LINQ, avec le nom de l'ensemble d'entités relatif fourni sous la forme de paramètre `path`. Pour plus d’informations, consultez chargement d’un [contenu différé](loading-deferred-content-wcf-data-services.md).  
  
 Les exemples suivants illustrent les différentes façons d'utiliser la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> dans une requête :  
  
- Dans la syntaxe de requête LINQ :  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandspecific)]  
  
- Avec les méthodes de requête LINQ :  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandmethodspecific)]

 Les deux exemples précédents sont traduits dans l'URI de requête : `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.  
  
<a name="unsupportedMethods"></a>

## <a name="unsupported-linq-methods"></a>Méthodes LINQ non prises en charge  

 Le tableau suivant contient les classes des méthodes LINQ qui ne sont pas prises en charge et ne peuvent pas être incluses dans une requête exécutée sur un service OData :  
  
|Type d’opération|Méthode non prise en charge|  
|--------------------|------------------------|  
|Opérateurs de jeu|Aucun opérateur de jeu n'est pris en charge sur un <xref:System.Data.Services.Client.DataServiceQuery%601>, impliquant ce qui suit :<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Opérations de tri|Les opérateur de tri suivants, qui nécessitent un <xref:System.Collections.Generic.IComparer%601>, ne sont pas pris en charge sur un <xref:System.Data.Services.Client.DataServiceQuery%601> :<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Opérateurs de projection et de filtrage|Les opérateurs de projection et de filtrage suivants, qui acceptent un argument de position, ne sont pas pris en charge sur <xref:System.Data.Services.Client.DataServiceQuery%601> :<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Opérateurs de groupement|Aucun opérateur de groupement n'est pris en charge sur un <xref:System.Data.Services.Client.DataServiceQuery%601>, impliquant ce qui suit :<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Les opérations de groupement doivent être exécutées sur le client.|  
|Opérateurs d'agrégation|Aucune opération d'agrégation n'est prise en charge sur un <xref:System.Data.Services.Client.DataServiceQuery%601>, impliquant ce qui suit :<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Les opérations d'agrégation doivent soit être exécutées sur le client, soit être encapsulées par une opération de service.|  
|Opérateurs de pagination|Les opérateur de pagination suivants ne sont pas pris en charge sur un <xref:System.Data.Services.Client.DataServiceQuery%601> :<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A><br/><br/>**Remarque :**  Les opérateurs de pagination qui sont exécutés sur une séquence vide retournent la valeur null.|  
|Autres opérateurs|Les opérateurs suivants ne sont pas non plus pris en charge sur un <xref:System.Data.Services.Client.DataServiceQuery%601> :<br /><br /> - <xref:System.Linq.Enumerable.Empty%2A><br />- <xref:System.Linq.Enumerable.Range%2A><br />- <xref:System.Linq.Enumerable.Repeat%2A><br />- <xref:System.Linq.Enumerable.ToDictionary%2A><br />- <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>

## <a name="supported-expression-functions"></a>Fonctions d'expression prises en charge  

 Les méthodes et propriétés CLR (Common-Language Runtime) suivantes sont prises en charge, car elles peuvent être traduites dans une expression de requête pour être incluses dans l’URI de la demande à un service OData :  
  
|Membre <xref:System.String>|Fonction OData prise en charge|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<xref:System.DateTime> Membre<sup>1</sup>|Fonction OData prise en charge|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup> Les propriétés de date et d’heure équivalentes de <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType> et de la <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> méthode dans Visual Basic sont également prises en charge.  
  
|Membre <xref:System.Math>|Fonction OData prise en charge|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|Membre <xref:System.Linq.Expressions.Expression>|Fonction OData prise en charge|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 Le client peut également être en mesure d'évaluer les fonctions CLR supplémentaires sur le client. Une exception <xref:System.NotSupportedException> est levée pour toute expression qui ne peut pas être évaluée sur le client ou traduite dans un URI de requête valide pour l'évaluation sur le serveur.  
  
## <a name="see-also"></a>Voir aussi

- [Interrogation du service de données](querying-the-data-service-wcf-data-services.md)
- [Projections de requêtes](query-projections-wcf-data-services.md)
- [Matérialisation d'objet](object-materialization-wcf-data-services.md)
- [OData : Conventions d'URI](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)
