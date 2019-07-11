---
title: ICorDebugThread::GetProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad87b6552df25926b5b4184b7884c1d444c4f1be
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769074"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="01c3a-102">ICorDebugThread::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="01c3a-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="01c3a-103">Obtient un pointeur d’interface vers le processus qui ICorDebugThread fait partie.</span><span class="sxs-lookup"><span data-stu-id="01c3a-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01c3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01c3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01c3a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="01c3a-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="01c3a-106">[out] Pointeur vers l’adresse d’un objet d’interface ICorDebugProcess qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="01c3a-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01c3a-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="01c3a-107">Requirements</span></span>  
 <span data-ttu-id="01c3a-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01c3a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01c3a-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01c3a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01c3a-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01c3a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01c3a-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01c3a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
