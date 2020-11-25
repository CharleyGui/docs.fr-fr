---
title: ICorDebug::DebugActiveProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 1713623fa575bea6df649106b37212f7aeaee6db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723465"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="f5cc1-102">ICorDebug::DebugActiveProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="f5cc1-102">ICorDebug::DebugActiveProcess Method</span></span>

<span data-ttu-id="f5cc1-103">Joint le débogueur à un processus existant.</span><span class="sxs-lookup"><span data-stu-id="f5cc1-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5cc1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5cc1-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5cc1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f5cc1-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="f5cc1-106">dans ID du processus auquel le débogueur doit être attaché.</span><span class="sxs-lookup"><span data-stu-id="f5cc1-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="f5cc1-107">dans Valeur booléenne qui a la valeur `true` si le débogueur doit se comporter comme le débogueur Win32 pour le processus et distribuer les rappels non managés ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="f5cc1-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="f5cc1-108">à Pointeur vers l’adresse d’un objet « ICorDebugProcess » qui représente le processus auquel le débogueur a été attaché.</span><span class="sxs-lookup"><span data-stu-id="f5cc1-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5cc1-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="f5cc1-109">Remarks</span></span>  

 <span data-ttu-id="f5cc1-110">Le débogage d’interopérabilité n’est pas pris en charge sur les plateformes Win9x et non-x86, telles que les plateformes basées sur IA-64 et AMD64.</span><span class="sxs-lookup"><span data-stu-id="f5cc1-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5cc1-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f5cc1-111">Requirements</span></span>  

 <span data-ttu-id="f5cc1-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5cc1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5cc1-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5cc1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5cc1-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5cc1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5cc1-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5cc1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cc1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5cc1-116">See also</span></span>

- [<span data-ttu-id="f5cc1-117">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="f5cc1-117">ICorDebug Interface</span></span>](icordebug-interface.md)
