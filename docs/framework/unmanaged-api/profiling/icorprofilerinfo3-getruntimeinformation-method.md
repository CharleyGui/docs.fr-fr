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
ms.openlocfilehash: e3d167be9a4091ae57a3283424186142e90ca7a1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868549"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="6a9de-102">ICorProfilerInfo3::GetRuntimeInformation, méthode</span><span class="sxs-lookup"><span data-stu-id="6a9de-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="6a9de-103">Fournit des informations de version sur le common language runtime (CLR) en cours de profilage.</span><span class="sxs-lookup"><span data-stu-id="6a9de-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a9de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a9de-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6a9de-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="6a9de-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="6a9de-106">à ID représentatif d’une instance CLR en cours d’exécution dans un processus.</span><span class="sxs-lookup"><span data-stu-id="6a9de-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="6a9de-107">Il s’agit du même que le `ClrInstanceID` que l’événement de démarrage suivi d’événements pour Windows (ETW) signale.</span><span class="sxs-lookup"><span data-stu-id="6a9de-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="6a9de-108">à Type au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6a9de-108">[out] The runtime type.</span></span> <span data-ttu-id="6a9de-109">Ce paramètre retourne `COR_PRF_DESKTOP_CLR` pour la version de bureau du CLR, ou `COR_PRF_CORE_CLR` pour la version principale du CLR utilisée dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="6a9de-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="6a9de-110">à Numéro de version principale du CLR.</span><span class="sxs-lookup"><span data-stu-id="6a9de-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="6a9de-111">à Numéro de version mineure du CLR.</span><span class="sxs-lookup"><span data-stu-id="6a9de-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="6a9de-112">à Numéro de la version de build du CLR.</span><span class="sxs-lookup"><span data-stu-id="6a9de-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="6a9de-113">à Numéro de version du CLR qui est associé à une mise à jour logicielle.</span><span class="sxs-lookup"><span data-stu-id="6a9de-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="6a9de-114">dans Longueur, en caractères, de la mémoire tampon vers laquelle `szVersionString` pointe.</span><span class="sxs-lookup"><span data-stu-id="6a9de-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="6a9de-115">à Longueur, en caractères, de `szVersionString`.</span><span class="sxs-lookup"><span data-stu-id="6a9de-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="6a9de-116">à Chaîne de version CLR.</span><span class="sxs-lookup"><span data-stu-id="6a9de-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a9de-117">Notes</span><span class="sxs-lookup"><span data-stu-id="6a9de-117">Remarks</span></span>  
 <span data-ttu-id="6a9de-118">Vous pouvez passer NULL pour n’importe quel paramètre.</span><span class="sxs-lookup"><span data-stu-id="6a9de-118">You may pass null for any parameter.</span></span> <span data-ttu-id="6a9de-119">Toutefois, `pcchVersionString` ne peut pas avoir la valeur null, sauf si `szVersionString` est également null.</span><span class="sxs-lookup"><span data-stu-id="6a9de-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a9de-120">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="6a9de-120">Requirements</span></span>  
 <span data-ttu-id="6a9de-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a9de-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a9de-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6a9de-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6a9de-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a9de-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a9de-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a9de-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a9de-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a9de-125">See also</span></span>

- [<span data-ttu-id="6a9de-126">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="6a9de-126">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="6a9de-127">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="6a9de-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="6a9de-128">Profilage</span><span class="sxs-lookup"><span data-stu-id="6a9de-128">Profiling</span></span>](index.md)
