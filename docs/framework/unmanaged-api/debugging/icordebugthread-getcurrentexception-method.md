---
title: ICorDebugThread::GetCurrentException, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
ms.openlocfilehash: 8082b2a3654f1605f18f3b68f54464dc83c8e60a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133486"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="e0274-102">ICorDebugThread::GetCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="e0274-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="e0274-103">Obtient un pointeur d’interface vers un objet ICorDebugValue qui représente une exception actuellement levée par du code managé.</span><span class="sxs-lookup"><span data-stu-id="e0274-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0274-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0274-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0274-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e0274-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="e0274-106">à Pointeur vers l’adresse d’un objet `ICorDebugValue` qui représente l’exception actuellement levée par le code managé.</span><span class="sxs-lookup"><span data-stu-id="e0274-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0274-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e0274-107">Remarks</span></span>  
 <span data-ttu-id="e0274-108">L’objet exception existera à partir du moment où l’exception sera levée jusqu’à la fin du bloc `catch`.</span><span class="sxs-lookup"><span data-stu-id="e0274-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="e0274-109">Une évaluation de fonction, qui est effectuée par les méthodes ICorDebugEval, supprime l’objet exception lors de l’installation et le restaure à la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="e0274-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="e0274-110">Les exceptions peuvent être imbriquées (par exemple, si une exception est levée dans un filtre ou une évaluation de fonction), il peut donc y avoir plusieurs exceptions en suspens sur un seul thread.</span><span class="sxs-lookup"><span data-stu-id="e0274-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="e0274-111">`GetCurrentException` retourne l’exception la plus récente.</span><span class="sxs-lookup"><span data-stu-id="e0274-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="e0274-112">L’objet et le type de l’exception peuvent changer tout au long de la durée de vie de l’exception.</span><span class="sxs-lookup"><span data-stu-id="e0274-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="e0274-113">Par exemple, après la levée d’une exception de type x, le common language runtime (CLR) peut manquer de mémoire et le promouvoir en une exception de mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="e0274-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0274-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="e0274-114">Requirements</span></span>  
 <span data-ttu-id="e0274-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0274-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0274-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0274-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0274-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0274-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0274-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0274-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
