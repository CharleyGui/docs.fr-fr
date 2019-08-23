---
title: ICorProfilerInfo, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo
helpviewer_keywords:
- ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: eb4e4ce0-06e7-4469-bbc4-edc2eb5da4b1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b82d9ac610cb393696ef94fb797a48b737b0231
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965745"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo, interface
Fournit des méthodes à utiliser par les profileurs de code pour communiquer avec le common language runtime (CLR) afin de contrôler la surveillance des événements et les informations de demande.  
  
> [!NOTE]
> Chaque méthode de l' `ICorProfilerInfo` interface retourne un HRESULT pour indiquer la réussite ou l’échec. Pour obtenir la liste des codes de retour possibles, consultez CorError. h.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BeginInprocDebugging, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|Initialise la prise en charge du débogage en cours de processus. Cette méthode est obsolète dans la version 2,0 de .NET Framework.|  
|[EndInprocDebugging, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|Arrête une session de débogage en cours de processus. Cette méthode est obsolète dans la version 2,0 de .NET Framework.|  
|[ForceGC, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|Force garbage collection se produire dans le Runtime.|  
|[GetAppDomainInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|Obtient des informations sur le domaine d’application spécifié.|  
|[GetAssemblyInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|Obtient des informations sur l’assembly spécifié.|  
|[GetClassFromObject, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|Obtient le `ClassID` d’un<br /><br /> objet, en fonction `ObjectID`de son.|  
|[GetClassFromToken, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|Obtient l’ID de la classe, en fonction du jeton de métadonnées. Cette méthode est obsolète dans la version 2,0 de .NET Framework. Utilisez la méthode [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) à la place.|  
|[GetClassIDInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|Obtient le module parent et le jeton de métadonnées pour la classe spécifiée.|  
|[GetCodeInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|Obtient l'étendue de code natif associée à l'ID de la fonction spécifiée. Cette méthode est obsolète. Utilisez la méthode [ICorProfilerInfo2:: GetCodeInfo2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) à la place.|  
|[GetCurrentThreadID, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|Obtient l’ID du thread actuel, s’il s’agit d’un thread managé.|  
|[GetEventMask, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|Obtient les catégories d’événements actuelles pour lesquelles le profileur veut recevoir des notifications d’événements du CLR.|  
|[GetFunctionFromIP, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|Mappe un pointeur d’instruction de code managé `FunctionID`à un.|  
|[GetFunctionFromToken, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|Obtient l’ID d’une fonction. Cette méthode est obsolète dans la version 2,0 de .NET Framework. Utilisez la méthode [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) à la place.|  
|[GetFunctionInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|Obtient la classe parente et le jeton de métadonnées pour la fonction spécifiée.|  
|[GetHandleFromThread, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Mappe l’ID d’un thread à un handle de thread Win32.|  
|[GetILFunctionBody, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|Obtient un pointeur vers le corps d’une méthode dans le code MSIL (Microsoft Intermediate Language), en commençant à son en-tête.|  
|[GetILFunctionBodyAllocator, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|Obtient une interface qui fournit une méthode pour allouer de la mémoire à utiliser pour échanger le corps d’une méthode dans le code MSIL.|  
|[GetILToNativeMapping, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|Obtient un mappage des offsets MSIL aux offsets natifs pour le code contenu dans la fonction spécifiée.|  
|[GetInprocInspectionInterface, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|Obtient un objet qui peut être interrogé pour une interface ICorDebugProcess. Cette méthode est obsolète dans la version 2,0 de .NET Framework.|  
|[GetInprocInspectionIThisThread, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|Obtient un objet qui peut être interrogé pour l’interface ICorDebugThread. Cette méthode est obsolète dans la version 2,0 de .NET Framework.|  
|[GetModuleInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|Pour un ID de module donné, retourne le nom de fichier du module et l'ID de l'assembly parent du module.|  
|[GetModuleMetaData, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|Obtient une instance d’interface de métadonnées mappée au module spécifié.|  
|[GetObjectSize, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|Obtient la taille d’un objet spécifié.|  
|[GetThreadContext, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|Obtient l’identité de contexte actuellement associée au thread spécifié.|  
|[GetThreadInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|Obtient l’identité de thread Win32 actuelle pour le thread spécifié.|  
|[GetTokenAndMetadataFromFunction, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Obtient le jeton de métadonnées et une instance de l’interface de métadonnées qui peuvent être utilisées par rapport au jeton pour la fonction spécifiée.|  
|[IsArrayClass, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|Détermine si la classe spécifiée est une classe de tableau.|  
|[SetEnterLeaveFunctionHooks, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|Spécifie les fonctions implémentées par le profileur à appeler sur les raccordements «Enter», «Leave» et «tailcall» des fonctions managées.|  
|[SetEventMask, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|Définit une valeur qui spécifie les types d’événements pour lesquels le profileur veut recevoir des notifications du CLR.|  
|[SetFunctionIDMapper, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|Spécifie la fonction implémentée par le profileur qui sera appelée pour mapper des valeurs `FunctionID` sur d'autres valeurs, qui sont passées aux raccordements d'entrée/sortie de fonction du profileur.|  
|[SetFunctionReJIT, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|Non implémenté. Ne pas utiliser.|  
|[SetILFunctionBody, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|Remplace le corps de la fonction spécifiée dans le module spécifié.|  
|[SetILInstrumentedCodeMap, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|Spécifie comment les décalages du MSIL d’origine d’une fonction spécifiée correspondent aux nouveaux décalages du code MSIL modifié par le profileur de la fonction.|  
  
## <a name="remarks"></a>Notes  
 Un profileur appelle une méthode dans `ICorProfilerInfo` l’interface pour communiquer avec le CLR afin de contrôler la surveillance des événements et les informations de demande.  
  
 Les méthodes de l' `ICorProfilerInfo` interface sont implémentées par le CLR à l’aide du modèle à thread libre. Chaque méthode retourne un HRESULT pour indiquer la réussite ou l'échec. Pour obtenir la liste des codes de retour possibles, consultez CorError. h.  
  
 Le CLR passe, via l’implémentation de [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)du profileur, une `ICorProfilerInfo` interface à chaque profileur de code pendant l’initialisation. Un profileur de code peut ensuite appeler les `ICorProfilerInfo` méthodes de l’interface pour obtenir des informations sur le code managé en cours d’exécution sous le contrôle du CLR.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl, CorProf. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
