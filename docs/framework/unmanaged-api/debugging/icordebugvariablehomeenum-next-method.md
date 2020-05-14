---
title: 'ICorDebugVariableHomeEnum :: Next, méthode'
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
ms.openlocfilehash: 980f563d3b11fbfcce48b6d7c05275af520e14f1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396502"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="c1f0a-102">ICorDebugVariableHomeEnum :: Next, méthode</span><span class="sxs-lookup"><span data-stu-id="c1f0a-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="c1f0a-103">Obtient le nombre spécifié d’instances [ICorDebugVariableHome](icordebugvariablehome-interface.md) qui contiennent des informations sur les variables locales et les arguments d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="c1f0a-103">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1f0a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1f0a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1f0a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c1f0a-106">[in] Nombre d'objets à récupérer.</span><span class="sxs-lookup"><span data-stu-id="c1f0a-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="c1f0a-107">Tableau de pointeurs, chacun pointant vers un objet [ICorDebugVariableHome](icordebugvariablehome-interface.md) qui fournit des informations sur une variable locale ou un argument d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="c1f0a-107">An array of pointers, each of which points to a [ICorDebugVariableHome](icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c1f0a-108">à Nombre d’instances réellement retournées dans les objets.</span><span class="sxs-lookup"><span data-stu-id="c1f0a-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1f0a-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c1f0a-109">Return Value</span></span>  
 <span data-ttu-id="c1f0a-110">La méthode retourne les valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="c1f0a-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="c1f0a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1f0a-111">HRESULT</span></span>|<span data-ttu-id="c1f0a-112">Description</span><span class="sxs-lookup"><span data-stu-id="c1f0a-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c1f0a-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="c1f0a-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c1f0a-114">Le nombre réel d’instances récupérées, comme indiqué dans `pceltFetched` , est inférieur au nombre d’instances demandé.</span><span class="sxs-lookup"><span data-stu-id="c1f0a-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1f0a-115">Notes</span><span class="sxs-lookup"><span data-stu-id="c1f0a-115">Remarks</span></span>  
 <span data-ttu-id="c1f0a-116">La méthode [ICorDebugVariableHomeEnum :: Next](icordebugvariablehomeenum-next-method.md) récupère un nombre maximal d' `celt` objets commençant à la position actuelle de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="c1f0a-116">The [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="c1f0a-117">Lorsque la méthode est retournée, `pceltFetched` contient le nombre réel d’objets récupérés.</span><span class="sxs-lookup"><span data-stu-id="c1f0a-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1f0a-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c1f0a-118">Requirements</span></span>  
 <span data-ttu-id="c1f0a-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1f0a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1f0a-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1f0a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1f0a-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1f0a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1f0a-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1f0a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1f0a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1f0a-123">See also</span></span>

- [<span data-ttu-id="c1f0a-124">ICorDebugVariableHomeEnum, interface</span><span class="sxs-lookup"><span data-stu-id="c1f0a-124">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="c1f0a-125">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="c1f0a-125">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
