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
ms.openlocfilehash: 5e5510ec098b2c1aa3b768830b812328287fd31a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503027"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="cff32-102">ICorProfilerInfo::GetAppDomainInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="cff32-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="cff32-103">Accepte un ID de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="cff32-103">Accepts an application domain ID.</span></span> <span data-ttu-id="cff32-104">Retourne un nom de domaine d'application et l'ID du processus qui le contient.</span><span class="sxs-lookup"><span data-stu-id="cff32-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff32-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cff32-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cff32-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cff32-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="cff32-107">[in] ID du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="cff32-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="cff32-108">[in] Longueur, en caractères, de la mémoire tampon de retour `szName`.</span><span class="sxs-lookup"><span data-stu-id="cff32-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cff32-109">[out] Pointeur vers la longueur totale en caractères du nom de domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="cff32-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="cff32-110">[out] Mémoire tampon de caractères larges fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="cff32-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="cff32-111">Suite au retour de la méthode, `szName` contient le nom de domaine d'application complet ou partiel.</span><span class="sxs-lookup"><span data-stu-id="cff32-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="cff32-112">[out] Pointeur vers l'ID du processus qui contient le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="cff32-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cff32-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="cff32-113">Remarks</span></span>  
 <span data-ttu-id="cff32-114">Suite au retour de cette méthode, vous devez vérifier que la mémoire tampon `szName` est suffisamment grande pour contenir le nom complet du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="cff32-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="cff32-115">Pour ce faire, comparez la valeur vers laquelle `pcchName` pointe à celle du paramètre `cchName`.</span><span class="sxs-lookup"><span data-stu-id="cff32-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="cff32-116">Si `pcchName` pointe vers une valeur supérieure à `cchName`, allouez une mémoire tampon `szName` plus grande, mettez à jour `cchName` pour refléter la nouvelle taille et rappelez `GetAppDomainInfo`.</span><span class="sxs-lookup"><span data-stu-id="cff32-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="cff32-117">Vous pouvez également commencer par appeler `GetAppDomainInfo` avec un tampon `szName` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="cff32-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="cff32-118">Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcchName` et rappeler `GetAppDomainInfo`.</span><span class="sxs-lookup"><span data-stu-id="cff32-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cff32-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cff32-119">Requirements</span></span>  
 <span data-ttu-id="cff32-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cff32-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cff32-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cff32-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cff32-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cff32-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cff32-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cff32-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff32-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cff32-124">See also</span></span>

- [<span data-ttu-id="cff32-125">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="cff32-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="cff32-126">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="cff32-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cff32-127">Profilage</span><span class="sxs-lookup"><span data-stu-id="cff32-127">Profiling</span></span>](index.md)
