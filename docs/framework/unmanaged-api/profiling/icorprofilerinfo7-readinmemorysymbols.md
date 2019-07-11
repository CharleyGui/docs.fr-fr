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
ms.openlocfilehash: 2a878ccf94fb4f6d67daa3a4dd42fcf98faf34a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748641"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="341d9-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="341d9-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="341d9-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="341d9-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="341d9-104">Lit les octets à partir d’un flux de symbole d’en mémoire.</span><span class="sxs-lookup"><span data-stu-id="341d9-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="341d9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="341d9-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="341d9-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="341d9-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="341d9-107">[in] L’identificateur du module qui contient le flux en mémoire.</span><span class="sxs-lookup"><span data-stu-id="341d9-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="341d9-108">[in] Offset dans le flux en mémoire à partir duquel commencer la lecture des octets.</span><span class="sxs-lookup"><span data-stu-id="341d9-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="341d9-109">[out] Pointeur vers la mémoire tampon à laquelle les données seront copiées.</span><span class="sxs-lookup"><span data-stu-id="341d9-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="341d9-110">La mémoire tampon doit avoir `countSymbolBytes` d’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="341d9-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="341d9-111">[in] Le nombre d’octets à copier.</span><span class="sxs-lookup"><span data-stu-id="341d9-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="341d9-112">[out] Lorsque la méthode est retournée, contient le nombre réel d’octets lus.</span><span class="sxs-lookup"><span data-stu-id="341d9-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="341d9-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="341d9-113">Return Value</span></span>  
 <span data-ttu-id="341d9-114">`S_OK`, si un nombre d’octets lus.</span><span class="sxs-lookup"><span data-stu-id="341d9-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="341d9-115">`CORPROF_E_MODULE_IS_DYNAMIC`, si le module a été créé à l’aide de <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="341d9-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="341d9-116">Notes</span><span class="sxs-lookup"><span data-stu-id="341d9-116">Remarks</span></span>  
 <span data-ttu-id="341d9-117">Le `ReadInMemorySymbols` méthode tente de lire `countSymbolBytes` de données en commençant au décalage `symbolsReadOffset` dans le flux en mémoire.</span><span class="sxs-lookup"><span data-stu-id="341d9-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="341d9-118">Les données sont copiées vers `pSymbolBytes`, qui est censé avoir `countSymbolBytes` d’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="341d9-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="341d9-119">`pCountSymbolsBytesRead` contient le nombre réel d’octets lus, qui peut être inférieure à `countSymbolBytes` si la fin du flux est atteinte.</span><span class="sxs-lookup"><span data-stu-id="341d9-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="341d9-120">L’implémentation actuelle ne prend pas en charge de Reflection.Emit.</span><span class="sxs-lookup"><span data-stu-id="341d9-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="341d9-121">Si le module a été créé à l’aide de Reflection.Emit, la méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="341d9-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="341d9-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="341d9-122">Requirements</span></span>  
 <span data-ttu-id="341d9-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="341d9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="341d9-124">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="341d9-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="341d9-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="341d9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="341d9-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="341d9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="341d9-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="341d9-127">See also</span></span>

- [<span data-ttu-id="341d9-128">ICorProfilerInfo7, interface</span><span class="sxs-lookup"><span data-stu-id="341d9-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
