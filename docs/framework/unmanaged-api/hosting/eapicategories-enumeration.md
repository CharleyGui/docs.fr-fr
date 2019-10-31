---
title: EApiCategories, énumération
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
ms.openlocfilehash: 0fd9409a5157e1013365c94f01631f130a76f54b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131211"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="948cd-102">EApiCategories, énumération</span><span class="sxs-lookup"><span data-stu-id="948cd-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="948cd-103">Décrit les catégories de fonctionnalités que l’hôte peut empêcher de s’exécuter dans du code de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="948cd-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="948cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="948cd-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a><span data-ttu-id="948cd-105">Membres</span><span class="sxs-lookup"><span data-stu-id="948cd-105">Members</span></span>  
  
|<span data-ttu-id="948cd-106">Membre</span><span class="sxs-lookup"><span data-stu-id="948cd-106">Member</span></span>|<span data-ttu-id="948cd-107">Description</span><span class="sxs-lookup"><span data-stu-id="948cd-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="948cd-108">Spécifie que l’exécution de toutes les classes et membres managés couverts par d’autres `EApiCategories` champs est bloquée dans du code d’un code d’approbation partiel.</span><span class="sxs-lookup"><span data-stu-id="948cd-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="948cd-109">Spécifie que les classes et les membres managés qui autorisent la création, la manipulation et la destruction de processus externes ne sont pas exécutés dans du code d’un code d’approbation partiel.</span><span class="sxs-lookup"><span data-stu-id="948cd-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="948cd-110">Spécifie que les classes et les membres managés qui autorisent la création, la manipulation et la destruction de threads externes ne sont pas exécutés dans du code d’un code d’approbation partiel.</span><span class="sxs-lookup"><span data-stu-id="948cd-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="948cd-111">Spécifie que les types et membres managés susceptibles d’entraîner une fuite de mémoire lors de l’abandon ne peuvent pas s’exécuter dans du code d’un niveau de confiance partiel.</span><span class="sxs-lookup"><span data-stu-id="948cd-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="948cd-112">Spécifie qu’il n’est pas possible de bloquer l’exécution des catégories de code managé dans du code de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="948cd-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="948cd-113">Spécifie que l’utilisation de l’infrastructure de sécurité common language runtime (CLR) par le code d’un point de confiance partiel est bloquée.</span><span class="sxs-lookup"><span data-stu-id="948cd-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="948cd-114">Spécifie que les classes et les membres managés dont les fonctionnalités peuvent affecter le processus hébergé ne peuvent pas s’exécuter dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="948cd-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="948cd-115">Spécifie que les classes et les membres managés dont les fonctionnalités peuvent affecter les threads dans le processus hébergé ne peuvent pas s’exécuter dans du code de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="948cd-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="948cd-116">Spécifie que les classes et les membres managés qui exposent l’état partagé ne sont pas en cours d’exécution dans du code de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="948cd-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="948cd-117">Spécifie que les classes et les membres de common language runtime qui autorisent le code utilisateur à contenir des verrous ne pourront pas s’exécuter dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="948cd-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="948cd-118">Spécifie que les classes et les membres managés qui autorisent ou nécessitent une interaction humaine ne sont pas en cours d’exécution dans du code partiellement fiable.</span><span class="sxs-lookup"><span data-stu-id="948cd-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="948cd-119">Notes</span><span class="sxs-lookup"><span data-stu-id="948cd-119">Remarks</span></span>  
 <span data-ttu-id="948cd-120">La méthode [ICLRHostProtectionManager :: SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) prend un paramètre de type `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="948cd-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="948cd-121">L’énumération `EApiCategories` et la méthode `SetProtectedCategories` sont directement liées à la classe <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> managée.</span><span class="sxs-lookup"><span data-stu-id="948cd-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="948cd-122">La classe managée est utilisée avec l’énumération <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>, dont les valeurs correspondent directement aux valeurs de `EApiCategories`, pour marquer les membres et les types managés qui exposent les fonctionnalités correspondant aux catégories décrites par `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="948cd-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="948cd-123">spécifications</span><span class="sxs-lookup"><span data-stu-id="948cd-123">Requirements</span></span>  
 <span data-ttu-id="948cd-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="948cd-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="948cd-125">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="948cd-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="948cd-126">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="948cd-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="948cd-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="948cd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="948cd-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="948cd-128">See also</span></span>

- [<span data-ttu-id="948cd-129">ICLRHostProtectionManager, interface</span><span class="sxs-lookup"><span data-stu-id="948cd-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="948cd-130">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="948cd-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
