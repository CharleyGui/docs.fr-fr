---
title: 'ICorDebugCode4 :: EnumerateVariableHomes, méthode'
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
ms.openlocfilehash: ca452b230e2508f2d69c9aa38f274db506f3a906
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784090"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="faa66-102">ICorDebugCode4 :: EnumerateVariableHomes, méthode</span><span class="sxs-lookup"><span data-stu-id="faa66-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="faa66-103">Obtient un énumérateur pour les variables locales et les arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="faa66-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faa66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faa66-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faa66-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="faa66-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="faa66-106">Pointeur vers l’adresse d’un objet d’interface [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) qui est un énumérateur pour les variables locales et les arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="faa66-106">A pointer to the address of an [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faa66-107">Notes</span><span class="sxs-lookup"><span data-stu-id="faa66-107">Remarks</span></span>  
 <span data-ttu-id="faa66-108">L’objet d’interface [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) est un énumérateur standard dérivé de l’interface « ICorDebugEnum » qui vous permet d’énumérer des objets [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="faa66-108">The [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="faa66-109">La collection peut inclure plusieurs objets [ICorDebugVariableHome](icordebugvariablehome-interface.md) pour le même emplacement ou index d’argument s’ils ont des maisons différentes à des points différents dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="faa66-109">The collection may include multiple [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faa66-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="faa66-110">Requirements</span></span>  
 <span data-ttu-id="faa66-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faa66-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faa66-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="faa66-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="faa66-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="faa66-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="faa66-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faa66-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa66-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="faa66-115">See also</span></span>

- [<span data-ttu-id="faa66-116">ICorDebugCode4, interface</span><span class="sxs-lookup"><span data-stu-id="faa66-116">ICorDebugCode4 Interface</span></span>](icordebugcode4-interface.md)
- [<span data-ttu-id="faa66-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="faa66-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
