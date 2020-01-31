---
title: ICorDebugManagedCallback2::Exception, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
ms.openlocfilehash: e7125d923fb1d3757bb4ca53f5a7db806b241dd9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781524"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="87fb0-102">ICorDebugManagedCallback2::Exception, méthode</span><span class="sxs-lookup"><span data-stu-id="87fb0-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="87fb0-103">Notifie le débogueur qu’une recherche d’un gestionnaire d’exceptions a démarré.</span><span class="sxs-lookup"><span data-stu-id="87fb0-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87fb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87fb0-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87fb0-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="87fb0-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="87fb0-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread sur lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="87fb0-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="87fb0-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="87fb0-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="87fb0-108">dans Pointeur vers un objet ICorDebugFrame qui représente un frame, tel que déterminé par le paramètre `dwEventType`.</span><span class="sxs-lookup"><span data-stu-id="87fb0-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="87fb0-109">Pour plus d’informations, consultez le tableau dans la section Notes.</span><span class="sxs-lookup"><span data-stu-id="87fb0-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="87fb0-110">dans Entier qui spécifie un décalage, tel que déterminé par le paramètre `dwEventType`.</span><span class="sxs-lookup"><span data-stu-id="87fb0-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="87fb0-111">Pour plus d’informations, consultez le tableau dans la section Notes.</span><span class="sxs-lookup"><span data-stu-id="87fb0-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="87fb0-112">dans Valeur de l’énumération CorDebugExceptionCallbackType, qui spécifie le type de ce rappel d’exception.</span><span class="sxs-lookup"><span data-stu-id="87fb0-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="87fb0-113">dans Valeur de l’énumération [CorDebugExceptionFlags,](cordebugexceptionflags-enumeration.md) qui spécifie des informations supplémentaires sur l’exception.</span><span class="sxs-lookup"><span data-stu-id="87fb0-113">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87fb0-114">Notes</span><span class="sxs-lookup"><span data-stu-id="87fb0-114">Remarks</span></span>  
 <span data-ttu-id="87fb0-115">Le rappel `Exception` est appelé à différents moments pendant la phase de recherche du processus de gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="87fb0-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="87fb0-116">Autrement dit, il peut être appelé plusieurs fois tout en déroulant une exception.</span><span class="sxs-lookup"><span data-stu-id="87fb0-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="87fb0-117">L’exception en cours de traitement peut être récupérée à partir de l’objet ICorDebugThread référencé par le paramètre `pThread`.</span><span class="sxs-lookup"><span data-stu-id="87fb0-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="87fb0-118">Le frame et le décalage particuliers sont déterminés par le paramètre `dwEventType` comme suit :</span><span class="sxs-lookup"><span data-stu-id="87fb0-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="87fb0-119">Valeur de `dwEventType`</span><span class="sxs-lookup"><span data-stu-id="87fb0-119">Value of `dwEventType`</span></span>|<span data-ttu-id="87fb0-120">Valeur de `pFrame`</span><span class="sxs-lookup"><span data-stu-id="87fb0-120">Value of `pFrame`</span></span>|<span data-ttu-id="87fb0-121">Valeur de `nOffset`</span><span class="sxs-lookup"><span data-stu-id="87fb0-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="87fb0-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="87fb0-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="87fb0-123">Frame qui a levé l’exception.</span><span class="sxs-lookup"><span data-stu-id="87fb0-123">The frame that threw the exception.</span></span>|<span data-ttu-id="87fb0-124">Pointeur d’instruction dans le frame.</span><span class="sxs-lookup"><span data-stu-id="87fb0-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="87fb0-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="87fb0-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="87fb0-126">Frame de code utilisateur le plus proche du point de l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="87fb0-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="87fb0-127">Pointeur d’instruction dans le frame.</span><span class="sxs-lookup"><span data-stu-id="87fb0-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="87fb0-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="87fb0-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="87fb0-129">Frame qui contient le gestionnaire catch.</span><span class="sxs-lookup"><span data-stu-id="87fb0-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="87fb0-130">Offset MSIL (Microsoft Intermediate Language) du début du gestionnaire catch.</span><span class="sxs-lookup"><span data-stu-id="87fb0-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="87fb0-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="87fb0-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="87fb0-132">NULL</span><span class="sxs-lookup"><span data-stu-id="87fb0-132">NULL</span></span>|<span data-ttu-id="87fb0-133">Non défini.</span><span class="sxs-lookup"><span data-stu-id="87fb0-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87fb0-134">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="87fb0-134">Requirements</span></span>  
 <span data-ttu-id="87fb0-135">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87fb0-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87fb0-136">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87fb0-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87fb0-137">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87fb0-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87fb0-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87fb0-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87fb0-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87fb0-139">See also</span></span>

- [<span data-ttu-id="87fb0-140">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="87fb0-140">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="87fb0-141">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="87fb0-141">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
