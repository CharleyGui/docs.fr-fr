---
title: ICorProfilerObjectEnum::Clone, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
ms.openlocfilehash: 8153dbd27e168e3a5bd8e5aeada955a0382aaf75
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868250"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="8fe62-102">ICorProfilerObjectEnum::Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="8fe62-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="8fe62-103">Obtient un pointeur d’interface vers une copie de cette interface [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8fe62-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fe62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fe62-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fe62-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="8fe62-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="8fe62-106">à Pointeur vers le pointeur d’interface qui pointe à son tour vers la copie de cette `ICorProfilerObjectEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="8fe62-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="8fe62-107">La copie conserve son propre état d’énumération séparément de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="8fe62-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="8fe62-108">Toutefois, la position initiale du curseur de la copie sera la même que la position actuelle du curseur de cet énumérateur.</span><span class="sxs-lookup"><span data-stu-id="8fe62-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fe62-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="8fe62-109">Requirements</span></span>  
 <span data-ttu-id="8fe62-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fe62-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fe62-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8fe62-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8fe62-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fe62-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fe62-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fe62-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe62-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fe62-114">See also</span></span>

- [<span data-ttu-id="8fe62-115">ICorProfilerObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="8fe62-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
