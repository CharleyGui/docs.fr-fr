---
title: ICorDebugCode4::EnumerateVariableHomes (méthode)
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0e6acdf6996f437c85b629b0af886287b1aef03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748558"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="185d7-102">ICorDebugCode4::EnumerateVariableHomes (méthode)</span><span class="sxs-lookup"><span data-stu-id="185d7-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="185d7-103">Obtient un énumérateur pour les variables locales et les arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="185d7-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="185d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="185d7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="185d7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="185d7-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="185d7-106">Un pointeur vers l’adresse d’un [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) objet d’interface qui est un énumérateur pour les variables locales et les arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="185d7-106">A pointer to the address of an [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="185d7-107">Notes</span><span class="sxs-lookup"><span data-stu-id="185d7-107">Remarks</span></span>  
 <span data-ttu-id="185d7-108">Le [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) objet d’interface est un énumérateur standard dérivé de l’interface « ICorDebugEnum » qui vous permet d’énumérer les [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objets.</span><span class="sxs-lookup"><span data-stu-id="185d7-108">The [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="185d7-109">La collection peut inclure plusieurs [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objets pour l’index d’emplacement ou un argument même s’ils ont des habitations différentes à différents moments dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="185d7-109">The collection may include multiple [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="185d7-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="185d7-110">Requirements</span></span>  
 <span data-ttu-id="185d7-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="185d7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="185d7-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="185d7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="185d7-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="185d7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="185d7-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="185d7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="185d7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="185d7-115">See also</span></span>

- [<span data-ttu-id="185d7-116">ICorDebugCode4, interface</span><span class="sxs-lookup"><span data-stu-id="185d7-116">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)
- [<span data-ttu-id="185d7-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="185d7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
