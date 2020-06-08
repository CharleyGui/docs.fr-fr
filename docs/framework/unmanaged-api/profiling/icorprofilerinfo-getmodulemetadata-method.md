---
title: ICorProfilerInfo::GetModuleMetaData, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: 62b34128be99ce7750d45e6c19e26bef7fcc98c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502949"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="a507a-102">ICorProfilerInfo::GetModuleMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="a507a-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="a507a-103">Obtient une instance d’interface de métadonnées mappée au module spécifié.</span><span class="sxs-lookup"><span data-stu-id="a507a-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a507a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a507a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a507a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a507a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a507a-106">dans ID du module auquel l’instance d’interface sera mappée.</span><span class="sxs-lookup"><span data-stu-id="a507a-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="a507a-107">dans Valeur de l’énumération [CorOpenFlags](../metadata/coropenflags-enumeration.md) qui spécifie le mode d’ouverture des fichiers manifeste.</span><span class="sxs-lookup"><span data-stu-id="a507a-107">[in] A value of the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="a507a-108">Seuls les `ofRead` `ofWrite` bits et `ofNoTransform` sont valides.</span><span class="sxs-lookup"><span data-stu-id="a507a-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="a507a-109">dans ID de référence (GUID) de l’interface de métadonnées dont l’instance sera récupérée.</span><span class="sxs-lookup"><span data-stu-id="a507a-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="a507a-110">Consultez la page [interfaces de métadonnées](../metadata/metadata-interfaces.md) pour obtenir la liste des interfaces.</span><span class="sxs-lookup"><span data-stu-id="a507a-110">See [Metadata Interfaces](../metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="a507a-111">à Pointeur vers l’adresse de l’instance de l’interface de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a507a-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a507a-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="a507a-112">Remarks</span></span>  
 <span data-ttu-id="a507a-113">Vous pouvez demander que les métadonnées soient ouvertes en mode lecture/écriture, mais cela entraîne une exécution plus lente des métadonnées du programme, car les modifications apportées aux métadonnées ne peuvent pas être optimisées comme elles le faisaient du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a507a-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="a507a-114">Certains modules (tels que les modules de ressources) n’ont pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a507a-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="a507a-115">Dans ce cas, `GetModuleMetaData` retourne une valeur HRESULT de S_FALSE et une valeur null dans \* `ppOut` .</span><span class="sxs-lookup"><span data-stu-id="a507a-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a507a-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a507a-116">Requirements</span></span>  
 <span data-ttu-id="a507a-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a507a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a507a-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a507a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a507a-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a507a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a507a-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a507a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a507a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a507a-121">See also</span></span>

- [<span data-ttu-id="a507a-122">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="a507a-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
