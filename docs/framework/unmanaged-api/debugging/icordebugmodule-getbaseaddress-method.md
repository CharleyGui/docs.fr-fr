---
title: ICorDebugModule::GetBaseAddress, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
ms.openlocfilehash: 9270afa1d8c8ddd74cfe6dd05e39c1480f5767e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206937"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="682dd-102">ICorDebugModule::GetBaseAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="682dd-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="682dd-103">Obtient l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="682dd-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="682dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="682dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="682dd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="682dd-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="682dd-106">à `CORDB_ADDRESS`Qui spécifie l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="682dd-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="682dd-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="682dd-107">Remarks</span></span>  
 <span data-ttu-id="682dd-108">Si le module est une image native (autrement dit, si le module a été produit par le générateur d’images natives, NGen. exe), son adresse de base sera égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="682dd-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="682dd-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="682dd-109">Requirements</span></span>  
 <span data-ttu-id="682dd-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="682dd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="682dd-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="682dd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="682dd-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="682dd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="682dd-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="682dd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="682dd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="682dd-114">See also</span></span>
