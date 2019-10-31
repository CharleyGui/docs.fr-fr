---
title: 'ICorDebugVariableHome :: GetCode, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
ms.openlocfilehash: 4770eb3e93104dd3862eb2163faf1dc7fe9008ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125136"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="a6726-102">ICorDebugVariableHome :: GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="a6726-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="a6726-103">Obtient l’instance « ICorDebugCode » qui contient cet objet [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a6726-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6726-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6726-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6726-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a6726-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="a6726-106">à Pointeur vers l’adresse de l’instance « ICorDebugCode » qui contient cet objet [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a6726-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6726-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="a6726-107">Requirements</span></span>  
 <span data-ttu-id="a6726-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6726-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6726-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6726-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6726-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6726-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6726-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6726-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6726-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6726-112">See also</span></span>

- [<span data-ttu-id="a6726-113">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="a6726-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
