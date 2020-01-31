---
title: ICorProfilerInfo::GetAppDomainInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 0407b7057753f7fdee6ea6b1d05144b135b6378a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864087"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="e4d60-102">ICorProfilerInfo::GetAppDomainInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="e4d60-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="e4d60-103">Accepte un ID de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="e4d60-103">Accepts an application domain ID.</span></span> <span data-ttu-id="e4d60-104">Retourne un nom de domaine d'application et l'ID du processus qui le contient.</span><span class="sxs-lookup"><span data-stu-id="e4d60-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4d60-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4d60-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4d60-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="e4d60-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="e4d60-107">[in] ID du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="e4d60-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e4d60-108">[in] Longueur, en caractères, de la mémoire tampon de retour `szName`.</span><span class="sxs-lookup"><span data-stu-id="e4d60-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e4d60-109">[out] Pointeur vers la longueur totale en caractères du nom de domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="e4d60-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="e4d60-110">[out] Mémoire tampon de caractères larges fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="e4d60-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="e4d60-111">Suite au retour de la méthode, `szName` contient le nom de domaine d'application complet ou partiel.</span><span class="sxs-lookup"><span data-stu-id="e4d60-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="e4d60-112">[out] Pointeur vers l'ID du processus qui contient le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="e4d60-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4d60-113">Notes</span><span class="sxs-lookup"><span data-stu-id="e4d60-113">Remarks</span></span>  
 <span data-ttu-id="e4d60-114">Suite au retour de cette méthode, vous devez vérifier que la mémoire tampon `szName` est suffisamment grande pour contenir le nom complet du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="e4d60-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="e4d60-115">Pour ce faire, comparez la valeur vers laquelle `pcchName` pointe à celle du paramètre `cchName`.</span><span class="sxs-lookup"><span data-stu-id="e4d60-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="e4d60-116">Si `pcchName` pointe vers une valeur supérieure à `cchName`, allouez une mémoire tampon `szName` plus grande, mettez à jour `cchName` pour refléter la nouvelle taille et rappelez `GetAppDomainInfo`.</span><span class="sxs-lookup"><span data-stu-id="e4d60-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="e4d60-117">Vous pouvez également commencer par appeler `GetAppDomainInfo` avec un tampon `szName` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="e4d60-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="e4d60-118">Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcchName` et rappeler `GetAppDomainInfo`.</span><span class="sxs-lookup"><span data-stu-id="e4d60-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4d60-119">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e4d60-119">Requirements</span></span>  
 <span data-ttu-id="e4d60-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4d60-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4d60-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e4d60-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4d60-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4d60-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4d60-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4d60-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d60-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4d60-124">See also</span></span>

- [<span data-ttu-id="e4d60-125">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="e4d60-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="e4d60-126">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="e4d60-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e4d60-127">Profilage</span><span class="sxs-lookup"><span data-stu-id="e4d60-127">Profiling</span></span>](index.md)
