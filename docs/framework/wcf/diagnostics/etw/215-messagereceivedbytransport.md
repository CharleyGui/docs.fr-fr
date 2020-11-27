---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: 2f247e751a0690f13d059eff29d633c6d047775d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279075"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="ace6c-102">215 - MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="ace6c-102">215 - MessageReceivedByTransport</span></span>

## <a name="properties"></a><span data-ttu-id="ace6c-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ace6c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ace6c-104">id</span><span class="sxs-lookup"><span data-stu-id="ace6c-104">ID</span></span>|<span data-ttu-id="ace6c-105">215</span><span class="sxs-lookup"><span data-stu-id="ace6c-105">215</span></span>|  
|<span data-ttu-id="ace6c-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="ace6c-106">Keywords</span></span>|<span data-ttu-id="ace6c-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ace6c-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ace6c-108">Level</span><span class="sxs-lookup"><span data-stu-id="ace6c-108">Level</span></span>|<span data-ttu-id="ace6c-109">Informations</span><span class="sxs-lookup"><span data-stu-id="ace6c-109">Information</span></span>|  
|<span data-ttu-id="ace6c-110">Channel</span><span class="sxs-lookup"><span data-stu-id="ace6c-110">Channel</span></span>|<span data-ttu-id="ace6c-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="ace6c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ace6c-112">Description</span><span class="sxs-lookup"><span data-stu-id="ace6c-112">Description</span></span>  

 <span data-ttu-id="ace6c-113">Cet événement se produit lorsqu'un transport basé sur TCP reçoit un message.</span><span class="sxs-lookup"><span data-stu-id="ace6c-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="ace6c-114">Notez qu'au niveau du transport, plusieurs messages peuvent être échangés entre clients et services pour une seule opération.</span><span class="sxs-lookup"><span data-stu-id="ace6c-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="ace6c-115">Cela peut être dû au comportement d'infrastructure, la sécurité étant un bon exemple.</span><span class="sxs-lookup"><span data-stu-id="ace6c-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="ace6c-116">Par conséquent, le nombre d'événements `MessageReceivedByTransport` émis varie en fonction de la liaison de votre service et de sa configuration.</span><span class="sxs-lookup"><span data-stu-id="ace6c-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ace6c-117">Cet événement n'est pas émis pour les transports unidirectionnels.</span><span class="sxs-lookup"><span data-stu-id="ace6c-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ace6c-118">Message</span><span class="sxs-lookup"><span data-stu-id="ace6c-118">Message</span></span>  

 <span data-ttu-id="ace6c-119">Le transport a reçu un message de '%1'.</span><span class="sxs-lookup"><span data-stu-id="ace6c-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ace6c-120">Détails</span><span class="sxs-lookup"><span data-stu-id="ace6c-120">Details</span></span>  
  
|<span data-ttu-id="ace6c-121">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ace6c-121">Data Item Name</span></span>|<span data-ttu-id="ace6c-122">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ace6c-122">Data Item Type</span></span>|<span data-ttu-id="ace6c-123">Description</span><span class="sxs-lookup"><span data-stu-id="ace6c-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ace6c-124">Adresse d'écoute</span><span class="sxs-lookup"><span data-stu-id="ace6c-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="ace6c-125">Adresse qui a reçu le message.</span><span class="sxs-lookup"><span data-stu-id="ace6c-125">The address that received the message.</span></span>|  
|<span data-ttu-id="ace6c-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="ace6c-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="ace6c-127">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="ace6c-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ace6c-128">Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ».</span><span class="sxs-lookup"><span data-stu-id="ace6c-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ace6c-129">Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="ace6c-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ace6c-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ace6c-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ace6c-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ace6c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
