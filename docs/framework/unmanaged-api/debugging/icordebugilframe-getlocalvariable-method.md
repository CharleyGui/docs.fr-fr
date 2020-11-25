---
title: ICorDebugILFrame::GetLocalVariable, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
ms.openlocfilehash: 54ecce830b928ded115233eb99932cc15a471033
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703133"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="599a5-102">ICorDebugILFrame::GetLocalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="599a5-102">ICorDebugILFrame::GetLocalVariable Method</span></span>

<span data-ttu-id="599a5-103">Obtient la valeur de la variable locale spécifiée dans ce frame de pile MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="599a5-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="599a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="599a5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="599a5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="599a5-105">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="599a5-106">dans Index de la variable locale dans ce frame de pile MSIL.</span><span class="sxs-lookup"><span data-stu-id="599a5-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="599a5-107">[en sortie] Un pointeur vers l'adresse d'un objet ICorDebugValue qui représente la valeur extraite.</span><span class="sxs-lookup"><span data-stu-id="599a5-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="599a5-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="599a5-108">Remarks</span></span>  

 <span data-ttu-id="599a5-109">La `GetLocalVariable` méthode peut être utilisée dans un frame de pile MSIL ou dans un frame compilé juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="599a5-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="599a5-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="599a5-110">Requirements</span></span>  

 <span data-ttu-id="599a5-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="599a5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="599a5-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="599a5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="599a5-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="599a5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="599a5-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="599a5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
