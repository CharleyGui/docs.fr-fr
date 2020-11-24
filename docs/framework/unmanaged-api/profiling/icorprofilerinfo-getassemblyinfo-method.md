---
title: ICorProfilerInfo::GetAssemblyInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
ms.openlocfilehash: ff81da15b17ab0a7fbe62b08e358f65eed3edb71
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680267"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="c4d01-102">ICorProfilerInfo::GetAssemblyInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="c4d01-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>

<span data-ttu-id="c4d01-103">Accepte un ID d'assembly et retourne le nom de l'assembly et l'ID de son module de manifeste.</span><span class="sxs-lookup"><span data-stu-id="c4d01-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4d01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4d01-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4d01-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c4d01-105">Parameters</span></span>  

 `assemblyId`  
 <span data-ttu-id="c4d01-106">[in] Identificateur de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="c4d01-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c4d01-107">[in] Longueur, en caractères, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="c4d01-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c4d01-108">[out] Pointeur vers la longueur totale en caractères du nom de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="c4d01-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="c4d01-109">[out] Mémoire tampon de caractères larges fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="c4d01-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="c4d01-110">Suite au retour de la méthode, celle-ci contient le nom de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="c4d01-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="c4d01-111">[out] Pointeur vers l'ID du domaine d'application qui contient l'assembly.</span><span class="sxs-lookup"><span data-stu-id="c4d01-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="c4d01-112">[out] Pointeur vers l'ID du module du manifeste de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="c4d01-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4d01-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="c4d01-113">Remarks</span></span>  

 <span data-ttu-id="c4d01-114">Suite au retour de cette méthode, vous devez vérifier que la mémoire tampon `szName` est suffisamment grande pour contenir le nom complet de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="c4d01-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="c4d01-115">Pour ce faire, comparez la valeur vers laquelle `pcchName` pointe à celle du paramètre `cchName`.</span><span class="sxs-lookup"><span data-stu-id="c4d01-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="c4d01-116">Si `pcchName` pointe vers une valeur supérieure à `cchName`, allouez une mémoire tampon `szName` plus grande, mettez à jour `cchName` pour refléter la nouvelle taille et rappelez `GetAssemblyInfo`.</span><span class="sxs-lookup"><span data-stu-id="c4d01-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="c4d01-117">Vous pouvez également commencer par appeler `GetAssemblyInfo` avec un tampon `szName` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="c4d01-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="c4d01-118">Vous pouvez ensuite ajuster la taille de la mémoire tampon en fonction de la valeur retournée dans `pcchName` et rappeler `GetAssemblyInfo`.</span><span class="sxs-lookup"><span data-stu-id="c4d01-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4d01-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c4d01-119">Requirements</span></span>  

 <span data-ttu-id="c4d01-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4d01-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4d01-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c4d01-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4d01-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4d01-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4d01-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4d01-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d01-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4d01-124">See also</span></span>

- [<span data-ttu-id="c4d01-125">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="c4d01-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="c4d01-126">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="c4d01-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c4d01-127">Profilage</span><span class="sxs-lookup"><span data-stu-id="c4d01-127">Profiling</span></span>](index.md)
