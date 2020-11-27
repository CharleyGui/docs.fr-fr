---
title: 1027 - StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: cb5671ce7a30a7096104ba0ca6c4f36bed6b93f9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275230"
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="c9365-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="c9365-102">1027 - StartTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="c9365-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c9365-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9365-104">id</span><span class="sxs-lookup"><span data-stu-id="c9365-104">ID</span></span>|<span data-ttu-id="c9365-105">1027</span><span class="sxs-lookup"><span data-stu-id="c9365-105">1027</span></span>|  
|<span data-ttu-id="c9365-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="c9365-106">Keywords</span></span>|<span data-ttu-id="c9365-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c9365-107">WFRuntime</span></span>|  
|<span data-ttu-id="c9365-108">Level</span><span class="sxs-lookup"><span data-stu-id="c9365-108">Level</span></span>|<span data-ttu-id="c9365-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="c9365-109">Verbose</span></span>|  
|<span data-ttu-id="c9365-110">Channel</span><span class="sxs-lookup"><span data-stu-id="c9365-110">Channel</span></span>|<span data-ttu-id="c9365-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="c9365-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c9365-112">Description</span><span class="sxs-lookup"><span data-stu-id="c9365-112">Description</span></span>  

 <span data-ttu-id="c9365-113">Indique qu'un TransactionContextWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="c9365-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c9365-114">Message</span><span class="sxs-lookup"><span data-stu-id="c9365-114">Message</span></span>  

 <span data-ttu-id="c9365-115">Début de l’exécution d’un TransactionContextWorkItem pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="c9365-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c9365-116">Détails</span><span class="sxs-lookup"><span data-stu-id="c9365-116">Details</span></span>  
  
|<span data-ttu-id="c9365-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c9365-117">Data Item Name</span></span>|<span data-ttu-id="c9365-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c9365-118">Data Item Type</span></span>|<span data-ttu-id="c9365-119">Description</span><span class="sxs-lookup"><span data-stu-id="c9365-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c9365-120">Activité</span><span class="sxs-lookup"><span data-stu-id="c9365-120">Activity</span></span>|<span data-ttu-id="c9365-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9365-121">xs:string</span></span>|<span data-ttu-id="c9365-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c9365-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c9365-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c9365-123">DisplayName</span></span>|<span data-ttu-id="c9365-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9365-124">xs:string</span></span>|<span data-ttu-id="c9365-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c9365-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c9365-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c9365-126">InstanceId</span></span>|<span data-ttu-id="c9365-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9365-127">xs:string</span></span>|<span data-ttu-id="c9365-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c9365-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c9365-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c9365-129">AppDomain</span></span>|<span data-ttu-id="c9365-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9365-130">xs:string</span></span>|<span data-ttu-id="c9365-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c9365-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
