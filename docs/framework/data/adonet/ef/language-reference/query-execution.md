---
title: Exécution des requêtes
description: Découvrez les différentes méthodes d’exécution d’une requête LINQ to Entities, y compris l’exécution différée des requêtes, l’exécution immédiate des requêtes et le stockage de l’exécution.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
ms.openlocfilehash: e776df6d35b6cc8c24cd83e902bc4d050347343b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286790"
---
# <a name="query-execution"></a>Exécution des requêtes
Après avoir été créée par un utilisateur, une requête LINQ est convertie en arborescence de commandes. Une arborescence de commandes est une représentation de requête compatible avec Entity Framework. L’arborescence de requêtes est ensuite exécutée sur la source de données. Pendant l'exécution de la requête, toutes les expressions de la requête (c'est-à-dire, toutes ses composantes) sont évaluées, y compris les expressions utilisées dans la matérialisation des résultats.  
  
 Le moment où les expressions d'une requête sont exécutées peut varier. Les requêtes LINQ sont toujours exécutées lorsque la variable de requête fait l'objet d'une itération, et non au moment où elle est créée. C’est ce que l’on appelle *l’exécution différée*. Vous pouvez également forcer l'exécution immédiate de la requête, ce qui est utile pour mettre en cache les résultats de la requête. Ce sujet est abordé plus loin dans cette rubrique.  
  
 Lorsqu'une requête LINQ to Entities est exécutée, il est possible que certaines expressions de la requête soient exécutées sur le serveur et que certaines parties soient exécutées localement sur le client. L'évaluation côté client d'une expression a lieu avant l'exécution de la requête sur le serveur. Si une expression est évaluée sur le client, le résultat de cette évaluation remplace l'expression de la requête, et la requête est ensuite exécutée sur le serveur. Étant donné que les requêtes sont exécutées sur la source de données, la configuration de la source de données prévaut sur le comportement spécifié dans le client. Par exemple, la gestion des valeurs Null et la précision numérique dépendent des paramètres du serveur. Toutes les exceptions levées pendant l'exécution de la requête sur le serveur sont passées directement au client.  

> [!TIP]
> Pour obtenir un résumé pratique des opérateurs de requête dans un format de table, qui vous permet d’identifier rapidement le comportement d’exécution d’un opérateur, consultez [classification des opérateurs de requête standard par mode d’exécution (C#)](../../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md).

## <a name="deferred-query-execution"></a>Exécution de requête différée  
 Dans une requête qui retourne une séquence, la variable de requête elle-même ne contient jamais les résultats de la requête et stocke uniquement les commandes de requête. L'exécution de la requête est différée jusqu'à ce que la variable de requête soit itérée au sein d'une boucle `foreach` ou `For Each`. C’est ce qu’on appelle une *exécution différée*. autrement dit, l’exécution de la requête a lieu un certain temps après la construction de la requête. Vous pouvez ainsi exécuter une requête aussi fréquemment que vous le souhaitez. Cela est utile lorsque, par exemple, l'une de vos bases de données est en cours de mise à jour par d'autres applications. Dans votre application, vous pouvez créer une requête pour récupérer les informations les plus récentes et l'exécuter à plusieurs reprises, pour retourner chaque fois les informations à jour.  
  
 L'exécution différée permet de combiner plusieurs requêtes ou d'étendre une requête. Lorsqu'une requête est étendue, elle est modifiée de manière à inclure les nouvelles opérations, et l'exécution finale reflète les modifications. Dans l'exemple suivant, la première requête retourne tous les produits. La deuxième requête étend la première en utilisant `Where` pour retourner tous les produits de taille « L » :  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Une fois qu'une requête est exécutée, toutes les requêtes suivantes utilisent les opérateurs LINQ en mémoire. L'itération sur la variable de requête par le biais d'une instruction `foreach` ou `For Each` ou par l'appel à l'un des opérateurs de conversion LINQ provoqueront une exécution immédiate. Ces opérateurs de conversion sont notamment : <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A> et <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
## <a name="immediate-query-execution"></a>Exécution de requête immédiate  
 Contrairement à l'exécution différée des requêtes qui produisent une séquence de valeurs, les requêtes qui retournent une valeur singleton sont exécutées immédiatement. Les requêtes <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.First%2A> et <xref:System.Linq.Enumerable.Max%2A> en sont quelques exemples. Elles s'exécutent immédiatement parce que la requête doit produire une séquence pour calculer le résultat singleton. Vous pouvez également forcer l'exécution immédiate. Cela peut s'avérer utile lorsque vous souhaitez mettre en cache les résultats d'une requête. Pour forcer l'exécution immédiate d'une requête qui ne produit pas de valeur singleton, vous pouvez appeler la méthode <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> ou <xref:System.Linq.Enumerable.ToArray%2A> sur une requête ou une variable de requête. L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.ToArray%2A> pour évaluer immédiatement une séquence dans un tableau.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Vous pouvez également forcer l’exécution en plaçant la boucle `foreach` ou `For Each` de suite après l’expression de requête, mais en appelant <xref:System.Linq.Enumerable.ToList%2A> ou <xref:System.Linq.Enumerable.ToArray%2A>, vous mettez en cache toutes les données contenues dans un objet de collection unique.  
  
## <a name="store-execution"></a>Exécution sur les magasins  
 En règle générale, les expressions dans LINQ to Entities sont évaluées sur le serveur, et le comportement de l'expression n'est pas censé suivre la sémantique CLR (Common Language Runtime), mais celle de la source de données. Toutefois, il y a des exceptions à cette règle, notamment lorsque l'expression est exécutée sur le client. Cela peut donner lieu à des résultats inattendus, par exemple lorsque le serveur et le client sont situés dans des fuseaux horaires différents.  
  
 Il est possible que certaines expressions de la requête soient exécutées sur le client. En général, l'exécution de la requête est supposée se produire en grande partie sur le serveur. En dehors des méthodes exécutées sur des éléments de requête mappés à la source de données, il existe souvent, dans la requête, des expressions qui peuvent être exécutées localement. L'exécution locale d'une expression de requête génère une valeur qui peut être utilisée dans l'exécution de la requête ou dans la construction du résultat.  
  
 Certaines opérations sont toujours exécutées sur le client, notamment la liaison de valeurs, les sous-expressions, les sous-requêtes de clôtures et la matérialisation d'objets dans les résultats de requête. En conséquence de quoi, ces éléments (par exemple, les valeurs de paramètres) ne peuvent pas être mis à jour pendant l'exécution. Des types anonymes peuvent être construits par incorporation dans la source de données, mais ils ne sont pas censés l'être. Des regroupements inline peuvent être construits dans la source de données, mais cela n'est pas systématique. En règle générale, il est préférable de ne pas faire de suppositions sur ce qui est construit sur le serveur.  
  
 Cette section décrit les scénarios dans lesquels le code est exécuté localement sur le client. Pour plus d’informations sur les types d’expressions exécutés localement, consultez [expressions dans les requêtes LINQ to Entities](expressions-in-linq-to-entities-queries.md).  
  
### <a name="literals-and-parameters"></a>Littéraux et paramètres  
 Les variables locales, telles que la variable `orderID` de l'exemple suivant, sont évaluées sur le client.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Les paramètres de méthode sont également évalués sur le client. Le paramètre `orderID` passé dans la méthode `MethodParameterExample` ci-dessous en est l'illustration.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>Conversion des littéraux sur le client  
 Le cast d'une valeur `null` en type CLR est exécutée sur le client :  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Le cast en type, tel qu'un type <xref:System.Decimal> Nullable, est exécutée sur le client :  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Constructeurs pour littéraux  
 Les nouveaux types CLR qui peuvent être mappés aux types de modèle conceptuel sont exécutés sur le client :  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 Les nouveaux tableaux sont également exécutés sur le client.  
  
## <a name="store-exceptions"></a>Exceptions de magasin  
 Les erreurs de magasin rencontrées lors de l'exécution d'une requête sont transmises au client. Elles ne sont ni mappées, ni gérées.  
  
## <a name="store-configuration"></a>Configuration de magasin  
 Lorsque la requête s'exécute sur le magasin, la configuration de ce dernier prévaut sur tous les comportements du client, et la sémantique du magasin est exprimée pour l'ensemble des opérations et des expressions. Il peut en résulter une différence de comportement entre le CLR et l'exécution sur le magasin dans certains domaines tels que les comparaisons de valeurs Null, le tri de GUID, la précision et l'exactitude des opérations faisant intervenir des types de données non précis (par exemple, les types à virgule flottante ou <xref:System.DateTime>) et les opérations de chaîne. Il est important de garder cela à l'esprit au moment d'examiner des résultats de requête.  
  
 Par exemple, voici quelques différences de comportement entre le CLR et SQL Server :  
  
- SQL Server trie les GUID de façon différente par rapport au CLR.  
  
- Des différences peuvent également être constatées sur le plan de la précision des résultats lorsque le type Décimal est utilisé dans SQL Server. Cela est dû aux exigences de précision fixe inhérentes au type Décimal de SQL Server. Par exemple, la moyenne des valeurs <xref:System.Decimal> 0,0, 0,0 et 1,0 est de 0,3333333333333333333333333333 dans la mémoire du client, mais de 0,333333 dans le magasin (selon la précision par défaut du type Décimal de SQL Server).  
  
- De même, le traitement de certaines opérations de comparaison de chaînes est différent selon qu'elles sont traitées dans SQL Server ou dans le CLR. Le comportement en matière de comparaison de chaînes dépend des paramètres de classement du serveur.  
  
- Les appels de fonction ou de méthode éventuellement inclus dans une requête LINQ to Entities sont mappés aux fonctions canoniques d'Entity Framework, qui sont ensuite traduites dans Transact-SQL et exécutées sur la base de données SQL Server. Dans certains cas, le comportement affiché par ces fonctions mappées peut être différent de l'implémentation dans les bibliothèques de classes de base. Par exemple, l'appel des méthodes <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A> et <xref:System.String.EndsWith%2A> avec une chaîne vide en guise de paramètre retourne une valeur `true` en cas d'exécution dans le CLR, mais retourne une valeur `false` en cas d'exécution dans SQL Server. La méthode <xref:System.String.EndsWith%2A> peut également retourner des résultats différents. En effet, SQL Server considère que deux chaînes sont égales si seul un espace à droite les différencie. Or, dans ce cas, le CLR les considère différentes. Ceci est illustré dans l'exemple suivant :  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]
