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
ms.openlocfilehash: d6ce5a5cc64a5eb805faa5bb17a42a662940affe
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210252"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="d7684-102">ICorDebugILFrame::GetLocalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="d7684-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="d7684-103">Obtient la valeur de la variable locale spécifiée dans ce frame de pile MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="d7684-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7684-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7684-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7684-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d7684-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="d7684-106">dans Index de la variable locale dans ce frame de pile MSIL.</span><span class="sxs-lookup"><span data-stu-id="d7684-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d7684-107">[en sortie] Un pointeur vers l'adresse d'un objet ICorDebugValue qui représente la valeur extraite.</span><span class="sxs-lookup"><span data-stu-id="d7684-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7684-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="d7684-108">Remarks</span></span>  
 <span data-ttu-id="d7684-109">La `GetLocalVariable` méthode peut être utilisée dans un frame de pile MSIL ou dans un frame compilé juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="d7684-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7684-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d7684-110">Requirements</span></span>  
 <span data-ttu-id="d7684-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7684-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7684-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7684-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7684-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7684-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7684-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7684-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
