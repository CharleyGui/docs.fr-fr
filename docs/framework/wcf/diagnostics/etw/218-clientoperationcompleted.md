---
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: d74aa77aff7b45b50f6891c999889011d9e03381
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278854"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="1614e-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="1614e-102">218 - ClientOperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="1614e-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1614e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1614e-104">id</span><span class="sxs-lookup"><span data-stu-id="1614e-104">ID</span></span>|<span data-ttu-id="1614e-105">218</span><span class="sxs-lookup"><span data-stu-id="1614e-105">218</span></span>|  
|<span data-ttu-id="1614e-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="1614e-106">Keywords</span></span>|<span data-ttu-id="1614e-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1614e-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1614e-108">Level</span><span class="sxs-lookup"><span data-stu-id="1614e-108">Level</span></span>|<span data-ttu-id="1614e-109">Informations</span><span class="sxs-lookup"><span data-stu-id="1614e-109">Information</span></span>|  
|<span data-ttu-id="1614e-110">Channel</span><span class="sxs-lookup"><span data-stu-id="1614e-110">Channel</span></span>|<span data-ttu-id="1614e-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="1614e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1614e-112">Description</span><span class="sxs-lookup"><span data-stu-id="1614e-112">Description</span></span>  

 <span data-ttu-id="1614e-113">Cet événement est émis par les clients juste après la fin d'une opération.</span><span class="sxs-lookup"><span data-stu-id="1614e-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="1614e-114">Dans le cas des opérations monodirectionnelles, il est émis juste après l'envoi réussi du message.</span><span class="sxs-lookup"><span data-stu-id="1614e-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="1614e-115">Dans le cas des opérations demande-réponse, il est émis juste après la réception de la réponse.</span><span class="sxs-lookup"><span data-stu-id="1614e-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1614e-116">Message</span><span class="sxs-lookup"><span data-stu-id="1614e-116">Message</span></span>  

 <span data-ttu-id="1614e-117">Le client a terminé d'exécuter l'action '%1' associée au contrat '%2'.</span><span class="sxs-lookup"><span data-stu-id="1614e-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="1614e-118">Le message a été envoyé à '%3'.</span><span class="sxs-lookup"><span data-stu-id="1614e-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1614e-119">Détails</span><span class="sxs-lookup"><span data-stu-id="1614e-119">Details</span></span>  
  
|<span data-ttu-id="1614e-120">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1614e-120">Data Item Name</span></span>|<span data-ttu-id="1614e-121">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1614e-121">Data Item Type</span></span>|<span data-ttu-id="1614e-122">Description</span><span class="sxs-lookup"><span data-stu-id="1614e-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1614e-123">Action</span><span class="sxs-lookup"><span data-stu-id="1614e-123">Action</span></span>|<span data-ttu-id="1614e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="1614e-124">xs:string</span></span>|<span data-ttu-id="1614e-125">En-tête d'action SOAP du message sortant.</span><span class="sxs-lookup"><span data-stu-id="1614e-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="1614e-126">Nom de contrat</span><span class="sxs-lookup"><span data-stu-id="1614e-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="1614e-127">Nom du contrat.</span><span class="sxs-lookup"><span data-stu-id="1614e-127">The name of the contract.</span></span> <span data-ttu-id="1614e-128">Exemple : ICalculator.</span><span class="sxs-lookup"><span data-stu-id="1614e-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="1614e-129">Destination</span><span class="sxs-lookup"><span data-stu-id="1614e-129">Destination</span></span>|`xs:string`|<span data-ttu-id="1614e-130">Adresse du point de terminaison de service auquel le message a été envoyé.</span><span class="sxs-lookup"><span data-stu-id="1614e-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="1614e-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="1614e-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="1614e-132">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="1614e-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1614e-133">Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ».</span><span class="sxs-lookup"><span data-stu-id="1614e-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1614e-134">Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="1614e-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1614e-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1614e-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1614e-136">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1614e-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
