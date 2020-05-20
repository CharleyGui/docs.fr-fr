---
title: EClrFailure, énumération
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
ms.openlocfilehash: e07210203d8a8010890eeb511ff1c08821bfc4a7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616331"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="3c2ad-102">EClrFailure, énumération</span><span class="sxs-lookup"><span data-stu-id="3c2ad-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="3c2ad-103">Décrit l’ensemble des échecs pour lesquels un hôte peut définir des actions de stratégie.</span><span class="sxs-lookup"><span data-stu-id="3c2ad-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c2ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c2ad-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="3c2ad-105">Membres</span><span class="sxs-lookup"><span data-stu-id="3c2ad-105">Members</span></span>  
  
|<span data-ttu-id="3c2ad-106">Membre</span><span class="sxs-lookup"><span data-stu-id="3c2ad-106">Member</span></span>|<span data-ttu-id="3c2ad-107">Description</span><span class="sxs-lookup"><span data-stu-id="3c2ad-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="3c2ad-108">Une erreur s’est produite lors d’une tentative d’allocation d’une ressource (par exemple, un thread, un bloc de mémoire ou un verrou) dans une zone de code non critique.</span><span class="sxs-lookup"><span data-stu-id="3c2ad-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="3c2ad-109">Une erreur s’est produite lors d’une tentative d’allocation d’une ressource (par exemple, un thread, un bloc de mémoire ou un verrou) dans une zone critique de code.</span><span class="sxs-lookup"><span data-stu-id="3c2ad-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="3c2ad-110">Le common language runtime (CLR) n’est plus en mesure d’exécuter du code managé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3c2ad-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="3c2ad-111">Désormais, les appels à toutes les fonctions d’hébergement retournent une valeur HRESULT de HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3c2ad-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="3c2ad-112">Un thread n’a pas réussi à libérer un verrou lors du retour d’un <xref:System.AppDomain> objet.</span><span class="sxs-lookup"><span data-stu-id="3c2ad-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="3c2ad-113">L’hôte ne peut pas définir cet échec pour provoquer l’abandon d’un thread.</span><span class="sxs-lookup"><span data-stu-id="3c2ad-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="3c2ad-114">Un dépassement de capacité de la pile s’est produit.</span><span class="sxs-lookup"><span data-stu-id="3c2ad-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="3c2ad-115">Une tentative de lecture ou d’écriture de mémoire protégée a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="3c2ad-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="3c2ad-116">Non pris en charge dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3c2ad-116">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="3c2ad-117">Un échec de contrat de code s’est produit.</span><span class="sxs-lookup"><span data-stu-id="3c2ad-117">A code contract failure occurred.</span></span> <span data-ttu-id="3c2ad-118">Consultez la section [contrats de code](../../debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="3c2ad-118">See [Code Contracts](../../debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c2ad-119">Notes</span><span class="sxs-lookup"><span data-stu-id="3c2ad-119">Remarks</span></span>  
 <span data-ttu-id="3c2ad-120">Consultez la méthode [ICLRPolicyManager :: SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) pour obtenir la liste des valeurs [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) que l’hôte peut utiliser pour spécifier les actions de stratégie pour les conditions d’échec.</span><span class="sxs-lookup"><span data-stu-id="3c2ad-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="3c2ad-121">Pour plus d’informations sur les régions de code critiques et non critiques, consultez [EClrOperation](eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="3c2ad-121">For more information about critical and non-critical regions of code, see [EClrOperation](eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c2ad-122">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="3c2ad-122">Requirements</span></span>  
 <span data-ttu-id="3c2ad-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c2ad-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c2ad-124">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3c2ad-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c2ad-125">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3c2ad-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c2ad-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c2ad-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c2ad-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c2ad-127">See also</span></span>

- [<span data-ttu-id="3c2ad-128">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="3c2ad-128">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="3c2ad-129">SetActionOnFailure, méthode</span><span class="sxs-lookup"><span data-stu-id="3c2ad-129">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="3c2ad-130">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="3c2ad-130">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="3c2ad-131">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="3c2ad-131">Hosting Enumerations</span></span>](hosting-enumerations.md)
