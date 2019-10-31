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
ms.openlocfilehash: 01c7cb2e4359a477c26f995602dbf29668e567c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131020"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="64d67-102">ICorDebugILFrame::GetArgument, méthode</span><span class="sxs-lookup"><span data-stu-id="64d67-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="64d67-103">Obtient la valeur de l’argument spécifié dans ce frame de pile MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="64d67-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64d67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64d67-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="64d67-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="64d67-106">dans Index de l’argument dans ce frame de pile MSIL.</span><span class="sxs-lookup"><span data-stu-id="64d67-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="64d67-107">à Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur récupérée.</span><span class="sxs-lookup"><span data-stu-id="64d67-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64d67-108">Notes</span><span class="sxs-lookup"><span data-stu-id="64d67-108">Remarks</span></span>  
 <span data-ttu-id="64d67-109">La méthode `GetArgument` peut être utilisée dans un frame de pile MSIL ou dans un frame compilé juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="64d67-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d67-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="64d67-110">Requirements</span></span>  
 <span data-ttu-id="64d67-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64d67-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d67-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64d67-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64d67-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64d67-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64d67-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d67-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
