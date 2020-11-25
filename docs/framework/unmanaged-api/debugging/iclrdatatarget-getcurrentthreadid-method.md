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
ms.openlocfilehash: 3a355822710394e9351f10be78dea283e2e9907c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703589"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="1e9fd-102">ICLRDataTarget::GetCurrentThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="1e9fd-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>

<span data-ttu-id="1e9fd-103">Obtient l’identificateur de système d’exploitation pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="1e9fd-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e9fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e9fd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e9fd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1e9fd-105">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="1e9fd-106">à Pointeur vers l’identificateur de système d’exploitation du thread actuel pour le processus cible.</span><span class="sxs-lookup"><span data-stu-id="1e9fd-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e9fd-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="1e9fd-107">Remarks</span></span>  

 <span data-ttu-id="1e9fd-108">S’il n’existe aucun thread actuel pour le processus cible, la `GetCurrentThreadID` méthode peut échouer.</span><span class="sxs-lookup"><span data-stu-id="1e9fd-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e9fd-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1e9fd-109">Requirements</span></span>  

 <span data-ttu-id="1e9fd-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e9fd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e9fd-111">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="1e9fd-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="1e9fd-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e9fd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e9fd-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e9fd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e9fd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e9fd-114">See also</span></span>

- [<span data-ttu-id="1e9fd-115">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="1e9fd-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
