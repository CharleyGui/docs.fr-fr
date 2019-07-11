---
title: ICorProfilerCallback::COMClassicVTableDestroyed, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8043ae8a3d384ab0936ae96e39174a7afc80a636
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776207"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="ab13b-102">ICorProfilerCallback::COMClassicVTableDestroyed, méthode</span><span class="sxs-lookup"><span data-stu-id="ab13b-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="ab13b-103">Notifie le profileur qu’une vtable d’interopérabilité COM est en cours de destruction.</span><span class="sxs-lookup"><span data-stu-id="ab13b-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab13b-104">Ce rappel est susceptible de ne jamais se produire, car la destruction de vtable survient très près de l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="ab13b-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab13b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab13b-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab13b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab13b-106">Parameters</span></span>  
 `wrappedClassId`  
 <span data-ttu-id="ab13b-107">[in] L’ID de la classe pour laquelle cette vtable a été créée.</span><span class="sxs-lookup"><span data-stu-id="ab13b-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="ab13b-108">[in] ID de l’interface implémentée par la classe.</span><span class="sxs-lookup"><span data-stu-id="ab13b-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="ab13b-109">Cette valeur peut être NULL si l’interface est uniquement interne.</span><span class="sxs-lookup"><span data-stu-id="ab13b-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="ab13b-110">[in] Pointeur vers le début de la vtable.</span><span class="sxs-lookup"><span data-stu-id="ab13b-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab13b-111">Notes</span><span class="sxs-lookup"><span data-stu-id="ab13b-111">Remarks</span></span>  
 <span data-ttu-id="ab13b-112">Le profileur ne doit pas bloquer dans son implémentation de cette méthode, car la pile ne peut pas être dans un état qui autorise le garbage collection, et par conséquent, le garbage collection préemptif ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="ab13b-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="ab13b-113">Si le profileur bloque ici et le garbage collection est tenté, le runtime bloque jusqu'à ce que ce rappel renvoie.</span><span class="sxs-lookup"><span data-stu-id="ab13b-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="ab13b-114">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="ab13b-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab13b-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ab13b-115">Requirements</span></span>  
 <span data-ttu-id="ab13b-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab13b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab13b-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ab13b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab13b-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab13b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab13b-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab13b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab13b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab13b-120">See also</span></span>

- [<span data-ttu-id="ab13b-121">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="ab13b-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ab13b-122">COMClassicVTableCreated, méthode</span><span class="sxs-lookup"><span data-stu-id="ab13b-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
