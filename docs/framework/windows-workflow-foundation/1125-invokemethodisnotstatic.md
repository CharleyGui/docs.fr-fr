---
title: 1125 - InvokeMethodIsNotStatic
ms.date: 03/30/2017
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
ms.openlocfilehash: 0405b4e1207db5c056fbd478b98c408258daf0c3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294207"
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="53044-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="53044-102">1125 - InvokeMethodIsNotStatic</span></span>

## <a name="properties"></a><span data-ttu-id="53044-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="53044-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="53044-104">id</span><span class="sxs-lookup"><span data-stu-id="53044-104">ID</span></span>|<span data-ttu-id="53044-105">1 125</span><span class="sxs-lookup"><span data-stu-id="53044-105">1125</span></span>|  
|<span data-ttu-id="53044-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="53044-106">Keywords</span></span>|<span data-ttu-id="53044-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="53044-107">WFRuntime</span></span>|  
|<span data-ttu-id="53044-108">Level</span><span class="sxs-lookup"><span data-stu-id="53044-108">Level</span></span>|<span data-ttu-id="53044-109">Informations</span><span class="sxs-lookup"><span data-stu-id="53044-109">Information</span></span>|  
|<span data-ttu-id="53044-110">Channel</span><span class="sxs-lookup"><span data-stu-id="53044-110">Channel</span></span>|<span data-ttu-id="53044-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="53044-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="53044-112">Description</span><span class="sxs-lookup"><span data-stu-id="53044-112">Description</span></span>  

 <span data-ttu-id="53044-113">Pendant l'étape CacheMetadata, l'activité InvokeMethod indique que la méthode à appeler n'est pas statique.</span><span class="sxs-lookup"><span data-stu-id="53044-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="53044-114">Message</span><span class="sxs-lookup"><span data-stu-id="53044-114">Message</span></span>  

 <span data-ttu-id="53044-115">InvokeMethod « %1 » - la méthode n'est pas statique.</span><span class="sxs-lookup"><span data-stu-id="53044-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="53044-116">Détails</span><span class="sxs-lookup"><span data-stu-id="53044-116">Details</span></span>  
  
|<span data-ttu-id="53044-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="53044-117">Data Item Name</span></span>|<span data-ttu-id="53044-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="53044-118">Data Item Type</span></span>|<span data-ttu-id="53044-119">Description</span><span class="sxs-lookup"><span data-stu-id="53044-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="53044-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="53044-120">InvokeMethod</span></span>|<span data-ttu-id="53044-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="53044-121">xs:string</span></span>|<span data-ttu-id="53044-122">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="53044-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="53044-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="53044-123">AppDomain</span></span>|<span data-ttu-id="53044-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="53044-124">xs:string</span></span>|<span data-ttu-id="53044-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="53044-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
