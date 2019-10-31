---
title: ICorDebugThread::GetActiveFrame, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
ms.openlocfilehash: d623893bd77e46832b0bd823ed60c23e4eee29ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133536"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="d13de-102">ICorDebugThread::GetActiveFrame, méthode</span><span class="sxs-lookup"><span data-stu-id="d13de-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="d13de-103">Obtient un pointeur d’interface vers le frame actif (le plus récent) sur cet objet ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="d13de-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d13de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d13de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d13de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d13de-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="d13de-106">à Pointeur vers l’adresse d’un objet d’interface ICorDebugFrame qui représente un frame.</span><span class="sxs-lookup"><span data-stu-id="d13de-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d13de-107">Notes</span><span class="sxs-lookup"><span data-stu-id="d13de-107">Remarks</span></span>  
 <span data-ttu-id="d13de-108">Le paramètre `ppFrame` a la valeur null si aucun frame n’est actuellement actif.</span><span class="sxs-lookup"><span data-stu-id="d13de-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d13de-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="d13de-109">Requirements</span></span>  
 <span data-ttu-id="d13de-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d13de-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d13de-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d13de-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d13de-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d13de-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d13de-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d13de-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
