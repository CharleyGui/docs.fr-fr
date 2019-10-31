---
title: ICorDebugModule2::GetJITCompilerFlags, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.GetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::GetJITCompilerFlags
helpviewer_keywords:
- GetJITCompilerFlags method [.NET Framework debugging]
- ICorDebugModule2::GetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: 7212d9f4-989b-44e3-b8d4-ffc35922f6a0
topic_type:
- apiref
ms.openlocfilehash: 1216629fc7e1c3e720d5f296b9293b3c4b7f8721
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127895"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="9a010-102">ICorDebugModule2::GetJITCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="9a010-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="9a010-103">Obtient les indicateurs qui contrôlent la compilation juste-à-temps (JIT) de ce ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="9a010-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a010-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a010-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a010-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9a010-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="9a010-106">à Pointeur vers une valeur de l’énumération [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) qui contrôle la compilation JIT.</span><span class="sxs-lookup"><span data-stu-id="9a010-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a010-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="9a010-107">Requirements</span></span>  
 <span data-ttu-id="9a010-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a010-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a010-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a010-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a010-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a010-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a010-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a010-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
