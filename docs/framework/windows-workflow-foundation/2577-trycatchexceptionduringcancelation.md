---
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: 33c68984e88eaa5e3028899a7c3066c94a65e8eb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271237"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="2ce7b-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="2ce7b-102">2577 - TryCatchExceptionDuringCancelation</span></span>

## <a name="properties"></a><span data-ttu-id="2ce7b-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2ce7b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2ce7b-104">id</span><span class="sxs-lookup"><span data-stu-id="2ce7b-104">ID</span></span>|<span data-ttu-id="2ce7b-105">2577</span><span class="sxs-lookup"><span data-stu-id="2ce7b-105">2577</span></span>|  
|<span data-ttu-id="2ce7b-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="2ce7b-106">Keywords</span></span>|<span data-ttu-id="2ce7b-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="2ce7b-107">WFActivities</span></span>|  
|<span data-ttu-id="2ce7b-108">Level</span><span class="sxs-lookup"><span data-stu-id="2ce7b-108">Level</span></span>|<span data-ttu-id="2ce7b-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="2ce7b-109">Warning</span></span>|  
|<span data-ttu-id="2ce7b-110">Channel</span><span class="sxs-lookup"><span data-stu-id="2ce7b-110">Channel</span></span>|<span data-ttu-id="2ce7b-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="2ce7b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2ce7b-112">Description</span><span class="sxs-lookup"><span data-stu-id="2ce7b-112">Description</span></span>  

 <span data-ttu-id="2ce7b-113">Indique qu'une activité enfant de l'activité TryCatch a levé une exception durant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="2ce7b-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2ce7b-114">Message</span><span class="sxs-lookup"><span data-stu-id="2ce7b-114">Message</span></span>  

 <span data-ttu-id="2ce7b-115">Une activité enfant de l'activité TryCatch « %1 » a levé une exception durant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="2ce7b-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2ce7b-116">Détails</span><span class="sxs-lookup"><span data-stu-id="2ce7b-116">Details</span></span>  
  
|<span data-ttu-id="2ce7b-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2ce7b-117">Data Item Name</span></span>|<span data-ttu-id="2ce7b-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2ce7b-118">Data Item Type</span></span>|<span data-ttu-id="2ce7b-119">Description</span><span class="sxs-lookup"><span data-stu-id="2ce7b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2ce7b-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2ce7b-120">DisplayName</span></span>|<span data-ttu-id="2ce7b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2ce7b-121">xs:string</span></span>|<span data-ttu-id="2ce7b-122">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="2ce7b-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="2ce7b-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2ce7b-123">AppDomain</span></span>|<span data-ttu-id="2ce7b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2ce7b-124">xs:string</span></span>|<span data-ttu-id="2ce7b-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2ce7b-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
