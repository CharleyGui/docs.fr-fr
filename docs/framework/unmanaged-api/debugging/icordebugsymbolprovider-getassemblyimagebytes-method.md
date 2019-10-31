---
title: 'ICorDebugSymbolProvider :: Getassemblyimagebytes,, méthode'
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 3184ba116704df8945b53766e62435a4252eaa11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138933"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="85f59-102">ICorDebugSymbolProvider :: Getassemblyimagebytes,, méthode</span><span class="sxs-lookup"><span data-stu-id="85f59-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="85f59-103">Lit les données d’un assembly fusionné pour une adresse virtuelle relative (RVA) donnée dans l’assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="85f59-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85f59-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,   
   [in] ULONG32 length,   
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85f59-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="85f59-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="85f59-106">[in] Adresse virtuelle relative (RVA) dans un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="85f59-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="85f59-107">Nombre d'octets à lire à partir de l'assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="85f59-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="85f59-108">Pointeur vers l’adresse d’un objet [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) qui contient des informations sur la mémoire tampon avec les métadonnées de l’assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="85f59-108">A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85f59-109">Notes</span><span class="sxs-lookup"><span data-stu-id="85f59-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85f59-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="85f59-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85f59-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="85f59-111">Requirements</span></span>  
 <span data-ttu-id="85f59-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85f59-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85f59-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85f59-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85f59-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85f59-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85f59-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85f59-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f59-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85f59-116">See also</span></span>

- [<span data-ttu-id="85f59-117">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="85f59-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="85f59-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="85f59-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
