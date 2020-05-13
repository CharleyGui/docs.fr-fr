---
title: ICorDebugFrame::GetCaller, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
ms.openlocfilehash: b29de0b70daa783197e78fe985d379d4124bc140
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205145"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="6a1f5-102">ICorDebugFrame::GetCaller, méthode</span><span class="sxs-lookup"><span data-stu-id="6a1f5-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="6a1f5-103">Obtient un pointeur vers l’objet ICorDebugFrame dans la chaîne actuelle qui a appelé ce frame.</span><span class="sxs-lookup"><span data-stu-id="6a1f5-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a1f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a1f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a1f5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6a1f5-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="6a1f5-106">à Pointeur vers l’adresse d’un `ICorDebugFrame` objet qui représente le frame appelant.</span><span class="sxs-lookup"><span data-stu-id="6a1f5-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="6a1f5-107">Cette valeur est null si le frame appelé est le frame le plus à l’extérieur dans la chaîne actuelle.</span><span class="sxs-lookup"><span data-stu-id="6a1f5-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a1f5-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6a1f5-108">Requirements</span></span>  
 <span data-ttu-id="6a1f5-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a1f5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a1f5-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a1f5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a1f5-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a1f5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a1f5-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a1f5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
