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
ms.openlocfilehash: 9d1196749e033c71b0c8923d0325eb4886122d1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733657"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="a0198-102">GetCLRIdentityManager, fonction</span><span class="sxs-lookup"><span data-stu-id="a0198-102">GetCLRIdentityManager Function</span></span>

<span data-ttu-id="a0198-103">Obtient un pointeur vers une interface qui permet au common language runtime (CLR) de gérer les identités.</span><span class="sxs-lookup"><span data-stu-id="a0198-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="a0198-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a0198-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0198-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0198-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0198-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0198-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="a0198-107">dans `REFIID` (Identificateur d’interface) qui spécifie l’interface à obtenir.</span><span class="sxs-lookup"><span data-stu-id="a0198-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="a0198-108">Cette valeur doit être IID_ICLRAssemblyIdentityManager ou IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="a0198-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="a0198-109">à Pointeur vers l’adresse d’un objet [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) ou [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a0198-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0198-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="a0198-110">Remarks</span></span>  

 <span data-ttu-id="a0198-111">Appelez la fonction [GetRealProcAddress,](getrealprocaddress-function.md) pour obtenir un pointeur vers la `GetCLRIdentityManager` fonction.</span><span class="sxs-lookup"><span data-stu-id="a0198-111">Call the [GetRealProcAddress](getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0198-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a0198-112">Requirements</span></span>  

 <span data-ttu-id="a0198-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0198-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0198-114">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a0198-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0198-115">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="a0198-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="a0198-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0198-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0198-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0198-117">See also</span></span>

- [<span data-ttu-id="a0198-118">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="a0198-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
