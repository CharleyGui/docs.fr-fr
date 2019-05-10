---
title: LINQ (Language-Integrated Query) (C#)
ms.date: 02/02/2017
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
ms.openlocfilehash: fbd73d879a3e2fe4cc38d6c8548434d21ca06467
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64597081"
---
# <a name="language-integrated-query-linq"></a>LINQ (Language-Integrated Query)

LINQ (Language-Integrated Query) est le nom d’un ensemble de technologies basé sur l’intégration de fonctions de requête directement dans le langage C#. En règle générale, les requêtes de données sont exprimées comme de simples chaînes, sans vérification de type au moment de l’exécution, ni prise en charge d’IntelliSense. En outre, vous devez apprendre un langage de requête différent pour chaque type de source de données : bases de données SQL, documents XML, divers services web, etc. Avec LINQ, une requête est une construction de langage de premier ordre, comme les classes, les méthodes et les événements.

Pour un développeur qui écrit des requêtes, la partie « intégrée au langage » la plus visible de LINQ est l’expression de requête. Les expressions de requête sont écrites selon une *syntaxe de requête* déclarative. En utilisant la syntaxe de requête, vous pouvez effectuer des opérations de filtrage, de classement et de regroupement sur des sources de données avec un minimum de code. Vous utilisez les mêmes modèles d’expression de requête de base pour interroger et transformer des données dans les bases de données SQL, les jeux de données ADO .NET, les flux et documents XML et les collections .NET.

L’exemple suivant montre l’opération de requête complète. L’opération complète comprend la création d’une source de données, la définition de l’expression de requête et l’exécution de la requête dans une instruction `foreach`.

[!code-csharp[csProgGuideLINQ#11](../../../../../samples/snippets/csharp/concepts/linq/index_1.cs)]

## <a name="query-expression-overview"></a>Vue d’ensemble des expressions de requête

- Les expressions de requête peuvent être utilisées pour interroger et transformer des données à partir de n’importe quelle source de données compatible LINQ. Par exemple, une même requête peut récupérer des données d’une base de données SQL et générer un flux XML en sortie.  
  
- Les expressions de requête sont faciles à maîtriser, car elles utilisent de nombreuses constructions familières du langage C#.  
  
- Les variables d’une expression de requête sont toutes fortement typées, même si, dans de nombreux cas, il n’est pas nécessaire de fournir le type explicitement, car le compilateur peut le déduire. Pour plus d’informations, consultez la page [Relations entre les types dans les opérations de requête LINQ](type-relationships-in-linq-query-operations.md).  
  
- Une requête ne s’exécute pas tant que vous n’avez pas itéré la variable de requête, par exemple dans une instruction `foreach`. Pour plus d’informations, consultez la page [Introduction aux requêtes LINQ](introduction-to-linq-queries.md).  
  
- Lors de la compilation, les expressions de requête sont converties en appels de méthode d’opérateur de requête standard en fonction des règles définies dans la spécification du langage C#. Toute requête exprimable avec la syntaxe de requête peut également être exprimée avec la syntaxe de méthode. Toutefois, dans la plupart des cas, la syntaxe de requête est plus lisible et plus concise. Pour plus d’informations, consultez les pages [Spécification du langage C#](~/_csharplang/spec/expressions.md#query-expressions) et [Vue d’ensemble des opérateurs de requête standard](standard-query-operators-overview.md).  
  
- En règle générale, lorsque vous écrivez des requêtes LINQ, nous vous recommandons d’utiliser la syntaxe de requête dans la mesure du possible et la syntaxe de méthode si nécessaire. Il n’y a aucune différence de sémantique ou de performances entre les deux formats. Les expressions de requête sont souvent plus lisibles que les expressions équivalentes écrites avec la syntaxe de méthode.  
  
- Certaines opérations de requête, comme <xref:System.Linq.Enumerable.Count%2A> ou <xref:System.Linq.Enumerable.Max%2A>, n’ont pas d’expression de requête équivalente et doivent par conséquent être exprimées sous la forme d’un appel de méthode. La syntaxe de méthode peut être combinée avec la syntaxe de requête de différentes manières. Pour plus d’informations, consultez la page [Syntaxe de requête et syntaxe de méthode dans LINQ](query-syntax-and-method-syntax-in-linq.md).  
  
- Les expressions de requête peuvent être compilées dans des arborescences d’expressions ou des délégués, selon le type auquel la requête est appliquée. Les requêtes <xref:System.Collections.Generic.IEnumerable%601> sont compilées en délégués. Les requêtes <xref:System.Linq.IQueryable> et <xref:System.Linq.IQueryable%601> sont compilées en arborescences d’expression. Pour plus d’informations, consultez la page [Arborescences d’expressions](../../../expression-trees.md).  

## <a name="next-steps"></a>Étapes suivantes

Pour approfondir votre connaissance de LINQ, commencez par vous familiariser avec certains concepts de base expliqués sur la page [Principes de base des expressions de requête](../../../linq/query-expression-basics.md), puis lisez la documentation relative à la technologie LINQ qui vous intéresse :   
- Documents XML : [LINQ to XML](linq-to-xml.md)  
  
- ADO.NET Entity Framework : [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)  
  
- Chaînes, fichiers, collections .NET, etc. : [LINQ to Objects](linq-to-objects.md)

Pour approfondir votre compréhension de LINQ en général, consultez la page [LINQ en C#](../../../linq/linq-in-csharp.md).

Pour commencer à travailler avec LINQ en C#, consultez le didacticiel [Travailler avec LINQ](../../../tutorials/working-with-linq.md).
