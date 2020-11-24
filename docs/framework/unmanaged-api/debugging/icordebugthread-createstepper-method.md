---
title: ICorDebugThread::CreateStepper, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
ms.openlocfilehash: dcaa5adc41a9e451b123b088dd900f01d9161689
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688274"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="4497a-102">ICorDebugThread::CreateStepper, méthode</span><span class="sxs-lookup"><span data-stu-id="4497a-102">ICorDebugThread::CreateStepper Method</span></span>

<span data-ttu-id="4497a-103">Crée un objet ICorDebugStepper qui permet d’effectuer un pas à pas détaillé dans le frame actif de ce ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="4497a-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4497a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4497a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4497a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4497a-105">Parameters</span></span>  

 `ppStepper`  
 <span data-ttu-id="4497a-106">à Pointeur vers l’adresse d’un `ICorDebugStepper` objet qui permet d’effectuer un pas à pas détaillé dans le frame actif de ce thread.</span><span class="sxs-lookup"><span data-stu-id="4497a-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4497a-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="4497a-107">Remarks</span></span>  

 <span data-ttu-id="4497a-108">Le frame actif peut être du code non managé.</span><span class="sxs-lookup"><span data-stu-id="4497a-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="4497a-109">L' `ICorDebugStepper` interface doit être utilisée pour exécuter le pas à pas réel.</span><span class="sxs-lookup"><span data-stu-id="4497a-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4497a-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4497a-110">Requirements</span></span>  

 <span data-ttu-id="4497a-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4497a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4497a-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4497a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4497a-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4497a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4497a-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4497a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
