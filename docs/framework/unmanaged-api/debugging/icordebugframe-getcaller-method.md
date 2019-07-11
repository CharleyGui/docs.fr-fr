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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a637cebb9e1aef20c600353eb14fe900ad7513c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754162"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="24bfd-102">ICorDebugFrame::GetCaller, méthode</span><span class="sxs-lookup"><span data-stu-id="24bfd-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="24bfd-103">Obtient un pointeur vers l’objet ICorDebugFrame dans la chaîne actuelle qui a appelé ce frame.</span><span class="sxs-lookup"><span data-stu-id="24bfd-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24bfd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24bfd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24bfd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="24bfd-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="24bfd-106">[out] Un pointeur vers l’adresse d’un `ICorDebugFrame` objet qui représente le frame d’appel.</span><span class="sxs-lookup"><span data-stu-id="24bfd-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="24bfd-107">Cette valeur est null si le frame appelé est le frame le plus extérieur dans la chaîne actuelle.</span><span class="sxs-lookup"><span data-stu-id="24bfd-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24bfd-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="24bfd-108">Requirements</span></span>  
 <span data-ttu-id="24bfd-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24bfd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24bfd-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24bfd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24bfd-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24bfd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24bfd-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24bfd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
