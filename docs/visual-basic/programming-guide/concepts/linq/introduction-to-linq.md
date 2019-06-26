---
title: Introduction à LINQ (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: 7c42cf73dce91bfb4da1b886613635532460f0e6
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402408"
---
# <a name="introduction-to-linq-visual-basic"></a>Introduction à LINQ (Visual Basic)
LINQ (Language-Integrated Query) est une nouveauté du .NET Framework 3.5 qui crée un pont entre le monde des objets et celui des données.  
  
 En règle générale, les requêtes de données sont exprimées comme de simples chaînes, sans vérification de type au moment de l’exécution, ni prise en charge d’IntelliSense. En outre, vous devez apprendre un langage de requête différent pour chaque type de source de données : bases de données SQL, documents XML, divers services web, etc. LINQ permet une *requête* une construction de langage de premier ordre en Visual Basic. Vous pouvez écrire des requêtes pour des collections d’objets fortement typées à l’aide de mots clés de langage et d’opérateurs familiers.  
  
 Vous pouvez écrire des requêtes LINQ en Visual Basic pour SQL Server bases de données XML documents, jeux de données ADO.NET et toute collection d’objets qui prend en charge <xref:System.Collections.IEnumerable> ou générique <xref:System.Collections.Generic.IEnumerable%601> interface. La prise en charge LINQ est également fournie par des tierces parties pour de nombreux services web et autres implémentations de base de données.  
  
 Vous pouvez utiliser des requêtes LINQ dans de nouveaux projets, ou avec des requêtes non LINQ dans des projets existants. La seule exigence est que le projet cible .NET Framework 3.5 ou version ultérieure.  
  
 L’illustration suivante de Visual Studio montre une requête LINQ partiellement terminée, exécutée sur une base de données SQL Server, en C# et en Visual Basic, avec un contrôle de type complet et une prise en charge IntelliSense.  
  
 ![Diagramme qui montre une requête LINQ avec Intellisense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d’informations sur LINQ, commencez par vous familiariser avec certains concepts de base dans la section mise en route [mise en route avec LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), puis lisez la documentation de la technologie LINQ dans lequel vous êtes vous souhaitez :  
  
- Bases de données SQL Server : [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
- Documents XML : [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
- Datasets ADO.NET : [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
- Chaînes, fichiers, collections .NET, etc. : [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Voir aussi

- [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
