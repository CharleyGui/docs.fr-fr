---
title: ICorDebugInstanceFieldSymbol::GetOffset, méthode
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 2d73de46bbb1023f20dd9023076630611c74be5d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724921"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="49f67-102">ICorDebugInstanceFieldSymbol::GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="49f67-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>

<span data-ttu-id="49f67-103">Obtient l'offset en octets de ce champ d'instance dans sa classe parente.</span><span class="sxs-lookup"><span data-stu-id="49f67-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49f67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49f67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49f67-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49f67-105">Parameters</span></span>  

 `pcbOffset`  
 <span data-ttu-id="49f67-106">Pointeur vers le nombre d'octets correspondant à l'offset de ce champ d'instance dans sa classe parente.</span><span class="sxs-lookup"><span data-stu-id="49f67-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49f67-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="49f67-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49f67-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="49f67-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49f67-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="49f67-109">Requirements</span></span>  

 <span data-ttu-id="49f67-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49f67-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49f67-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49f67-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49f67-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49f67-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49f67-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49f67-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49f67-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49f67-114">See also</span></span>

- [<span data-ttu-id="49f67-115">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="49f67-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="49f67-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="49f67-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
