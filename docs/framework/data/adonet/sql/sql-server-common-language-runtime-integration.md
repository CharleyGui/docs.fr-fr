---
title: Intégration CLR SQL Server
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: d9fe0f03c88584607c6bc38fcbcff3f9424fd40c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183024"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="b6a8a-102">Intégration CLR SQL Server</span><span class="sxs-lookup"><span data-stu-id="b6a8a-102">SQL Server Common Language Runtime Integration</span></span>

<span data-ttu-id="b6a8a-103">SQL Server 2005 a introduit l'intégration du composant Common Language Runtime (CLR) de .NET Framework pour Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="b6a8a-104">Cela signifie que vous pouvez écrire des procédures stockées, des déclencheurs, des types définis par l'utilisateur, des fonctions définies par l'utilisateur, des agrégats définis par l'utilisateur et des fonctions de flux évaluées par une table, en utilisant tout langage .NET Framework, notamment Microsoft Visual Basic .NET et Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="b6a8a-105">L'espace de noms <xref:Microsoft.SqlServer.Server> contient un ensemble de nouvelles API permettant au code managé d'interagir avec l'environnement Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="b6a8a-106">Cette section décrit les fonctions et les comportements spécifiques à l'intégration de CLR dans SQL Server et aux extensions spécifiques au mode in-process SQL Server pour ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="b6a8a-107">Cette section a uniquement pour but de fournir les informations indispensables pour commencer à programmer avec l'intégration de CLR dans SQL Server et n'est nullement exhaustive.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="b6a8a-108">Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="b6a8a-109">**Documentation SQL Server**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-109">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="b6a8a-110">Concepts de programmation pour l'intégration du CLR</span><span class="sxs-lookup"><span data-stu-id="b6a8a-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](/sql/relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts)  
  
## <a name="in-this-section"></a><span data-ttu-id="b6a8a-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b6a8a-111">In This Section</span></span>  

 [<span data-ttu-id="b6a8a-112">Introduction à l'intégration CLR SQL Server</span><span class="sxs-lookup"><span data-stu-id="b6a8a-112">Introduction to SQL Server CLR Integration</span></span>](introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="b6a8a-113">Fournit une présentation de l'intégration de CLR dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="b6a8a-114">Fournit des liens vers d'autres rubriques.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="b6a8a-115">Fonctions CLR définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="b6a8a-115">CLR User-Defined Functions</span></span>](clr-user-defined-functions.md)  
 <span data-ttu-id="b6a8a-116">Explique comment implémenter et utiliser les différents types de fonctions CLR : fonctions table, scalaires et d'agrégation définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="b6a8a-117">Types CLR définis par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="b6a8a-117">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
 <span data-ttu-id="b6a8a-118">Explique comment implémenter et utiliser les types CLR définis par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="b6a8a-119">Fournit des liens vers d'autres rubriques.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="b6a8a-120">Procédures stockées du CLR</span><span class="sxs-lookup"><span data-stu-id="b6a8a-120">CLR Stored Procedures</span></span>](clr-stored-procedures.md)  
 <span data-ttu-id="b6a8a-121">Explique comment implémenter et utiliser les procédures stockées CLR.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="b6a8a-122">Fournit des liens vers d'autres rubriques.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="b6a8a-123">Déclencheurs CLR</span><span class="sxs-lookup"><span data-stu-id="b6a8a-123">CLR Triggers</span></span>](clr-triggers.md)  
 <span data-ttu-id="b6a8a-124">Explique comment implémenter et utiliser les déclencheurs CLR.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="b6a8a-125">Fournit des liens vers d'autres rubriques.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="b6a8a-126">Connexion contextuelle</span><span class="sxs-lookup"><span data-stu-id="b6a8a-126">The Context Connection</span></span>](the-context-connection.md)  
 <span data-ttu-id="b6a8a-127">Décrit la connexion de contexte.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="b6a8a-128">Comportement SQL Server spécifique au processus d'ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6a8a-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="b6a8a-129">Décrit les extensions spécifiques au mode in-process SQL Server pour ADO.NET et la connexion de contexte.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="b6a8a-130">Fournit des liens vers d'autres rubriques.</span><span class="sxs-lookup"><span data-stu-id="b6a8a-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6a8a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6a8a-131">See also</span></span>

- [<span data-ttu-id="b6a8a-132">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6a8a-132">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="b6a8a-133">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b6a8a-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
