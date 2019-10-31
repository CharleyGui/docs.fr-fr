---
title: ICLRDataTarget::GetCurrentThreadID, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
ms.openlocfilehash: ccb5cda11a2466496a4b3981e8185cbb7130f66f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122895"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="1c1c2-102">ICLRDataTarget::GetCurrentThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="1c1c2-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="1c1c2-103">Obtient l’identificateur de système d’exploitation pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="1c1c2-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c1c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c1c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c1c2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1c1c2-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="1c1c2-106">à Pointeur vers l’identificateur de système d’exploitation du thread actuel pour le processus cible.</span><span class="sxs-lookup"><span data-stu-id="1c1c2-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c1c2-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1c1c2-107">Remarks</span></span>  
 <span data-ttu-id="1c1c2-108">S’il n’existe aucun thread actuel pour le processus cible, la méthode `GetCurrentThreadID` peut échouer.</span><span class="sxs-lookup"><span data-stu-id="1c1c2-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c1c2-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="1c1c2-109">Requirements</span></span>  
 <span data-ttu-id="1c1c2-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c1c2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c1c2-111">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="1c1c2-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="1c1c2-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c1c2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c1c2-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c1c2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c1c2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c1c2-114">See also</span></span>

- [<span data-ttu-id="1c1c2-115">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="1c1c2-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
