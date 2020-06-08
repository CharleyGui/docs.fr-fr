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
ms.openlocfilehash: cc8ab6f0c8115da4d74280023dc692b66846ed94
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497749"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo, interface
Fournit des méthodes à utiliser par les profileurs de code pour communiquer avec le common language runtime (CLR) afin de contrôler la surveillance des événements et les informations de demande.  
  
> [!NOTE]
> Chaque méthode de l' `ICorProfilerInfo` interface retourne un HRESULT pour indiquer la réussite ou l’échec. Pour obtenir la liste des codes de retour possibles, consultez CorError. h.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BeginInprocDebugging, méthode](icorprofilerinfo-begininprocdebugging-method.md)|Initialise la prise en charge du débogage en cours de processus. Cette méthode est obsolète dans la version 2,0 de .NET Framework.|  
|[EndInprocDebugging, méthode](icorprofilerinfo-endinprocdebugging-method.md)|Arrête une session de débogage en cours de processus. Cette méthode est obsolète dans la version 2,0 de .NET Framework.|  
|[ForceGC, méthode](icorprofilerinfo-forcegc-method.md)|Force garbage collection se produire dans le Runtime.|  
|[GetAppDomainInfo, méthode](icorprofilerinfo-getappdomaininfo-method.md)|Obtient des informations sur le domaine d’application spécifié.|  
|[GetAssemblyInfo, méthode](icorprofilerinfo-getassemblyinfo-method.md)|Obtient des informations sur l’assembly spécifié.|  
|[GetClassFromObject, méthode](icorprofilerinfo-getclassfromobject-method.md)|Obtient le `ClassID` d’un<br /><br /> objet, en fonction de son `ObjectID` .|  
|[GetClassFromToken, méthode](icorprofilerinfo-getclassfromtoken-method.md)|Obtient l’ID de la classe, en fonction du jeton de métadonnées. Cette méthode est obsolète dans la version 2,0 de .NET Framework. Utilisez la méthode [ICorProfilerInfo2 :: GetClassFromTokenAndTypeArgs,](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) à la place.|  
|[GetClassIDInfo, méthode](icorprofilerinfo-getclassidinfo-method.md)|Obtient le module parent et le jeton de métadonnées pour la classe spécifiée.|  
|[GetCodeInfo, méthode](icorprofilerinfo-getcodeinfo-method.md)|Obtient l'étendue de code natif associée à l'ID de la fonction spécifiée. Cette méthode est obsolète. Utilisez la méthode [ICorProfilerInfo2 :: GetCodeInfo2,](icorprofilerinfo2-getcodeinfo2-method.md) à la place.|  
|[GetCurrentThreadID, méthode](icorprofilerinfo-getcurrentthreadid-method.md)|Obtient l’ID du thread actuel, s’il s’agit d’un thread managé.|  
|[GetEventMask, méthode](icorprofilerinfo-geteventmask-method.md)|Obtient les catégories d’événements actuelles pour lesquelles le profileur veut recevoir des notifications d’événements du CLR.|  
|[GetFunctionFromIP, méthode](icorprofilerinfo-getfunctionfromip-method.md)|Mappe un pointeur d’instruction de code managé à un `FunctionID` .|  
|[GetFunctionFromToken, méthode](icorprofilerinfo-getfunctionfromtoken-method.md)|Obtient l’ID d’une fonction. Cette méthode est obsolète dans la version 2,0 de .NET Framework. Utilisez la méthode [ICorProfilerInfo2 :: GetFunctionFromTokenAndTypeArgs,](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) à la place.|  
|[GetFunctionInfo, méthode](icorprofilerinfo-getfunctioninfo-method.md)|Obtient la classe parente et le jeton de métadonnées pour la fonction spécifiée.|  
|[GetHandleFromThread, méthode](icorprofilerinfo-gethandlefromthread-method.md)|Mappe l’ID d’un thread à un handle de thread Win32.|  
|[GetILFunctionBody, méthode](icorprofilerinfo-getilfunctionbody-method.md)|Obtient un pointeur vers le corps d’une méthode dans le code MSIL (Microsoft Intermediate Language), en commençant à son en-tête.|  
|[GetILFunctionBodyAllocator, méthode](icorprofilerinfo-getilfunctionbodyallocator-method.md)|Obtient une interface qui fournit une méthode pour allouer de la mémoire à utiliser pour échanger le corps d’une méthode dans le code MSIL.|  
|[GetILToNativeMapping, méthode](icorprofilerinfo-getiltonativemapping-method.md)|Obtient un mappage des offsets MSIL aux offsets natifs pour le code contenu dans la fonction spécifiée.|  
|[GetInprocInspectionInterface, méthode](icorprofilerinfo-getinprocinspectioninterface-method.md)|Obtient un objet qui peut être interrogé pour une interface ICorDebugProcess. Cette méthode est obsolète dans la version 2,0 de .NET Framework.|  
|[GetInprocInspectionIThisThread, méthode](icorprofilerinfo-getinprocinspectionithisthread-method.md)|Obtient un objet qui peut être interrogé pour l’interface ICorDebugThread. Cette méthode est obsolète dans la version 2,0 de .NET Framework.|  
|[GetModuleInfo, méthode](icorprofilerinfo-getmoduleinfo-method.md)|Pour un ID de module donné, retourne le nom de fichier du module et l'ID de l'assembly parent du module.|  
|[GetModuleMetaData, méthode](icorprofilerinfo-getmodulemetadata-method.md)|Obtient une instance d’interface de métadonnées mappée au module spécifié.|  
|[GetObjectSize, méthode](icorprofilerinfo-getobjectsize-method.md)|Obtient la taille d’un objet spécifié.|  
|[GetThreadContext, méthode](icorprofilerinfo-getthreadcontext-method.md)|Obtient l’identité de contexte actuellement associée au thread spécifié.|  
|[GetThreadInfo, méthode](icorprofilerinfo-getthreadinfo-method.md)|Obtient l’identité de thread Win32 actuelle pour le thread spécifié.|  
|[GetTokenAndMetadataFromFunction, méthode](icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Obtient le jeton de métadonnées et une instance de l’interface de métadonnées qui peuvent être utilisées par rapport au jeton pour la fonction spécifiée.|  
|[IsArrayClass, méthode](icorprofilerinfo-isarrayclass-method.md)|Détermine si la classe spécifiée est une classe de tableau.|  
|[SetEnterLeaveFunctionHooks, méthode](icorprofilerinfo-setenterleavefunctionhooks-method.md)|Spécifie les fonctions implémentées par le profileur à appeler sur les raccordements « Enter », « Leave » et « tailcall » des fonctions managées.|  
|[SetEventMask, méthode](icorprofilerinfo-seteventmask-method.md)|Définit une valeur qui spécifie les types d’événements pour lesquels le profileur veut recevoir des notifications du CLR.|  
|[SetFunctionIDMapper, méthode](icorprofilerinfo-setfunctionidmapper-method.md)|Spécifie la fonction implémentée par le profileur qui sera appelée pour mapper des valeurs `FunctionID` sur d'autres valeurs, qui sont passées aux raccordements d'entrée/sortie de fonction du profileur.|  
|[SetFunctionReJIT, méthode](icorprofilerinfo-setfunctionrejit-method.md)|Non implémenté. Ne pas utiliser.|  
|[SetILFunctionBody, méthode](icorprofilerinfo-setilfunctionbody-method.md)|Remplace le corps de la fonction spécifiée dans le module spécifié.|  
|[SetILInstrumentedCodeMap, méthode](icorprofilerinfo-setilinstrumentedcodemap-method.md)|Spécifie comment les décalages du MSIL d’origine d’une fonction spécifiée correspondent aux nouveaux décalages du code MSIL modifié par le profileur de la fonction.|  
  
## <a name="remarks"></a>Remarques  
 Un profileur appelle une méthode dans l' `ICorProfilerInfo` interface pour communiquer avec le CLR afin de contrôler la surveillance des événements et les informations de demande.  
  
 Les méthodes de l' `ICorProfilerInfo` interface sont implémentées par le CLR à l’aide du modèle à thread libre. Chaque méthode retourne un HRESULT pour indiquer la réussite ou l'échec. Pour obtenir la liste des codes de retour possibles, consultez CorError. h.  
  
 Le CLR passe, via l’implémentation de [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md)du profileur, une `ICorProfilerInfo` interface à chaque profileur de code pendant l’initialisation. Un profileur de code peut ensuite appeler les méthodes de l' `ICorProfilerInfo` interface pour obtenir des informations sur le code managé en cours d’exécution sous le contrôle du CLR.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
