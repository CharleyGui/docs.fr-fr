---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ff8a1e099934f5bf71fef0afbb7e54c0d1851fae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267180"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="baf81-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="baf81-102">4211 - QueuingSqlRetry</span></span>

## <a name="properties"></a><span data-ttu-id="baf81-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="baf81-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="baf81-104">id</span><span class="sxs-lookup"><span data-stu-id="baf81-104">ID</span></span>|<span data-ttu-id="baf81-105">4211</span><span class="sxs-lookup"><span data-stu-id="baf81-105">4211</span></span>|  
|<span data-ttu-id="baf81-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="baf81-106">Keywords</span></span>|<span data-ttu-id="baf81-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="baf81-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="baf81-108">Level</span><span class="sxs-lookup"><span data-stu-id="baf81-108">Level</span></span>|<span data-ttu-id="baf81-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="baf81-109">Warning</span></span>|  
|<span data-ttu-id="baf81-110">Channel</span><span class="sxs-lookup"><span data-stu-id="baf81-110">Channel</span></span>|<span data-ttu-id="baf81-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="baf81-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="baf81-112">Description</span><span class="sxs-lookup"><span data-stu-id="baf81-112">Description</span></span>  

 <span data-ttu-id="baf81-113">Indique une nouvelle tentative de mise en file d'attente SQL.</span><span class="sxs-lookup"><span data-stu-id="baf81-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="baf81-114">Message</span><span class="sxs-lookup"><span data-stu-id="baf81-114">Message</span></span>  

 <span data-ttu-id="baf81-115">Mise en file d'attente d'une tentative SQL avec un retard de %1 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="baf81-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="baf81-116">Détails</span><span class="sxs-lookup"><span data-stu-id="baf81-116">Details</span></span>  
  
|<span data-ttu-id="baf81-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="baf81-117">Data Item Name</span></span>|<span data-ttu-id="baf81-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="baf81-118">Data Item Type</span></span>|<span data-ttu-id="baf81-119">Description</span><span class="sxs-lookup"><span data-stu-id="baf81-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="baf81-120">Retarder</span><span class="sxs-lookup"><span data-stu-id="baf81-120">Delay</span></span>|<span data-ttu-id="baf81-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="baf81-121">xs:string</span></span>|<span data-ttu-id="baf81-122">Le délai entre les tentatives.</span><span class="sxs-lookup"><span data-stu-id="baf81-122">The delay between retries.</span></span>|  
|<span data-ttu-id="baf81-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="baf81-123">AppDomain</span></span>|<span data-ttu-id="baf81-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="baf81-124">xs:string</span></span>|<span data-ttu-id="baf81-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="baf81-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
