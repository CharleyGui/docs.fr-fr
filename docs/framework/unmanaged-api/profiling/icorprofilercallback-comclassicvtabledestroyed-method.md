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
ms.openlocfilehash: aa02b4def015d5badfd0003e08bea5289fe58e17
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700182"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="b4f4e-102">ICorProfilerCallback::COMClassicVTableDestroyed, méthode</span><span class="sxs-lookup"><span data-stu-id="b4f4e-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>

<span data-ttu-id="b4f4e-103">Notifie le profileur qu’un COM Interop vtable est en cours de destruction.</span><span class="sxs-lookup"><span data-stu-id="b4f4e-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4f4e-104">Ce rappel ne se produit probablement jamais, car la destruction des vtables se ferme très près de l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="b4f4e-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4f4e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4f4e-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4f4e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b4f4e-106">Parameters</span></span>

- `wrappedClassId`

  <span data-ttu-id="b4f4e-107">\[in] ID de la classe pour laquelle ce vtable a été créé.</span><span class="sxs-lookup"><span data-stu-id="b4f4e-107">\[in] The ID of the class for which this vtable was created.</span></span>

- `implementedIID`

  <span data-ttu-id="b4f4e-108">\[in] ID de l’interface implémentée par la classe.</span><span class="sxs-lookup"><span data-stu-id="b4f4e-108">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="b4f4e-109">Cette valeur peut être NULL si l’interface est interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="b4f4e-109">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="b4f4e-110">\[in] pointeur vers le début de la vtable.</span><span class="sxs-lookup"><span data-stu-id="b4f4e-110">\[in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4f4e-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="b4f4e-111">Remarks</span></span>  

 <span data-ttu-id="b4f4e-112">Le profileur ne doit pas se bloquer dans son implémentation de cette méthode, car la pile n’est peut-être pas dans un État qui autorise garbage collection, et par conséquent, Preemptive garbage collection ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="b4f4e-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b4f4e-113">Si le profileur est bloqué ici et que garbage collection est tentée, le runtime se bloque jusqu’à ce que ce rappel soit retourné.</span><span class="sxs-lookup"><span data-stu-id="b4f4e-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b4f4e-114">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’elle provoque une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="b4f4e-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4f4e-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b4f4e-115">Requirements</span></span>  

 <span data-ttu-id="b4f4e-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4f4e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4f4e-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4f4e-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4f4e-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4f4e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4f4e-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4f4e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f4e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4f4e-120">See also</span></span>

- [<span data-ttu-id="b4f4e-121">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="b4f4e-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b4f4e-122">COMClassicVTableCreated, méthode</span><span class="sxs-lookup"><span data-stu-id="b4f4e-122">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
