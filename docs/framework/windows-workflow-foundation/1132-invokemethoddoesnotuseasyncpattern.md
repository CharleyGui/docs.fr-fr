---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 9249bdd0fe996ee7c1b04783ac8fef2c48063cc0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294155"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="509b7-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="509b7-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="509b7-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="509b7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="509b7-104">id</span><span class="sxs-lookup"><span data-stu-id="509b7-104">ID</span></span>|<span data-ttu-id="509b7-105">1132</span><span class="sxs-lookup"><span data-stu-id="509b7-105">1132</span></span>|  
|<span data-ttu-id="509b7-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="509b7-106">Keywords</span></span>|<span data-ttu-id="509b7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="509b7-107">WFRuntime</span></span>|  
|<span data-ttu-id="509b7-108">Level</span><span class="sxs-lookup"><span data-stu-id="509b7-108">Level</span></span>|<span data-ttu-id="509b7-109">Informations</span><span class="sxs-lookup"><span data-stu-id="509b7-109">Information</span></span>|  
|<span data-ttu-id="509b7-110">Channel</span><span class="sxs-lookup"><span data-stu-id="509b7-110">Channel</span></span>|<span data-ttu-id="509b7-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="509b7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="509b7-112">Description</span><span class="sxs-lookup"><span data-stu-id="509b7-112">Description</span></span>  

 <span data-ttu-id="509b7-113">Pendant l’étape CacheMetadata, l’activité InvokeMethod indique qu’elle n’utilise pas le modèle asynchrone lors de l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="509b7-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="509b7-114">Message</span><span class="sxs-lookup"><span data-stu-id="509b7-114">Message</span></span>  

 <span data-ttu-id="509b7-115">InvokeMethod « %1 » - la méthode n’utilise pas un modèle asynchrone.</span><span class="sxs-lookup"><span data-stu-id="509b7-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="509b7-116">Détails</span><span class="sxs-lookup"><span data-stu-id="509b7-116">Details</span></span>  
  
|<span data-ttu-id="509b7-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="509b7-117">Data Item Name</span></span>|<span data-ttu-id="509b7-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="509b7-118">Data Item Type</span></span>|<span data-ttu-id="509b7-119">Description</span><span class="sxs-lookup"><span data-stu-id="509b7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="509b7-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="509b7-120">InvokeMethod</span></span>|<span data-ttu-id="509b7-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="509b7-121">xs:string</span></span>|<span data-ttu-id="509b7-122">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="509b7-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="509b7-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="509b7-123">AppDomain</span></span>|<span data-ttu-id="509b7-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="509b7-124">xs:string</span></span>|<span data-ttu-id="509b7-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="509b7-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
