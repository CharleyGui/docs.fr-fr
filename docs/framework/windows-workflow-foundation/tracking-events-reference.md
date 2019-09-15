---
title: Référence des événements de suivi
ms.date: 03/30/2017
ms.assetid: c1c1ee87-f80a-449b-acd0-50d81eef116e
ms.openlocfilehash: af0c4441b89345b67c46c714d9ab3e5ceb9e3d6f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988966"
---
# <a name="tracking-events-reference"></a>Référence des événements de suivi
Pendant l'exécution, un workflow dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] déclenche des événements de suivi en parcourant différentes étapes de sa durée de vie. L'hôte peut s'abonner à ces événements et rester informé sur l'état de la progression du workflow pendant sa durée de vie. Les événements de suivi déclenchés sont traités dans cette section.  
  
## <a name="event-reference"></a>Référence d'événement  
  
|ID d'événement|Niveau d'événement|Message d'événement.|Mots clés|  
|--------------|-----------------|-------------------|--------------|  
|[100 - WorkflowInstanceRecord](100-workflowinstancerecord.md)|Information|TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[101 - WorkflowInstanceUnhandledExceptionRecord](101-workflowinstanceunhandledexceptionrecord.md)|Error|TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName=%8, Exception=%9, Annotations= %10, ProfileName = %11|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[102 - WorkflowInstanceAbortedRecord](102-workflowinstanceabortedrecord.md)|Warning|TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[103 - ActivityStateRecord](103-activitystaterecord.md)|Information|TrackRecord = ActivityStateRecord, InstanceID =% 1, RecordNumber=%2, EventTime=%3, état =% 4, Name=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Arguments=%9, Variables=%10, Annotations=%11, ProfileName =% 12|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[104 - ActivityScheduledRecord](104-activityscheduledrecord.md)|Information|TrackRecord = ActivityScheduledRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, Name = %4, ActivityId = %5, ActivityInstanceId = %6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = %10, ChildActivityTypeName =%11, Annotations=%12, ProfileName = %13|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[105 - FaultPropagationRecord](105-faultpropagationrecord.md)|Warning|TrackRecord = FaultPropagationRecord, InstanceID=%1, RecordNumber=%2, EventTime=%3, FaultSourceActivityName=%4, FaultSourceActivityId=%5, FaultSourceActivityInstanceId=%6, FaultSourceActivityTypeName=%7, FaultHandlerActivityName=%8, FaultHandlerActivityId = %9, FaultHandlerActivityInstanceId =%10, FaultHandlerActivityTypeName=%11, Fault=%12, IsFaultSource=%13, Annotations=%14, ProfileName = %15|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[106 - CancelRequestRecord](106-cancelrequestrecord.md)|Information|TrackRecord = CancelRequestedRecord, InstanceID=%1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityId=%5, ActivityInstanceId=%6, ActivityTypeName =% 7, ChildActivityName =% 8, ChildActivityId =% 9, ChildActivityInstanceId =% 10, ChildActivityTypeName =% 11, Annotations=%12, ProfileName =% 13|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[107 -- BookmarkResumptionRecord](107-bookmarkresumptionrecord.md)|Information|TrackRecord = BookmarkResumptionRecord, InstanceID=%1, RecordNumber=%2,EventTime=%3, Name=%4, SubInstanceID=%5, OwnerActivityName=%6, OwnerActivityId =%7, OwnerActivityInstanceId=%8, OwnerActivityTypeName=%9, Annotations=%10, ProfileName = %11|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[108 - CustomTrackingRecordInfo](108-customtrackingrecordinfo.md)|Information|TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName = %11|UserEvents, EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[110 - CustomTrackingRecordWarning](110-customtrackingrecordwarning.md)|Warning|TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName = %11|UserEvents, EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[111 - CustomTrackingRecordError](111-customtrackingrecorderror.md)|Error|TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName = %11|UserEvents, EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[112 - WorkflowInstanceSuspendedRecord](112-workflowinstancesuspendedrecord.md)|Information|TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[113 - WorkflowInstanceTerminatedRecord](113-workflowinstanceterminatedrecord.md)|Error|TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|[114 - WorkflowInstanceRecordWithId](114-workflowinstancerecordwithid.md)|Information|TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|HealthMonitoring, WFTracking|  
|[115 - WorkflowInstanceAbortedRecordWithId](115-workflowinstanceabortedrecordwithid.md)|Warning|TrackRecord = WorkflowInstanceAbortedRecord, InstanceID =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, Reason =% 5, annotations =% 6, ProfileName =% 7, WorkflowDefinitionIdentity =% 8|HealthMonitoring, WFTracking|  
|[116 - WorkflowInstanceSuspendedRecordWithId](116-workflowinstancesuspendedrecordwithid.md)|Information|TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8|HealthMonitoring, WFTracking|  
|[117 - WorkflowInstanceTerminatedRecordWithId](117-workflowinstanceterminatedrecordwithid.md)|Error|TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, Reason =% 5, annotations =% 6, ProfileName =% 7, WorkflowDefinitionIdentity =% 8|HealthMonitoring, WFTracking|  
|[118 - WorkflowInstanceUnhandledExceptionRecordWithId](118-workflowinstanceunhandledexceptionrecordwithid.md)|Error|TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceID =% 1, RecordNumber =% 2, EventTime =% 3, ActivityDefinitionId =% 4, SourceName =% 5, SourceId =% 6, SourceInstanceId =% 7, SourceTypeName =% 8, exception =% 9, annotations =% 10, ProfileName = % 11, WorkflowDefinitionIdentity =% 12|HealthMonitoring, WFTrackingHealthMonitoring, WFTracking|  
|[119 - WorkflowInstanceUpdatedRecord](119-workflowinstanceupdatedrecord.md)|Information|TrackRecord= WorkflowInstanceUpdatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, Annotations = %8, ProfileName = %9|HealthMonitoring, WFTracking|  
|[225 - TraceCorrelationKeys](225-tracecorrelationkeys.md)|Information|Clé de corrélation '%1' calculée à l'aide des valeurs '%2' dans l'étendue parente '%3'.|Dépannage de WFServices|  
|[440 - StartSignpostEvent1](440-startsignpostevent.md)|Information|Limite d'activité.|Dépannage de WFServices|  
|[441- StopSignpostEvent1](441-stopsignpostevent.md)|Information|Limite d'activité.|Dépannage de WFServices|  
|[1001 - WorkflowApplicationCompleted](1001-workflowapplicationcompleted.md)|Information|ID WorkflowInstance : « %1 » s'est terminé à l'état Closed.|WFRuntime|  
|[1002 - WorkflowApplicationTerminated](1002-workflowapplicationterminated.md)|Information|Identificateur de WorkflowApplication : « %1 » a été arrêté. Il s'est terminé dans l'état Faulted avec une exception.|WFRuntime|  
|[1003 - WorkflowInstanceCanceled](1003-workflowinstancecanceled.md)|Information|ID WorkflowInstance : « %1 » s'est terminé à l'état Canceled.|WFRuntime|  
|[1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md)|Information|ID WorkflowInstance : « %1 » a été abandonné avec une exception.|WFRuntime|  
|[1005 - WorkflowApplicationIdled](1005-workflowapplicationidled.md)|Information|ID WorkflowApplication : « %1 » est devenu inactif.|WFRuntime|  
|[1006 - WorkflowApplicationUnhandledException](1006-workflowapplicationunhandledexception.md)|Error|WorkflowInstance ID : '% 1 'a rencontré une exception non gérée.  L’exception provient de l’activité « % 2 », DisplayName : « % 3 ».  L’action suivante sera effectuée :% 4.|WFRuntime|  
|[1007 - WorkflowApplicationPersisted](1007-workflowapplicationpersisted.md)|Information|ID WorkflowApplication : « %1 » était Persisted.|WFRuntime|  
|[1008 - WorkflowApplicationUnloaded](1008-workflowapplicationunloaded.md)|Information|ID WorkflowInstance : « %1 » était Unloaded.|WFRuntime|  
|[1009 - ActivityScheduled](1009-activityscheduled.md)|Information|L'activité parent « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié l'activité enfant « %4 », DisplayName : « %5 », InstanceId : « %6 ».|WFRuntime|  
|[1010 - ActivityCompleted](1010-activitycompleted.md)|Information|L'activité parent « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié l'activité enfant « %4 », DisplayName : « %5 », InstanceId : « %6 ».|WFRuntime|  
|[1011 - ScheduleExecuteActivityWorkItem](1011-scheduleexecuteactivityworkitem.md)|Détaillé|ExecuteActivityWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».|WFRuntime|  
|[1012 - StartExecuteActivityWorkItem](1012-startexecuteactivityworkitem.md)|Détaillé|Début de l'exécution d'un ExecuteActivityWorkItem pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».|WFRuntime|  
|[1013 - CompleteExecuteActivityWorkItem](1013-completeexecuteactivityworkitem.md)|Détaillé|ExecuteActivityWorkItem est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».|WFRuntime|  
|[1014 - ScheduleCompletionWorkItem](1014-schedulecompletionworkitem.md)|Détaillé|Un CompletionWorkItem a été planifié pour l’activité parente « % 1 », DisplayName : « % 2 », InstanceId : « % 3 ».  Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».|WFRuntime|  
|[1015 - StartCompletionWorkItem](1015-startcompletionworkitem.md)|Détaillé|Début de l'exécution d'un CompletionWorkItem pour l'activité parente « %1 », DisplayName : « %2 », InstanceId : « %3 ». Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».|WFRuntime|  
|[1016 - CompleteCompletionWorkItem](1016-completecompletionworkitem.md)|Détaillé|Un CompletionWorkItem est achevé pour l'activité parente « %1 », DisplayName : « %2 », InstanceId : « %3 ». Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».|WFRuntime|  
|[1017 - ScheduleCancelActivityWorkItem](1017-schedulecancelactivityworkitem.md)|Détaillé|CancelActivityWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».|WFRuntime|  
|[1018 - StartCancelActivityWorkItem](1018-startcancelactivityworkitem.md)|Détaillé|Début de l'exécution d'un CancelActivityWorkItem pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».|WFRuntime|  
|[1019 - CompleteCancelActivityWorkItem](1019-completecancelactivityworkitem.md)|Détaillé|CancelActivityWorkItem est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».|WFRuntime|  
|[1020 - CreateBookmark](1020-createbookmark.md)|Détaillé|Un signet a été créé pour l’activité « % 1 », DisplayName : « % 2 », InstanceId : « % 3 ».  BookmarkName : %4, BookmarkScope : %5.|WFRuntime|  
|[1021 - ScheduleBookmarkWorkItem](1021-schedulebookmarkworkitem.md)|Détaillé|Un BookmarkWorkItem a été planifié pour l’activité « % 1 », DisplayName : « % 2 », InstanceId : « % 3 ».  BookmarkName : %4, BookmarkScope : %5.|WFRuntime|  
|[1022 - StartBookmarkWorkItem](1022-startbookmarkworkitem.md)|Détaillé|Début de l’exécution d’un BookmarkWorkItem pour l’activité'% 1 ', DisplayName : '% 2 ', InstanceId : '% 3 '.  BookmarkName : %4, BookmarkScope : %5.|WFRuntime|  
|[1023 - CompleteBookmarkWorkItem](1023-completebookmarkworkitem.md)|Détaillé|Un BookmarkWorkItem est achevé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ». BookmarkName : %4, BookmarkScope : %5.|WFRuntime|  
|[1024 - CreateBookmarkScope](1024-createbookmarkscope.md)|Détaillé|Un BookmarkScope a été créé : %1.|WFRuntime|  
|[1025 - BookmarkScopeInitialized](1025-bookmarkscopeinitialized.md)|Détaillé|Le BookmarkScope avec TemporaryId : « %1 » a été initialisé avec l'ID : « %2 ».|WFRuntime|  
|[1026 - ScheduleTransactionContextWorkItem](1026-scheduletransactioncontextworkitem.md)|Détaillé|TransactionContextWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».|WFRuntime|  
|[1027 - StartTransactionContextWorkItem](1027-starttransactioncontextworkitem.md)|Détaillé|Début de l’exécution d’un TransactionContextWorkItem pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».|WFRuntime|  
|[1028 - CompleteTransactionContextWorkItem](1028-completetransactioncontextworkitem.md)|Détaillé|TransactionContextWorkItem est terminé pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».|WFRuntime|  
|[1029 - ScheduleFaultWorkItem](1029-schedulefaultworkitem.md)|Détaillé|Un FaultWorkItem a été planifié pour l’activité « % 1 », DisplayName : « % 2 », InstanceId : « % 3 ».  L'exception a été propagée à partir de l'activité « %4 », DisplayName : « %5 », InstanceId : « %6 ».|WFRuntime|  
|[1030 - StartFaultWorkItem](1030-startfaultworkitem.md)|Détaillé|Début de l’exécution d’un FaultWorkItem pour l’activité'% 1 ', DisplayName : '% 2 ', InstanceId : '% 3 '.  L'exception a été propagée à partir de l'activité « %4 », DisplayName : « %5 », InstanceId : « %6 ».|WFRuntime|  
|[1031 - CompleteFaultWorkItem](1031-completefaultworkitem.md)|Détaillé|Un FaultWorkItem est achevé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ». L'exception a été propagée à partir de l'activité « %4 », DisplayName : « %5 », InstanceId : « %6 ».|WFRuntime|  
|[1032 - ScheduleRuntimeWorkItem](1032-scheduleruntimeworkitem.md)|Détaillé|Un élément de travail runtime a été planifié pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».|WFRuntime|  
|[1033 - StartRuntimeWorkItem](1033-startruntimeworkitem.md)|Détaillé|Début de l’exécution d’un élément de travail runtime pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».|WFRuntime|  
|[1034 - CompleteRuntimeWorkItem](1034-completeruntimeworkitem.md)|Détaillé|Un élément de travail runtime est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».|WFRuntime|  
|[1035 - RuntimeTransactionSet](1035-runtimetransactionset.md)|Détaillé|La transaction d’exécution a été définie par l’activité « % 1 », DisplayName : « % 2 », InstanceId : « % 3 ».  Exécution isolée de l’activité'% 4 ', DisplayName : '% 5 ', InstanceId : '% 6 '.|WFRuntime|  
|[1036 - RuntimeTransactionCompletionRequested](1036-runtimetransactioncompletionrequested.md)|Détaillé|L’activité « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié la fin de la transaction runtime.|WFRuntime|  
|[1037 - RuntimeTransactionComplete](1037-runtimetransactioncomplete.md)|Détaillé|La transaction runtime s’est terminée en état « %1 ».|WFRuntime|  
|[1038 - EnterNoPersistBlock](1038-enternopersistblock.md)|Détaillé|Entrée dans un bloc sans persistance.|WFRuntime|  
|[1039 - ExitNoPersistBlock](1039-exitnopersistblock.md)|Détaillé|Sortie d'un bloc sans persistance.|WFRuntime|  
|[1040 - InArgumentBound](1040-inargumentbound.md)|Détaillé|Dans l’argument « %1 » de l’activité « %2 », DisplayName : « %3 », InstanceId : « %4 » a été lié avec la valeur : %5.|WFActivities|  
|[1041 - WorkflowApplicationPersistableIdle](1041-workflowapplicationpersistableidle.md)|Information|ID WorkflowApplication : « % 1 » est inactif et persistable.  L’action suivante sera effectuée :% 2.|WFRuntime|  
|[1101 - WorkflowActivityStart](1101-workflowactivitystart.md)|Information|ID WorkflowInstance : « %1 » Activité E2E|WFRuntime|  
|[1102 - WorkflowActivityStop](1102-workflowactivitystop.md)|Information|ID WorkflowInstance : « %1 » Activité E2E|WFRuntime|  
|[1103 - WorkflowActivitySuspend](1103-workflowactivitysuspend.md)|Information|ID WorkflowInstance : « %1 » Activité E2E|WFRuntime|  
|[1104 - WorkflowActivityResume](1104-workflowactivityresume.md)|Information|ID WorkflowInstance : « %1 » Activité E2E|WFRuntime|  
|[1124 - InvokeMethodIsStatic](1124-invokemethodisstatic.md)|Information|InvokeMethod « %1 » - la méthode est statique.|WFRuntime|  
|[1125 - InvokeMethodIsNotStatic](1125-invokemethodisnotstatic.md)|Information|InvokeMethod « %1 » - la méthode n'est pas statique.|WFRuntime|  
|[1126 - InvokedMethodThrewException](1126-invokedmethodthrewexception.md)|Information|Une exception a été levée dans la méthode appelée par l'activité « %1 ». %2|WFRuntime|  
|[1131 - InvokeMethodUseAsyncPattern](1131-invokemethoduseasyncpattern.md)|Information|InvokeMethod « %1 » - la méthode utilise un modèle asynchrone de « %2 » et « %3 ».|WFRuntime|  
|[1132 - InvokeMethodDoesNotUseAsyncPattern](1132-invokemethoddoesnotuseasyncpattern.md)|Information|InvokeMethod « %1 » - la méthode n’utilise pas un modèle asynchrone.|WFRuntime|  
|[1140 - FlowchartStart](1140-flowchartstart.md)|Information|Flowchart « %1 » - Le début a été planifié|WFActivities|  
|[1141 - FlowchartEmpty](1141-flowchartempty.md)|Warning|Flowchart « %1 » - a été exécuté sans nœuds. Une exception a été levée dans la méthode appelée par l'activité « %1 ». %2|WFActivities|  
|[1143 - FlowchartNextNull](1143-flowchartnextnull.md)|Information|Flowchart « %1 »/FlowStep - Le nœud suivant est Null. L'exécution de Flowchart va se terminer.|WFActivities|  
|[1146 - FlowchartSwitchCase](1146-flowchartswitchcase.md)|Information|Flowchart « %1 »/FlowSwitch - Le cas « %2 » a été sélectionné.|WFActivities|  
|[1147 - FlowchartSwitchDefault](1147-flowchartswitchdefault.md)|Information|Flowchart '%1'/FlowSwitch - cas par défaut a été sélectionné.|WFActivities|  
|[1148 - FlowchartSwitchCaseNotFound](1148-flowchartswitchcasenotfound.md)|Information|Flowchart « %1 »/FlowSwitch - impossible de trouver l'activité Case ou un cas par défaut correspondant au résultat de l'expression. L'exécution de Flowchart va se terminer.|WFActivities|  
|[1150 - CompensationState](1150-compensationstate.md)|Information|CompensableActivity « %1 » est dans l'état « %2 ».|WFActivities|  
|[1223 - SwitchCaseNotFound](1223-switchcasenotfound.md)|Information|L'activité Switch « %1 » n'a pas trouvé une activité Case qui correspond au résultat Expression.|WFActivities|  
|[1449 - WfMessageReceived](1449-wfmessagereceived.md)|Information|Message reçu par le workflow|WFServices|  
|[1450 - WfMessageSent](1450-wfmessagesent.md)|Information|Message envoyé à partir du workflow|WFServices|  
|[2021 - ExecuteWorkItemStart](2021-executeworkitemstart.md)|Détaillé|Début de l'exécution de l'élément de travail|WFRuntime|  
|[2022 - ExecuteWorkItemStop](2022-executeworkitemstop.md)|Détaillé|Arrêt de l'exécution de l'élément de travail|WFRuntime|  
|[2023 - SendMessageChannelCacheMiss](2023-sendmessagechannelcachemiss.md)|Détaillé|Échec de SendMessageChannelCache|WFRuntime|  
|[2024 - InternalCacheMetadataStart](2024-internalcachemetadatastart.md)|Détaillé|InternalCacheMetadata a démarré sur l'activité « %1 ».|WFRuntime|  
|[2025 - InternalCacheMetadataStop](2025-internalcachemetadatastop.md)|Détaillé|InternalCacheMetadata s'est arrêté sur l'activité « %1 ».|WFRuntime|  
|[2026 - CompileVbExpressionStart](2026-compilevbexpressionstart.md)|Détaillé|Compilation de l'expression Visual Basic « %1 »|WFRuntime|  
|[2027 - CacheRootMetadataStart](2027-cacherootmetadatastart.md)|Détaillé|CacheRootMetadata a démarré sur l'activité « %1 »|WFRuntime|  
|[2028 - CacheRootMetadataStop](2028-cacherootmetadatastop.md)|Détaillé|CacheRootMetadata s'est arrêté sur l'activité %1.|WFRuntime|  
|[2029 - CompileVbExpressionStop](2029-compilevbexpressionstop.md)|Détaillé|Compilation de l'expression Visual Basic terminée.|WFRuntime|  
|[2576 - TryCatchExceptionFromTry](2576-trycatchexceptionfromtry.md)|Information|L'activité TryCatch « %1 » a intercepté une exception de type « %2 ».|WFActivities|  
|[2577 - TryCatchExceptionDuringCancelation](2577-trycatchexceptionduringcancelation.md)|Warning|Une activité enfant de l'activité TryCatch « %1 » a levé une exception durant l'annulation.|WFActivities|  
|[2578 - TryCatchExceptionFromCatchOrFinally](2578-trycatchexceptionfromcatchorfinally.md)|Warning|Une activité Catch ou Finally associée à l'activité TryCatch « %1 » a levé une exception.|WFActivities|  
|[3501 - InferredContractDescription](3501-inferredcontractdescription.md)|Information|ContractDescription avec Name='%1' et Namespace='%2' a été déduit de WorkflowService.|WFServices|  
|[3502 - InferredOperationDescription](3502-inferredoperationdescription.md)|Information|OperationDescription avec Name='%1' dans le contrat « %2 » a été déduit de WorkflowService. IsOneWay=%3.|WFServices|  
|[3503 - DuplicateCorrelationQuery](3503-duplicatecorrelationquery.md)|Warning|CorrelationQuery en double trouvé avec Where='%1'. Cette requête en double ne sera pas utilisée lors du calcul de la corrélation.|WFServices|  
|[3507 - ServiceEndpointAdded](3507-serviceendpointadded.md)|Information|Un point de terminaison du service a été ajouté pour l'adresse « %1 », la liaison « %2 » et le contrat « %3 ».|WFServices|  
|[3508 - TrackingProfileNotFound](3508-trackingprofilenotfound.md)|Détaillé|TrackingProfile « %1 » pour le ActivityDefinitionId « %2 » introuvable. TrackingProfile est introuvable dans le fichier de configuration ou ActivityDefinitionId ne correspond pas.|WFServices|  
|[3550 - BufferOutOfOrderMessageNoInstance](3550-bufferoutofordermessagenoinstance.md)|Information|Impossible d'effectuer l'opération « %1 » actuellement. Une autre tentative sera faite lorsque l'instance de service sera prête à traiter cette opération.|WFServices|  
|[3551 - BufferOutOfOrderMessageNoBookmark](3551-bufferoutofordermessagenobookmark.md)|Information|Impossible d'effectuer actuellement l'opération « %2 » sur l'instance de service « %1 ». Une autre tentative sera faite lorsque l'instance de service sera prête à traiter cette opération.|WFServices|  
|[3552 - MaxPendingMessagesPerChannelExceeded](3552-maxpendingmessagesperchannelexceeded.md)|Warning|La limite « MaxPendingMessagesPerChannel » de la limitation « % 1 » a été atteinte. Pour accroître cette limite, modifiez la propriété MaxPendingMessagesPerChannel sur BufferedReceiveServiceBehavior.|Quota WFServices|  
|[3557 - TransactedReceiveScopeEndCommitFailed](3557-transactedreceivescopeendcommitfailed.md)|Information|L'appel à EndCommit sur le CommittableTransaction avec l'ID = « %1 » a levé un TransactionException avec le message suivant : « %2 ».|WFServices|  
|[4201 - EndSqlCommandExecute](4201-endsqlcommandexecute.md)|Détaillé|Fin de l'exécution de la commande SQL : %1|WFInstanceStore|  
|[4202 - StartSqlCommandExecute](4202-startsqlcommandexecute.md)|Détaillé|Démarrage de l'exécution de la commande SQL : %1|WFInstanceStore|  
|[4203 - RenewLockSystemError](4203-renewlocksystemerror.md)|Error|Échec de l'extension de l'expiration du verrou ; l'expiration du verrou a déjà été passée ou le propriétaire de verrou a été supprimé. Abandon de SqlWorkflowInstanceStore.|WFInstanceStore|  
|[4205 - FoundProcessingError](4205-foundprocessingerror.md)|Error|Échec de la commande : %1|WFInstanceStore|  
|[4206 - UnlockInstanceException](4206-unlockinstanceexception.md)|Error|Exception %1 rencontrée lors de la tentative de déverrouillage de l'instance.|WFInstanceStore|  
|[4207 - MaximumRetriesExceededForSqlCommand](4207-maximumretriesexceededforsqlcommand.md)|Information|Abandon des tentatives d'exécution d'une commande SQL, le nombre maximal de tentatives ayant été atteint.|Quota WFInstanceStore|  
|[4208 - RetryingSqlCommandDueToSqlError](4208-retryingsqlcommandduetosqlerror.md)|Information|Nouvelle tentative d'exécution d'une commande SQL en raison du numéro d'erreur SQL %1.|WFInstanceStore|  
|[4209 - TimeoutOpeningSqlConnection](4209-timeoutopeningsqlconnection.md)|Error|Expiration du délai d'attente lors de la tentative d'ouverture d'une connexion SQL. L'opération ne s'est pas terminée dans le délai imparti de %1. Le temps alloué à cette opération peut avoir été une partie d'un délai d'expiration plus long.|WFInstanceStore|  
|[4210 - SqlExceptionCaught](4210-sqlexceptioncaught.md)|Warning|Message %2 avec numéro d'exception SQL %1 intercepté.|WFInstanceStore|  
|[4211 - QueuingSqlRetry](4211-queuingsqlretry.md)|Warning|Mise en file d'attente d'une tentative SQL avec un retard de %1 millisecondes.|WFInstanceStore|  
|[4212 - LockRetryTimeout](4212-lockretrytimeout.md)|Warning|Délai d’attente lors de l’acquisition du verrou d’instance.  L'opération ne s'est pas terminée dans le délai imparti de %1. Le temps alloué à cette opération peut avoir été une partie d'un délai d'expiration plus long.|WFInstanceStore|  
|[4213 - RunnableInstancesDetectionError](4213-runnableinstancesdetectionerror.md)|Error|Échec de la détection des instances exécutables en raison de l'exception suivante|WFInstanceStore|  
|[4214 - InstanceLocksRecoveryError](4214-instancelocksrecoveryerror.md)|Error|Échec de la récupération des verrous d'instance en raison de l'exception suivante|WFInstanceStore|  
|[39456 - TrackingRecordDropped](39456-trackingrecorddropped.md)|Warning|La taille de l'enregistrement de suivi %1 dépasse la valeur maximale autorisée par la session ETW pour le fournisseur %2|WFTracking|  
|[39457 - TrackingRecordRaised](39457-trackingrecordraised.md)|Information|Enregistrement suivi %1 élevé à %2.|WFRuntime|  
|[39458 - TrackingRecordTruncated](39458-trackingrecordtruncated.md)|Warning|Enregistrement de suivi %1 tronqué écrit dans la session ETW avec le fournisseur %2. Les données de variables/annotations/utilisateur ont été supprimées|WFTracking|  
|[39459 - TrackingDataExtracted](39459-trackingdataextracted.md)|Détaillé|Données de suivi %1 extraites dans l'activité %2.|WFRuntime|  
|[39460 - TrackingValueNotSerializable](39460-trackingvaluenotserializable.md)|Warning|La variable ou l’argument « %1 » extrait ne peut pas être sérialisé.|WFTracking|  
|[57398 - MaxInstancesExceeded](57398-maxinstancesexceeded.md)|Warning|Le système a atteint la limite définie pour la limitation des 'MaxConcurrentInstances'. La limite a été définie sur %1. La valeur de limitation peut être modifiée en modifiant l'attribut « maxConcurrentInstances » de l'élément serviceThrottle ou en modifiant la propriété « MaxConcurrentInstances » à l'aide du comportement ServiceThrottlingBehavior.|WFServices|
