---
title: ICorDebugILFrame::GetArgument, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e9f627f1ba213f663f042d1107afd1eb05b56b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757864"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="6340d-102">ICorDebugILFrame::GetArgument, méthode</span><span class="sxs-lookup"><span data-stu-id="6340d-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="6340d-103">Obtient la valeur de l’argument spécifié dans ce frame de pile Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="6340d-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6340d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6340d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6340d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6340d-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="6340d-106">[in] L’index de l’argument dans ce frame de pile MSIL.</span><span class="sxs-lookup"><span data-stu-id="6340d-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="6340d-107">[out] Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur récupérée.</span><span class="sxs-lookup"><span data-stu-id="6340d-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6340d-108">Notes</span><span class="sxs-lookup"><span data-stu-id="6340d-108">Remarks</span></span>  
 <span data-ttu-id="6340d-109">Le `GetArgument` méthode peut être utilisée dans un frame de pile MSIL ou dans un frame compilé juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="6340d-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6340d-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6340d-110">Requirements</span></span>  
 <span data-ttu-id="6340d-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6340d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6340d-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6340d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6340d-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6340d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6340d-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6340d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
