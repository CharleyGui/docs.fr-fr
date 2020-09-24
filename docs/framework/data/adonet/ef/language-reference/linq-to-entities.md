---
title: LINQ to Entities
description: Découvrez comment créer et exécuter des requêtes LINQ to Entities, qui vous permettent d’écrire des requêtes sur le modèle conceptuel Entity Framework à l’aide de Visual Basic ou Visual C#.
ms.date: 03/30/2017
ms.assetid: 641f9b68-9046-47a1-abb0-1c8eaeda0e2d
ms.openlocfilehash: 809cbd10be6a2bc44bb4bff0ba3ea363da676f7f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150789"
---
# <a name="linq-to-entities"></a>LINQ to Entities

LINQ to Entities assure une prise en charge de la technologie LINQ (Language Integrated Query), ce qui permet aux développeurs d'écrire des requêtes par rapport au modèle conceptuel Entity Framework à l'aide du langage Visual Basic ou Visual C#. Les requêtes exécutées avec Entity Framework sont représentées par des requêtes d'arborescence de commandes, lesquelles s'exécutent par rapport au contexte de l'objet. LINQ to Entities convertit les requêtes LINQ (Language-Integrated Query) en requêtes d'arborescence de commandes, exécute les requêtes avec Entity Framework, puis retourne les objets qui peuvent être utilisés aussi bien par Entity Framework que par LINQ. Voici le processus de création et d'exécution d'une requête LINQ to Entities :  
  
1. Construisez une instance de l'objet <xref:System.Data.Objects.ObjectQuery%601> à partir de l'objet <xref:System.Data.Objects.ObjectContext>.  
  
2. Composez une requête LINQ to Entities en C# ou en Visual Basic en utilisant l'instance de l'objet <xref:System.Data.Objects.ObjectQuery%601>.  
  
3. Convertissez les expressions et opérateurs de requête standard LINQ en arborescences de commandes.  
  
4. Exécutez la requête dans l'arborescence des commandes sur la source de données. Toutes les exceptions levées sur la source de données pendant l'exécution sont passées directement au client.  
  
5. Retournez les résultats de la requête au client.  
  
## <a name="constructing-an-objectquery-instance"></a>Construction d'une instance d'ObjectQuery  

 La classe générique <xref:System.Data.Objects.ObjectQuery%601> représente une requête qui retourne une collection de zéro ou plusieurs entités typées. Une requête d'objet est généralement construite à partir d'un contexte d'objet existant, au lieu d'être construite manuellement, et appartient toujours à ce contexte d'objet. Ce contexte fournit les informations relatives à la connexion et aux métadonnées qui sont requises pour composer et exécuter la requête. La classe générique <xref:System.Data.Objects.ObjectQuery%601> implémente l'interface générique <xref:System.Linq.IQueryable%601>, dont les méthodes de générateur permettent la construction incrémentielle de requêtes LINQ. Vous pouvez également permettre au compilateur de déduire le type des entités à l'aide du mot clé C# `var` (`Dim` en Visual Basic, avec l'inférence de type local activée).  
  
## <a name="composing-the-queries"></a>Composition des requêtes  

 Les instances de la classe générique <xref:System.Data.Objects.ObjectQuery%601>, laquelle implémente l'interface générique <xref:System.Linq.IQueryable%601>, servent de source de données pour les requêtes LINQ to Entities. Dans une requête, vous spécifiez exactement les informations que vous voulez récupérer à partir de la source de données. Une requête peut également spécifier la manière dont ces informations doivent être triées, regroupées et mises en forme avant d'être retournées. Dans LINQ, une requête est stockée dans une variable. Cette variable de requête n'effectue aucune action et ne retourne aucune donnée ; elle stocke uniquement les informations de requête. Une fois que vous avez créé une requête, vous devez l'exécuter pour extraire des données.  
  
 Les requêtes LINQ to Entities peuvent être composées dans deux syntaxes différentes : la syntaxe d'expression de requête et la syntaxe de requête fondée sur une méthode. La syntaxe d'expression de requête et la syntaxe de requête fondée sur une méthode sont nouvelles dans C# 3.0 et dans Visual Basic 9.0.  
  
 Pour plus d’informations, consultez [requêtes dans LINQ to Entities](queries-in-linq-to-entities.md).  
  
## <a name="query-conversion"></a>Conversion de requête  

 Pour exécuter une requête LINQ to Entities avec Entity Framework, cette requête doit être convertie en représentation arborescente des commandes qui peut être exécutée avec Entity Framework.  
  
 Les requêtes LINQ to Entities sont constituées d’opérateurs de requête standard LINQ (tels que <xref:System.Linq.Queryable.Select%2A> , <xref:System.Linq.Queryable.Where%2A> , et <xref:System.Linq.Queryable.GroupBy%2A> ) et d’expressions (x > 10, contact. LastName, etc.). Les opérateurs LINQ ne sont pas définis par une classe ; ce sont des méthodes sur une classe. Dans LINQ, les expressions peuvent contenir tout ce que les types de l’espace de noms <xref:System.Linq.Expressions> autorisent et, par extension, tout ce qui peut être représenté dans une fonction lambda. Il s’agit d’un sur-ensemble des expressions qui sont autorisées par Entity Framework, lesquelles sont, par définition, limitées aux opérations autorisées sur la base de données et prises en charge par l’objet <xref:System.Data.Objects.ObjectQuery%601>.  
  
 Dans Entity Framework, les opérateurs et les expressions sont représentés par une seule hiérarchie des types, qui sont ensuite placés dans une arborescence de commandes. L'arborescence de commandes est utilisée par Entity Framework pour exécuter la requête. Si la requête LINQ ne peut pas être exprimée sous la forme d’une arborescence de commandes, une exception est levée au moment de la conversion de la requête. La conversion de requêtes LINQ to Entities implique deux sous-conversions : la conversion des opérateurs de requête standard et la conversion des expressions.  
  
 Plusieurs opérateurs de requête standard LINQ n'ont pas de traduction valide dans LINQ to Entities. Les tentatives d'utilisation de ces opérateurs provoquent une exception au moment de la traduction de la requête. Pour obtenir la liste des opérateurs LINQ to Entities pris en charge, consultez [Méthodes LINQ prises en charge et non prises en charge (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md).  
  
 Pour plus d’informations sur l’utilisation des opérateurs de requête standard dans LINQ to Entities, consultez [opérateurs de requête standard dans les requêtes LINQ to Entities](standard-query-operators-in-linq-to-entities-queries.md).  
  
 En règle générale, les expressions dans LINQ to Entities sont évaluées sur le serveur. Par conséquent, le comportement de l'expression n'est pas censé suivre la sémantique CLR. Pour plus d’informations, consultez [expressions dans les requêtes LINQ to Entities](expressions-in-linq-to-entities-queries.md).  
  
 Pour plus d’informations sur la façon dont les appels de méthode CLR sont mappés aux fonctions canoniques dans la source de données, consultez [méthode CLR pour le mappage de fonction canonique](clr-method-to-canonical-function-mapping.md).  
  
 Pour plus d’informations sur l’appel des fonctions canoniques, de base de données et personnalisées à partir de LINQ to Entities des requêtes, consultez [appel de fonctions dans des requêtes LINQ to Entities](calling-functions-in-linq-to-entities-queries.md).  
  
## <a name="query-execution"></a>Exécution des requêtes  

 Une fois la requête LINQ créée par l’utilisateur, elle est convertie en une représentation compatible avec Entity Framework (sous la forme d’arborescences de commandes), qui est ensuite exécutée sur la source de données. Au moment de l'exécution de la requête, l'ensemble des expressions de requête (ou des composants de la requête) sont évalués sur le client ou sur le serveur. Cela comprend les expressions qui sont utilisées dans la matérialisation des résultats ou les projections d'entités. Pour plus d’informations, consultez exécution de la [requête](query-execution.md). Pour plus d’informations sur l’amélioration des performances en compilant une requête, puis en l’exécutant plusieurs fois avec des paramètres différents, consultez [requêtes compilées (LINQ to Entities)](compiled-queries-linq-to-entities.md).  
  
## <a name="materialization"></a>Matérialisation  

 La matérialisation est le processus qui consiste à retourner les résultats d'une requête au client sous forme de types CLR. Dans LINQ to Entities, les enregistrements de données de résultats de requête ne sont jamais retournés ; il y a toujours un type CLR de sauvegarde, défini par l’utilisateur ou par Entity Framework, ou généré par le compilateur (types anonymes). Toute matérialisation d’objets est effectuée par Entity Framework. Toute erreur qui résulte d’une impossibilité d’effectuer un mappage entre Entity Framework et le CLR lève une exception à lever pendant la matérialisation d’objets.  
  
 Les résultats de la requête sont généralement retournés sous l'une des formes suivantes :  
  
- une collection de zéro, un ou plusieurs objets entité typés ou une projection de types complexes définis dans le modèle conceptuel ;  
  
- Types CLR pris en charge par l’Entity Framework.  
  
- Collections inline.  
  
- Types anonymes.  
  
 Pour plus d’informations, consultez résultats de la [requête](query-results.md).  
  
## <a name="in-this-section"></a>Dans cette section  

 [Requêtes dans LINQ to Entities](queries-in-linq-to-entities.md)  
  
 [Expressions dans les requêtes LINQ to Entities](expressions-in-linq-to-entities-queries.md)  
  
 [Appel de fonctions dans les requêtes LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)  
  
 [Requêtes compilées (LINQ to Entities)](compiled-queries-linq-to-entities.md)  
  
 [Exécution de la requête](query-execution.md)  
  
 [Résultats de la requête](query-results.md)  
  
 [Opérateurs de requête standard dans les requêtes LINQ to Entities](standard-query-operators-in-linq-to-entities-queries.md)  
  
 [Mappage de la méthode CLR aux fonctions de chaînes canoniques](clr-method-to-canonical-function-mapping.md)  
  
 [Méthodes LINQ prises en charge et non prises en charge (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md)  
  
 [Problèmes connus et éléments à prendre en compte dans LINQ to Entities](known-issues-and-considerations-in-linq-to-entities.md)  
  
## <a name="see-also"></a>Voir aussi

- [Problèmes connus et éléments à prendre en compte dans LINQ to Entities](known-issues-and-considerations-in-linq-to-entities.md)
- [LINQ (Language-Integrated Query) - C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (Language-Integrated Query) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ et ADO.NET](../../linq-and-ado-net.md)
- [ADO.NET Entity Framework](../index.md)
