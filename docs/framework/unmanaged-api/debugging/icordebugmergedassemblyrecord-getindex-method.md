---
title: ICorDebugMergedAssemblyRecord::GetIndex, méthode
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: b13e589e32b3317b567a4a89a5b48fc1299a1a84
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206950"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="94722-102">ICorDebugMergedAssemblyRecord::GetIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="94722-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="94722-103">Obtient l'index de préfixe de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="94722-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94722-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94722-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94722-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="94722-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="94722-106">[out] Pointeur vers l'index de préfixe.</span><span class="sxs-lookup"><span data-stu-id="94722-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94722-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="94722-107">Remarks</span></span>  
 <span data-ttu-id="94722-108">L'index de préfixe est utilisé pour empêcher les collisions de noms dans les noms de types de métadonnées fusionnées.</span><span class="sxs-lookup"><span data-stu-id="94722-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94722-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="94722-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94722-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="94722-110">Requirements</span></span>  
 <span data-ttu-id="94722-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94722-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94722-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94722-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94722-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94722-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94722-114">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94722-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94722-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94722-115">See also</span></span>

- [<span data-ttu-id="94722-116">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="94722-116">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="94722-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="94722-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
