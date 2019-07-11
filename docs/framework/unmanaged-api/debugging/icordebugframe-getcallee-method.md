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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10a5247632f242a4b4e0d33cf7fa7233d1b1e13b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754200"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="a83ba-102">ICorDebugFrame::GetCallee, méthode</span><span class="sxs-lookup"><span data-stu-id="a83ba-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="a83ba-103">Obtient un pointeur vers l’objet ICorDebugFrame dans la chaîne actuelle qui a appelé ce frame.</span><span class="sxs-lookup"><span data-stu-id="a83ba-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a83ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a83ba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a83ba-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a83ba-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="a83ba-106">[out] Un pointeur vers l’adresse d’un `ICorDebugFrame` objet qui représente le frame appelé.</span><span class="sxs-lookup"><span data-stu-id="a83ba-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="a83ba-107">Cette valeur est null si le frame appelant est le plus profond frame dans la chaîne actuelle.</span><span class="sxs-lookup"><span data-stu-id="a83ba-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a83ba-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a83ba-108">Requirements</span></span>  
 <span data-ttu-id="a83ba-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a83ba-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a83ba-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a83ba-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a83ba-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a83ba-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a83ba-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a83ba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
