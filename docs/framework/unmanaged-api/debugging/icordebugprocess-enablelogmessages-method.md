---
title: ICorDebugProcess::EnableLogMessages, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b199d3226ec391fadc356b5efacdbf10a3e25adf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766162"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="41082-102">ICorDebugProcess::EnableLogMessages, méthode</span><span class="sxs-lookup"><span data-stu-id="41082-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="41082-103">Active et désactive la transmission de messages de journal au débogueur.</span><span class="sxs-lookup"><span data-stu-id="41082-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41082-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41082-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41082-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="41082-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="41082-106">[in] `true` permet la transmission de messages du journal ; `false` désactive la transmission.</span><span class="sxs-lookup"><span data-stu-id="41082-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41082-107">Notes</span><span class="sxs-lookup"><span data-stu-id="41082-107">Remarks</span></span>  
 <span data-ttu-id="41082-108">Cette méthode est valide uniquement après la [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) rappel se produit.</span><span class="sxs-lookup"><span data-stu-id="41082-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41082-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="41082-109">Requirements</span></span>  
 <span data-ttu-id="41082-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41082-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41082-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41082-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41082-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41082-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41082-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41082-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
