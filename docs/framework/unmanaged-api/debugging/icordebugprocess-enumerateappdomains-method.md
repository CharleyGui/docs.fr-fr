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
ms.openlocfilehash: 4489238df05edef384b4073ee738a184ff8809ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178673"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="6fe53-102">ICorDebugProcess::EnumerateAppDomains, méthode</span><span class="sxs-lookup"><span data-stu-id="6fe53-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="6fe53-103">Énumère tous les domaines d’application dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="6fe53-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fe53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fe53-104">Syntax</span></span>  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fe53-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6fe53-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="6fe53-106">[out] Un pointeur à l’adresse d’un [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) qui est un enumérateur pour les domaines d’application dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="6fe53-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fe53-107">Notes </span><span class="sxs-lookup"><span data-stu-id="6fe53-107">Remarks</span></span>  
 <span data-ttu-id="6fe53-108">Cette méthode peut être utilisée avant [l’ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="6fe53-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fe53-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6fe53-109">Requirements</span></span>  
 <span data-ttu-id="6fe53-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fe53-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fe53-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fe53-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fe53-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fe53-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fe53-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fe53-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
