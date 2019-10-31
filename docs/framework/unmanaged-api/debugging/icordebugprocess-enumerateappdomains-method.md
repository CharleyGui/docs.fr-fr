---
title: ICorDebugProcess::EnumerateAppDomains, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
ms.openlocfilehash: e09e25503ad00ab3542f0c4f50221b6014b25561
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128881"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="cfb05-102">ICorDebugProcess::EnumerateAppDomains, méthode</span><span class="sxs-lookup"><span data-stu-id="cfb05-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="cfb05-103">Énumère tous les domaines d’application dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="cfb05-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfb05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfb05-104">Syntax</span></span>  
  
``` cpp 
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfb05-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cfb05-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="cfb05-106">à Pointeur vers l’adresse d’un [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) qui est un énumérateur pour les domaines d’application dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="cfb05-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfb05-107">Notes</span><span class="sxs-lookup"><span data-stu-id="cfb05-107">Remarks</span></span>  
 <span data-ttu-id="cfb05-108">Cette méthode peut être utilisée avant le rappel [ICorDebugManagedCallback :: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cfb05-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfb05-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="cfb05-109">Requirements</span></span>  
 <span data-ttu-id="cfb05-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfb05-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfb05-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfb05-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfb05-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfb05-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfb05-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfb05-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
