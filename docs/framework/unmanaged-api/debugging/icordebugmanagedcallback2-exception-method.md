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
ms.openlocfilehash: 612b63ba9aa3504cab5196932293946d486955ce
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210200"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="92d8c-102">ICorDebugManagedCallback2::Exception, méthode</span><span class="sxs-lookup"><span data-stu-id="92d8c-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="92d8c-103">Notifie le débogueur qu’une recherche d’un gestionnaire d’exceptions a démarré.</span><span class="sxs-lookup"><span data-stu-id="92d8c-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92d8c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92d8c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="92d8c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="92d8c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="92d8c-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread sur lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="92d8c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="92d8c-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="92d8c-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="92d8c-108">dans Pointeur vers un objet ICorDebugFrame qui représente un frame, tel que déterminé par le `dwEventType` paramètre.</span><span class="sxs-lookup"><span data-stu-id="92d8c-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="92d8c-109">Pour plus d’informations, consultez le tableau dans la section Notes.</span><span class="sxs-lookup"><span data-stu-id="92d8c-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="92d8c-110">dans Entier qui spécifie un décalage, tel que déterminé par le `dwEventType` paramètre.</span><span class="sxs-lookup"><span data-stu-id="92d8c-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="92d8c-111">Pour plus d’informations, consultez le tableau dans la section Notes.</span><span class="sxs-lookup"><span data-stu-id="92d8c-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="92d8c-112">dans Valeur de l’énumération CorDebugExceptionCallbackType, qui spécifie le type de ce rappel d’exception.</span><span class="sxs-lookup"><span data-stu-id="92d8c-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="92d8c-113">dans Valeur de l’énumération [CorDebugExceptionFlags,](cordebugexceptionflags-enumeration.md) qui spécifie des informations supplémentaires sur l’exception.</span><span class="sxs-lookup"><span data-stu-id="92d8c-113">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92d8c-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="92d8c-114">Remarks</span></span>  
 <span data-ttu-id="92d8c-115">Le `Exception` rappel est appelé à différents moments pendant la phase de recherche du processus de gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="92d8c-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="92d8c-116">Autrement dit, il peut être appelé plusieurs fois tout en déroulant une exception.</span><span class="sxs-lookup"><span data-stu-id="92d8c-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="92d8c-117">L’exception en cours de traitement peut être récupérée à partir de l’objet ICorDebugThread référencé par le `pThread` paramètre.</span><span class="sxs-lookup"><span data-stu-id="92d8c-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="92d8c-118">Le frame et le décalage particuliers sont déterminés par le `dwEventType` paramètre comme suit :</span><span class="sxs-lookup"><span data-stu-id="92d8c-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="92d8c-119">Valeur de `dwEventType`</span><span class="sxs-lookup"><span data-stu-id="92d8c-119">Value of `dwEventType`</span></span>|<span data-ttu-id="92d8c-120">Valeur de `pFrame`</span><span class="sxs-lookup"><span data-stu-id="92d8c-120">Value of `pFrame`</span></span>|<span data-ttu-id="92d8c-121">Valeur de `nOffset`</span><span class="sxs-lookup"><span data-stu-id="92d8c-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="92d8c-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="92d8c-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="92d8c-123">Frame qui a levé l’exception.</span><span class="sxs-lookup"><span data-stu-id="92d8c-123">The frame that threw the exception.</span></span>|<span data-ttu-id="92d8c-124">Pointeur d’instruction dans le frame.</span><span class="sxs-lookup"><span data-stu-id="92d8c-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="92d8c-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="92d8c-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="92d8c-126">Frame de code utilisateur le plus proche du point de l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="92d8c-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="92d8c-127">Pointeur d’instruction dans le frame.</span><span class="sxs-lookup"><span data-stu-id="92d8c-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="92d8c-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="92d8c-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="92d8c-129">Frame qui contient le gestionnaire catch.</span><span class="sxs-lookup"><span data-stu-id="92d8c-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="92d8c-130">Offset MSIL (Microsoft Intermediate Language) du début du gestionnaire catch.</span><span class="sxs-lookup"><span data-stu-id="92d8c-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="92d8c-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="92d8c-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="92d8c-132">NULL</span><span class="sxs-lookup"><span data-stu-id="92d8c-132">NULL</span></span>|<span data-ttu-id="92d8c-133">Non défini.</span><span class="sxs-lookup"><span data-stu-id="92d8c-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92d8c-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="92d8c-134">Requirements</span></span>  
 <span data-ttu-id="92d8c-135">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92d8c-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92d8c-136">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92d8c-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92d8c-137">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92d8c-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92d8c-138">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92d8c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92d8c-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92d8c-139">See also</span></span>

- [<span data-ttu-id="92d8c-140">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="92d8c-140">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="92d8c-141">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="92d8c-141">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
