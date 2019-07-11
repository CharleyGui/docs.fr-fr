---
title: ICorDebugVariableHome::GetCode (méthode)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c0cae29cceb3f23c7d09cf096937c99641d5a87
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773592"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="8f423-102">ICorDebugVariableHome::GetCode (méthode)</span><span class="sxs-lookup"><span data-stu-id="8f423-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="8f423-103">Obtient l’instance « ICorDebugCode » qui contient ce [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="8f423-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f423-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f423-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f423-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8f423-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="8f423-106">[out] Un pointeur vers l’adresse de l’instance « ICorDebugCode » qui contient ce [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="8f423-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f423-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8f423-107">Requirements</span></span>  
 <span data-ttu-id="8f423-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f423-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f423-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f423-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f423-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f423-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f423-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f423-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f423-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f423-112">See also</span></span>

- [<span data-ttu-id="8f423-113">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="8f423-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
