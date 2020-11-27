---
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: 2fc509dac7e13f30f74c24d8b98cba55ed5f8e1d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275113"
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="2c0eb-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="2c0eb-102">1028 - CompleteTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="2c0eb-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2c0eb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c0eb-104">id</span><span class="sxs-lookup"><span data-stu-id="2c0eb-104">ID</span></span>|<span data-ttu-id="2c0eb-105">1028</span><span class="sxs-lookup"><span data-stu-id="2c0eb-105">1028</span></span>|  
|<span data-ttu-id="2c0eb-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="2c0eb-106">Keywords</span></span>|<span data-ttu-id="2c0eb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2c0eb-107">WFRuntime</span></span>|  
|<span data-ttu-id="2c0eb-108">Level</span><span class="sxs-lookup"><span data-stu-id="2c0eb-108">Level</span></span>|<span data-ttu-id="2c0eb-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="2c0eb-109">Verbose</span></span>|  
|<span data-ttu-id="2c0eb-110">Channel</span><span class="sxs-lookup"><span data-stu-id="2c0eb-110">Channel</span></span>|<span data-ttu-id="2c0eb-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="2c0eb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2c0eb-112">Description</span><span class="sxs-lookup"><span data-stu-id="2c0eb-112">Description</span></span>  

 <span data-ttu-id="2c0eb-113">Indique qu'un TransactionContextWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="2c0eb-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2c0eb-114">Message</span><span class="sxs-lookup"><span data-stu-id="2c0eb-114">Message</span></span>  

 <span data-ttu-id="2c0eb-115">TransactionContextWorkItem est terminé pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="2c0eb-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2c0eb-116">Détails</span><span class="sxs-lookup"><span data-stu-id="2c0eb-116">Details</span></span>  
  
|<span data-ttu-id="2c0eb-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2c0eb-117">Data Item Name</span></span>|<span data-ttu-id="2c0eb-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2c0eb-118">Data Item Type</span></span>|<span data-ttu-id="2c0eb-119">Description</span><span class="sxs-lookup"><span data-stu-id="2c0eb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2c0eb-120">Activité</span><span class="sxs-lookup"><span data-stu-id="2c0eb-120">Activity</span></span>|<span data-ttu-id="2c0eb-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c0eb-121">xs:string</span></span>|<span data-ttu-id="2c0eb-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="2c0eb-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="2c0eb-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2c0eb-123">DisplayName</span></span>|<span data-ttu-id="2c0eb-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c0eb-124">xs:string</span></span>|<span data-ttu-id="2c0eb-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="2c0eb-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="2c0eb-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2c0eb-126">InstanceId</span></span>|<span data-ttu-id="2c0eb-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c0eb-127">xs:string</span></span>|<span data-ttu-id="2c0eb-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="2c0eb-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2c0eb-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2c0eb-129">AppDomain</span></span>|<span data-ttu-id="2c0eb-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="2c0eb-130">xs:string</span></span>|<span data-ttu-id="2c0eb-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2c0eb-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
