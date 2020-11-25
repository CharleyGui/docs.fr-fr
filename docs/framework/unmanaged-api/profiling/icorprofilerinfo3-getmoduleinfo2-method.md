---
title: ICorProfilerInfo3::GetModuleInfo2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
ms.openlocfilehash: 2213b674cce27c77156b8de1bbf20d2975e3e55c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721593"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="5387a-102">ICorProfilerInfo3::GetModuleInfo2, méthode</span><span class="sxs-lookup"><span data-stu-id="5387a-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>

<span data-ttu-id="5387a-103">Étant donné un ID de module, retourne le nom de fichier du module, l'ID de l'assembly parent du module et un masque de bits qui décrit les propriétés du module.</span><span class="sxs-lookup"><span data-stu-id="5387a-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5387a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5387a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5387a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5387a-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="5387a-106">[in] ID du module pour lequel les informations sont récupérées.</span><span class="sxs-lookup"><span data-stu-id="5387a-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="5387a-107">[out] Adresse de base à laquelle le module est chargé.</span><span class="sxs-lookup"><span data-stu-id="5387a-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5387a-108">[in] Longueur, en caractères, de la mémoire tampon de retour `szName`.</span><span class="sxs-lookup"><span data-stu-id="5387a-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5387a-109">[out] Pointeur vers la longueur de caractère totale du nom de fichier du module qui est retourné.</span><span class="sxs-lookup"><span data-stu-id="5387a-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="5387a-110">[out] Mémoire tampon de caractères larges fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="5387a-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="5387a-111">Suite au retour de la méthode, cette mémoire tampon contient le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="5387a-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="5387a-112">[out] Pointeur vers l'ID de l'assembly parent du module.</span><span class="sxs-lookup"><span data-stu-id="5387a-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="5387a-113">à Masque de masque des valeurs de l’énumération [COR_PRF_MODULE_FLAGS](cor-prf-module-flags-enumeration.md) qui spécifient les propriétés du module.</span><span class="sxs-lookup"><span data-stu-id="5387a-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5387a-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="5387a-114">Remarks</span></span>  

 <span data-ttu-id="5387a-115">Pour les modules dynamiques, le paramètre `szName` est le nom de métadonnées du module et l'adresse de base est 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="5387a-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="5387a-116">Le nom de métadonnées est la valeur figurant dans la colonne Nom de la table Module dans les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="5387a-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="5387a-117">Cela est également exposé en tant que <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> propriété au code managé, et en tant que `szName` paramètre de la méthode [IMetaDataImport :: GetScopeProps,](../metadata/imetadataimport-getscopeprops-method.md) au code client des métadonnées non managées.</span><span class="sxs-lookup"><span data-stu-id="5387a-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="5387a-118">Bien que la `GetModuleInfo2` méthode puisse être appelée dès que l’ID du module existe, l’ID de l’assembly parent n’est pas disponible tant que le profileur n’a pas reçu le rappel [ICorProfilerCallback :: ModuleAttachedToAssembly,](icorprofilercallback-moduleattachedtoassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5387a-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="5387a-119">Suite au retour de `GetModuleInfo2`, vous devez vérifier que la mémoire tampon `szName` est suffisamment grande pour contenir le nom de fichier complet du module.</span><span class="sxs-lookup"><span data-stu-id="5387a-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="5387a-120">Pour ce faire, comparez la valeur vers laquelle `pcchName` pointe à celle du paramètre `cchName`.</span><span class="sxs-lookup"><span data-stu-id="5387a-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="5387a-121">Si `pcchName` pointe vers une valeur supérieure à `cchName`, allouez une mémoire tampon `szName` plus grande, mettez à jour `cchName` pour refléter la nouvelle taille et rappelez `GetModuleInfo2`.</span><span class="sxs-lookup"><span data-stu-id="5387a-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="5387a-122">Vous pouvez également commencer par appeler `GetModuleInfo2` avec un tampon `szName` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="5387a-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="5387a-123">Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcchName` et rappeler `GetModuleInfo2`.</span><span class="sxs-lookup"><span data-stu-id="5387a-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5387a-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5387a-124">Requirements</span></span>  

 <span data-ttu-id="5387a-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5387a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5387a-126">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5387a-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5387a-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5387a-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5387a-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5387a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5387a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5387a-129">See also</span></span>

- [<span data-ttu-id="5387a-130">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="5387a-130">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="5387a-131">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="5387a-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5387a-132">Profilage</span><span class="sxs-lookup"><span data-stu-id="5387a-132">Profiling</span></span>](index.md)
