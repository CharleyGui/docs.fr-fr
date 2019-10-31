---
title: ICorDebugFrame::GetCallee, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
ms.openlocfilehash: b83dec65e1dd4fc610be3190e8126e6d9d38a6e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121223"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="0dba7-102">ICorDebugFrame::GetCallee, méthode</span><span class="sxs-lookup"><span data-stu-id="0dba7-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="0dba7-103">Obtient un pointeur vers l’objet ICorDebugFrame dans la chaîne actuelle appelée par ce frame.</span><span class="sxs-lookup"><span data-stu-id="0dba7-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dba7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0dba7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dba7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0dba7-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="0dba7-106">à Pointeur vers l’adresse d’un objet `ICorDebugFrame` qui représente le frame appelé.</span><span class="sxs-lookup"><span data-stu-id="0dba7-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="0dba7-107">Cette valeur est null si le frame appelant est le frame le plus profond dans la chaîne actuelle.</span><span class="sxs-lookup"><span data-stu-id="0dba7-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dba7-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="0dba7-108">Requirements</span></span>  
 <span data-ttu-id="0dba7-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dba7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dba7-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0dba7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0dba7-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0dba7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dba7-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dba7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
