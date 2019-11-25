---
title: Introduction à LINQ
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: add442583bd81665533b704c0c9721b111cddd78
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338905"
---
# <a name="introduction-to-linq-visual-basic"></a>Introduction to LINQ (Visual Basic)
LINQ (Language-Integrated Query) est une nouveauté du .NET Framework 3.5 qui crée un pont entre le monde des objets et celui des données.  
  
 En règle générale, les requêtes de données sont exprimées comme de simples chaînes, sans vérification de type au moment de l’exécution, ni prise en charge d’IntelliSense. En outre, il vous faut apprendre un langage de requête différent pour chaque type de source de données : bases de données SQL, documents XML, services web, etc. LINQ makes a *query* a first-class language construct in Visual Basic. Vous pouvez écrire des requêtes pour des collections d’objets fortement typées à l’aide de mots clés de langage et d’opérateurs familiers.  
  
 You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface. La prise en charge LINQ est également fournie par des tierces parties pour de nombreux services web et autres implémentations de base de données.  
  
 Vous pouvez utiliser des requêtes LINQ dans de nouveaux projets, ou avec des requêtes non LINQ dans des projets existants. La seule exigence est que le projet cible .NET Framework 3.5 ou version ultérieure.  
  
 L’illustration suivante de Visual Studio montre une requête LINQ partiellement terminée, exécutée sur une base de données SQL Server, en C# et en Visual Basic, avec un contrôle de type complet et une prise en charge IntelliSense.  
  
 ![Diagramme qui montre une requête LINQ avec Intellisense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a>Étapes suivantes  
 To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:  
  
- Bases de données SQL Server : [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
- XML documents: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
- Datasets ADO.NET [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
- .NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Voir aussi

- [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
