---
title: ICorDebugNativeFrame::CanSetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: d266ec7f82d7d4c7c66f137aafc1c8865d6f8889
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792801"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="1a6b2-102">ICorDebugNativeFrame::CanSetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="1a6b2-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="1a6b2-103">Obtient un HRESULT qui indique s’il est possible de définir en toute sécurité le pointeur d’instruction (IP) à l’emplacement d’offset spécifié en code natif.</span><span class="sxs-lookup"><span data-stu-id="1a6b2-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a6b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a6b2-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a6b2-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="1a6b2-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="1a6b2-106">dans Paramètre souhaité pour le pointeur d’instruction.</span><span class="sxs-lookup"><span data-stu-id="1a6b2-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a6b2-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1a6b2-107">Remarks</span></span>  
 <span data-ttu-id="1a6b2-108">Utilisez la méthode `CanSetIP` avant d’appeler la méthode [ICorDebugNativeFrame :: SetIP](icordebugnativeframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1a6b2-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="1a6b2-109">Si `CanSetIP` retourne un HRESULT autre que S_OK, vous pouvez toujours appeler `ICorDebugNativeFrame::SetIP`, mais il n’existe aucune garantie que le débogueur continue l’exécution sécurisée et correcte du code en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="1a6b2-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a6b2-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="1a6b2-110">Requirements</span></span>  
 <span data-ttu-id="1a6b2-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a6b2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a6b2-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a6b2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a6b2-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a6b2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a6b2-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a6b2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a6b2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a6b2-115">See also</span></span>
