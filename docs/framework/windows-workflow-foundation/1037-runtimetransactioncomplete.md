---
title: 1037 - RuntimeTransactionComplete
ms.date: 03/30/2017
ms.assetid: 2c8c31e0-42a9-4f46-865b-2da9ab16a0ba
ms.openlocfilehash: ad05151a1497ea4b31e0fe33fe2983c1f145f224
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294246"
---
# <a name="1037---runtimetransactioncomplete"></a><span data-ttu-id="78c8a-102">1037 - RuntimeTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="78c8a-102">1037 - RuntimeTransactionComplete</span></span>

## <a name="properties"></a><span data-ttu-id="78c8a-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="78c8a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78c8a-104">id</span><span class="sxs-lookup"><span data-stu-id="78c8a-104">ID</span></span>|<span data-ttu-id="78c8a-105">1037</span><span class="sxs-lookup"><span data-stu-id="78c8a-105">1037</span></span>|  
|<span data-ttu-id="78c8a-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="78c8a-106">Keywords</span></span>|<span data-ttu-id="78c8a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="78c8a-107">WFRuntime</span></span>|  
|<span data-ttu-id="78c8a-108">Level</span><span class="sxs-lookup"><span data-stu-id="78c8a-108">Level</span></span>|<span data-ttu-id="78c8a-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="78c8a-109">Verbose</span></span>|  
|<span data-ttu-id="78c8a-110">Channel</span><span class="sxs-lookup"><span data-stu-id="78c8a-110">Channel</span></span>|<span data-ttu-id="78c8a-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="78c8a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="78c8a-112">Description</span><span class="sxs-lookup"><span data-stu-id="78c8a-112">Description</span></span>  

 <span data-ttu-id="78c8a-113">Indique que la transaction runtime s’est terminée.</span><span class="sxs-lookup"><span data-stu-id="78c8a-113">Indicates the runtime transaction has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="78c8a-114">Message</span><span class="sxs-lookup"><span data-stu-id="78c8a-114">Message</span></span>  

 <span data-ttu-id="78c8a-115">La transaction runtime s’est terminée en état « %1 ».</span><span class="sxs-lookup"><span data-stu-id="78c8a-115">The runtime transaction has completed with the state '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="78c8a-116">Détails</span><span class="sxs-lookup"><span data-stu-id="78c8a-116">Details</span></span>  
  
|<span data-ttu-id="78c8a-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="78c8a-117">Data Item Name</span></span>|<span data-ttu-id="78c8a-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="78c8a-118">Data Item Type</span></span>|<span data-ttu-id="78c8a-119">Description</span><span class="sxs-lookup"><span data-stu-id="78c8a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="78c8a-120">State</span><span class="sxs-lookup"><span data-stu-id="78c8a-120">State</span></span>|<span data-ttu-id="78c8a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="78c8a-121">xs:string</span></span>|<span data-ttu-id="78c8a-122">État de la transaction.</span><span class="sxs-lookup"><span data-stu-id="78c8a-122">The state of the transaction.</span></span>|  
|<span data-ttu-id="78c8a-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="78c8a-123">AppDomain</span></span>|<span data-ttu-id="78c8a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="78c8a-124">xs:string</span></span>|<span data-ttu-id="78c8a-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="78c8a-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
