---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes, méthode
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 6361b12802876ef480acbe1cc13f32b77ba0be49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178493"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="dc530-102">ICorDebugSymbolProvider::GetAssemblyImageBytes, méthode</span><span class="sxs-lookup"><span data-stu-id="dc530-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>
<span data-ttu-id="dc530-103">Lit les données d’un assembly fusionné pour une adresse virtuelle relative (RVA) donnée dans l’assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="dc530-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc530-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc530-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc530-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dc530-105">Parameters</span></span>  
 `rva`  
 <span data-ttu-id="dc530-106">[in] Adresse virtuelle relative (RVA) dans un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="dc530-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="dc530-107">Nombre d'octets à lire à partir de l'assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="dc530-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="dc530-108">Un pointeur à l’adresse d’un objet [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) qui contient des informations sur le tampon de mémoire avec des métadonnées d’assemblage fusionnées.</span><span class="sxs-lookup"><span data-stu-id="dc530-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc530-109">Notes </span><span class="sxs-lookup"><span data-stu-id="dc530-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc530-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dc530-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc530-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dc530-111">Requirements</span></span>  
 <span data-ttu-id="dc530-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc530-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc530-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc530-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc530-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc530-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc530-115">**.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc530-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc530-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc530-116">See also</span></span>

- [<span data-ttu-id="dc530-117">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="dc530-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="dc530-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="dc530-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
