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
ms.openlocfilehash: f30516a8f59b90de9b4c052d92a8c88575ace3c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178823"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="7ab47-102">ICorDebugILFrame::GetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="7ab47-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="7ab47-103">Obtient la valeur du pointeur d’instruction et une valeur de combinaison bitwise qui décrit comment la valeur du pointeur d’instruction a été obtenue.</span><span class="sxs-lookup"><span data-stu-id="7ab47-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ab47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ab47-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ab47-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ab47-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="7ab47-106">[out] La valeur du pointeur d’instruction.</span><span class="sxs-lookup"><span data-stu-id="7ab47-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="7ab47-107">[out] Un pointeur à une combinaison un peu sage des valeurs d’énumération CorDebugMappingResult qui décrivent comment la valeur du pointeur d’instruction a été obtenue.</span><span class="sxs-lookup"><span data-stu-id="7ab47-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ab47-108">Notes </span><span class="sxs-lookup"><span data-stu-id="7ab47-108">Remarks</span></span>  
 <span data-ttu-id="7ab47-109">La valeur du pointeur d’instruction est la compensation de l’image de pile dans le code de la langue intermédiaire Microsoft (MSIL) de la fonction.</span><span class="sxs-lookup"><span data-stu-id="7ab47-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="7ab47-110">Si le cadre de pile est actif, cette adresse est la prochaine instruction à exécuter.</span><span class="sxs-lookup"><span data-stu-id="7ab47-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="7ab47-111">Si le cadre de pile n’est pas actif, cette adresse est la prochaine instruction à exécuter lorsque le cadre de pile est réactivé.</span><span class="sxs-lookup"><span data-stu-id="7ab47-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="7ab47-112">Si ce cadre est un cadre juste-à-temps (JIT) compilé, la valeur du pointeur d’instruction sera déterminée en cartographiant à l’envers à partir du pointeur d’instruction natif réel, de sorte que la valeur peut être seulement approximative.</span><span class="sxs-lookup"><span data-stu-id="7ab47-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ab47-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7ab47-113">Requirements</span></span>  
 <span data-ttu-id="7ab47-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ab47-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ab47-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ab47-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ab47-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ab47-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ab47-117">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ab47-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
