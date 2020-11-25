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
ms.openlocfilehash: 86cb1a2eb18840419d2a4e8ee4f6475edafe8397
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724622"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="d9d49-102">ICorDebugProcess::EnableLogMessages, méthode</span><span class="sxs-lookup"><span data-stu-id="d9d49-102">ICorDebugProcess::EnableLogMessages Method</span></span>

<span data-ttu-id="d9d49-103">Active et désactive la transmission des messages du journal au débogueur.</span><span class="sxs-lookup"><span data-stu-id="d9d49-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9d49-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9d49-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d9d49-105">Parameters</span></span>  

 `fOnOff`  
 <span data-ttu-id="d9d49-106">[in] `true` active la transmission des messages du journal ; `false` désactive la transmission.</span><span class="sxs-lookup"><span data-stu-id="d9d49-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9d49-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="d9d49-107">Remarks</span></span>  

 <span data-ttu-id="d9d49-108">Cette méthode est valide uniquement après l’exécution du rappel [ICorDebugManagedCallback :: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d9d49-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9d49-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d9d49-109">Requirements</span></span>  

 <span data-ttu-id="d9d49-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9d49-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9d49-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9d49-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9d49-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9d49-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9d49-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9d49-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
