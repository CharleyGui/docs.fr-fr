---
title: Définition des services de données WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: 26cfee95f7cd3b956ff263d90b713e9d70b98202
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975334"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="eb3f7-102">Définition des services de données WCF</span><span class="sxs-lookup"><span data-stu-id="eb3f7-102">Defining WCF Data Services</span></span>

<span data-ttu-id="eb3f7-103">Cette section décrit comment créer et configurer des WCF Data Services pour exposer des données en tant que flux Open Data Protocol (OData).</span><span class="sxs-lookup"><span data-stu-id="eb3f7-103">This section describes how to create and configure WCF Data Services to expose data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="eb3f7-104">Pour plus d’informations sur les étapes de base nécessaires à la création d’un service de données, consultez [exposition de vos données en tant que service](exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="eb3f7-104">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="eb3f7-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="eb3f7-105">In This Section</span></span>

 [<span data-ttu-id="eb3f7-106">Configuration du service de données</span><span class="sxs-lookup"><span data-stu-id="eb3f7-106">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="eb3f7-107">Décrit les options de configuration du service de données fournies par WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="eb3f7-107">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="eb3f7-108">Fournisseurs de services de données</span><span class="sxs-lookup"><span data-stu-id="eb3f7-108">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)

 <span data-ttu-id="eb3f7-109">Décrit les modèles de fournisseur pour l'exposition de données sous la forme d'un service de données.</span><span class="sxs-lookup"><span data-stu-id="eb3f7-109">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="eb3f7-110">Opérations de service</span><span class="sxs-lookup"><span data-stu-id="eb3f7-110">Service Operations</span></span>](service-operations-wcf-data-services.md)

 <span data-ttu-id="eb3f7-111">Décrit comment définir des opérations de service qui exposent des méthodes sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="eb3f7-111">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="eb3f7-112">Personnalisation des flux</span><span class="sxs-lookup"><span data-stu-id="eb3f7-112">Feed Customization</span></span>](feed-customization-wcf-data-services.md)

 <span data-ttu-id="eb3f7-113">Décrit comment créer un mappage entre les entités du modèle de données défini par le fournisseur de services de données et les éléments du flux de données.</span><span class="sxs-lookup"><span data-stu-id="eb3f7-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="eb3f7-114">Intercepteurs</span><span class="sxs-lookup"><span data-stu-id="eb3f7-114">Interceptors</span></span>](interceptors-wcf-data-services.md)

 <span data-ttu-id="eb3f7-115">Décrit comment définir des méthodes d'intercepteur pour appliquer une logique métier personnalisée sur des requêtes au service de données.</span><span class="sxs-lookup"><span data-stu-id="eb3f7-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="eb3f7-116">Développement et déploiement de WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="eb3f7-116">Developing and Deploying WCF Data Services</span></span>](developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="eb3f7-117">Explique comment développer et déployer un service de données à l'aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="eb3f7-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="eb3f7-118">Sécurisation de WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="eb3f7-118">Securing WCF Data Services</span></span>](securing-wcf-data-services.md)

 <span data-ttu-id="eb3f7-119">Décrit l'authentification et l'autorisation du service de données et fournit des considérations sur la sécurité.</span><span class="sxs-lookup"><span data-stu-id="eb3f7-119">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="eb3f7-120">Hébergement du service de données</span><span class="sxs-lookup"><span data-stu-id="eb3f7-120">Hosting the Data Service</span></span>](hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="eb3f7-121">Décrit comment sélectionner un hôte pour votre service de données.</span><span class="sxs-lookup"><span data-stu-id="eb3f7-121">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="eb3f7-122">Gestion de version d’un service de données</span><span class="sxs-lookup"><span data-stu-id="eb3f7-122">Data Service Versioning</span></span>](data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="eb3f7-123">Décrit comment utiliser les différentes versions d’OData.</span><span class="sxs-lookup"><span data-stu-id="eb3f7-123">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="eb3f7-124">Détails relatifs à l’implémentation du protocole WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="eb3f7-124">WCF Data Services Protocol Implementation Details</span></span>](wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="eb3f7-125">Décrit les fonctionnalités facultatives du protocole OData qui ne sont pas implémentées actuellement par WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="eb3f7-125">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb3f7-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb3f7-126">See also</span></span>

- [<span data-ttu-id="eb3f7-127">Bibliothèque cliente WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="eb3f7-127">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="eb3f7-128">Accès aux ressources d’un service de données</span><span class="sxs-lookup"><span data-stu-id="eb3f7-128">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="eb3f7-129">Bien démarrer</span><span class="sxs-lookup"><span data-stu-id="eb3f7-129">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
