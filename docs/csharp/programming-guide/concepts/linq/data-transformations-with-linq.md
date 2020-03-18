---
title: Transformations de données avec LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: 393e3bd24c4bc8b89064e01e1048b24254f5f83b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635949"
---
# <a name="data-transformations-with-linq-c"></a>Transformations de données avec LINQ (C#)
La requête intégrée en langue (LINQ) ne consiste pas seulement à récupérer des données. C’est également un outil puissant pour la transformation de données. En utilisant une requête LINQ, vous pouvez utiliser une séquence source comme entrée et la modifier de plusieurs façons pour créer une nouvelle séquence de sortie. Vous pouvez modifier la séquence elle-même sans modifier les éléments eux-mêmes en les triant et en les regroupant. Mais peut-être la caractéristique la plus puissante des requêtes LINQ est la capacité de créer de nouveaux types. Cette opération est effectuée dans la clause [select](../../../language-reference/keywords/select-clause.md). Par exemple, il est possible de réaliser les tâches suivantes :  
  
- Fusionner plusieurs séquences d’entrée en une séquence de sortie unique ayant un nouveau type.  
  
- Créer des séquences de sortie dont les éléments se composent d’une seule propriété ou de plusieurs propriétés de chaque élément de la séquence source.  
  
- Créer des séquences de sortie dont les éléments se composent des résultats des opérations effectuées sur les données sources.  
  
- Créer des séquences de sortie dans un format différent. Par exemple, vous pouvez transformer des données de lignes ou de fichiers texte SQL en données XML.  
  
 Voici une liste non exhaustive d’exemples. Bien sûr, ces transformations peuvent être combinées de plusieurs façons dans la même requête. Par ailleurs, la séquence de sortie d’une requête peut être utilisée comme séquence d’entrée pour une nouvelle requête.  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a>Combinaison de plusieurs entrées en une séquence de sortie  
 Vous pouvez utiliser une requête LINQ pour créer une séquence de sortie qui contient des éléments de plus d’une séquence d’entrée. L’exemple suivant montre comment combiner deux structures de données en mémoire, mais les mêmes principes peuvent être appliqués pour combiner des données provenant de sources XML, SQL ou DataSet. Prenons l’exemple des deux types de classe suivants :  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 L’exemple suivant présente la requête :  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 Pour plus d’informations, consultez [join, clause](../../../language-reference/keywords/join-clause.md) et [select, clause](../../../language-reference/keywords/select-clause.md).  
  
## <a name="selecting-a-subset-of-each-source-element"></a>Sélection d’un sous-ensemble de chaque élément source  
 Pour sélectionner un sous-ensemble de chaque élément de la séquence source, deux méthodes principales s’offrent à vous :  
  
1. Pour sélectionner un seul membre de l’élément source, utilisez l’opérateur point. Dans l’exemple suivant, supposons qu’un objet `Customer` contienne plusieurs propriétés publiques comprenant une chaîne nommée `City`. Une fois exécutée, cette requête génère une séquence de sortie de chaînes.  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. Pour créer des éléments qui contiennent plusieurs propriétés de l’élément source, vous pouvez utiliser un initialiseur d’objet avec un objet nommé ou un type anonyme. L’exemple suivant montre comment utiliser un type anonyme pour encapsuler deux propriétés de chaque élément `Customer` :  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Pour plus d’informations, consultez [Initialiseurs d’objets et de collections](../../classes-and-structs/object-and-collection-initializers.md) et [Types anonymes](../../classes-and-structs/anonymous-types.md).  
  
## <a name="transforming-in-memory-objects-into-xml"></a>Transformation d’objets en mémoire en XML  
 Les requêtes LINQ facilitent la transformation des données entre les structures de données en mémoire, les bases de données SQL, les ADO.NET les ensembles de données et les flux ou documents XML. L’exemple suivant transforme des objets d’une structure de données en mémoire en éléments XML.  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 Le code génère la sortie XML suivante :  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 Pour plus d’informations, consultez [Création d’arborescences XML en C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).  
  
## <a name="performing-operations-on-source-elements"></a>Exécution d’opérations sur les éléments sources  
 Une séquence de sortie ne contient pas toujours des éléments ou des propriétés d’élément de la séquence source. La sortie peut être plutôt une séquence de valeurs calculée en utilisant les éléments sources comme arguments d’entrée. La requête simple suivante, quand elle est exécutée, génère en sortie une séquence de chaînes dont les valeurs représentent un calcul basé sur la séquence source d’éléments de type `double`.  
  
> [!NOTE]
> Les méthodes d’appel dans les expressions de requête ne sont pas prises en charge si la requête est traduite dans un autre domaine. Par exemple, vous ne pouvez pas appeler une méthode C# ordinaire dans [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], car SQL Server n’a pas de contexte pour cette méthode. Toutefois, vous pouvez mapper des procédures stockées à des méthodes et appeler celles-ci. Pour plus d’informations, consultez [Procédures stockées](../../../../framework/data/adonet/sql/linq/stored-procedures.md).  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a>Voir aussi

- [LINQ (Language-Integrated Query) (C#)](./index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)
- [LINQ to XML (C#)](./linq-to-xml-overview.md)
- [Expressions de requête LINQ](../../../linq/index.md)
- [clause de sélection](../../../language-reference/keywords/select-clause.md)
