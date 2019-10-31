---
title: 'ICorProfilerInfo7 :: ReadInMemorySymbols'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
ms.openlocfilehash: ae51490be96f3eb6524831c93739c3befbc30b37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132037"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="891ef-102">ICorProfilerInfo7 :: ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="891ef-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="891ef-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="891ef-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="891ef-104">Lit les octets d’un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="891ef-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="891ef-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="891ef-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="891ef-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="891ef-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="891ef-107">dans Identificateur du module contenant le flux en mémoire.</span><span class="sxs-lookup"><span data-stu-id="891ef-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="891ef-108">dans Offset dans le flux en mémoire à partir duquel commencer la lecture des octets.</span><span class="sxs-lookup"><span data-stu-id="891ef-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="891ef-109">à Pointeur vers la mémoire tampon dans laquelle les données seront copiées.</span><span class="sxs-lookup"><span data-stu-id="891ef-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="891ef-110">La mémoire tampon doit avoir `countSymbolBytes` d’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="891ef-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="891ef-111">dans Nombre d’octets à copier.</span><span class="sxs-lookup"><span data-stu-id="891ef-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="891ef-112">à Lorsque la méthode est retournée, contient le nombre réel d’octets lus.</span><span class="sxs-lookup"><span data-stu-id="891ef-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="891ef-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="891ef-113">Return Value</span></span>  
 <span data-ttu-id="891ef-114">`S_OK`, si un nombre d’octets différent de zéro a été lu.</span><span class="sxs-lookup"><span data-stu-id="891ef-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="891ef-115">`CORPROF_E_MODULE_IS_DYNAMIC`, si le module a été créé à l’aide de <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="891ef-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="891ef-116">Notes</span><span class="sxs-lookup"><span data-stu-id="891ef-116">Remarks</span></span>  
 <span data-ttu-id="891ef-117">La méthode `ReadInMemorySymbols` tente de lire `countSymbolBytes` de données à partir du décalage `symbolsReadOffset` dans le flux en mémoire.</span><span class="sxs-lookup"><span data-stu-id="891ef-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="891ef-118">Les données sont copiées vers `pSymbolBytes`, qui est censée avoir `countSymbolBytes` d’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="891ef-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="891ef-119">`pCountSymbolsBytesRead` contient le nombre réel d’octets lus, qui peut être inférieur à `countSymbolBytes` si la fin du flux est atteinte.</span><span class="sxs-lookup"><span data-stu-id="891ef-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="891ef-120">L’implémentation actuelle ne prend pas en charge la réflexion. Emit.</span><span class="sxs-lookup"><span data-stu-id="891ef-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="891ef-121">Si le module a été créé à l’aide de Reflection. Emit, la méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="891ef-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="891ef-122">spécifications</span><span class="sxs-lookup"><span data-stu-id="891ef-122">Requirements</span></span>  
 <span data-ttu-id="891ef-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="891ef-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="891ef-124">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="891ef-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="891ef-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="891ef-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="891ef-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="891ef-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="891ef-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="891ef-127">See also</span></span>

- [<span data-ttu-id="891ef-128">ICorProfilerInfo7, interface</span><span class="sxs-lookup"><span data-stu-id="891ef-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
