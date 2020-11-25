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
ms.openlocfilehash: 863fa1bf50830bb46e5c2939c99fe1e15897ac3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724128"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="114fe-102">ICorProfilerInfo::GetModuleInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="114fe-102">ICorProfilerInfo::GetModuleInfo Method</span></span>

<span data-ttu-id="114fe-103">Pour un ID de module donné, retourne le nom de fichier du module et l'ID de l'assembly parent du module.</span><span class="sxs-lookup"><span data-stu-id="114fe-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="114fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="114fe-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="114fe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="114fe-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="114fe-106">[in] ID du module pour lequel les informations sont récupérées.</span><span class="sxs-lookup"><span data-stu-id="114fe-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="114fe-107">[out] Adresse de base à laquelle le module est chargé.</span><span class="sxs-lookup"><span data-stu-id="114fe-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="114fe-108">[in] Longueur, en caractères, de la mémoire tampon de retour `szName`.</span><span class="sxs-lookup"><span data-stu-id="114fe-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="114fe-109">[out] Pointeur vers la longueur de caractère totale du nom de fichier du module qui est retourné.</span><span class="sxs-lookup"><span data-stu-id="114fe-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="114fe-110">[out] Mémoire tampon de caractères larges fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="114fe-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="114fe-111">Suite au retour de la méthode, cette mémoire tampon contient le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="114fe-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="114fe-112">[out] Pointeur vers l'ID de l'assembly parent du module.</span><span class="sxs-lookup"><span data-stu-id="114fe-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="114fe-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="114fe-113">Remarks</span></span>  

 <span data-ttu-id="114fe-114">Pour les modules dynamiques, le paramètre `szName` est une chaîne vide et l'adresse de base est 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="114fe-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="114fe-115">Bien que la `GetModuleInfo` méthode puisse être appelée dès que l’ID du module existe, l’ID de l’assembly parent n’est pas disponible tant que le profileur n’a pas reçu le rappel [ICorProfilerCallback :: ModuleAttachedToAssembly,](icorprofilercallback-moduleattachedtoassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="114fe-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="114fe-116">Suite au retour de `GetModuleInfo`, vous devez vérifier que la mémoire tampon `szName` est suffisamment grande pour contenir le nom de fichier complet du module.</span><span class="sxs-lookup"><span data-stu-id="114fe-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="114fe-117">Pour ce faire, comparez la valeur vers laquelle `pcchName` pointe à celle du paramètre `cchName`.</span><span class="sxs-lookup"><span data-stu-id="114fe-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="114fe-118">Si `pcchName` pointe vers une valeur supérieure à `cchName`, allouez une mémoire tampon `szName` plus grande, mettez à jour `cchName` pour refléter la nouvelle taille et rappelez `GetModuleInfo`.</span><span class="sxs-lookup"><span data-stu-id="114fe-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="114fe-119">Vous pouvez également commencer par appeler `GetModuleInfo` avec un tampon `szName` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="114fe-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="114fe-120">Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcchName` et rappeler `GetModuleInfo`.</span><span class="sxs-lookup"><span data-stu-id="114fe-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="114fe-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="114fe-121">Requirements</span></span>  

 <span data-ttu-id="114fe-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="114fe-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="114fe-123">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="114fe-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="114fe-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="114fe-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="114fe-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="114fe-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="114fe-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="114fe-126">See also</span></span>

- [<span data-ttu-id="114fe-127">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="114fe-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="114fe-128">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="114fe-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="114fe-129">Profilage</span><span class="sxs-lookup"><span data-stu-id="114fe-129">Profiling</span></span>](index.md)
- [<span data-ttu-id="114fe-130">GetModuleInfo2, méthode</span><span class="sxs-lookup"><span data-stu-id="114fe-130">GetModuleInfo2 Method</span></span>](icorprofilerinfo3-getmoduleinfo2-method.md)
