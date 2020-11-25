---
title: ICorDebugInternalFrame::GetFrameType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
ms.openlocfilehash: c675ba4b56cecd1990184cd2f0e805250c3dfeb7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724882"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="dfe0c-102">ICorDebugInternalFrame::GetFrameType, méthode</span><span class="sxs-lookup"><span data-stu-id="dfe0c-102">ICorDebugInternalFrame::GetFrameType Method</span></span>

<span data-ttu-id="dfe0c-103">Obtient le type de ce frame interne.</span><span class="sxs-lookup"><span data-stu-id="dfe0c-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfe0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfe0c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfe0c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dfe0c-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="dfe0c-106">à Pointeur vers une valeur de l’énumération CorDebugInternalFrameType, qui indique le type de frame interne représenté par cet `ICorDebugInternalFrame` objet.</span><span class="sxs-lookup"><span data-stu-id="dfe0c-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfe0c-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="dfe0c-107">Remarks</span></span>  

 <span data-ttu-id="dfe0c-108">Le type de frame interne ne sera jamais STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="dfe0c-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="dfe0c-109">Les débogueurs doivent ignorer correctement les types de frame interne non reconnus.</span><span class="sxs-lookup"><span data-stu-id="dfe0c-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfe0c-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dfe0c-110">Requirements</span></span>  

 <span data-ttu-id="dfe0c-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfe0c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfe0c-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfe0c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfe0c-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfe0c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfe0c-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfe0c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
