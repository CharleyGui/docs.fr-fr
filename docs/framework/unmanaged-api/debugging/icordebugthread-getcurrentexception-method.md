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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a6d53ebfebb8c883065ce119c2338a2225f0472
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762483"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="3994a-102">ICorDebugThread::GetCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="3994a-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="3994a-103">Obtient un pointeur d’interface vers un objet ICorDebugValue qui représente une exception levée par le code managé.</span><span class="sxs-lookup"><span data-stu-id="3994a-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3994a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3994a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3994a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3994a-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="3994a-106">[out] Un pointeur vers l’adresse d’un `ICorDebugValue` objet qui représente l’exception levée par code managé.</span><span class="sxs-lookup"><span data-stu-id="3994a-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3994a-107">Notes</span><span class="sxs-lookup"><span data-stu-id="3994a-107">Remarks</span></span>  
 <span data-ttu-id="3994a-108">L’objet exception existe à partir du moment où l’exception est levée jusqu'à la fin de la `catch` bloc.</span><span class="sxs-lookup"><span data-stu-id="3994a-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="3994a-109">Une évaluation de fonction, qui est effectuée par les méthodes ICorDebugEval, effacera l’objet exception sur le programme d’installation et restaurez-la sur la saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="3994a-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="3994a-110">Les exceptions peuvent être imbriquées (par exemple, si une exception est levée dans un filtre ou dans une évaluation de fonction), afin qu’il peut y avoir plusieurs exceptions en attente sur un thread unique.</span><span class="sxs-lookup"><span data-stu-id="3994a-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="3994a-111">`GetCurrentException` Retourne l’exception la plus récente.</span><span class="sxs-lookup"><span data-stu-id="3994a-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="3994a-112">L’objet exception et le type peuvent changer pendant la durée de vie de l’exception.</span><span class="sxs-lookup"><span data-stu-id="3994a-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="3994a-113">Par exemple, après la levée d’une exception de type x, le common language runtime (CLR) peut manquer de mémoire et le promouvoir en une exception de mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="3994a-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3994a-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3994a-114">Requirements</span></span>  
 <span data-ttu-id="3994a-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3994a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3994a-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3994a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3994a-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3994a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3994a-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3994a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
