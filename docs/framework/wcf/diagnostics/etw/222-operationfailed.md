---
title: 222 - OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: 64b41ee78e943ca16eaa791133454ec62ccf6ed8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263085"
---
# <a name="222---operationfailed"></a><span data-ttu-id="ef0b2-102">222 - OperationFailed</span><span class="sxs-lookup"><span data-stu-id="ef0b2-102">222 - OperationFailed</span></span>

## <a name="properties"></a><span data-ttu-id="ef0b2-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ef0b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef0b2-104">id</span><span class="sxs-lookup"><span data-stu-id="ef0b2-104">ID</span></span>|<span data-ttu-id="ef0b2-105">222</span><span class="sxs-lookup"><span data-stu-id="ef0b2-105">222</span></span>|  
|<span data-ttu-id="ef0b2-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="ef0b2-106">Keywords</span></span>|<span data-ttu-id="ef0b2-107">EndToEndMonitoring, HealthMonitoring, Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ef0b2-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ef0b2-108">Level</span><span class="sxs-lookup"><span data-stu-id="ef0b2-108">Level</span></span>|<span data-ttu-id="ef0b2-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="ef0b2-109">Warning</span></span>|  
|<span data-ttu-id="ef0b2-110">Channel</span><span class="sxs-lookup"><span data-stu-id="ef0b2-110">Channel</span></span>|<span data-ttu-id="ef0b2-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="ef0b2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ef0b2-112">Description</span><span class="sxs-lookup"><span data-stu-id="ef0b2-112">Description</span></span>  

 <span data-ttu-id="ef0b2-113">Cet événement est émis lorsque l'`OperationInvoker` par défaut du modèle de service a rencontré une exception lors de l'appel de sa méthode.</span><span class="sxs-lookup"><span data-stu-id="ef0b2-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="ef0b2-114">Notez que les exceptions dérivant de `FaultException` empêchent cet événement d'être émis.</span><span class="sxs-lookup"><span data-stu-id="ef0b2-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ef0b2-115">Message</span><span class="sxs-lookup"><span data-stu-id="ef0b2-115">Message</span></span>  

 <span data-ttu-id="ef0b2-116">La méthode '%1' a levé une exception non gérée lors de l'appel effectué par l'OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="ef0b2-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="ef0b2-117">Durée de l'appel de méthode : '%2' ms.</span><span class="sxs-lookup"><span data-stu-id="ef0b2-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ef0b2-118">Détails</span><span class="sxs-lookup"><span data-stu-id="ef0b2-118">Details</span></span>  
  
|<span data-ttu-id="ef0b2-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ef0b2-119">Data Item Name</span></span>|<span data-ttu-id="ef0b2-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ef0b2-120">Data Item Type</span></span>|<span data-ttu-id="ef0b2-121">Description</span><span class="sxs-lookup"><span data-stu-id="ef0b2-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ef0b2-122">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="ef0b2-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="ef0b2-123">Nom CLR de la méthode qui a été appelée par l'`OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="ef0b2-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="ef0b2-124">Duration</span><span class="sxs-lookup"><span data-stu-id="ef0b2-124">Duration</span></span>|`xs:long`|<span data-ttu-id="ef0b2-125">Durée, en millisecondes, prise par l'`OperationInvoker` pour appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="ef0b2-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="ef0b2-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="ef0b2-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="ef0b2-127">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="ef0b2-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ef0b2-128">Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ».</span><span class="sxs-lookup"><span data-stu-id="ef0b2-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ef0b2-129">Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="ef0b2-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ef0b2-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ef0b2-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ef0b2-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ef0b2-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
