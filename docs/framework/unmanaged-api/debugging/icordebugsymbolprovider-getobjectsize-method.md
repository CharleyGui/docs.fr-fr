---
title: ICorDebugSymbolProvider::GetObjectSize, méthode
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: 64324df49ad0b5dfa3c25455950bddc3d687b178
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379556"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="c9f31-102">ICorDebugSymbolProvider::GetObjectSize, méthode</span><span class="sxs-lookup"><span data-stu-id="c9f31-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="c9f31-103">Retourne la taille d'un objet en fonction de sa signature typespec.</span><span class="sxs-lookup"><span data-stu-id="c9f31-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9f31-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9f31-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c9f31-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="c9f31-106">[in] Nombre d'octets dans la signature typespec.</span><span class="sxs-lookup"><span data-stu-id="c9f31-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="c9f31-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="c9f31-107">typeSig</span></span>  
 <span data-ttu-id="c9f31-108">[in] Signature typespec.</span><span class="sxs-lookup"><span data-stu-id="c9f31-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="c9f31-109">[out] Pointeur vers la taille de l'objet.</span><span class="sxs-lookup"><span data-stu-id="c9f31-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9f31-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="c9f31-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9f31-111">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c9f31-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9f31-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c9f31-112">Requirements</span></span>  
 <span data-ttu-id="c9f31-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9f31-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9f31-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9f31-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9f31-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9f31-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9f31-116">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9f31-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f31-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9f31-117">See also</span></span>

- [<span data-ttu-id="c9f31-118">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="c9f31-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="c9f31-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c9f31-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
