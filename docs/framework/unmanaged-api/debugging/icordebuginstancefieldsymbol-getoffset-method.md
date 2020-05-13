---
title: ICorDebugInstanceFieldSymbol::GetOffset, méthode
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 7d553c1a446e06f34c20da18c0edfe6773cfb597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209979"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="c1daf-102">ICorDebugInstanceFieldSymbol::GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="c1daf-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="c1daf-103">Obtient l'offset en octets de ce champ d'instance dans sa classe parente.</span><span class="sxs-lookup"><span data-stu-id="c1daf-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1daf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1daf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1daf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1daf-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="c1daf-106">Pointeur vers le nombre d'octets correspondant à l'offset de ce champ d'instance dans sa classe parente.</span><span class="sxs-lookup"><span data-stu-id="c1daf-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1daf-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="c1daf-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1daf-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c1daf-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1daf-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c1daf-109">Requirements</span></span>  
 <span data-ttu-id="c1daf-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1daf-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1daf-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1daf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1daf-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1daf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1daf-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1daf-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1daf-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1daf-114">See also</span></span>

- [<span data-ttu-id="c1daf-115">ICorDebugInstanceFieldSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="c1daf-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="c1daf-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c1daf-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
