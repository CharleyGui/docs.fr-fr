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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ea4947582e4e8bfdb6873a90c5284e9ae9d8a62
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736252"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="c3a84-102">GetCLRIdentityManager, fonction</span><span class="sxs-lookup"><span data-stu-id="c3a84-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="c3a84-103">Obtient un pointeur vers une interface qui autorise le common language runtime (CLR) pour gérer les identités.</span><span class="sxs-lookup"><span data-stu-id="c3a84-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="c3a84-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c3a84-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a84-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3a84-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3a84-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3a84-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="c3a84-107">[in] Un `REFIID` (un identificateur d’interface) qui spécifie quelle interface à obtenir.</span><span class="sxs-lookup"><span data-stu-id="c3a84-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="c3a84-108">Cette valeur doit être IID_ICLRAssemblyIdentityManager ou IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="c3a84-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="c3a84-109">[out] Un pointeur vers l’adresse un [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) ou un [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="c3a84-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3a84-110">Notes</span><span class="sxs-lookup"><span data-stu-id="c3a84-110">Remarks</span></span>  
 <span data-ttu-id="c3a84-111">Appelez le [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) fonction pour obtenir un pointeur vers le `GetCLRIdentityManager` (fonction).</span><span class="sxs-lookup"><span data-stu-id="c3a84-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3a84-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c3a84-112">Requirements</span></span>  
 <span data-ttu-id="c3a84-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3a84-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3a84-114">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c3a84-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3a84-115">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="c3a84-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="c3a84-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3a84-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a84-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3a84-117">See also</span></span>

- [<span data-ttu-id="c3a84-118">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="c3a84-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
