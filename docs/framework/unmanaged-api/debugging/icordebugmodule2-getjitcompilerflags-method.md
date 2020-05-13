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
ms.openlocfilehash: 6af5bc22616be196be7fdb0d417800d631d87506
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213645"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="f72a8-102">ICorDebugModule2::GetJITCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="f72a8-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="f72a8-103">Obtient les indicateurs qui contrôlent la compilation juste-à-temps (JIT) de ce ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="f72a8-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f72a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f72a8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f72a8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f72a8-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="f72a8-106">à Pointeur vers une valeur de l’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) qui contrôle la compilation JIT.</span><span class="sxs-lookup"><span data-stu-id="f72a8-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f72a8-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f72a8-107">Requirements</span></span>  
 <span data-ttu-id="f72a8-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f72a8-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f72a8-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f72a8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f72a8-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f72a8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f72a8-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f72a8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
