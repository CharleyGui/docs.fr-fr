---
title: Introduction à l'intégration CLR SQL Server
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: 41dd89af4f45c673cf6b7283fc39aaf91fd9963c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452407"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="fd43a-102">Introduction à l'intégration CLR SQL Server</span><span class="sxs-lookup"><span data-stu-id="fd43a-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="fd43a-103">Le CLR (Common Language Runtime) est le cœur de Microsoft .NET Framework et fournit l'environnement d'exécution de la totalité du code .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd43a-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="fd43a-104">Le code qui s'exécute au sein du CLR est désigné sous le nom de code managé.</span><span class="sxs-lookup"><span data-stu-id="fd43a-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="fd43a-105">Le CLR fournit divers fonctions et services requis pour l'exécution du programme, y compris la compilation juste-à-temps (JIT), l'allocation et la gestion de la mémoire, la mise en application de la cohérence des types, la gestion des exceptions, la gestion des threads et la sécurité.</span><span class="sxs-lookup"><span data-stu-id="fd43a-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="fd43a-106">Avec le CLR hébergé dans Microsoft SQL Server (intégration du CLR), vous pouvez créer des procédures stockées, des déclencheurs, des fonctions définies par l'utilisateur, des types définis par l'utilisateur et des agrégats définis par l'utilisateur en code managé.</span><span class="sxs-lookup"><span data-stu-id="fd43a-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="fd43a-107">Comme le code managé est compilé en code natif avant l'exécution, vous pouvez obtenir une amélioration significative des performances dans certains scénarios.</span><span class="sxs-lookup"><span data-stu-id="fd43a-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="fd43a-108">Le code managé utilise la sécurité d'accès du code CAS (Code Access Security), des liaisons de code et des domaines d'application pour empêcher les assemblys d'effectuer certaines opérations.</span><span class="sxs-lookup"><span data-stu-id="fd43a-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="fd43a-109">SQL Server utilise CAS pour vous aider à sécuriser le code managé et empêcher toute compromission du système d'exploitation ou du serveur de base de données.</span><span class="sxs-lookup"><span data-stu-id="fd43a-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="fd43a-110">Cette section a uniquement pour but de fournir les informations indispensables pour commencer à programmer avec l'intégration de CLR dans SQL Server et n'est nullement exhaustive.</span><span class="sxs-lookup"><span data-stu-id="fd43a-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="fd43a-111">Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="fd43a-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="fd43a-112">**Documentation SQL Server**</span><span class="sxs-lookup"><span data-stu-id="fd43a-112">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="fd43a-113">Vue d’ensemble de l’intégration du CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="fd43a-113">Common Language Runtime (CLR) Integration Overview</span></span>](/sql/relational-databases/clr-integration/common-language-runtime-integration-overview)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="fd43a-114">Activation de l'intégration du CLR</span><span class="sxs-lookup"><span data-stu-id="fd43a-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="fd43a-115">La fonctionnalité d’intégration de Common Language Runtime (CLR) est désactivée par défaut dans Microsoft SQL Server et doit être activée afin d’utiliser des objets implémentés à l’aide de l’intégration de CLR.</span><span class="sxs-lookup"><span data-stu-id="fd43a-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="fd43a-116">Pour activer l'intégration de CLR à l'aide de Transact-SQL, utilisez l'option `clr enabled` de la procédure stockée `sp_configure` comme indiqué :</span><span class="sxs-lookup"><span data-stu-id="fd43a-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```sql  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="fd43a-117">Vous pouvez désactiver l'intégration de CLR en attribuant à l'option `clr enabled` la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="fd43a-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="fd43a-118">Lorsque vous désactivez l'intégration de CLR, SQL Server arrête d'exécuter toutes les routines CLR et décharge tous les domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="fd43a-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="fd43a-119">Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="fd43a-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="fd43a-120">**Documentation SQL Server**</span><span class="sxs-lookup"><span data-stu-id="fd43a-120">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="fd43a-121">Activation de l’intégration du CLR</span><span class="sxs-lookup"><span data-stu-id="fd43a-121">Enabling CLR Integration</span></span>](/sql/relational-databases/clr-integration/clr-integration-enabling)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="fd43a-122">Déploiement d'un assembly CLR</span><span class="sxs-lookup"><span data-stu-id="fd43a-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="fd43a-123">Une fois que les méthodes CLR ont été testées et vérifiées sur le serveur de test, elles peuvent être distribuées sur les serveurs de production à l'aide d'un script de déploiement.</span><span class="sxs-lookup"><span data-stu-id="fd43a-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="fd43a-124">Le script de déploiement peut être généré manuellement ou à l'aide de SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="fd43a-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="fd43a-125">Pour plus d’informations, consultez la version de SQL Server Documentation pour la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="fd43a-125">For more detailed information, see the version of SQL Server documentation for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="fd43a-126">**Documentation SQL Server**</span><span class="sxs-lookup"><span data-stu-id="fd43a-126">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="fd43a-127">Déploiement d’objets de base de données CLR</span><span class="sxs-lookup"><span data-stu-id="fd43a-127">Deploying CLR Database Objects</span></span>](/sql/relational-databases/clr-integration/deploying-clr-database-objects)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="fd43a-128">Sécurité de l'intégration du CLR</span><span class="sxs-lookup"><span data-stu-id="fd43a-128">CLR Integration Security</span></span>  
 <span data-ttu-id="fd43a-129">Le modèle de sécurité de l'intégration de Microsoft SQL Server avec le CLR Microsoft .NET Framework gère et sécurise l'accès entre différents types d'objets CLR et non CLR s'exécutant avec SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fd43a-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="fd43a-130">Ces objets peuvent être appelés par une instruction Transact-SQL ou un autre objet CLR en cours d'exécution sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="fd43a-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="fd43a-131">Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="fd43a-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="fd43a-132">**Documentation SQL Server**</span><span class="sxs-lookup"><span data-stu-id="fd43a-132">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="fd43a-133">Sécurité de l’intégration du CLR</span><span class="sxs-lookup"><span data-stu-id="fd43a-133">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="fd43a-134">Débogage d'un assembly CLR</span><span class="sxs-lookup"><span data-stu-id="fd43a-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="fd43a-135">Microsoft SQL Server prend en charge le débogage d'objets Transact-SQL et Common Language Runtime (CLR) dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="fd43a-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="fd43a-136">Le débogage fonctionne avec tous les langages : les utilisateurs peuvent accéder sans difficulté à des objets CLR à partir de Transact-SQL et inversement.</span><span class="sxs-lookup"><span data-stu-id="fd43a-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="fd43a-137">Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="fd43a-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="fd43a-138">**Documentation SQL Server**</span><span class="sxs-lookup"><span data-stu-id="fd43a-138">**SQL Server documentation**</span></span>  
  
- [<span data-ttu-id="fd43a-139">Débogage d’objets de base de données CLR</span><span class="sxs-lookup"><span data-stu-id="fd43a-139">Debugging CLR Database Objects</span></span>](/sql/relational-databases/clr-integration/debugging-clr-database-objects)  
  
## <a name="see-also"></a><span data-ttu-id="fd43a-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd43a-140">See also</span></span>

- [<span data-ttu-id="fd43a-141">Sécurité d’accès du code et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fd43a-141">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="fd43a-142">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fd43a-142">ADO.NET Overview</span></span>](../ado-net-overview.md)
