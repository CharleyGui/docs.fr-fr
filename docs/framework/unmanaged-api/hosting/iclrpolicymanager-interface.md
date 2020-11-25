---
title: ICLRPolicyManager, interface
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 7092a1c792fee7f6173dcde211b8e807f6ab02a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725584"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="4813e-102">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="4813e-102">ICLRPolicyManager Interface</span></span>

<span data-ttu-id="4813e-103">Fournit des méthodes qui permettent à l’hôte de spécifier des actions de stratégie à prendre en cas d’échecs et de délais d’attente.</span><span class="sxs-lookup"><span data-stu-id="4813e-103">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4813e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4813e-104">Methods</span></span>  
  
|<span data-ttu-id="4813e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4813e-105">Method</span></span>|<span data-ttu-id="4813e-106">Description</span><span class="sxs-lookup"><span data-stu-id="4813e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4813e-107">SetActionOnFailure, méthode</span><span class="sxs-lookup"><span data-stu-id="4813e-107">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="4813e-108">Spécifie l’action de stratégie que le common language runtime (CLR) doit prendre lorsque l’échec spécifié se produit.</span><span class="sxs-lookup"><span data-stu-id="4813e-108">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="4813e-109">SetActionOnTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="4813e-109">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="4813e-110">Spécifie l’action de stratégie que le CLR doit prendre lorsque l’opération spécifiée expire.</span><span class="sxs-lookup"><span data-stu-id="4813e-110">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="4813e-111">SetDefaultAction, méthode</span><span class="sxs-lookup"><span data-stu-id="4813e-111">SetDefaultAction Method</span></span>](iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="4813e-112">Spécifie l’action de stratégie que le CLR doit prendre lorsque l’opération spécifiée se produit.</span><span class="sxs-lookup"><span data-stu-id="4813e-112">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="4813e-113">SetTimeout, méthode</span><span class="sxs-lookup"><span data-stu-id="4813e-113">SetTimeout Method</span></span>](iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="4813e-114">Définit une valeur de délai d’attente pour l’opération spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4813e-114">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="4813e-115">SetTimeoutAndAction, méthode</span><span class="sxs-lookup"><span data-stu-id="4813e-115">SetTimeoutAndAction Method</span></span>](iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="4813e-116">Définit une valeur de délai d’attente pour l’opération spécifiée et spécifie l’action de stratégie que le CLR doit prendre lorsque l’opération se produit.</span><span class="sxs-lookup"><span data-stu-id="4813e-116">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="4813e-117">SetUnhandledExceptionPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="4813e-117">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="4813e-118">Spécifie le comportement du CLR lorsqu’une exception non gérée se produit.</span><span class="sxs-lookup"><span data-stu-id="4813e-118">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4813e-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4813e-119">Requirements</span></span>  

 <span data-ttu-id="4813e-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4813e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4813e-121">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4813e-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4813e-122">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4813e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4813e-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4813e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4813e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4813e-124">See also</span></span>

- [<span data-ttu-id="4813e-125">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="4813e-125">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="4813e-126">EClrOperation, énumération</span><span class="sxs-lookup"><span data-stu-id="4813e-126">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="4813e-127">EPolicyAction, énumération</span><span class="sxs-lookup"><span data-stu-id="4813e-127">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="4813e-128">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="4813e-128">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
