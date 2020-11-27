---
title: 221 - MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 47e871b70e3ef2419543b4710c2988736665cb46
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263098"
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="f35a0-102">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="f35a0-102">221 - MessageReceivedFromTransport</span></span>

## <a name="properties"></a><span data-ttu-id="f35a0-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f35a0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f35a0-104">id</span><span class="sxs-lookup"><span data-stu-id="f35a0-104">ID</span></span>|<span data-ttu-id="f35a0-105">221</span><span class="sxs-lookup"><span data-stu-id="f35a0-105">221</span></span>|  
|<span data-ttu-id="f35a0-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="f35a0-106">Keywords</span></span>|<span data-ttu-id="f35a0-107">EndToEndMonitoring, Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f35a0-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f35a0-108">Level</span><span class="sxs-lookup"><span data-stu-id="f35a0-108">Level</span></span>|<span data-ttu-id="f35a0-109">Informations</span><span class="sxs-lookup"><span data-stu-id="f35a0-109">Information</span></span>|  
|<span data-ttu-id="f35a0-110">Channel</span><span class="sxs-lookup"><span data-stu-id="f35a0-110">Channel</span></span>|<span data-ttu-id="f35a0-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="f35a0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f35a0-112">Description</span><span class="sxs-lookup"><span data-stu-id="f35a0-112">Description</span></span>  

 <span data-ttu-id="f35a0-113">Cet événement est émis lorsque le modèle de service reçoit un message du transport.</span><span class="sxs-lookup"><span data-stu-id="f35a0-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f35a0-114">Message</span><span class="sxs-lookup"><span data-stu-id="f35a0-114">Message</span></span>  

 <span data-ttu-id="f35a0-115">Le répartiteur a reçu un message du transport.</span><span class="sxs-lookup"><span data-stu-id="f35a0-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="f35a0-116">ID de corrélation == '%1.'</span><span class="sxs-lookup"><span data-stu-id="f35a0-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f35a0-117">Détails</span><span class="sxs-lookup"><span data-stu-id="f35a0-117">Details</span></span>  
  
|<span data-ttu-id="f35a0-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f35a0-118">Data Item Name</span></span>|<span data-ttu-id="f35a0-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f35a0-119">Data Item Type</span></span>|<span data-ttu-id="f35a0-120">Description</span><span class="sxs-lookup"><span data-stu-id="f35a0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f35a0-121">ID de corrélation :</span><span class="sxs-lookup"><span data-stu-id="f35a0-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="f35a0-122">ID d'activité utilisé pour mettre en corrélation un événement `MessageSentToTransport` provenant d'un service ou d'un client avec son événement `MessageReceivedFromTransport` correspondant à l'autre bout.</span><span class="sxs-lookup"><span data-stu-id="f35a0-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="f35a0-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="f35a0-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="f35a0-124">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="f35a0-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f35a0-125">Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ».</span><span class="sxs-lookup"><span data-stu-id="f35a0-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f35a0-126">Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="f35a0-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f35a0-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f35a0-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f35a0-128">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f35a0-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
