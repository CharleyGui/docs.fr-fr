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
ms.openlocfilehash: 6b598352f734cf47514a82de1d0fca65d430a9ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209966"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="d53c6-102">ICorDebugInternalFrame::GetFrameType, méthode</span><span class="sxs-lookup"><span data-stu-id="d53c6-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="d53c6-103">Obtient le type de ce frame interne.</span><span class="sxs-lookup"><span data-stu-id="d53c6-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d53c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d53c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d53c6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d53c6-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="d53c6-106">à Pointeur vers une valeur de l’énumération CorDebugInternalFrameType, qui indique le type de frame interne représenté par cet `ICorDebugInternalFrame` objet.</span><span class="sxs-lookup"><span data-stu-id="d53c6-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d53c6-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="d53c6-107">Remarks</span></span>  
 <span data-ttu-id="d53c6-108">Le type de frame interne ne sera jamais STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="d53c6-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="d53c6-109">Les débogueurs doivent ignorer correctement les types de frame interne non reconnus.</span><span class="sxs-lookup"><span data-stu-id="d53c6-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d53c6-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d53c6-110">Requirements</span></span>  
 <span data-ttu-id="d53c6-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d53c6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d53c6-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d53c6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d53c6-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d53c6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d53c6-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d53c6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
