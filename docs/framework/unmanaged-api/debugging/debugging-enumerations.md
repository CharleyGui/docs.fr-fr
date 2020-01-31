---
title: Énumérations de débogage
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: a83b1aa0b2cc068ed2f73dca04083b1085d45201
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789159"
---
# <a name="debugging-enumerations"></a>Énumérations de débogage
Cette section décrit les énumérations non managées utilisées par l'API de débogage.  
  
## <a name="in-this-section"></a>Dans cette section  
 [CLR_DEBUGGING_PROCESS_FLAGS, énumération](clr-debugging-process-flags-enumeration.md)  
 Fournit des valeurs utilisées par la méthode [ICLRDebugging :: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .  
  
 [CLRDataEnumMemoryFlags, énumération](clrdataenummemoryflags-enumeration.md)  
 Indique les régions de mémoire qu’un appel à la méthode [ICLRDataEnumMemoryRegions :: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) doit inclure.  
  
 [COR_PUB_ENUMPROCESS, énumération](cor-pub-enumprocess-enumeration.md)  
 Identifie le type de processus à énumérer.  
  
 [CorDebugBlockingReason, énumération](cordebugblockingreason-enumeration.md)  
 Spécifie les raisons pour lesquelles un thread peut être bloqué sur un objet donné.  
  
 CorDebugChainReason  
 Indique la ou les raisons de la mise en route d'une chaîne d'appels.  
  
 [CorDebugCodeInvokeKind, énumération](cordebugcodeinvokekind-enumeration.md)  
 Indique de quelle manière une fonction exportée appelle du code managé.  
  
 [CorDebugCodeInvokePurpose, énumération](cordebugcodeinvokepurpose-enumeration.md)  
 Indique pourquoi une fonction exportée appelle du code managé.  
  
 CorDebugCreateProcessFlags  
 Fournit des options de débogage supplémentaires qui peuvent être utilisées dans un appel à la méthode [ICorDebug :: CreateProcess](icordebug-createprocess-method.md) .  
  
 [CorDebugDebugEventKind, énumération](cordebugdebugeventkind-enumeration.md)  
 Indique le type d’événement dont les informations sont décodées par la méthode [DecodeEvent](icordebugprocess6-decodeevent-method.md) .  
  
 [CorDebugDecodeEventFlagsWindows, énumération](cordebugdecodeeventflagswindows-enumeration.md)  
 Fournit des informations supplémentaires sur les événements de débogage propres à la plateforme Windows.  
  
 CorDebugExceptionCallbackType  
 Indique le type de rappel effectué à partir d’un événement [ICorDebugManagedCallback2 :: exception](icordebugmanagedcallback2-exception-method.md) .  
  
 [CorDebugExceptionFlags, énumération](cordebugexceptionflags-enumeration.md)  
 Fournit des informations supplémentaires sur une exception.  
  
 CorDebugExceptionUnwindCallbackType  
 Indique l'événement qui est signalé par le rappel lors de la phase de déroulement.  
  
 [CorDebugGCType, énumération](cordebuggctype-enumeration.md)  
 Indique si le récupérateur de mémoire s'exécute sur une station de travail ou sur un serveur.  
  
 [CorDebugGenerationTypes, énumération](cordebuggenerationtypes-enumeration.md)  
 Spécifie la génération d’une région de la mémoire sur le tas managé.  
  
 CorDebugHandleType  
 Indique le type de handle.  
  
 [CorDebugIlToNativeMappingTypes, énumération](cordebugiltonativemappingtypes-enumeration.md)  
 Indique si une plage particulière d'instructions natives correspond à une région spéciale du code.  
  
 CorDebugIntercept  
 Indique les types de code qui peuvent l'objet d'une exécution pas à pas.  
  
 [CorDebugInterfaceVersion, énumération](cordebuginterfaceversion-enumeration.md)  
 Spécifie une version de .NET Framework ou la version de .NET Framework où une interface a été introduite.  
  
 CorDebugInternalFrameType  
 Identifie le type de frame de pile.  
  
 [CorDebugJITCompilerFlags, énumération](cordebugjitcompilerflags-enumeration.md)  
 Contient des valeurs qui influencent le comportement du compilateur juste-à-temps managé.  
  
 [CorDebugJITCompilerFlagsDeprecated, énumération](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Obsolète. Utilisez à la place le membre `CORDEBUG_JIT_DEFAULT` de l’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .  
  
 CorDebugMappingResult  
 Fournit les détails sur la façon dont la valeur du pointeur d'instruction a été obtenue.  
  
 [CorDebugMDAFlags, énumération](cordebugmdaflags-enumeration.md)  
 Spécifie l'état du thread sur lequel l'Assistant Débogage managé est déclenché.  
  
 [CorDebugNGenPolicy, énumération](cordebugngenpolicy-enumeration.md)  
 Fournit une valeur qui détermine si un débogueur charge les images natives (NGen) depuis le cache d'images natives.  
  
 [CorDebugPlatform, énumération](cordebugplatform-enumeration.md)  
 Fournit les valeurs de plateforme cible utilisées par la méthode [ICorDebugDataTarget :: GetPlatform](icordebugdatatarget-getplatform-method.md) .  
  
 [CorDebugRecordFormat, énumération](cordebugrecordformat-enumeration.md)  
 Décrit le format des données dans un tableau d'octets qui contient des informations sur un événement de débogage d'exception native.  
  
 CorDebugRegister  
 Spécifie les registres associés à une architecture de processeur donnée.  
  
 [CorDebugSetContextFlag, énumération](cordebugsetcontextflag-enumeration.md)  
 Indique si le contexte provient du frame (ou feuille) actif ou s'il a été calculé par déroulement à partir d'un autre frame.  
  
 [CorDebugStateChange, énumération](cordebugstatechange-enumeration.md)  
 Représente la quantité de données mises en cache à ignorer sur la base des modifications apportées au processus.  
  
 CorDebugStepReason  
 Indique le résultat d'une étape individuelle.  
  
 CorDebugThreadState  
 Spécifie l'état d'un thread pour le débogage.  
  
 \>CorDebugUnmappedStop  
 Spécifie le type de code non mappé qui peut déclencher un arrêt dans l'exécution du code par l'exécution pas à pas.  
  
 CorDebugUserState  
 Indique l'état de l'utilisateur d'un thread.  
  
 [CorGCReferenceType, énumération](corgcreferencetype-enumeration.md)  
 Identifie la source d'un objet pour lequel l'espace occupé en mémoire peut être récupéré.  
  
 [ILCodeKind, énumération](ilcodekind-enumeration.md)  
 Fournit des valeurs qui spécifient si le débogueur peut accéder aux variables locales ou au code ajoutés dans l'instrumentation ReJIT du profileur.  
  
 [LoggingLevelEnum, énumération](logginglevelenum-enumeration.md)  
 Indique le niveau de gravité d'un message de description qui est écrit dans le journal des événements quand un thread managé consigne un événement.  
  
 [LogSwitchCallReason, énumération](logswitchcallreason-enumeration.md)  
 Indique l'opération qui a été effectuée sur un commutateur de débogage/suivi.  
  
 [VariableLocationType, énumération](variablelocationtype-enumeration.md)  
 Indique le type d’emplacement natif d’une variable.  
  
 [WriteableMetadataUpdateMode, énumération](writeablemetadataupdatemode-enumeration.md)  
 Fournit des valeurs qui spécifient si les mises à jour en mémoire apportées aux métadonnées sont visibles par un débogueur. 

 [Énumération ClrDataSourceType](clrdatasourcetype-enumeration.md) Fournit des valeurs utilisées par la structure CLRDATA_IL_ADDRESS_MAP.

## <a name="related-sections"></a>Rubriques connexes  
 [Coclasses de débogage](debugging-coclasses.md)  
  
 [Interfaces de débogage](debugging-interfaces.md)  
  
 [Fonctions statiques globales de débogage](debugging-global-static-functions.md)  
  
 [Structures de débogage](debugging-structures.md)
