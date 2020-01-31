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
ms.openlocfilehash: fdfa38a4cdbbaad2fc2c987a10a122af4a1fc9a9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791036"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="cfe71-102">ICorDebugVariableHome :: GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="cfe71-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="cfe71-103">Obtient l’instance « ICorDebugCode » qui contient cet objet [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="cfe71-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfe71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfe71-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfe71-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="cfe71-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="cfe71-106">à Pointeur vers l’adresse de l’instance « ICorDebugCode » qui contient cet objet [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="cfe71-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfe71-107">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="cfe71-107">Requirements</span></span>  
 <span data-ttu-id="cfe71-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfe71-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfe71-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfe71-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfe71-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfe71-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfe71-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfe71-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfe71-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfe71-112">See also</span></span>

- [<span data-ttu-id="cfe71-113">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="cfe71-113">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
