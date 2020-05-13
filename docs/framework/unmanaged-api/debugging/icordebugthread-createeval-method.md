---
title: ICorDebugThread::CreateEval, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
ms.openlocfilehash: f66ef88646c314502dcb610cec8ce822cab1fca2
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379283"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="9a498-102">ICorDebugThread::CreateEval, méthode</span><span class="sxs-lookup"><span data-stu-id="9a498-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="9a498-103">Crée un objet ICorDebugEval qui collecte et expose les fonctionnalités de ce ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="9a498-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a498-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a498-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a498-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9a498-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="9a498-106">à Pointeur vers l’adresse d’un `ICorDebugEval` objet qui collecte et expose les fonctionnalités de ce thread.</span><span class="sxs-lookup"><span data-stu-id="9a498-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a498-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="9a498-107">Remarks</span></span>  
 <span data-ttu-id="9a498-108">L’objet d’évaluation envoie une nouvelle chaîne sur le thread avant de procéder à son calcul.</span><span class="sxs-lookup"><span data-stu-id="9a498-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="9a498-109">Cela interrompt le calcul en cours d’exécution sur le thread jusqu’à ce que l’évaluation soit terminée.</span><span class="sxs-lookup"><span data-stu-id="9a498-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a498-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9a498-110">Requirements</span></span>  
 <span data-ttu-id="9a498-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a498-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a498-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a498-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a498-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a498-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a498-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a498-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
