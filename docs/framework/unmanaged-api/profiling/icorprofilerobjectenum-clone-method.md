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
ms.openlocfilehash: 99778240afb7e296b93cd87ab91feeca20d02637
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428278"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="5c433-102">ICorProfilerObjectEnum::Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="5c433-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="5c433-103">Obtient un pointeur d’interface vers une copie de cette interface [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5c433-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c433-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c433-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c433-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5c433-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="5c433-106">à Pointeur vers le pointeur d’interface qui pointe à son tour vers la copie de cette `ICorProfilerObjectEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="5c433-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="5c433-107">La copie conserve son propre état d’énumération séparément de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="5c433-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="5c433-108">Toutefois, la position initiale du curseur de la copie sera la même que la position actuelle du curseur de cet énumérateur.</span><span class="sxs-lookup"><span data-stu-id="5c433-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c433-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5c433-109">Requirements</span></span>  
 <span data-ttu-id="5c433-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c433-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c433-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5c433-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5c433-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c433-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c433-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c433-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c433-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c433-114">See also</span></span>

- [<span data-ttu-id="5c433-115">ICorProfilerObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="5c433-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
