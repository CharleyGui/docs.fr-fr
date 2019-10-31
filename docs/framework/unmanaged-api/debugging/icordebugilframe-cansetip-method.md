---
title: ICorDebugILFrame::CanSetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: 57d83d1f301cbfd43f8f553d9aef4beb3baf95f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131082"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="0a9fc-102">ICorDebugILFrame::CanSetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="0a9fc-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="0a9fc-103">Obtient un HRESULT qui indique s’il est possible de définir en toute sécurité le pointeur d’instruction à l’emplacement de décalage spécifié dans le code MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="0a9fc-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a9fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a9fc-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a9fc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a9fc-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="0a9fc-106">dans Paramètre souhaité pour le pointeur d’instruction.</span><span class="sxs-lookup"><span data-stu-id="0a9fc-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a9fc-107">Notes</span><span class="sxs-lookup"><span data-stu-id="0a9fc-107">Remarks</span></span>  
 <span data-ttu-id="0a9fc-108">Utilisez la méthode `CanSetIP` avant d’appeler la méthode [ICorDebugILFrame :: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0a9fc-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="0a9fc-109">Si `CanSetIP` retourne un HRESULT autre que S_OK, vous pouvez toujours appeler `ICorDebugILFrame::SetIP`, mais il n’existe aucune garantie que le débogueur continue l’exécution sécurisée et correcte du code en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="0a9fc-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a9fc-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="0a9fc-110">Requirements</span></span>  
 <span data-ttu-id="0a9fc-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a9fc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a9fc-112">**En-tête :** CorDebug. idl, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="0a9fc-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="0a9fc-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a9fc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a9fc-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a9fc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
