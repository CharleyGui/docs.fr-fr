---
title: ICorDebugSymbolProvider::GetCodeRange, méthode
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: f61a98dbd5a65207a46e033d54f9d5f60adac201
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709114"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="2b663-102">ICorDebugSymbolProvider::GetCodeRange, méthode</span><span class="sxs-lookup"><span data-stu-id="2b663-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>

<span data-ttu-id="2b663-103">Obtient l'adresse de début et la taille de la méthode pour une adresse virtuelle relative (RVA) donnée dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="2b663-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b663-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b663-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b663-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2b663-105">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="2b663-106">[in] Adresse virtuelle relative (RVA) dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="2b663-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="2b663-107">[out] Pointeur vers l'adresse de début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="2b663-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="2b663-108">Pointeur vers la taille du code de la méthode (nombre d'octets du code de la méthode).</span><span class="sxs-lookup"><span data-stu-id="2b663-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b663-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="2b663-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b663-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2b663-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b663-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2b663-111">Requirements</span></span>  

 <span data-ttu-id="2b663-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b663-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b663-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b663-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b663-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b663-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b663-115">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b663-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b663-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b663-116">See also</span></span>

- [<span data-ttu-id="2b663-117">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="2b663-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="2b663-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2b663-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
