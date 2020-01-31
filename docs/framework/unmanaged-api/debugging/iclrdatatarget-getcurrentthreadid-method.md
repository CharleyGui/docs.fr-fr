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
ms.openlocfilehash: 35515d7c2b82ec2c42461406363964e0b60eb243
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785466"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="01536-102">ICLRDataTarget::GetCurrentThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="01536-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="01536-103">Obtient l’identificateur de système d’exploitation pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="01536-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01536-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01536-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01536-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="01536-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="01536-106">à Pointeur vers l’identificateur de système d’exploitation du thread actuel pour le processus cible.</span><span class="sxs-lookup"><span data-stu-id="01536-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01536-107">Notes</span><span class="sxs-lookup"><span data-stu-id="01536-107">Remarks</span></span>  
 <span data-ttu-id="01536-108">S’il n’existe aucun thread actuel pour le processus cible, la méthode `GetCurrentThreadID` peut échouer.</span><span class="sxs-lookup"><span data-stu-id="01536-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01536-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="01536-109">Requirements</span></span>  
 <span data-ttu-id="01536-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01536-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01536-111">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="01536-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="01536-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01536-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01536-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01536-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01536-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01536-114">See also</span></span>

- [<span data-ttu-id="01536-115">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="01536-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
