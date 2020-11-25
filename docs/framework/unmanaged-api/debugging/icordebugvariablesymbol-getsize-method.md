---
title: Méthode ICorDebugVariableSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: 1079351e75ec9c48a9657f514ee56e2e6a4b0920
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731369"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="a6641-102">Méthode ICorDebugVariableSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="a6641-102">ICorDebugVariableSymbol::GetSize Method</span></span>

<span data-ttu-id="a6641-103">Obtient la taille d'une variable en octets.</span><span class="sxs-lookup"><span data-stu-id="a6641-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6641-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6641-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6641-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a6641-105">Parameters</span></span>  

 `pcbValue`  
 <span data-ttu-id="a6641-106">Pointeur vers un entier non signé 32 bits contenant la taille de la variable.</span><span class="sxs-lookup"><span data-stu-id="a6641-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6641-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="a6641-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6641-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a6641-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6641-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a6641-109">Requirements</span></span>  

 <span data-ttu-id="a6641-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6641-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6641-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6641-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6641-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6641-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6641-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6641-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6641-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6641-114">See also</span></span>

- [<span data-ttu-id="a6641-115">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="a6641-115">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="a6641-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a6641-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
