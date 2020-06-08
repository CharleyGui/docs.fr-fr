---
title: ICorProfilerInfo3::GetRuntimeInformation, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: b8e503af11fa1d02aac2ec83edde0ffbd562d8e5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496397"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="eb7e2-102">ICorProfilerInfo3::GetRuntimeInformation, méthode</span><span class="sxs-lookup"><span data-stu-id="eb7e2-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="eb7e2-103">Fournit des informations de version sur le common language runtime (CLR) en cours de profilage.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb7e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb7e2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb7e2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eb7e2-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="eb7e2-106">à ID représentatif d’une instance CLR en cours d’exécution dans un processus.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="eb7e2-107">Il s’agit du même que celui `ClrInstanceID` que l’événement de démarrage suivi d’événements pour Windows (ETW) signale.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="eb7e2-108">à Type au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-108">[out] The runtime type.</span></span> <span data-ttu-id="eb7e2-109">Ce paramètre retourne `COR_PRF_DESKTOP_CLR` pour la version de bureau du CLR ou `COR_PRF_CORE_CLR` pour la version principale du CLR utilisé dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="eb7e2-110">à Numéro de version principale du CLR.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="eb7e2-111">à Numéro de version mineure du CLR.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="eb7e2-112">à Numéro de la version de build du CLR.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="eb7e2-113">à Numéro de version du CLR qui est associé à une mise à jour logicielle.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="eb7e2-114">dans Longueur, en caractères, de la mémoire tampon `szVersionString` vers laquelle pointe.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="eb7e2-115">à Longueur, en caractères, de `szVersionString` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="eb7e2-116">à Chaîne de version CLR.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb7e2-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="eb7e2-117">Remarks</span></span>  
 <span data-ttu-id="eb7e2-118">Vous pouvez passer NULL pour n’importe quel paramètre.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-118">You may pass null for any parameter.</span></span> <span data-ttu-id="eb7e2-119">Toutefois, `pcchVersionString` ne peut pas avoir la valeur null, sauf si `szVersionString` a également la valeur null.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb7e2-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eb7e2-120">Requirements</span></span>  
 <span data-ttu-id="eb7e2-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb7e2-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb7e2-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb7e2-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb7e2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb7e2-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb7e2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb7e2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb7e2-125">See also</span></span>

- [<span data-ttu-id="eb7e2-126">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="eb7e2-126">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="eb7e2-127">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="eb7e2-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="eb7e2-128">Profilage</span><span class="sxs-lookup"><span data-stu-id="eb7e2-128">Profiling</span></span>](index.md)
