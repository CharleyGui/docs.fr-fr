---
title: Cycle de vie de la programmation de base
description: En savoir plus sur les tâches de création d’une application WCF. WCF permet aux applications de communiquer sur le même ordinateur, sur des réseaux ou sur différentes plateformes d’application.
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: f958bd06f617a5648b31332ebe9e7662d45cd241
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294844"
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="da6a3-104">Cycle de vie de la programmation de base</span><span class="sxs-lookup"><span data-stu-id="da6a3-104">Basic Programming Lifecycle</span></span>

<span data-ttu-id="da6a3-105">Windows Communication Foundation (WCF) permet aux applications de communiquer si elles se trouvent sur le même ordinateur, sur Internet ou sur différentes plateformes d’application.</span><span class="sxs-lookup"><span data-stu-id="da6a3-105">Windows Communication Foundation (WCF) enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="da6a3-106">Cette rubrique décrit les tâches requises pour générer une application WCF.</span><span class="sxs-lookup"><span data-stu-id="da6a3-106">This topic outlines the tasks that are required to build a WCF application.</span></span> <span data-ttu-id="da6a3-107">Pour obtenir un exemple d’application fonctionnel, consultez [prise en main didacticiel](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="da6a3-107">For a working sample application, see [Getting Started Tutorial](getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="da6a3-108">Tâches de base</span><span class="sxs-lookup"><span data-stu-id="da6a3-108">The Basic Tasks</span></span>  

 <span data-ttu-id="da6a3-109">Les tâches de base à accomplir sont les suivantes, dans l’ordre :</span><span class="sxs-lookup"><span data-stu-id="da6a3-109">The basic tasks to perform are, in order:</span></span>  
  
1. <span data-ttu-id="da6a3-110">Définition du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="da6a3-110">Define the service contract.</span></span> <span data-ttu-id="da6a3-111">Un contrat de service spécifie la signature d'un service, les données qu'il échange et les autres données requises contractuellement.</span><span class="sxs-lookup"><span data-stu-id="da6a3-111">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="da6a3-112">Pour plus d’informations, consultez [conception de contrats de service](designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="da6a3-112">For more information, see [Designing Service Contracts](designing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="da6a3-113">Implémentation du contrat.</span><span class="sxs-lookup"><span data-stu-id="da6a3-113">Implement the contract.</span></span> <span data-ttu-id="da6a3-114">Pour implémenter un contrat de service, créez une classe qui implémente le contrat et spécifiez les comportements personnalisés requis pour le runtime.</span><span class="sxs-lookup"><span data-stu-id="da6a3-114">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="da6a3-115">Pour plus d’informations, consultez [implémentation de contrats de service](implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="da6a3-115">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
3. <span data-ttu-id="da6a3-116">Configuration du service en spécifiant les informations de points de terminaison et d'autres informations de comportement.</span><span class="sxs-lookup"><span data-stu-id="da6a3-116">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="da6a3-117">Pour plus d’informations, consultez [Configuration des services](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="da6a3-117">For more information, see [Configuring Services](configuring-services.md).</span></span>  
  
4. <span data-ttu-id="da6a3-118">Hébergement du service.</span><span class="sxs-lookup"><span data-stu-id="da6a3-118">Host the service.</span></span> <span data-ttu-id="da6a3-119">Pour plus d’informations, consultez [services d’hébergement](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="da6a3-119">For more information, see [Hosting Services](hosting-services.md).</span></span>  
  
5. <span data-ttu-id="da6a3-120">Création d'une application cliente.</span><span class="sxs-lookup"><span data-stu-id="da6a3-120">Build a client application.</span></span> <span data-ttu-id="da6a3-121">Pour plus d’informations, consultez [génération de clients](building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="da6a3-121">For more information, see [Building Clients](building-clients.md).</span></span>  
  
 <span data-ttu-id="da6a3-122">Bien que les rubriques de cette section suivent cet ordre, certains scénarios ne commencent pas au début.</span><span class="sxs-lookup"><span data-stu-id="da6a3-122">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="da6a3-123">Par exemple, si vous souhaitez générer un client pour un service préexistant, démarrez à l'étape 5.</span><span class="sxs-lookup"><span data-stu-id="da6a3-123">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="da6a3-124">Autrement, si vous générez un service que d'autres utiliseront, vous pouvez ignorer l'étape 5.</span><span class="sxs-lookup"><span data-stu-id="da6a3-124">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="da6a3-125">Une fois que vous êtes familiarisé avec le développement de contrats de service, vous pouvez également lire la [Présentation de l’extensibilité](introduction-to-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="da6a3-125">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](introduction-to-extensibility.md).</span></span> <span data-ttu-id="da6a3-126">Si vous rencontrez des problèmes avec votre service, vérifiez le Guide de [démarrage rapide de WCF Troubleshooting](wcf-troubleshooting-quickstart.md) pour déterminer si d’autres ont des problèmes identiques ou similaires.</span><span class="sxs-lookup"><span data-stu-id="da6a3-126">If you have problems with your service, check [WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da6a3-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da6a3-127">See also</span></span>

- [<span data-ttu-id="da6a3-128">Implémentation de contrats de service</span><span class="sxs-lookup"><span data-stu-id="da6a3-128">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
