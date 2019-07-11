---
title: ICorDebugILFrame::GetIP, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d7eca3c2825707c9190436377bba7e4bb0d5447
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757977"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="31608-102">ICorDebugILFrame::GetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="31608-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="31608-103">Obtient la valeur de pointeur d’instruction et une valeur de combinaison de bits qui décrit la façon dont la valeur de pointeur d’instruction a été obtenue.</span><span class="sxs-lookup"><span data-stu-id="31608-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31608-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31608-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31608-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31608-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="31608-106">[out] La valeur de pointeur d’instruction.</span><span class="sxs-lookup"><span data-stu-id="31608-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="31608-107">[out] Pointeur vers une combinaison au niveau du bit des valeurs d’énumération CorDebugMappingResult qui décrivent comment la valeur du pointeur d’instruction a été obtenue.</span><span class="sxs-lookup"><span data-stu-id="31608-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31608-108">Notes</span><span class="sxs-lookup"><span data-stu-id="31608-108">Remarks</span></span>  
 <span data-ttu-id="31608-109">La valeur de pointeur d’instruction est l’offset du frame de pile dans le code de la fonction Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="31608-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="31608-110">Si le frame de pile est actif, cette adresse est l’instruction suivante à exécuter.</span><span class="sxs-lookup"><span data-stu-id="31608-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="31608-111">Si le frame de pile n’est pas actif, cette adresse est la prochaine instruction à exécuter lorsque le frame de pile est réactivé.</span><span class="sxs-lookup"><span data-stu-id="31608-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="31608-112">Si ce frame est un frame de compilé juste-à-temps (JIT), la valeur de pointeur d’instruction sera déterminée en mappant vers l’arrière à partir du pointeur d’instruction natif réel, donc la valeur peut être uniquement approximative.</span><span class="sxs-lookup"><span data-stu-id="31608-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31608-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="31608-113">Requirements</span></span>  
 <span data-ttu-id="31608-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31608-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31608-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31608-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31608-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31608-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31608-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31608-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
