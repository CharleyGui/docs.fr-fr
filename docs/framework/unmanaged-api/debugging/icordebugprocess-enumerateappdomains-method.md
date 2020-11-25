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
ms.openlocfilehash: 408658a0abcba9daf4c3046476e21fd4325c7144
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695138"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="49fad-102">ICorDebugProcess::EnumerateAppDomains, méthode</span><span class="sxs-lookup"><span data-stu-id="49fad-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>

<span data-ttu-id="49fad-103">Énumère tous les domaines d’application dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="49fad-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49fad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49fad-104">Syntax</span></span>  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49fad-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49fad-105">Parameters</span></span>  

 `ppAppDomains`  
 <span data-ttu-id="49fad-106">à Pointeur vers l’adresse d’un [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) qui est un énumérateur pour les domaines d’application dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="49fad-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49fad-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="49fad-107">Remarks</span></span>  

 <span data-ttu-id="49fad-108">Cette méthode peut être utilisée avant le rappel [ICorDebugManagedCallback :: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="49fad-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49fad-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="49fad-109">Requirements</span></span>  

 <span data-ttu-id="49fad-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49fad-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49fad-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49fad-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49fad-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49fad-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49fad-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49fad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
