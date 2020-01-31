---
title: 'IcorDebugVariableHome :: GetLiveRange, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLiveRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type:
- apiref
ms.openlocfilehash: 28e41106ffcaf1ed2ed87166e641bb5e5f447e47
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791027"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="67bfb-102">IcorDebugVariableHome :: GetLiveRange, méthode</span><span class="sxs-lookup"><span data-stu-id="67bfb-102">IcorDebugVariableHome::GetLiveRange Method</span></span>
<span data-ttu-id="67bfb-103">Obtient la plage native sur laquelle cette variable est active.</span><span class="sxs-lookup"><span data-stu-id="67bfb-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67bfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67bfb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67bfb-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="67bfb-105">Parameters</span></span>  
 `pStartOffset`  
 <span data-ttu-id="67bfb-106">à Décalage logique auquel la variable est active en premier.</span><span class="sxs-lookup"><span data-stu-id="67bfb-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="67bfb-107">à Décalage logique qui suit immédiatement le point de la dernière activité de la variable.</span><span class="sxs-lookup"><span data-stu-id="67bfb-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67bfb-108">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="67bfb-108">Requirements</span></span>  
 <span data-ttu-id="67bfb-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67bfb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67bfb-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67bfb-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67bfb-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67bfb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67bfb-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67bfb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67bfb-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67bfb-113">See also</span></span>

- [<span data-ttu-id="67bfb-114">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="67bfb-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
