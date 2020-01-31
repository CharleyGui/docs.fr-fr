---
title: ICorProfilerInfo::SetILFunctionBody, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: 296c3973403a5b09332efa24961d7a474d814aab
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863346"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="03e22-102">ICorProfilerInfo::SetILFunctionBody, méthode</span><span class="sxs-lookup"><span data-stu-id="03e22-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="03e22-103">Remplace le corps de la fonction spécifiée dans le module spécifié.</span><span class="sxs-lookup"><span data-stu-id="03e22-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03e22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03e22-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03e22-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="03e22-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="03e22-106">dans ID du module dans lequel la fonction réside.</span><span class="sxs-lookup"><span data-stu-id="03e22-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="03e22-107">dans Jeton de la fonction pour laquelle remplacer le corps.</span><span class="sxs-lookup"><span data-stu-id="03e22-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="03e22-108">dans Nouvel en-tête de la fonction.</span><span class="sxs-lookup"><span data-stu-id="03e22-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03e22-109">Notes</span><span class="sxs-lookup"><span data-stu-id="03e22-109">Remarks</span></span>  
 <span data-ttu-id="03e22-110">La méthode `SetILFunctionBody` remplace l’adresse virtuelle relative de la fonction dans les métadonnées afin qu’elle pointe vers le nouveau corps de la fonction, et ajuste toutes les structures de données internes selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="03e22-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="03e22-111">La méthode `SetILFunctionBody` peut être appelée uniquement sur les fonctions qui n’ont jamais été compilées par un compilateur juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="03e22-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="03e22-112">Utilisez la méthode [ICorProfilerInfo :: GetILFunctionBodyAllocator,](icorprofilerinfo-getilfunctionbodyallocator-method.md) pour allouer de l’espace pour la nouvelle méthode afin de garantir la compatibilité de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="03e22-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e22-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="03e22-113">Requirements</span></span>  
 <span data-ttu-id="03e22-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03e22-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03e22-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="03e22-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="03e22-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03e22-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03e22-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03e22-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e22-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03e22-118">See also</span></span>

- [<span data-ttu-id="03e22-119">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="03e22-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
