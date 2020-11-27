---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: bd3e7539922e6c430c4ffe5bd96ef1ac7dbd098f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261161"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="86f26-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="86f26-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="86f26-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="86f26-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86f26-104">id</span><span class="sxs-lookup"><span data-stu-id="86f26-104">ID</span></span>|<span data-ttu-id="86f26-105">3552</span><span class="sxs-lookup"><span data-stu-id="86f26-105">3552</span></span>|  
|<span data-ttu-id="86f26-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="86f26-106">Keywords</span></span>|<span data-ttu-id="86f26-107">Quota, WFServices</span><span class="sxs-lookup"><span data-stu-id="86f26-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="86f26-108">Level</span><span class="sxs-lookup"><span data-stu-id="86f26-108">Level</span></span>|<span data-ttu-id="86f26-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="86f26-109">Warning</span></span>|  
|<span data-ttu-id="86f26-110">Channel</span><span class="sxs-lookup"><span data-stu-id="86f26-110">Channel</span></span>|<span data-ttu-id="86f26-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="86f26-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="86f26-112">Description</span><span class="sxs-lookup"><span data-stu-id="86f26-112">Description</span></span>  

 <span data-ttu-id="86f26-113">Indique que la limitation « MaxPendingMessagesPerChannel » a été atteinte.</span><span class="sxs-lookup"><span data-stu-id="86f26-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="86f26-114">Message</span><span class="sxs-lookup"><span data-stu-id="86f26-114">Message</span></span>  

 <span data-ttu-id="86f26-115">La limitation « MaxPendingMessagesPerChannel » de « %1 » a été atteinte.</span><span class="sxs-lookup"><span data-stu-id="86f26-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="86f26-116">Pour accroître cette limite, modifiez la propriété MaxPendingMessagesPerChannel sur BufferedReceiveServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="86f26-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="86f26-117">Détails</span><span class="sxs-lookup"><span data-stu-id="86f26-117">Details</span></span>  
  
|<span data-ttu-id="86f26-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="86f26-118">Data Item Name</span></span>|<span data-ttu-id="86f26-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="86f26-119">Data Item Type</span></span>|<span data-ttu-id="86f26-120">Description</span><span class="sxs-lookup"><span data-stu-id="86f26-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="86f26-121">Limite</span><span class="sxs-lookup"><span data-stu-id="86f26-121">Limit</span></span>|<span data-ttu-id="86f26-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="86f26-122">xs:string</span></span>|<span data-ttu-id="86f26-123">La limite de MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="86f26-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="86f26-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="86f26-124">AppDomain</span></span>|<span data-ttu-id="86f26-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="86f26-125">xs:string</span></span>|<span data-ttu-id="86f26-126">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="86f26-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
