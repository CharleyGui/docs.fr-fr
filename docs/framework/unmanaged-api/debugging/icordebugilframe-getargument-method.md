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
ms.openlocfilehash: d17179dbeb9564b16c0c95a43502a53a67d3b9b8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703159"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="c9904-102">ICorDebugILFrame::GetArgument, méthode</span><span class="sxs-lookup"><span data-stu-id="c9904-102">ICorDebugILFrame::GetArgument Method</span></span>

<span data-ttu-id="c9904-103">Obtient la valeur de l’argument spécifié dans ce frame de pile MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="c9904-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9904-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9904-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9904-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c9904-105">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="c9904-106">dans Index de l’argument dans ce frame de pile MSIL.</span><span class="sxs-lookup"><span data-stu-id="c9904-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c9904-107">[en sortie] Un pointeur vers l'adresse d'un objet ICorDebugValue qui représente la valeur extraite.</span><span class="sxs-lookup"><span data-stu-id="c9904-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9904-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="c9904-108">Remarks</span></span>  

 <span data-ttu-id="c9904-109">La `GetArgument` méthode peut être utilisée dans un frame de pile MSIL ou dans un frame compilé juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="c9904-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9904-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c9904-110">Requirements</span></span>  

 <span data-ttu-id="c9904-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9904-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9904-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9904-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9904-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9904-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9904-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9904-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
