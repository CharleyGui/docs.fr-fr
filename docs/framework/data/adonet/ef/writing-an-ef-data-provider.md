---
title: Écriture d'un fournisseur de données Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 7841a33bf40c00ed3691a5416aae16d673bf8d1c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586736"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="81bb0-102">Écriture d'un fournisseur de données Entity Framework</span><span class="sxs-lookup"><span data-stu-id="81bb0-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="81bb0-103">Cette section explique comment écrire un [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] fournisseur pour prendre en charge d’une source de données autres que SQL Server.</span><span class="sxs-lookup"><span data-stu-id="81bb0-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="81bb0-104">Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclut un fournisseur qui prend en charge de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="81bb0-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="81bb0-105">Présentation du modèle de fournisseur Entity Framework</span><span class="sxs-lookup"><span data-stu-id="81bb0-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="81bb0-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] est une base de données indépendante et il est possible d'écrire un fournisseur à l'aide du modèle de fournisseur ADO.NET pour se connecter à un jeu divers de sources de données.</span><span class="sxs-lookup"><span data-stu-id="81bb0-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="81bb0-107">Le fournisseur de données Entity Framework (construit à l’aide du modèle de fournisseur de données ADO.NET) effectue les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="81bb0-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
- <span data-ttu-id="81bb0-108">Mappe des types primitifs d'Entity Data Model (EDM) aux types de fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="81bb0-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
- <span data-ttu-id="81bb0-109">Expose des fonctions spécifiques au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="81bb0-109">Exposes provider-specific functions.</span></span>  
  
- <span data-ttu-id="81bb0-110">Génère des commandes spécifiques au fournisseur pour un DbQueryCommandTree donné afin de prendre en charge des requêtes [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81bb0-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
- <span data-ttu-id="81bb0-111">Génère des commandes de mise à jour spécifiques au fournisseur pour un DbModificationCommandTree donné pour prendre en charge les mises à jour via [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81bb0-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
- <span data-ttu-id="81bb0-112">Expose des fichiers de mappage pour la définition de schéma du magasin afin de prendre en charge la génération d'un modèle selon une base de données.</span><span class="sxs-lookup"><span data-stu-id="81bb0-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
- <span data-ttu-id="81bb0-113">Expose des métadonnées (tables et vues, par exemple) via un modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="81bb0-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="81bb0-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="81bb0-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="81bb0-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="81bb0-115">Sample</span></span>  
 <span data-ttu-id="81bb0-116">Consultez le [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) pour obtenir un exemple d’un [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] fournisseur qui prend en charge d’une source de données autres que SQL Server.</span><span class="sxs-lookup"><span data-stu-id="81bb0-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81bb0-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="81bb0-117">In This Section</span></span>  
 [<span data-ttu-id="81bb0-118">Génération SQL</span><span class="sxs-lookup"><span data-stu-id="81bb0-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="81bb0-119">Génération SQL de modification</span><span class="sxs-lookup"><span data-stu-id="81bb0-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="81bb0-120">Spécification de manifeste du fournisseur</span><span class="sxs-lookup"><span data-stu-id="81bb0-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="81bb0-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81bb0-121">See also</span></span>

- [<span data-ttu-id="81bb0-122">Utilisation des fournisseurs de données</span><span class="sxs-lookup"><span data-stu-id="81bb0-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
