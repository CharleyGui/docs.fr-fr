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
ms.openlocfilehash: 4d66d09e02b907281f64400b0c605a7b5c44d476
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731044"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="0887e-102">IcorDebugVariableHome :: GetLiveRange, méthode</span><span class="sxs-lookup"><span data-stu-id="0887e-102">IcorDebugVariableHome::GetLiveRange Method</span></span>

<span data-ttu-id="0887e-103">Obtient la plage native sur laquelle cette variable est active.</span><span class="sxs-lookup"><span data-stu-id="0887e-103">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0887e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0887e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0887e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0887e-105">Parameters</span></span>  

 `pStartOffset`  
 <span data-ttu-id="0887e-106">à Décalage logique auquel la variable est active en premier.</span><span class="sxs-lookup"><span data-stu-id="0887e-106">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="0887e-107">à Décalage logique qui suit immédiatement le point de la dernière activité de la variable.</span><span class="sxs-lookup"><span data-stu-id="0887e-107">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0887e-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0887e-108">Requirements</span></span>  

 <span data-ttu-id="0887e-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0887e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0887e-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0887e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0887e-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0887e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0887e-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0887e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0887e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0887e-113">See also</span></span>

- [<span data-ttu-id="0887e-114">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="0887e-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
