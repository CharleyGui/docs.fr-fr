---
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: d958b506e057bc0d59f954debdc9da6015bf5f1f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273098"
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="9abc8-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="9abc8-102">39456 - TrackingRecordDropped</span></span>

## <a name="properties"></a><span data-ttu-id="9abc8-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9abc8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9abc8-104">id</span><span class="sxs-lookup"><span data-stu-id="9abc8-104">ID</span></span>|<span data-ttu-id="9abc8-105">39456</span><span class="sxs-lookup"><span data-stu-id="9abc8-105">39456</span></span>|  
|<span data-ttu-id="9abc8-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="9abc8-106">Keywords</span></span>|<span data-ttu-id="9abc8-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="9abc8-107">WFTracking</span></span>|  
|<span data-ttu-id="9abc8-108">Level</span><span class="sxs-lookup"><span data-stu-id="9abc8-108">Level</span></span>|<span data-ttu-id="9abc8-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="9abc8-109">Warning</span></span>|  
|<span data-ttu-id="9abc8-110">Channel</span><span class="sxs-lookup"><span data-stu-id="9abc8-110">Channel</span></span>|<span data-ttu-id="9abc8-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="9abc8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9abc8-112">Description</span><span class="sxs-lookup"><span data-stu-id="9abc8-112">Description</span></span>  

 <span data-ttu-id="9abc8-113">Indique qu'un enregistrement de suivi a été supprimé, car sa taille dépasse la taille maximale autorisée par le fournisseur de session ETW.</span><span class="sxs-lookup"><span data-stu-id="9abc8-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9abc8-114">Message</span><span class="sxs-lookup"><span data-stu-id="9abc8-114">Message</span></span>  

 <span data-ttu-id="9abc8-115">La taille de l'enregistrement de suivi %1 dépasse la valeur maximale autorisée par la session ETW pour le fournisseur %2</span><span class="sxs-lookup"><span data-stu-id="9abc8-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="9abc8-116">Détails</span><span class="sxs-lookup"><span data-stu-id="9abc8-116">Details</span></span>  
  
|<span data-ttu-id="9abc8-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9abc8-117">Data Item Name</span></span>|<span data-ttu-id="9abc8-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9abc8-118">Data Item Type</span></span>|<span data-ttu-id="9abc8-119">Description</span><span class="sxs-lookup"><span data-stu-id="9abc8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9abc8-120">Exception</span><span class="sxs-lookup"><span data-stu-id="9abc8-120">Exception</span></span>|<span data-ttu-id="9abc8-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9abc8-121">xs:string</span></span>|<span data-ttu-id="9abc8-122">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="9abc8-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="9abc8-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9abc8-123">AppDomain</span></span>|<span data-ttu-id="9abc8-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9abc8-124">xs:string</span></span>|<span data-ttu-id="9abc8-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9abc8-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
