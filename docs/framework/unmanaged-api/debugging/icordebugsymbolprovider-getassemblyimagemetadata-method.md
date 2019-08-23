---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata, méthode
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad86c42d0f23de25fe0e5b9123a0dba3695d8d64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964655"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="1ae57-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata, méthode</span><span class="sxs-lookup"><span data-stu-id="1ae57-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="1ae57-103">Retourne les métadonnées d'un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="1ae57-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ae57-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ae57-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1ae57-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="1ae57-106">à Pointeur vers l’adresse d’un objet [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) qui contient des informations sur la taille et l’adresse des métadonnées de l’assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="1ae57-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ae57-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1ae57-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ae57-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1ae57-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ae57-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1ae57-109">Requirements</span></span>  
 <span data-ttu-id="1ae57-110">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ae57-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ae57-111">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1ae57-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ae57-112">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ae57-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ae57-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ae57-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae57-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ae57-114">See also</span></span>

- [<span data-ttu-id="1ae57-115">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="1ae57-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="1ae57-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1ae57-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
