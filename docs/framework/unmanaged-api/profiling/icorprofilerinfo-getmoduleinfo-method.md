---
title: ICorProfilerInfo::GetModuleInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: aae6d33166a7685e07c4d82f654f803600e37eec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438893"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="faeb7-102">ICorProfilerInfo::GetModuleInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="faeb7-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="faeb7-103">Pour un ID de module donné, retourne le nom de fichier du module et l'ID de l'assembly parent du module.</span><span class="sxs-lookup"><span data-stu-id="faeb7-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faeb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faeb7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faeb7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="faeb7-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="faeb7-106">[in] ID du module pour lequel les informations sont récupérées.</span><span class="sxs-lookup"><span data-stu-id="faeb7-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="faeb7-107">[out] Adresse de base à laquelle le module est chargé.</span><span class="sxs-lookup"><span data-stu-id="faeb7-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="faeb7-108">[in] Longueur, en caractères, de la mémoire tampon de retour `szName`.</span><span class="sxs-lookup"><span data-stu-id="faeb7-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="faeb7-109">[out] Pointeur vers la longueur de caractère totale du nom de fichier du module qui est retourné.</span><span class="sxs-lookup"><span data-stu-id="faeb7-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="faeb7-110">[out] Mémoire tampon de caractères larges fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="faeb7-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="faeb7-111">Suite au retour de la méthode, cette mémoire tampon contient le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="faeb7-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="faeb7-112">[out] Pointeur vers l'ID de l'assembly parent du module.</span><span class="sxs-lookup"><span data-stu-id="faeb7-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faeb7-113">Notes</span><span class="sxs-lookup"><span data-stu-id="faeb7-113">Remarks</span></span>  
 <span data-ttu-id="faeb7-114">Pour les modules dynamiques, le paramètre `szName` est une chaîne vide et l'adresse de base est 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="faeb7-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="faeb7-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="faeb7-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="faeb7-116">Suite au retour de `GetModuleInfo`, vous devez vérifier que la mémoire tampon `szName` est suffisamment grande pour contenir le nom de fichier complet du module.</span><span class="sxs-lookup"><span data-stu-id="faeb7-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="faeb7-117">Pour ce faire, comparez la valeur vers laquelle `pcchName` pointe à celle du paramètre `cchName`.</span><span class="sxs-lookup"><span data-stu-id="faeb7-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="faeb7-118">Si `pcchName` pointe vers une valeur supérieure à `cchName`, allouez une mémoire tampon `szName` plus grande, mettez à jour `cchName` pour refléter la nouvelle taille et rappelez `GetModuleInfo`.</span><span class="sxs-lookup"><span data-stu-id="faeb7-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="faeb7-119">Vous pouvez également commencer par appeler `GetModuleInfo` avec un tampon `szName` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="faeb7-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="faeb7-120">Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcchName` et rappeler `GetModuleInfo`.</span><span class="sxs-lookup"><span data-stu-id="faeb7-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faeb7-121">spécifications</span><span class="sxs-lookup"><span data-stu-id="faeb7-121">Requirements</span></span>  
 <span data-ttu-id="faeb7-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faeb7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faeb7-123">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="faeb7-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="faeb7-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="faeb7-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="faeb7-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faeb7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faeb7-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="faeb7-126">See also</span></span>

- [<span data-ttu-id="faeb7-127">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="faeb7-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="faeb7-128">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="faeb7-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="faeb7-129">Profilage</span><span class="sxs-lookup"><span data-stu-id="faeb7-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
- [<span data-ttu-id="faeb7-130">GetModuleInfo2, méthode</span><span class="sxs-lookup"><span data-stu-id="faeb7-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
