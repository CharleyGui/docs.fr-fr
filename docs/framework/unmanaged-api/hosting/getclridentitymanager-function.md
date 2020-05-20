---
title: GetCLRIdentityManager, fonction
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
ms.openlocfilehash: 57f771d933e896677dfc0bd5d9dac58da2af22c8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617254"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="b2f55-102">GetCLRIdentityManager, fonction</span><span class="sxs-lookup"><span data-stu-id="b2f55-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="b2f55-103">Obtient un pointeur vers une interface qui permet au common language runtime (CLR) de gérer les identités.</span><span class="sxs-lookup"><span data-stu-id="b2f55-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="b2f55-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b2f55-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2f55-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2f55-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2f55-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2f55-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="b2f55-107">dans `REFIID`(Identificateur d’interface) qui spécifie l’interface à obtenir.</span><span class="sxs-lookup"><span data-stu-id="b2f55-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="b2f55-108">Cette valeur doit être IID_ICLRAssemblyIdentityManager ou IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="b2f55-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="b2f55-109">à Pointeur vers l’adresse d’un objet [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) ou [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b2f55-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2f55-110">Notes</span><span class="sxs-lookup"><span data-stu-id="b2f55-110">Remarks</span></span>  
 <span data-ttu-id="b2f55-111">Appelez la fonction [GetRealProcAddress,](getrealprocaddress-function.md) pour obtenir un pointeur vers la `GetCLRIdentityManager` fonction.</span><span class="sxs-lookup"><span data-stu-id="b2f55-111">Call the [GetRealProcAddress](getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2f55-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="b2f55-112">Requirements</span></span>  
 <span data-ttu-id="b2f55-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2f55-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2f55-114">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b2f55-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2f55-115">**Bibliothèque :** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="b2f55-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="b2f55-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2f55-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2f55-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2f55-117">See also</span></span>

- [<span data-ttu-id="b2f55-118">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="b2f55-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
