---
title: ICorProfilerInfo7::ReadInMemorySymbols
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3df5324e23ebeded38f3aa9843f81701f7fd333
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251047"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="1423c-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="1423c-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="1423c-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="1423c-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="1423c-104">Lit les octets à partir d’un flux de symbole d’en mémoire.</span><span class="sxs-lookup"><span data-stu-id="1423c-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1423c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1423c-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1423c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1423c-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1423c-107">[in] L’identificateur du module qui contient le flux en mémoire.</span><span class="sxs-lookup"><span data-stu-id="1423c-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="1423c-108">[in] Offset dans le flux en mémoire à partir duquel commencer la lecture des octets.</span><span class="sxs-lookup"><span data-stu-id="1423c-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="1423c-109">[out] Pointeur vers la mémoire tampon à laquelle les données seront copiées.</span><span class="sxs-lookup"><span data-stu-id="1423c-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="1423c-110">La mémoire tampon doit avoir `countSymbolBytes` d’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="1423c-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="1423c-111">[in] Le nombre d’octets à copier.</span><span class="sxs-lookup"><span data-stu-id="1423c-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="1423c-112">[out] Lorsque la méthode est retournée, contient le nombre réel d’octets lus.</span><span class="sxs-lookup"><span data-stu-id="1423c-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1423c-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1423c-113">Return Value</span></span>  
 <span data-ttu-id="1423c-114">`S_OK`, si un nombre d’octets lus.</span><span class="sxs-lookup"><span data-stu-id="1423c-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="1423c-115">`CORPROF_E_MODULE_IS_DYNAMIC`, si le module a été créé à l’aide de <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="1423c-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1423c-116">Notes</span><span class="sxs-lookup"><span data-stu-id="1423c-116">Remarks</span></span>  
 <span data-ttu-id="1423c-117">Le `ReadInMemorySymbols` méthode tente de lire `countSymbolBytes` de données en commençant au décalage `symbolsReadOffset` dans le flux en mémoire.</span><span class="sxs-lookup"><span data-stu-id="1423c-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="1423c-118">Les données sont copiées vers `pSymbolBytes`, qui est censé avoir `countSymbolBytes` d’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="1423c-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="1423c-119">`pCountSymbolsBytesRead` contient le nombre réel d’octets lus, qui peut être inférieure à `countSymbolBytes` si la fin du flux est atteinte.</span><span class="sxs-lookup"><span data-stu-id="1423c-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1423c-120">L’implémentation actuelle ne prend pas en charge de Reflection.Emit.</span><span class="sxs-lookup"><span data-stu-id="1423c-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="1423c-121">Si le module a été créé à l’aide de Reflection.Emit, la méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="1423c-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1423c-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1423c-122">Requirements</span></span>  
 <span data-ttu-id="1423c-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1423c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1423c-124">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1423c-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1423c-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1423c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1423c-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1423c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1423c-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1423c-127">See also</span></span>

- [<span data-ttu-id="1423c-128">ICorProfilerInfo7, interface</span><span class="sxs-lookup"><span data-stu-id="1423c-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
