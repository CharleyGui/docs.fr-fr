---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 2192b63b8a08657b69f6e3984f898bd6baddbc5f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294181"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="6af87-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="6af87-102">1131 - InvokeMethodUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="6af87-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="6af87-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6af87-104">id</span><span class="sxs-lookup"><span data-stu-id="6af87-104">ID</span></span>|<span data-ttu-id="6af87-105">1131</span><span class="sxs-lookup"><span data-stu-id="6af87-105">1131</span></span>|  
|<span data-ttu-id="6af87-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="6af87-106">Keywords</span></span>|<span data-ttu-id="6af87-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6af87-107">WFRuntime</span></span>|  
|<span data-ttu-id="6af87-108">Level</span><span class="sxs-lookup"><span data-stu-id="6af87-108">Level</span></span>|<span data-ttu-id="6af87-109">Informations</span><span class="sxs-lookup"><span data-stu-id="6af87-109">Information</span></span>|  
|<span data-ttu-id="6af87-110">Channel</span><span class="sxs-lookup"><span data-stu-id="6af87-110">Channel</span></span>|<span data-ttu-id="6af87-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="6af87-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6af87-112">Description</span><span class="sxs-lookup"><span data-stu-id="6af87-112">Description</span></span>  

 <span data-ttu-id="6af87-113">Pendant l’étape CacheMetadata, l’activité InvokeMethod indique qu’elle utilise le modèle asynchrone lors de l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="6af87-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6af87-114">Message</span><span class="sxs-lookup"><span data-stu-id="6af87-114">Message</span></span>  

 <span data-ttu-id="6af87-115">InvokeMethod « %1 » - la méthode utilise un modèle asynchrone de « %2 » et « %3 ».</span><span class="sxs-lookup"><span data-stu-id="6af87-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6af87-116">Détails</span><span class="sxs-lookup"><span data-stu-id="6af87-116">Details</span></span>  
  
|<span data-ttu-id="6af87-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="6af87-117">Data Item Name</span></span>|<span data-ttu-id="6af87-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="6af87-118">Data Item Type</span></span>|<span data-ttu-id="6af87-119">Description</span><span class="sxs-lookup"><span data-stu-id="6af87-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6af87-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="6af87-120">InvokeMethod</span></span>|<span data-ttu-id="6af87-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="6af87-121">xs:string</span></span>|<span data-ttu-id="6af87-122">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="6af87-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="6af87-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="6af87-123">BeginMethod</span></span>|<span data-ttu-id="6af87-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="6af87-124">xs:string</span></span>|<span data-ttu-id="6af87-125">Nom de la méthode Begin.</span><span class="sxs-lookup"><span data-stu-id="6af87-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="6af87-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="6af87-126">EndMethod</span></span>|<span data-ttu-id="6af87-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="6af87-127">xs:string</span></span>|<span data-ttu-id="6af87-128">Nom de la méthode End.</span><span class="sxs-lookup"><span data-stu-id="6af87-128">The name of the end method.</span></span>|  
|<span data-ttu-id="6af87-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6af87-129">AppDomain</span></span>|<span data-ttu-id="6af87-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="6af87-130">xs:string</span></span>|<span data-ttu-id="6af87-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6af87-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
