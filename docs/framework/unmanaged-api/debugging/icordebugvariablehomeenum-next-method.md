---
title: ICorDebugVariableHomeEnum::Next (méthode)
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41aff94b8241f07c8646ecc52c06567fc262f703
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774925"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="7c402-102">ICorDebugVariableHomeEnum::Next (méthode)</span><span class="sxs-lookup"><span data-stu-id="7c402-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="7c402-103">Obtient le nombre spécifié de [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances qui contiennent des informations sur les variables locales et les arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="7c402-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c402-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c402-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c402-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7c402-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7c402-106">[in] Nombre d'objets à récupérer.</span><span class="sxs-lookup"><span data-stu-id="7c402-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="7c402-107">Un tableau de pointeurs, chacun d’eux pointe vers un [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objet qui fournit des informations sur une variable locale ou un argument d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="7c402-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7c402-108">[out] Le nombre d’instances réellement retournés dans les objets.</span><span class="sxs-lookup"><span data-stu-id="7c402-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c402-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7c402-109">Return Value</span></span>  
 <span data-ttu-id="7c402-110">La méthode retourne les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="7c402-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="7c402-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c402-111">HRESULT</span></span>|<span data-ttu-id="7c402-112">Description</span><span class="sxs-lookup"><span data-stu-id="7c402-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7c402-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="7c402-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7c402-114">Le nombre réel d’instances récupérées, comme indiqué dans `pceltFetched`, est inférieur au nombre d’instances demandées.</span><span class="sxs-lookup"><span data-stu-id="7c402-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c402-115">Notes</span><span class="sxs-lookup"><span data-stu-id="7c402-115">Remarks</span></span>  
 <span data-ttu-id="7c402-116">Le [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) méthode récupère un maximum de `celt` objets commençant à la position actuelle de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="7c402-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="7c402-117">Lorsque la méthode est retournée, `pceltFetched` contient le nombre réel d’objets récupérés.</span><span class="sxs-lookup"><span data-stu-id="7c402-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c402-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7c402-118">Requirements</span></span>  
 <span data-ttu-id="7c402-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c402-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c402-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c402-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c402-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c402-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c402-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c402-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c402-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c402-123">See also</span></span>

- [<span data-ttu-id="7c402-124">ICorDebugVariableHomeEnum, interface</span><span class="sxs-lookup"><span data-stu-id="7c402-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="7c402-125">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="7c402-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
