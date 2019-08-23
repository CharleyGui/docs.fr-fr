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
ms.openlocfilehash: 95b463b23c230d620d746e48da49d75238ef2cb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955368"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="b3b96-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="b3b96-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="b3b96-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="b3b96-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="b3b96-104">Lit les octets d’un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="b3b96-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3b96-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3b96-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3b96-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b3b96-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="b3b96-107">dans Identificateur du module contenant le flux en mémoire.</span><span class="sxs-lookup"><span data-stu-id="b3b96-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="b3b96-108">dans Offset dans le flux en mémoire à partir duquel commencer la lecture des octets.</span><span class="sxs-lookup"><span data-stu-id="b3b96-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="b3b96-109">à Pointeur vers la mémoire tampon dans laquelle les données seront copiées.</span><span class="sxs-lookup"><span data-stu-id="b3b96-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="b3b96-110">La mémoire tampon doit `countSymbolBytes` avoir un espace disponible.</span><span class="sxs-lookup"><span data-stu-id="b3b96-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="b3b96-111">dans Nombre d’octets à copier.</span><span class="sxs-lookup"><span data-stu-id="b3b96-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="b3b96-112">à Lorsque la méthode est retournée, contient le nombre réel d’octets lus.</span><span class="sxs-lookup"><span data-stu-id="b3b96-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3b96-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b3b96-113">Return Value</span></span>  
 <span data-ttu-id="b3b96-114">`S_OK`, si un nombre d’octets différent de zéro a été lu.</span><span class="sxs-lookup"><span data-stu-id="b3b96-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="b3b96-115">`CORPROF_E_MODULE_IS_DYNAMIC`Si le module a été créé à <xref:System.Reflection.Emit>l’aide de.</span><span class="sxs-lookup"><span data-stu-id="b3b96-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3b96-116">Notes</span><span class="sxs-lookup"><span data-stu-id="b3b96-116">Remarks</span></span>  
 <span data-ttu-id="b3b96-117">La `ReadInMemorySymbols` méthode tente de lire `countSymbolBytes` des données en commençant à `symbolsReadOffset` l’offset dans le flux en mémoire.</span><span class="sxs-lookup"><span data-stu-id="b3b96-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="b3b96-118">Les données sont copiées `pSymbolBytes`vers, ce qui est supposé `countSymbolBytes` avoir un espace disponible.</span><span class="sxs-lookup"><span data-stu-id="b3b96-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="b3b96-119">`pCountSymbolsBytesRead`contient le nombre réel d’octets lus, qui peut être inférieur à `countSymbolBytes` si la fin du flux est atteinte.</span><span class="sxs-lookup"><span data-stu-id="b3b96-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3b96-120">L’implémentation actuelle ne prend pas en charge la réflexion. Emit.</span><span class="sxs-lookup"><span data-stu-id="b3b96-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="b3b96-121">Si le module a été créé à l’aide de Reflection. Emit `CORPROF_E_MODULE_IS_DYNAMIC`, la méthode retourne.</span><span class="sxs-lookup"><span data-stu-id="b3b96-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3b96-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b3b96-122">Requirements</span></span>  
 <span data-ttu-id="b3b96-123">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3b96-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3b96-124">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b3b96-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3b96-125">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3b96-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3b96-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3b96-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b96-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3b96-127">See also</span></span>

- [<span data-ttu-id="b3b96-128">ICorProfilerInfo7, interface</span><span class="sxs-lookup"><span data-stu-id="b3b96-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
