---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: f02a34673c51be6e0b127a64e4622131575d836f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275890"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="2969c-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="2969c-102">39458 - TrackingRecordTruncated</span></span>

## <a name="properties"></a><span data-ttu-id="2969c-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2969c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2969c-104">id</span><span class="sxs-lookup"><span data-stu-id="2969c-104">ID</span></span>|<span data-ttu-id="2969c-105">39458</span><span class="sxs-lookup"><span data-stu-id="2969c-105">39458</span></span>|  
|<span data-ttu-id="2969c-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="2969c-106">Keywords</span></span>|<span data-ttu-id="2969c-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="2969c-107">WFTracking</span></span>|  
|<span data-ttu-id="2969c-108">Level</span><span class="sxs-lookup"><span data-stu-id="2969c-108">Level</span></span>|<span data-ttu-id="2969c-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="2969c-109">Warning</span></span>|  
|<span data-ttu-id="2969c-110">Channel</span><span class="sxs-lookup"><span data-stu-id="2969c-110">Channel</span></span>|<span data-ttu-id="2969c-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="2969c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2969c-112">Description</span><span class="sxs-lookup"><span data-stu-id="2969c-112">Description</span></span>  

 <span data-ttu-id="2969c-113">Indique qu'un enregistrement de suivi a été tronqué.</span><span class="sxs-lookup"><span data-stu-id="2969c-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="2969c-114">Les données de variables/annotations/utilisateur ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="2969c-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2969c-115">Message</span><span class="sxs-lookup"><span data-stu-id="2969c-115">Message</span></span>  

 <span data-ttu-id="2969c-116">Enregistrement de suivi %1 tronqué écrit dans la session ETW avec le fournisseur %2.</span><span class="sxs-lookup"><span data-stu-id="2969c-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="2969c-117">Les données de variables/annotations/utilisateur ont été supprimées</span><span class="sxs-lookup"><span data-stu-id="2969c-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="2969c-118">Détails</span><span class="sxs-lookup"><span data-stu-id="2969c-118">Details</span></span>  
  
|<span data-ttu-id="2969c-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2969c-119">Data Item Name</span></span>|<span data-ttu-id="2969c-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2969c-120">Data Item Type</span></span>|<span data-ttu-id="2969c-121">Description</span><span class="sxs-lookup"><span data-stu-id="2969c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2969c-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="2969c-122">RecordNumber</span></span>|<span data-ttu-id="2969c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="2969c-123">xs:string</span></span>|<span data-ttu-id="2969c-124">Numéro d'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="2969c-124">The tracking record number.</span></span>|  
|<span data-ttu-id="2969c-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="2969c-125">ProviderId</span></span>|<span data-ttu-id="2969c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="2969c-126">xs:string</span></span>|<span data-ttu-id="2969c-127">ID du fournisseur ETW.</span><span class="sxs-lookup"><span data-stu-id="2969c-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="2969c-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2969c-128">AppDomain</span></span>|<span data-ttu-id="2969c-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="2969c-129">xs:string</span></span>|<span data-ttu-id="2969c-130">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2969c-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
