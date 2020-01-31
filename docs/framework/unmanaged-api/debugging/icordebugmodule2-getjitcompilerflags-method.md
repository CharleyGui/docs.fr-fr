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
ms.openlocfilehash: ab6551ba70ed4cd154b166eeb92138b6550d2cb2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792978"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="731c6-102">ICorDebugModule2::GetJITCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="731c6-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="731c6-103">Obtient les indicateurs qui contrôlent la compilation juste-à-temps (JIT) de ce ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="731c6-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="731c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="731c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="731c6-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="731c6-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="731c6-106">à Pointeur vers une valeur de l’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) qui contrôle la compilation JIT.</span><span class="sxs-lookup"><span data-stu-id="731c6-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="731c6-107">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="731c6-107">Requirements</span></span>  
 <span data-ttu-id="731c6-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="731c6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="731c6-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="731c6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="731c6-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="731c6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="731c6-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="731c6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
