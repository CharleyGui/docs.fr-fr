---
title: Guide de programmation
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: 542567cf07e86b642a23a879fa6e5476253005b8
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848936"
---
# <a name="programming-guide"></a><span data-ttu-id="0b4f8-102">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="0b4f8-102">Programming Guide</span></span>
<span data-ttu-id="0b4f8-103">Cette section contient des informations sur la création et l'utilisation de votre modèle objet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b4f8-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="0b4f8-104">Si vous utilisez Visual Studio, vous pouvez également utiliser le concepteur relationnel d’objet pour effectuer plusieurs de ces mêmes tâches.</span><span class="sxs-lookup"><span data-stu-id="0b4f8-104">If you are using Visual Studio, you can also use the Object Relational Designer to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="0b4f8-105">Vous pouvez également rechercher Microsoft Docs pour des questions spécifiques, et vous pouvez participer au [Forum LINQ](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), où vous pouvez discuter de sujets plus complexes en détail avec des experts.</span><span class="sxs-lookup"><span data-stu-id="0b4f8-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="0b4f8-106">Enfin, le [LINQ à SQL: .NET Language-Integrated Query for Relational Data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, avec des exemples de code Visual Basic et C.</span><span class="sxs-lookup"><span data-stu-id="0b4f8-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b4f8-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0b4f8-107">In This Section</span></span>  
 [<span data-ttu-id="0b4f8-108">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="0b4f8-108">Creating the Object Model</span></span>](creating-the-object-model.md)  
 <span data-ttu-id="0b4f8-109">Explique comment générer un modèle objet.</span><span class="sxs-lookup"><span data-stu-id="0b4f8-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="0b4f8-110">Communication avec la base de données</span><span class="sxs-lookup"><span data-stu-id="0b4f8-110">Communicating with the Database</span></span>](communicating-with-the-database.md)  
 <span data-ttu-id="0b4f8-111">Explique comment utiliser un objet <xref:System.Data.Linq.DataContext> comme un conduit vers la base de données.</span><span class="sxs-lookup"><span data-stu-id="0b4f8-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="0b4f8-112">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="0b4f8-112">Querying the Database</span></span>](querying-the-database.md)  
 <span data-ttu-id="0b4f8-113">Explique comment exécuter des requêtes dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]et fournit de nombreux exemples.</span><span class="sxs-lookup"><span data-stu-id="0b4f8-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="0b4f8-114">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="0b4f8-114">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)  
 <span data-ttu-id="0b4f8-115">Explique comment modifier des données dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="0b4f8-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="0b4f8-116">Soutien de débogage</span><span class="sxs-lookup"><span data-stu-id="0b4f8-116">Debugging Support</span></span>](debugging-support.md)  
 <span data-ttu-id="0b4f8-117">Décrit la prise en charge disponible pour le débogage des projets [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b4f8-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="0b4f8-118">Informations de base</span><span class="sxs-lookup"><span data-stu-id="0b4f8-118">Background Information</span></span>](background-information.md)  
 <span data-ttu-id="0b4f8-119">Inclut des éléments supplémentaires tels que la résolution de conflit d’accès concurrentiel, la création de nouvelles bases de données, etc., pour les utilisateurs plus expérimentés.</span><span class="sxs-lookup"><span data-stu-id="0b4f8-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0b4f8-120">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="0b4f8-120">Related Sections</span></span>  
 [<span data-ttu-id="0b4f8-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0b4f8-121">LINQ to SQL</span></span>](index.md)  
 <span data-ttu-id="0b4f8-122">Fournit des liens vers les rubriques qui expliquent la technologie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="0b4f8-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="0b4f8-123">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="0b4f8-123">Stored Procedures</span></span>](stored-procedures.md)  
 <span data-ttu-id="0b4f8-124">Inclut des liens vers les rubriques qui expliquent comment utiliser des procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="0b4f8-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="0b4f8-125">Présentation de LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="0b4f8-125">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="0b4f8-126">Fournit des ressources pour vous aider à commencer à en apprendre davantage sur LINQ à SQL à l’aide de C.</span><span class="sxs-lookup"><span data-stu-id="0b4f8-126">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="0b4f8-127">Introduction à LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b4f8-127">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="0b4f8-128">Fournit des ressources pour vous aider à commencer à en apprendre davantage sur LINQ à SQL en utilisant Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0b4f8-128">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>
