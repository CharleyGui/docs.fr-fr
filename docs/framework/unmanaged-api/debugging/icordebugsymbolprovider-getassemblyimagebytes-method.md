---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes, méthode
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: b52614065d599edf8e556524c33e8bc50b4924ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709178"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="0ec22-102">ICorDebugSymbolProvider::GetAssemblyImageBytes, méthode</span><span class="sxs-lookup"><span data-stu-id="0ec22-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>

<span data-ttu-id="0ec22-103">Lit les données d’un assembly fusionné pour une adresse virtuelle relative (RVA) donnée dans l’assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="0ec22-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ec22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ec22-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ec22-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0ec22-105">Parameters</span></span>  

 `rva`  
 <span data-ttu-id="0ec22-106">[in] Adresse virtuelle relative (RVA) dans un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="0ec22-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="0ec22-107">Nombre d'octets à lire à partir de l'assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="0ec22-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="0ec22-108">Pointeur vers l’adresse d’un objet [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) qui contient des informations sur la mémoire tampon avec les métadonnées de l’assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="0ec22-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ec22-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="0ec22-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ec22-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0ec22-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ec22-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0ec22-111">Requirements</span></span>  

 <span data-ttu-id="0ec22-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ec22-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ec22-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ec22-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ec22-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ec22-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ec22-115">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ec22-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ec22-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ec22-116">See also</span></span>

- [<span data-ttu-id="0ec22-117">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="0ec22-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="0ec22-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0ec22-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
