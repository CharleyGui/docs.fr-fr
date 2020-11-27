---
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 43ec434064f768fc976232c6d3013f17c80fe053
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267167"
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="efb67-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="efb67-102">4212 - LockRetryTimeout</span></span>

## <a name="properties"></a><span data-ttu-id="efb67-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="efb67-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="efb67-104">id</span><span class="sxs-lookup"><span data-stu-id="efb67-104">ID</span></span>|<span data-ttu-id="efb67-105">4212</span><span class="sxs-lookup"><span data-stu-id="efb67-105">4212</span></span>|  
|<span data-ttu-id="efb67-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="efb67-106">Keywords</span></span>|<span data-ttu-id="efb67-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="efb67-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="efb67-108">Level</span><span class="sxs-lookup"><span data-stu-id="efb67-108">Level</span></span>|<span data-ttu-id="efb67-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="efb67-109">Warning</span></span>|  
|<span data-ttu-id="efb67-110">Channel</span><span class="sxs-lookup"><span data-stu-id="efb67-110">Channel</span></span>|<span data-ttu-id="efb67-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="efb67-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="efb67-112">Description</span><span class="sxs-lookup"><span data-stu-id="efb67-112">Description</span></span>  

 <span data-ttu-id="efb67-113">Le fournisseur SQL a rencontré une expiration du délai d'attente lors de la tentative d'acquisition du verrou d'instance.</span><span class="sxs-lookup"><span data-stu-id="efb67-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="efb67-114">Message</span><span class="sxs-lookup"><span data-stu-id="efb67-114">Message</span></span>  

 <span data-ttu-id="efb67-115">Délai d’attente lors de l’acquisition du verrou d’instance.</span><span class="sxs-lookup"><span data-stu-id="efb67-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="efb67-116">L'opération ne s'est pas terminée dans le délai imparti de %1.</span><span class="sxs-lookup"><span data-stu-id="efb67-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="efb67-117">Le temps alloué à cette opération peut avoir été une partie d'un délai d'expiration plus long.</span><span class="sxs-lookup"><span data-stu-id="efb67-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="efb67-118">Détails</span><span class="sxs-lookup"><span data-stu-id="efb67-118">Details</span></span>  
  
|<span data-ttu-id="efb67-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="efb67-119">Data Item Name</span></span>|<span data-ttu-id="efb67-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="efb67-120">Data Item Type</span></span>|<span data-ttu-id="efb67-121">Description</span><span class="sxs-lookup"><span data-stu-id="efb67-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="efb67-122">Retarder</span><span class="sxs-lookup"><span data-stu-id="efb67-122">Delay</span></span>|<span data-ttu-id="efb67-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="efb67-123">xs:string</span></span>|<span data-ttu-id="efb67-124">Le délai entre les tentatives.</span><span class="sxs-lookup"><span data-stu-id="efb67-124">The delay between retries.</span></span>|  
|<span data-ttu-id="efb67-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="efb67-125">AppDomain</span></span>|<span data-ttu-id="efb67-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="efb67-126">xs:string</span></span>|<span data-ttu-id="efb67-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="efb67-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
