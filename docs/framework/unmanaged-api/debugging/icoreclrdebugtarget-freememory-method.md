---
title: Méthode ICoreClrDebugTarget::FreeMemory
ms.date: 03/30/2017
api_name:
- ICoreDebugTarget.FreeMemory
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type:
- apiref
ms.openlocfilehash: 6821aacb80726cf202c99428a401b53b5c6ee566
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121811"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="2c61d-102">Méthode ICoreClrDebugTarget::FreeMemory</span><span class="sxs-lookup"><span data-stu-id="2c61d-102">ICoreClrDebugTarget::FreeMemory Method</span></span>
<span data-ttu-id="2c61d-103">Libère la mémoire allouée par les méthodes [ICoreClrDebugTarget :: EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) et [ICoreClrDebugTarget :: EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2c61d-103">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c61d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c61d-104">Syntax</span></span>  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c61d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2c61d-105">Parameters</span></span>  
 `pMemory`  
 <span data-ttu-id="2c61d-106">dans Pointeur vers le tableau retourné par la méthode [ICoreClrDebugTarget :: EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) ou [ICoreClrDebugTarget :: EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2c61d-106">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c61d-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="2c61d-107">Requirements</span></span>  
 <span data-ttu-id="2c61d-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c61d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c61d-109">**En-tête :** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="2c61d-109">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="2c61d-110">**Bibliothèque :** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="2c61d-110">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="2c61d-111">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="2c61d-111">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c61d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c61d-112">See also</span></span>

- [<span data-ttu-id="2c61d-113">ICoreClrDebugTarget, interface</span><span class="sxs-lookup"><span data-stu-id="2c61d-113">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
