---
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 23262427c3da730eaf930a8b483c7c4d4ec3a3a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289839"
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="e93bf-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="e93bf-102">3508 - TrackingProfileNotFound</span></span>

## <a name="properties"></a><span data-ttu-id="e93bf-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e93bf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e93bf-104">id</span><span class="sxs-lookup"><span data-stu-id="e93bf-104">ID</span></span>|<span data-ttu-id="e93bf-105">3508</span><span class="sxs-lookup"><span data-stu-id="e93bf-105">3508</span></span>|  
|<span data-ttu-id="e93bf-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="e93bf-106">Keywords</span></span>|<span data-ttu-id="e93bf-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="e93bf-107">WFServices</span></span>|  
|<span data-ttu-id="e93bf-108">Level</span><span class="sxs-lookup"><span data-stu-id="e93bf-108">Level</span></span>|<span data-ttu-id="e93bf-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="e93bf-109">Verbose</span></span>|  
|<span data-ttu-id="e93bf-110">Channel</span><span class="sxs-lookup"><span data-stu-id="e93bf-110">Channel</span></span>|<span data-ttu-id="e93bf-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="e93bf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e93bf-112">Description</span><span class="sxs-lookup"><span data-stu-id="e93bf-112">Description</span></span>  

 <span data-ttu-id="e93bf-113">Indique si un TrackingProfile est introuvable dans le fichier de configuration ou un ActivityDefinitionId ne correspond pas au modèle.</span><span class="sxs-lookup"><span data-stu-id="e93bf-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e93bf-114">Message</span><span class="sxs-lookup"><span data-stu-id="e93bf-114">Message</span></span>  

 <span data-ttu-id="e93bf-115">TrackingProfile « %1 » pour le ActivityDefinitionId « %2 » introuvable.</span><span class="sxs-lookup"><span data-stu-id="e93bf-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="e93bf-116">TrackingProfile est introuvable dans le fichier de configuration ou ActivityDefinitionId ne correspond pas.</span><span class="sxs-lookup"><span data-stu-id="e93bf-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e93bf-117">Détails</span><span class="sxs-lookup"><span data-stu-id="e93bf-117">Details</span></span>  
  
|<span data-ttu-id="e93bf-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e93bf-118">Data Item Name</span></span>|<span data-ttu-id="e93bf-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e93bf-119">Data Item Type</span></span>|<span data-ttu-id="e93bf-120">Description</span><span class="sxs-lookup"><span data-stu-id="e93bf-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e93bf-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="e93bf-121">TrackingProfile</span></span>|<span data-ttu-id="e93bf-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e93bf-122">xs:string</span></span>|<span data-ttu-id="e93bf-123">Nom du modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="e93bf-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="e93bf-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="e93bf-124">ActivityDefinitionId</span></span>|<span data-ttu-id="e93bf-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e93bf-125">xs:string</span></span>|<span data-ttu-id="e93bf-126">ID de définition d'activité.</span><span class="sxs-lookup"><span data-stu-id="e93bf-126">The activity definition id.</span></span>|  
|<span data-ttu-id="e93bf-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e93bf-127">AppDomain</span></span>|<span data-ttu-id="e93bf-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e93bf-128">xs:string</span></span>|<span data-ttu-id="e93bf-129">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e93bf-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
