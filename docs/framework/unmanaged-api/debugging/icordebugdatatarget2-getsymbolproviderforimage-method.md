---
title: ICorDebugDataTarget2::GetSymbolProviderForImage, méthode
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 500d36b414be686071990a6e1b40dd8759d02ae9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178933"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="5d5c5-102">ICorDebugDataTarget2::GetSymbolProviderForImage, méthode</span><span class="sxs-lookup"><span data-stu-id="5d5c5-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="5d5c5-103">Retourne le fournisseur de symboles d'un module à partir de l'adresse de base de ce module.</span><span class="sxs-lookup"><span data-stu-id="5d5c5-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d5c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d5c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d5c5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5d5c5-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="5d5c5-106">[dans] Une [valeur CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) qui représente l’adresse de base d’un module.</span><span class="sxs-lookup"><span data-stu-id="5d5c5-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="5d5c5-107">[out] Un pointeur à l’adresse d’un objet [ICorDebugSymbolProvider.](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="5d5c5-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d5c5-108">Notes </span><span class="sxs-lookup"><span data-stu-id="5d5c5-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d5c5-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5d5c5-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d5c5-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5d5c5-110">Requirements</span></span>  
 <span data-ttu-id="5d5c5-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d5c5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d5c5-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d5c5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d5c5-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d5c5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d5c5-114">**.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d5c5-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d5c5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d5c5-115">See also</span></span>

- [<span data-ttu-id="5d5c5-116">ICorDebugDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="5d5c5-116">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="5d5c5-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5d5c5-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
