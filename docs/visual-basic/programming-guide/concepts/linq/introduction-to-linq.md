---
title: Introduction à LINQ
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: b0fa27fd81b85eb89712f9e81f42e06505878f86
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397556"
---
# <a name="introduction-to-linq-visual-basic"></a>Introduction à LINQ (Visual Basic)
LINQ (Language-Integrated Query) est une nouveauté du .NET Framework 3.5 qui crée un pont entre le monde des objets et celui des données.  
  
 En règle générale, les requêtes de données sont exprimées comme de simples chaînes, sans vérification de type au moment de l’exécution, ni prise en charge IntelliSense. En outre, vous devez apprendre un langage de requête différent pour chaque type de source de données : bases de données SQL, documents XML, services web, etc. LINQ fait d’une *requête* une construction de langage de première classe dans Visual Basic. Vous pouvez écrire des requêtes pour des collections d’objets fortement typées à l’aide de mots clés de langage et d’opérateurs familiers.  
  
 Vous pouvez écrire des requêtes LINQ dans Visual Basic pour SQL Server des bases de données, des documents XML, des jeux de données ADO.NET et toute collection d’objets prenant en charge <xref:System.Collections.IEnumerable> ou l' <xref:System.Collections.Generic.IEnumerable%601> interface générique. La prise en charge LINQ est également fournie par des tierces parties pour de nombreux services web et autres implémentations de base de données.  
  
 Vous pouvez utiliser des requêtes LINQ dans de nouveaux projets, ou avec des requêtes non LINQ dans des projets existants. La seule exigence est que le projet cible .NET Framework 3.5 ou version ultérieure.  
  
 L’illustration suivante de Visual Studio montre une requête LINQ partiellement terminée, exécutée sur une base de données SQL Server, en C# et en Visual Basic, avec un contrôle de type complet et une prise en charge IntelliSense.  
  
 ![Diagramme qui montre une requête LINQ avec Intellisense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d’informations sur LINQ, commencez par vous familiariser avec certains concepts de base de la section Prise en main [prise en main avec LINQ dans Visual Basic](getting-started-with-linq.md), puis lisez la documentation relative à la technologie LINQ qui vous intéresse :  
  
- Bases de données SQL Server : [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
- Documents XML : [LINQ to XML (Visual Basic)](linq-to-xml.md)  
  
- Datasets ADO.NET [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
- Collections, fichiers, chaînes .NET, etc. : [LINQ to Objects (Visual Basic)](linq-to-objects.md)  
  
## <a name="see-also"></a>Voir aussi

- [LINQ (Language-Integrated Query) (Visual Basic)](index.md)
