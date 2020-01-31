---
title: Méthode ICorDebugVariableSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: 6d60dbdefd09770fd5a18653c5118469323581e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790909"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="5ae89-102">Méthode ICorDebugVariableSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="5ae89-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="5ae89-103">Obtient la taille d'une variable en octets.</span><span class="sxs-lookup"><span data-stu-id="5ae89-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ae89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ae89-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ae89-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="5ae89-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="5ae89-106">Pointeur vers un entier non signé 32 bits contenant la taille de la variable.</span><span class="sxs-lookup"><span data-stu-id="5ae89-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ae89-107">Notes</span><span class="sxs-lookup"><span data-stu-id="5ae89-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ae89-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5ae89-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ae89-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="5ae89-109">Requirements</span></span>  
 <span data-ttu-id="5ae89-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ae89-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ae89-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ae89-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ae89-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ae89-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ae89-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ae89-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae89-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ae89-114">See also</span></span>

- [<span data-ttu-id="5ae89-115">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="5ae89-115">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="5ae89-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5ae89-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
