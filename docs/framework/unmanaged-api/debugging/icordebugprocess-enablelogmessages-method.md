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
ms.openlocfilehash: 3b850a462ce354b81f4406fce7fd9d8d9b6013d8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207901"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="c336e-102">ICorDebugProcess::EnableLogMessages, méthode</span><span class="sxs-lookup"><span data-stu-id="c336e-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="c336e-103">Active et désactive la transmission des messages du journal au débogueur.</span><span class="sxs-lookup"><span data-stu-id="c336e-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c336e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c336e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c336e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c336e-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="c336e-106">[in] `true` active la transmission des messages du journal ; `false`désactive la transmission.</span><span class="sxs-lookup"><span data-stu-id="c336e-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c336e-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="c336e-107">Remarks</span></span>  
 <span data-ttu-id="c336e-108">Cette méthode est valide uniquement après l’exécution du rappel [ICorDebugManagedCallback :: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c336e-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c336e-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c336e-109">Requirements</span></span>  
 <span data-ttu-id="c336e-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c336e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c336e-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c336e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c336e-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c336e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c336e-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c336e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
