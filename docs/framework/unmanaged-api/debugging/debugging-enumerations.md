---
title: Énumérations de débogage
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 7948b78da1db5267ce53364af1e4a26ff73801e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124329"
---
# <a name="debugging-enumerations"></a>Énumérations de débogage
Cette section décrit les énumérations non managées utilisées par l'API de débogage.  
  
## <a name="in-this-section"></a>Dans cette section  
 [CLR_DEBUGGING_PROCESS_FLAGS, énumération](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 Fournit des valeurs utilisées par la méthode [ICLRDebugging :: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) .  
  
 [CLRDataEnumMemoryFlags, énumération](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 Indique les régions de mémoire qu’un appel à la méthode [ICLRDataEnumMemoryRegions :: EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) doit inclure.  
  
 [COR_PUB_ENUMPROCESS, énumération](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 Identifie le type de processus à énumérer.  
  
 [CorDebugBlockingReason, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 Spécifie les raisons pour lesquelles un thread peut être bloqué sur un objet donné.  
  
 CorDebugChainReason,  
 Indique la ou les raisons de la mise en route d'une chaîne d'appels.  
  
 [CorDebugCodeInvokeKind, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 Indique de quelle manière une fonction exportée appelle du code managé.  
  
 [CorDebugCodeInvokePurpose, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 Indique pourquoi une fonction exportée appelle du code managé.  
  
 CorDebugCreateProcessFlags,  
 Fournit des options de débogage supplémentaires qui peuvent être utilisées dans un appel à la méthode [ICorDebug :: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) .  
  
 [CorDebugDebugEventKind, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 Indique le type d’événement dont les informations sont décodées par la méthode [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) .  
  
 [CorDebugDecodeEventFlagsWindows, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Fournit des informations supplémentaires sur les événements de débogage propres à la plateforme Windows.  
  
 CorDebugExceptionCallbackType,  
 Indique le type de rappel effectué à partir d’un événement [ICorDebugManagedCallback2 :: exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) .  
  
 [CorDebugExceptionFlags, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 Fournit des informations supplémentaires sur une exception.  
  
 CorDebugExceptionUnwindCallbackType,  
 Indique l'événement qui est signalé par le rappel lors de la phase de déroulement.  
  
 [CorDebugGCType, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 Indique si le récupérateur de mémoire s'exécute sur une station de travail ou sur un serveur.  
  
 [CorDebugGenerationTypes, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 Spécifie la génération d’une région de la mémoire sur le tas managé.  
  
 CorDebugHandleType,  
 Indique le type de handle.  
  
 [CorDebugIlToNativeMappingTypes, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 Indique si une plage particulière d'instructions natives correspond à une région spéciale du code.  
  
 CorDebugIntercept,  
 Indique les types de code qui peuvent l'objet d'une exécution pas à pas.  
  
 [CorDebugInterfaceVersion, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 Spécifie une version de .NET Framework ou la version de .NET Framework où une interface a été introduite.  
  
 CorDebugInternalFrameType,  
 Identifie le type de frame de pile.  
  
 [CorDebugJITCompilerFlags, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 Contient des valeurs qui influencent le comportement du compilateur juste-à-temps managé.  
  
 [CorDebugJITCompilerFlagsDeprecated, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Obsolète. Utilisez à la place le membre `CORDEBUG_JIT_DEFAULT` de l’énumération [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) .  
  
 CorDebugMappingResult,  
 Fournit les détails sur la façon dont la valeur du pointeur d'instruction a été obtenue.  
  
 [CorDebugMDAFlags, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 Spécifie l'état du thread sur lequel l'Assistant Débogage managé est déclenché.  
  
 [CorDebugNGenPolicy, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 Fournit une valeur qui détermine si un débogueur charge les images natives (NGen) depuis le cache d'images natives.  
  
 [CorDebugPlatform, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 Fournit les valeurs de plateforme cible utilisées par la méthode [ICorDebugDataTarget :: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .  
  
 [CorDebugRecordFormat, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 Décrit le format des données dans un tableau d'octets qui contient des informations sur un événement de débogage d'exception native.  
  
 CorDebugRegister  
 Spécifie les registres associés à une architecture de processeur donnée.  
  
 [CorDebugSetContextFlag, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 Indique si le contexte provient du frame (ou feuille) actif ou s'il a été calculé par déroulement à partir d'un autre frame.  
  
 [CorDebugStateChange, énumération](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 Représente la quantité de données mises en cache à ignorer sur la base des modifications apportées au processus.  
  
 CorDebugStepReason,  
 Indique le résultat d'une étape individuelle.  
  
 CorDebugThreadState,  
 Spécifie l'état d'un thread pour le débogage.  
  
 \>CorDebugUnmappedStop,  
 Spécifie le type de code non mappé qui peut déclencher un arrêt dans l'exécution du code par l'exécution pas à pas.  
  
 CorDebugUserState,  
 Indique l'état de l'utilisateur d'un thread.  
  
 [CorGCReferenceType, énumération](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 Identifie la source d'un objet pour lequel l'espace occupé en mémoire peut être récupéré.  
  
 [ILCodeKind, énumération](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 Fournit des valeurs qui spécifient si le débogueur peut accéder aux variables locales ou au code ajoutés dans l'instrumentation ReJIT du profileur.  
  
 [LoggingLevelEnum, énumération](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 Indique le niveau de gravité d'un message de description qui est écrit dans le journal des événements quand un thread managé consigne un événement.  
  
 [LogSwitchCallReason, énumération](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 Indique l'opération qui a été effectuée sur un commutateur de débogage/suivi.  
  
 [VariableLocationType, énumération](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 Indique le type d’emplacement natif d’une variable.  
  
 [WriteableMetadataUpdateMode, énumération](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 Fournit des valeurs qui spécifient si les mises à jour en mémoire apportées aux métadonnées sont visibles par un débogueur. 

 [Énumération ClrDataSourceType](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Fournit des valeurs utilisées par la structure CLRDATA_IL_ADDRESS_MAP.

## <a name="related-sections"></a>Rubriques connexes  
 [Coclasses de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Fonctions statiques globales de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
