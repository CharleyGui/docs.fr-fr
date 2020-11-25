---
title: ICorDebugNativeFrame::GetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
ms.openlocfilehash: c9c0598f8e7b3e8654124f50663c912f3cd61659
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709300"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="40576-102">ICorDebugNativeFrame::GetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="40576-102">ICorDebugNativeFrame::GetIP Method</span></span>

<span data-ttu-id="40576-103">Obtient l’emplacement de décalage de code natif auquel le pointeur d’instruction est actuellement défini.</span><span class="sxs-lookup"><span data-stu-id="40576-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40576-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40576-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40576-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="40576-105">Parameters</span></span>  

 `pnOffset`  
 <span data-ttu-id="40576-106">à Pointeur vers l’emplacement d’offset dans le code natif.</span><span class="sxs-lookup"><span data-stu-id="40576-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40576-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="40576-107">Remarks</span></span>  

 <span data-ttu-id="40576-108">Si le frame de pile représenté par ce « ICorDebugNativeFrame » est actif, le décalage est l’adresse de l’instruction suivante à exécuter.</span><span class="sxs-lookup"><span data-stu-id="40576-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="40576-109">Si ce frame de pile n’est pas actif, le décalage est l’adresse de l’instruction suivante à exécuter lorsque le frame de pile est réactivé.</span><span class="sxs-lookup"><span data-stu-id="40576-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40576-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="40576-110">Requirements</span></span>  

 <span data-ttu-id="40576-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40576-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40576-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40576-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40576-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40576-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40576-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40576-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40576-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40576-115">See also</span></span>
