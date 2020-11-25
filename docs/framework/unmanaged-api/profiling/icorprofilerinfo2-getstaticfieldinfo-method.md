---
title: ICorProfilerInfo2::GetStaticFieldInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: ff84bdfb8bbd5331fb94eed766f09137adf9e62c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703835"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="f86f8-102">ICorProfilerInfo2::GetStaticFieldInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="f86f8-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>

<span data-ttu-id="f86f8-103">Obtient une valeur qui indique le type de statique qui s’applique au champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="f86f8-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f86f8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f86f8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f86f8-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="f86f8-106">dans ID de la classe dans laquelle le champ statique est défini.</span><span class="sxs-lookup"><span data-stu-id="f86f8-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="f86f8-107">dans Jeton de métadonnées pour le champ statique.</span><span class="sxs-lookup"><span data-stu-id="f86f8-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="f86f8-108">à Pointeur vers une valeur de l’énumération [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) qui indique si le champ spécifié est statique et, le cas échéant, le type de statique qui s’applique au champ.</span><span class="sxs-lookup"><span data-stu-id="f86f8-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f86f8-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="f86f8-109">Remarks</span></span>  

 <span data-ttu-id="f86f8-110">Ces informations peuvent être utilisées pour déterminer la fonction à appeler pour obtenir l’adresse du champ statique.</span><span class="sxs-lookup"><span data-stu-id="f86f8-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="f86f8-111">Le code du profileur doit toujours vérifier les métadonnées d’un champ statique pour s’assurer qu’il possède effectivement une adresse.</span><span class="sxs-lookup"><span data-stu-id="f86f8-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="f86f8-112">Les littéraux statiques (c’est-à-dire les constantes) existent uniquement dans les métadonnées et n’ont pas d’adresse.</span><span class="sxs-lookup"><span data-stu-id="f86f8-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f86f8-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f86f8-113">Requirements</span></span>  

 <span data-ttu-id="f86f8-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f86f8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f86f8-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f86f8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f86f8-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f86f8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f86f8-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f86f8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f86f8-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f86f8-118">See also</span></span>

- [<span data-ttu-id="f86f8-119">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="f86f8-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f86f8-120">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="f86f8-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
