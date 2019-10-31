---
title: ICLRDebugging::CanUnloadNow, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebugging.CanUnloadNow Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::CanUnloadNow
helpviewer_keywords:
- CanUnloadNow method [.NET Framework debugging]
- ICLRDebugging::CanUnloadNow method [.NET Framework debugging]
ms.assetid: 62e0630c-8cb7-45d2-b622-5a472abfd8cf
topic_type:
- apiref
ms.openlocfilehash: 4eb6682ac5a8b7788d97f752f249d85886fba0b6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111647"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="aedc6-102">ICLRDebugging::CanUnloadNow, méthode</span><span class="sxs-lookup"><span data-stu-id="aedc6-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="aedc6-103">Détermine si une bibliothèque qui a été fournie par une interface [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) est toujours en cours d’utilisation ou si elle peut être déchargée.</span><span class="sxs-lookup"><span data-stu-id="aedc6-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aedc6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aedc6-104">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aedc6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aedc6-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="aedc6-106">dans Adresse de base d’un module dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="aedc6-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aedc6-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="aedc6-107">Return Value</span></span>  
 <span data-ttu-id="aedc6-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="aedc6-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="aedc6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aedc6-109">HRESULT</span></span>|<span data-ttu-id="aedc6-110">Description</span><span class="sxs-lookup"><span data-stu-id="aedc6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aedc6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="aedc6-111">S_OK</span></span>|<span data-ttu-id="aedc6-112">Le module référencé par `hmodule` peut être déchargé.</span><span class="sxs-lookup"><span data-stu-id="aedc6-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="aedc6-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="aedc6-113">S_FALSE</span></span>|<span data-ttu-id="aedc6-114">Le module référencé par `hmodule` est toujours en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="aedc6-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="aedc6-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="aedc6-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="aedc6-116">Le module indiqué n’est pas un module CLR.</span><span class="sxs-lookup"><span data-stu-id="aedc6-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="aedc6-117">Exceptions</span><span class="sxs-lookup"><span data-stu-id="aedc6-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aedc6-118">Notes</span><span class="sxs-lookup"><span data-stu-id="aedc6-118">Remarks</span></span>  
 <span data-ttu-id="aedc6-119">Cette méthode vérifie si toutes les instances d' `ICorDebug*` interfaces ont été libérées et qu’aucun thread n’est actuellement dans un appel à la méthode [ICLRDebugging :: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="aedc6-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aedc6-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="aedc6-120">Requirements</span></span>  
 <span data-ttu-id="aedc6-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aedc6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aedc6-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aedc6-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aedc6-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aedc6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aedc6-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aedc6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aedc6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aedc6-125">See also</span></span>

- [<span data-ttu-id="aedc6-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="aedc6-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="aedc6-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="aedc6-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
