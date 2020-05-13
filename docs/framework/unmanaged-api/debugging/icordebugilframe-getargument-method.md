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
ms.openlocfilehash: d715f5842bb7f75da5311d34bf7d4596f0801a92
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210278"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="e8537-102">ICorDebugILFrame::GetArgument, méthode</span><span class="sxs-lookup"><span data-stu-id="e8537-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="e8537-103">Obtient la valeur de l’argument spécifié dans ce frame de pile MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="e8537-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8537-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8537-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8537-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8537-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="e8537-106">dans Index de l’argument dans ce frame de pile MSIL.</span><span class="sxs-lookup"><span data-stu-id="e8537-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="e8537-107">[en sortie] Un pointeur vers l'adresse d'un objet ICorDebugValue qui représente la valeur extraite.</span><span class="sxs-lookup"><span data-stu-id="e8537-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8537-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="e8537-108">Remarks</span></span>  
 <span data-ttu-id="e8537-109">La `GetArgument` méthode peut être utilisée dans un frame de pile MSIL ou dans un frame compilé juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="e8537-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8537-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e8537-110">Requirements</span></span>  
 <span data-ttu-id="e8537-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8537-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8537-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8537-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8537-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8537-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8537-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8537-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
