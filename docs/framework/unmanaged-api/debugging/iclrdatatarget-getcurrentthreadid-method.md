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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45a409bda8861701e68d3ea1a956a4c35ce88ddd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738784"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="e21af-102">ICLRDataTarget::GetCurrentThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="e21af-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="e21af-103">Obtient l’identificateur de système d’exploitation pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="e21af-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e21af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e21af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e21af-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e21af-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="e21af-106">[out] Un pointeur vers l’identificateur de système d’exploitation du thread actuel pour le processus cible.</span><span class="sxs-lookup"><span data-stu-id="e21af-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e21af-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e21af-107">Remarks</span></span>  
 <span data-ttu-id="e21af-108">S’il n’existe aucun thread actuel pour le processus cible, le `GetCurrentThreadID` méthode peut échouer.</span><span class="sxs-lookup"><span data-stu-id="e21af-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e21af-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e21af-109">Requirements</span></span>  
 <span data-ttu-id="e21af-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e21af-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e21af-111">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e21af-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e21af-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e21af-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e21af-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e21af-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e21af-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e21af-114">See also</span></span>

- [<span data-ttu-id="e21af-115">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="e21af-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
