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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75b28dafae2861a2d33363f95a46bf1abf4cda35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756578"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="93634-102">ICorDebugILFrame::CanSetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="93634-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="93634-103">Obtient une valeur HRESULT qui indique s’il est sans risque de définir le pointeur d’instruction à l’emplacement de décalage spécifié dans le code de langage MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="93634-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93634-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93634-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93634-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="93634-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="93634-106">[in] Le paramètre souhaité pour le pointeur d’instruction.</span><span class="sxs-lookup"><span data-stu-id="93634-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93634-107">Notes</span><span class="sxs-lookup"><span data-stu-id="93634-107">Remarks</span></span>  
 <span data-ttu-id="93634-108">Utilisez le `CanSetIP` méthode avant d’appeler le [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="93634-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="93634-109">Si `CanSetIP` retourne un HRESULT autre que S_OK, vous pouvez toujours appeler `ICorDebugILFrame::SetIP`, mais il n’existe aucune garantie que le débogueur continue l’exécution sécurisée et correcte du code en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="93634-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93634-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="93634-110">Requirements</span></span>  
 <span data-ttu-id="93634-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93634-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93634-112">**En-tête :** CorDebug.idl, CorDebug,h</span><span class="sxs-lookup"><span data-stu-id="93634-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="93634-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93634-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93634-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93634-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
