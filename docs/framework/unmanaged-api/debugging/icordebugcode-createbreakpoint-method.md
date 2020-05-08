---
title: ICorDebugCode::CreateBreakpoint, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: 40582b1289875d5151ea96e3153c6e4760737e84
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893809"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="b9675-102">ICorDebugCode::CreateBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="b9675-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="b9675-103">Crée un point d’arrêt dans ce segment de code à l’offset spécifié.</span><span class="sxs-lookup"><span data-stu-id="b9675-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9675-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9675-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9675-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9675-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="b9675-106">dans Offset à partir duquel créer le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="b9675-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="b9675-107">à Pointeur vers l’adresse d’un objet « ICorDebugFunctionBreakpoint » qui représente le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="b9675-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9675-108">Notes </span><span class="sxs-lookup"><span data-stu-id="b9675-108">Remarks</span></span>  
 <span data-ttu-id="b9675-109">Avant que le point d’arrêt soit actif, il doit être ajouté à l’objet processus.</span><span class="sxs-lookup"><span data-stu-id="b9675-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="b9675-110">Si ce code est du code MSIL (Microsoft Intermediate Language), et qu’il existe une version native, compilée juste-à-temps (JIT), du code, le point d’arrêt est également appliqué dans le code compilé juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="b9675-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="b9675-111">(C’est également le cas si le code est compilé juste-à-temps ultérieurement.)</span><span class="sxs-lookup"><span data-stu-id="b9675-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9675-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b9675-112">Requirements</span></span>  
 <span data-ttu-id="b9675-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9675-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9675-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9675-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9675-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9675-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9675-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9675-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
