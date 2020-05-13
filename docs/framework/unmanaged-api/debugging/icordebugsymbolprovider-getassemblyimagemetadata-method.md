---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata, méthode
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: d118f0c984663e0844783ff52859698dd5335058
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376146"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="dc9d5-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata, méthode</span><span class="sxs-lookup"><span data-stu-id="dc9d5-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="dc9d5-103">Retourne les métadonnées d'un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="dc9d5-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc9d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc9d5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc9d5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dc9d5-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="dc9d5-106">à Pointeur vers l’adresse d’un objet [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) qui contient des informations sur la taille et l’adresse des métadonnées de l’assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="dc9d5-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc9d5-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="dc9d5-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc9d5-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dc9d5-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc9d5-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dc9d5-109">Requirements</span></span>  
 <span data-ttu-id="dc9d5-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc9d5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc9d5-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc9d5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc9d5-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc9d5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc9d5-113">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc9d5-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc9d5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc9d5-114">See also</span></span>

- [<span data-ttu-id="dc9d5-115">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="dc9d5-115">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="dc9d5-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="dc9d5-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
