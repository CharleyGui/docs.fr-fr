---
title: ICorDebugDataTarget2::GetSymbolProviderForImage, méthode
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 64a35f65bc3c31e091e2d94260efb84f20abb795
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122104"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="2ced6-102">ICorDebugDataTarget2::GetSymbolProviderForImage, méthode</span><span class="sxs-lookup"><span data-stu-id="2ced6-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="2ced6-103">Retourne le fournisseur de symboles d'un module à partir de l'adresse de base de ce module.</span><span class="sxs-lookup"><span data-stu-id="2ced6-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ced6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ced6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ced6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ced6-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="2ced6-106">dans Valeur [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) qui représente l’adresse de base d’un module.</span><span class="sxs-lookup"><span data-stu-id="2ced6-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="2ced6-107">à Pointeur vers l’adresse d’un objet [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2ced6-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ced6-108">Notes</span><span class="sxs-lookup"><span data-stu-id="2ced6-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ced6-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2ced6-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ced6-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="2ced6-110">Requirements</span></span>  
 <span data-ttu-id="2ced6-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ced6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ced6-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ced6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ced6-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ced6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ced6-114">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ced6-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ced6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ced6-115">See also</span></span>

- [<span data-ttu-id="2ced6-116">ICorDebugDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="2ced6-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="2ced6-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2ced6-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
