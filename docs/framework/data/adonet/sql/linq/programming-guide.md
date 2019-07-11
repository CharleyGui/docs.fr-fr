---
title: Guide de programmation
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: c63fbedc1cf7484943614c50e7dd7554a2ddea0e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742939"
---
# <a name="programming-guide"></a><span data-ttu-id="d46c1-102">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="d46c1-102">Programming Guide</span></span>
<span data-ttu-id="d46c1-103">Cette section contient des informations sur la création et l'utilisation de votre modèle objet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d46c1-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="d46c1-104">Si vous utilisez Visual Studio, vous pouvez également utiliser le concepteur objet/relationnel pour effectuer la plupart de ces tâches.</span><span class="sxs-lookup"><span data-stu-id="d46c1-104">If you are using Visual Studio, you can also use the Object Relational Designer to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="d46c1-105">Vous pouvez également rechercher Microsoft Docs des problèmes spécifiques, et vous pouvez participer à la [Forum LINQ](https://go.microsoft.com/fwlink/?LinkId=76488), où vous pourrez aborder des sujets plus complexes avec des experts.</span><span class="sxs-lookup"><span data-stu-id="d46c1-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="d46c1-106">Enfin, le [LINQ to SQL : Language-Integrated Query pour les données relationnelles](https://go.microsoft.com/fwlink/?LinkId=93205) détails du livre blanc [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologie, obtenir des exemples de code Visual Basic et c#.</span><span class="sxs-lookup"><span data-stu-id="d46c1-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d46c1-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d46c1-107">In This Section</span></span>  
 [<span data-ttu-id="d46c1-108">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="d46c1-108">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 <span data-ttu-id="d46c1-109">Explique comment générer un modèle objet.</span><span class="sxs-lookup"><span data-stu-id="d46c1-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="d46c1-110">Communication avec la base de données</span><span class="sxs-lookup"><span data-stu-id="d46c1-110">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)  
 <span data-ttu-id="d46c1-111">Explique comment utiliser un objet <xref:System.Data.Linq.DataContext> comme un conduit vers la base de données.</span><span class="sxs-lookup"><span data-stu-id="d46c1-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="d46c1-112">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="d46c1-112">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 <span data-ttu-id="d46c1-113">Explique comment exécuter des requêtes dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]et fournit de nombreux exemples.</span><span class="sxs-lookup"><span data-stu-id="d46c1-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="d46c1-114">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="d46c1-114">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 <span data-ttu-id="d46c1-115">Explique comment modifier des données dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="d46c1-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="d46c1-116">Prise en charge du débogage</span><span class="sxs-lookup"><span data-stu-id="d46c1-116">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 <span data-ttu-id="d46c1-117">Décrit la prise en charge disponible pour le débogage des projets [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d46c1-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="d46c1-118">Informations générales</span><span class="sxs-lookup"><span data-stu-id="d46c1-118">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 <span data-ttu-id="d46c1-119">Inclut des éléments supplémentaires tels que la résolution de conflit d’accès concurrentiel, la création de nouvelles bases de données, etc., pour les utilisateurs plus expérimentés.</span><span class="sxs-lookup"><span data-stu-id="d46c1-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d46c1-120">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d46c1-120">Related Sections</span></span>  
 [<span data-ttu-id="d46c1-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d46c1-121">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="d46c1-122">Fournit des liens vers les rubriques qui expliquent la technologie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="d46c1-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="d46c1-123">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="d46c1-123">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 <span data-ttu-id="d46c1-124">Inclut des liens vers les rubriques qui expliquent comment utiliser des procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="d46c1-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="d46c1-125">Introduction à LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="d46c1-125">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="d46c1-126">Fournit des ressources pour vous aider à commencer à en savoir plus sur LINQ à SQL avec C#.</span><span class="sxs-lookup"><span data-stu-id="d46c1-126">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="d46c1-127">Introduction à LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d46c1-127">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="d46c1-128">Fournit des ressources pour vous aider à commencer à en savoir plus sur LINQ to SQL à l’aide de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d46c1-128">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>
