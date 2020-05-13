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
ms.openlocfilehash: 3a4da6f958407c0b704ffb7372a77b7f022fc824
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379773"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="b8d0d-102">ICorDebugThread::GetCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="b8d0d-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="b8d0d-103">Obtient un pointeur d’interface vers un objet ICorDebugValue qui représente une exception actuellement levée par du code managé.</span><span class="sxs-lookup"><span data-stu-id="b8d0d-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8d0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8d0d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8d0d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b8d0d-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="b8d0d-106">à Pointeur vers l’adresse d’un `ICorDebugValue` objet qui représente l’exception actuellement levée par le code managé.</span><span class="sxs-lookup"><span data-stu-id="b8d0d-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8d0d-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="b8d0d-107">Remarks</span></span>  
 <span data-ttu-id="b8d0d-108">L’objet exception existera à partir du moment où l’exception sera levée jusqu’à la fin du `catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="b8d0d-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="b8d0d-109">Une évaluation de fonction, qui est effectuée par les méthodes ICorDebugEval, supprime l’objet exception lors de l’installation et le restaure à la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="b8d0d-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="b8d0d-110">Les exceptions peuvent être imbriquées (par exemple, si une exception est levée dans un filtre ou une évaluation de fonction), il peut donc y avoir plusieurs exceptions en suspens sur un seul thread.</span><span class="sxs-lookup"><span data-stu-id="b8d0d-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="b8d0d-111">`GetCurrentException`retourne l’exception la plus récente.</span><span class="sxs-lookup"><span data-stu-id="b8d0d-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="b8d0d-112">L’objet et le type de l’exception peuvent changer tout au long de la durée de vie de l’exception.</span><span class="sxs-lookup"><span data-stu-id="b8d0d-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="b8d0d-113">Par exemple, après la levée d’une exception de type x, le common language runtime (CLR) peut manquer de mémoire et le promouvoir en une exception de mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="b8d0d-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8d0d-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b8d0d-114">Requirements</span></span>  
 <span data-ttu-id="b8d0d-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8d0d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8d0d-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8d0d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8d0d-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8d0d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8d0d-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8d0d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
