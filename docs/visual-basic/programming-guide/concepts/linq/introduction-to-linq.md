---
title: Introduction à LINQ
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: 58613281d79769bfb5515f1291feb9b502a1e846
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549965"
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="c91a1-102">Introduction à LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c91a1-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="c91a1-103">LINQ (Language-Integrated Query) est une nouveauté du .NET Framework 3.5 qui crée un pont entre le monde des objets et celui des données.</span><span class="sxs-lookup"><span data-stu-id="c91a1-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="c91a1-104">En règle générale, les requêtes de données sont exprimées comme de simples chaînes, sans vérification de type au moment de l’exécution, ni prise en charge IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c91a1-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="c91a1-105">En outre, vous devez apprendre un langage de requête différent pour chaque type de source de données : bases de données SQL, documents XML, services web, etc.</span><span class="sxs-lookup"><span data-stu-id="c91a1-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="c91a1-106">LINQ fait d’une *requête* une construction de langage de première classe dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c91a1-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="c91a1-107">Vous pouvez écrire des requêtes pour des collections d’objets fortement typées à l’aide de mots clés de langage et d’opérateurs familiers.</span><span class="sxs-lookup"><span data-stu-id="c91a1-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="c91a1-108">Vous pouvez écrire des requêtes LINQ dans Visual Basic pour SQL Server des bases de données, des documents XML, des jeux de données ADO.NET et toute collection d’objets prenant en charge <xref:System.Collections.IEnumerable> ou l' <xref:System.Collections.Generic.IEnumerable%601> interface générique.</span><span class="sxs-lookup"><span data-stu-id="c91a1-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="c91a1-109">La prise en charge LINQ est également fournie par des tierces parties pour de nombreux services web et autres implémentations de base de données.</span><span class="sxs-lookup"><span data-stu-id="c91a1-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="c91a1-110">Vous pouvez utiliser des requêtes LINQ dans de nouveaux projets, ou avec des requêtes non LINQ dans des projets existants.</span><span class="sxs-lookup"><span data-stu-id="c91a1-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="c91a1-111">La seule exigence est que le projet cible .NET Framework 3.5 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c91a1-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="c91a1-112">L’illustration suivante de Visual Studio montre une requête LINQ partiellement terminée, exécutée sur une base de données SQL Server, en C# et en Visual Basic, avec un contrôle de type complet et une prise en charge IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c91a1-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 ![Diagramme qui montre une requête LINQ avec Intellisense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="c91a1-114">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="c91a1-114">Next Steps</span></span>  
 <span data-ttu-id="c91a1-115">Pour plus d’informations sur LINQ, commencez par vous familiariser avec certains concepts de base de la section Prise en main [prise en main avec LINQ dans Visual Basic](getting-started-with-linq.md), puis lisez la documentation relative à la technologie LINQ qui vous intéresse :</span><span class="sxs-lookup"><span data-stu-id="c91a1-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
- <span data-ttu-id="c91a1-116">Bases de données SQL Server : [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="c91a1-116">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
- <span data-ttu-id="c91a1-117">Documents XML : [LINQ to XML (Visual Basic)](../../../../standard/linq/linq-xml-overview.md)</span><span class="sxs-lookup"><span data-stu-id="c91a1-117">XML documents: [LINQ to XML (Visual Basic)](../../../../standard/linq/linq-xml-overview.md)</span></span>  
  
- <span data-ttu-id="c91a1-118">Datasets ADO.NET [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="c91a1-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
- <span data-ttu-id="c91a1-119">Collections, fichiers, chaînes .NET, etc. : [LINQ to Objects (Visual Basic)](linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="c91a1-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c91a1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c91a1-120">See also</span></span>

- [<span data-ttu-id="c91a1-121">LINQ (Language-Integrated Query) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c91a1-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
