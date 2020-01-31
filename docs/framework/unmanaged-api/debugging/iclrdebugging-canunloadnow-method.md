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
ms.openlocfilehash: 41b2e009f8f017a72147232015ea2357ae922ca1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793654"
---
# <a name="iclrdebuggingcanunloadnow-method"></a><span data-ttu-id="8b5d8-102">ICLRDebugging::CanUnloadNow, méthode</span><span class="sxs-lookup"><span data-stu-id="8b5d8-102">ICLRDebugging::CanUnloadNow Method</span></span>
<span data-ttu-id="8b5d8-103">Détermine si une bibliothèque qui a été fournie par une interface [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) est toujours en cours d’utilisation ou si elle peut être déchargée.</span><span class="sxs-lookup"><span data-stu-id="8b5d8-103">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b5d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b5d8-104">Syntax</span></span>  
  
```cpp  
HRESULT CanUnloadNow(HMODULE hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b5d8-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="8b5d8-105">Parameters</span></span>  
 `hmodule`  
 <span data-ttu-id="8b5d8-106">dans Adresse de base d’un module dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="8b5d8-106">[in] The base address of a module in the target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b5d8-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8b5d8-107">Return Value</span></span>  
 <span data-ttu-id="8b5d8-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8b5d8-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8b5d8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b5d8-109">HRESULT</span></span>|<span data-ttu-id="8b5d8-110">Description</span><span class="sxs-lookup"><span data-stu-id="8b5d8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b5d8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b5d8-111">S_OK</span></span>|<span data-ttu-id="8b5d8-112">Le module référencé par `hmodule` peut être déchargé.</span><span class="sxs-lookup"><span data-stu-id="8b5d8-112">The module that is referenced by `hmodule` can be unloaded.</span></span>|  
|<span data-ttu-id="8b5d8-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8b5d8-113">S_FALSE</span></span>|<span data-ttu-id="8b5d8-114">Le module référencé par `hmodule` est toujours en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="8b5d8-114">The module that is referenced by `hmodule` is still in use.</span></span>|  
|<span data-ttu-id="8b5d8-115">COR_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="8b5d8-115">COR_E_NOT_CLR</span></span>|<span data-ttu-id="8b5d8-116">Le module indiqué n’est pas un module CLR.</span><span class="sxs-lookup"><span data-stu-id="8b5d8-116">The indicated module is not a CLR module.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8b5d8-117">Exceptions</span><span class="sxs-lookup"><span data-stu-id="8b5d8-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b5d8-118">Notes</span><span class="sxs-lookup"><span data-stu-id="8b5d8-118">Remarks</span></span>  
 <span data-ttu-id="8b5d8-119">Cette méthode vérifie si toutes les instances d' `ICorDebug*` interfaces ont été libérées et qu’aucun thread n’est actuellement dans un appel à la méthode [ICLRDebugging :: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8b5d8-119">This method checks to see if all instances of `ICorDebug*` interfaces have been released and no thread is currently within a call to the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b5d8-120">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="8b5d8-120">Requirements</span></span>  
 <span data-ttu-id="8b5d8-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b5d8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b5d8-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b5d8-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b5d8-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b5d8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b5d8-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b5d8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5d8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b5d8-125">See also</span></span>

- [<span data-ttu-id="8b5d8-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8b5d8-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8b5d8-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="8b5d8-127">Debugging</span></span>](index.md)
