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
ms.openlocfilehash: 5f731b1459542c3f5378790b21f2ea576e89ad97
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893340"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="f8699-102">ICorDebugCode4 :: EnumerateVariableHomes, méthode</span><span class="sxs-lookup"><span data-stu-id="f8699-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="f8699-103">Obtient un énumérateur pour les variables locales et les arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="f8699-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8699-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8699-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8699-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8699-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="f8699-106">Pointeur vers l’adresse d’un objet d’interface [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) qui est un énumérateur pour les variables locales et les arguments dans une fonction.</span><span class="sxs-lookup"><span data-stu-id="f8699-106">A pointer to the address of an [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8699-107">Notes </span><span class="sxs-lookup"><span data-stu-id="f8699-107">Remarks</span></span>  
 <span data-ttu-id="f8699-108">L’objet d’interface [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) est un énumérateur standard dérivé de l’interface « ICorDebugEnum » qui vous permet d’énumérer des objets [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f8699-108">The [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="f8699-109">La collection peut inclure plusieurs objets [ICorDebugVariableHome](icordebugvariablehome-interface.md) pour le même emplacement ou index d’argument s’ils ont des maisons différentes à des points différents dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="f8699-109">The collection may include multiple [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8699-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f8699-110">Requirements</span></span>  
 <span data-ttu-id="f8699-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8699-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8699-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8699-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8699-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8699-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8699-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8699-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8699-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8699-115">See also</span></span>

- [<span data-ttu-id="f8699-116">ICorDebugCode4, interface</span><span class="sxs-lookup"><span data-stu-id="f8699-116">ICorDebugCode4 Interface</span></span>](icordebugcode4-interface.md)
- [<span data-ttu-id="f8699-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f8699-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
