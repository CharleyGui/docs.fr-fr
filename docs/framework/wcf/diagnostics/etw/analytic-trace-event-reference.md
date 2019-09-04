---
title: Référence d'événement de trace analytique
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: ae792a0b55b0559b13c2394bd27d85f224d1aea0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70243975"
---
# <a name="analytic-trace-event-reference"></a>Référence d'événement de trace analytique
Le tableau suivant définit les niveaux d’événements, les identificateurs et les messages associés au suivi analytique WCF.  
  
## <a name="event-reference"></a>Référence d'événement  
  
|ID d'événement|Niveau d'événement|Message d'événement.|Mots clés|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](../../../../../docs/framework/wcf/diagnostics/etw/131-bufferpoolallocation.md)|Détaillé|Le pool est en train d'allouer %1 octets.|Infrastructure|  
|[132 - BufferPoolChangeQuota](../../../../../docs/framework/wcf/diagnostics/etw/132-bufferpoolchangequota.md)|Détaillé|BufferPool de taille %1, modification du quota par %2.|Infrastructure|  
|[133 - ActionItemScheduled](../../../../../docs/framework/wcf/diagnostics/etw/133-actionitemscheduled.md)|Détaillé|Rappel du planificateur de threads d'E/S invoqué.|Infrastructure|  
|[134 - ActionItemCallbackInvoked](../../../../../docs/framework/wcf/diagnostics/etw/134-actionitemcallbackinvoked.md)|Détaillé|Rappel du planificateur de threads d'E/S invoqué.|Infrastructure|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/201-clientmessageinspectorafterreceiveinvoked.md)|Information|Le répartiteur a appelé 'AfterReceiveReply' sur un ClientMessageInspector de type '%1.'|Dépannage, ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/202-clientmessageinspectorbeforesendinvoked.md)|Information|Le répartiteur a appelé « BeforeSendRequest » sur un ClientMessageInspector de type « %1 ».|Dépannage, ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/203-clientparameterinspectoraftercallinvoked.md)|Information|Le répartiteur a appelé « AfterCall » sur un ClientParameterInspector. de type « %1 ».|Dépannage, ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/204-clientparameterinspectorbeforecallinvoked.md)|Information|Le répartiteur a appelé 'BeforeCall' sur un ClientParameterInspector de type '%1.'|Dépannage, ServiceModel|  
|[205 - OperationInvoked](../../../../../docs/framework/wcf/diagnostics/etw/205-operationinvoked.md)|Information|Un OperationInvoker a appelé la méthode '%1'.|EndToEndMonitoring, Dépannage, ServiceModel|  
|[206 - ErrorHandlerInvoked](../../../../../docs/framework/wcf/diagnostics/etw/206-errorhandlerinvoked.md)|Information|Le répartiteur a appelé un ErrorHandler de type '%1' avec une exception de type '%3'.  ErrorHandled == '%2.'|Dépannage, ServiceModel|  
|[207 - FaultProviderInvoked](../../../../../docs/framework/wcf/diagnostics/etw/207-faultproviderinvoked.md)|Information|Le répartiteur a appelé un FaultProvider de type '%1' avec une exception de type '%2.'|Dépannage, ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/208-messageinspectorafterreceiveinvoked.md)|Information|Le répartiteur a appelé 'AfterReceiveReply' sur un MessageInspector de type '%1'.|Dépannage, ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/209-messageinspectorbeforesendinvoked.md)|Information|Le répartiteur a appelé 'BeforeSendRequest' sur un MessageInspector de type '%1'.|Dépannage, ServiceModel|  
|[210 - MessageThrottleExceeded](../../../../../docs/framework/wcf/diagnostics/etw/210-messagethrottleexceeded.md)|Warning|La valeur '%1' de la limitation '%2' a été atteinte.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[211 - ParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/211-parameterinspectoraftercallinvoked.md)|Information|Le répartiteur a appelé 'AfterCall' sur un ParameterInspector de type '%1'.|Dépannage, ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/212-parameterinspectorbeforecallinvoked.md)|Information|Le répartiteur a appelé 'BeforeCall' sur un ParameterInspector de type '%1.'|Dépannage, ServiceModel|  
|[213 - ServiceHostStarted](../../../../../docs/framework/wcf/diagnostics/etw/213-servicehoststarted.md)|LogAlways|ServiceHost a démarré : '%1'.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)|Information|OperationInvoker a terminé l'appel de la méthode '%1'.  Durée de l'appel de méthode : '%2' ms.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[215 - MessageReceivedByTransport](../../../../../docs/framework/wcf/diagnostics/etw/215-messagereceivedbytransport.md)|Information|Le transport a reçu un message de '%1'.|Dépannage, ServiceModel|  
|[216 - MessageSentByTransport](../../../../../docs/framework/wcf/diagnostics/etw/216-messagesentbytransport.md)|Information|Le transport a envoyé un message à '%1.'|Dépannage, ServiceModel|  
|[217 - ClientOperationPrepared](../../../../../docs/framework/wcf/diagnostics/etw/217-clientoperationprepared.md)|Information|Le client exécute l'opération '%1' définie dans le contrat '%2'. Le message sera envoyé à '%3'.|Dépannage, ServiceModel|  
|[218 - ClientOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/218-clientoperationcompleted.md)|Information|Le client a terminé l'exécution de l'opération '%1' définie dans le contrat '%2'. Le message a été envoyé à '%3'.|Dépannage, ServiceModel|  
|[219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)|Error|Une exception non gérée de type '%2' s'est produite lors du traitement du message.  Exception totale ToString : %1.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[220 - MessageSentToTransport](../../../../../docs/framework/wcf/diagnostics/etw/220-messagesenttotransport.md)|Information|Le répartiteur a envoyé un message au transport. ID de corrélation == '%1.'|EndToEndMonitoring, Dépannage, ServiceModel|  
|[221 - MessageReceivedFromTransport](../../../../../docs/framework/wcf/diagnostics/etw/221-messagereceivedfromtransport.md)|Information|Le répartiteur a reçu un message du transport. ID de corrélation == '%1.'|EndToEndMonitoring, Dépannage, ServiceModel|  
|[222 - OperationFailed](../../../../../docs/framework/wcf/diagnostics/etw/222-operationfailed.md)|Warning|La méthode '%1' a levé une exception non gérée lors de l'appel effectué par l'OperationInvoker. Durée de l'appel de méthode : '%2' ms.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[223 - OperationFaulted](../../../../../docs/framework/wcf/diagnostics/etw/223-operationfaulted.md)|Warning|La méthode '%1' a levé un FaultException lors de l'appel effectué par l'OperationInvoker. Durée de l'appel de méthode : '%2' ms.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[224 - MessageThrottleAtSeventyPercent](../../../../../docs/framework/wcf/diagnostics/etw/224-messagethrottleatseventypercent.md)|Warning|La valeur de la limitation '%1' de '%2' est à 70%.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[226 - IdleServicesClosed](../../../../../docs/framework/wcf/diagnostics/etw/226-idleservicesclosed.md)|LogAlways|%1 services inactifs sur un total de %2 services activés ont été fermés.|HealthMonitoring WebHost|  
|[301 - UserDefinedErrorOccurred](../../../../../docs/framework/wcf/diagnostics/etw/301-userdefinederroroccurred.md)|Error|Nom : '%1', Référence : '%2', Charge : %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[302 - UserDefinedWarningOccurred](../../../../../docs/framework/wcf/diagnostics/etw/302-userdefinedwarningoccurred.md)|Warning|Nom : '%1', Référence : '%2', Charge : %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[303 - UserDefinedInformationEventOccured](../../../../../docs/framework/wcf/diagnostics/etw/303-userdefinedinformationeventoccured.md)|Information|Nom : '%1', Référence : '%2', Charge : %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[401- StopSignPostEvent](../../../../../docs/framework/wcf/diagnostics/etw/401-stopsignpostevent.md)|Information|Limite d'activité.|Résolution des problèmes|  
|[402 - StartSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/402-startsignpostevent.md)|Information|Limite d'activité.|Résolution des problèmes|  
|[403 - SuspendSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/403-suspendsignpostevent.md)|Information|Limite d'activité.|Résolution des problèmes|  
|[404 - ResumeSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/404-resumesignpostevent.md)|Information|Limite d'activité.|Résolution des problèmes|  
|[451 - MessageLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/451-messageloginfo.md)|Information|%1|Dépannage, WCFMessageLogging|  
|[452 - MessageLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/452-messagelogwarning.md)|Warning|%1|Dépannage, WCFMessageLogging|  
|[499 - TransferEmitted](../../../../../docs/framework/wcf/diagnostics/etw/499-transferemitted.md)|LogAlways|Événement Transfer émis.|Dépannage, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 - CompilationStart](../../../../../docs/framework/wcf/diagnostics/etw/501-compilationstart.md)|Information|Démarrer la compilation.|WebHost|  
|[502 - CompilationStop](../../../../../docs/framework/wcf/diagnostics/etw/502-compilationstop.md)|Information|Terminez la compilation.|WebHost|  
|[503 - ServiceHostFactoryCreationStart](../../../../../docs/framework/wcf/diagnostics/etw/503-servicehostfactorycreationstart.md)|Information|Début de la création de ServiceHostFactory.|WebHost|  
|[504 - ServiceHostFactoryCreationStop](../../../../../docs/framework/wcf/diagnostics/etw/504-servicehostfactorycreationstop.md)|Information|Fin de la création de ServiceHostFactory.|WebHost|  
|[505 - CreateServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/505-createservicehoststart.md)|Information|Démarrer CreateServiceHost.|WebHost|  
|[506 - CreateServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/506-createservicehoststop.md)|Information|Arrêter CreateServiceHost.|WebHost|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](../../../../../docs/framework/wcf/diagnostics/etw/507-hostedtransportconfigurationmanagerconfiginitstart.md)|Information|Initialisation du début de la configuration HostedTransportConfigurationManager.|WebHost|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](../../../../../docs/framework/wcf/diagnostics/etw/508-hostedtransportconfigurationmanagerconfiginitstop.md)|Information|Initialisation de la fin de la configuration HostedTransportConfigurationManager.|WebHost|  
|[509 - ServiceHostOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/509-servicehostopenstart.md)|Information|Initialisation de la fin de la configuration HostedTransportConfigurationManager.|ServiceHost|  
|[510 - ServiceHostOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/510-servicehostopenstop.md)|Information|Ouverture de ServiceHost terminée.|ServiceHost|  
|[513 - WebHostRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/513-webhostrequeststart.md)|Information|Réception d'une requête avec le chemin d'accès virtuel « %2 » en provenance de l'AppDomain « %1 ».|WebHost|  
|[514 - WebHostRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/514-webhostrequeststop.md)|Information|Arrêt de WebHostRequest.|WebHost|  
|[601 - CBAEntryRead](../../../../../docs/framework/wcf/diagnostics/etw/601-cbaentryread.md)|Détaillé|Adresse relative de l'élément ServiceActivation traitée : « %1 », adresse relative normalisée : « %2 ».||  
|[602 - CBAMatchFound](../../../../../docs/framework/wcf/diagnostics/etw/602-cbamatchfound.md)|Détaillé|La demande entrante correspond à un élément ServiceActivation avec l'adresse « %1 ».||  
|[603 - AspNetRoutingService](../../../../../docs/framework/wcf/diagnostics/etw/603-aspnetroutingservice.md)|Détaillé|La demande entrante correspond à un service WCF défini dans l'itinéraire Asp.Net avec l'adresse %1.|RoutingServices|  
|[604 - AspNetRoute](../../../../../docs/framework/wcf/diagnostics/etw/604-aspnetroute.md)|Détaillé|Un nouvel itinéraire Asp.Net « %1 » avec serviceType « %2 » et serviceHostFactoryType « %3 » est ajouté.|RoutingServices|  
|[605 - IncrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/605-incrementbusycount.md)|Détaillé|IncrementBusyCount appelé. Source : %1|WebHost|  
|[606 - DecrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/606-decrementbusycount.md)|Détaillé|DecrementBusyCount appelé. Source : %1|WebHost|  
|[701 - ServiceChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/701-servicechannelopenstart.md)|Détaillé|ServiceChannelOpen démarré.|WebHost|  
|[702 - ServiceChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/702-servicechannelopenstop.md)|Information|ServiceChannelOpen terminé.|ServiceModel|  
|[703 - ServiceChannelCallStart](../../../../../docs/framework/wcf/diagnostics/etw/703-servicechannelcallstart.md)|Information|ServiceChannelCall démarré.|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](../../../../../docs/framework/wcf/diagnostics/etw/704-servicechannelbegincallstart.md)|Information|Appels asynchrones ServiceChannel démarrés.|ServiceModel|  
|[706 - HttpSendMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/706-httpsendmessagestart.md)|Détaillé|Début de la requête d'envoi HTTP.|HTTP|  
|[707 - HttpSendStop](../../../../../docs/framework/wcf/diagnostics/etw/707-httpsendstop.md)|Détaillé|Arrêt de la requête d'envoi HTTP.|HTTP|  
|[708 - HttpMessageReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/708-httpmessagereceivestart.md)|Détaillé|Message reçu via transport HTTP.|HTTP|  
|[709 - DispatchMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/709-dispatchmessagestart.md)|Information|Distribution des messages démarrée.|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](../../../../../docs/framework/wcf/diagnostics/etw/710-httpcontextbeforeprocessauthentication.md)|Détaillé|Démarrer l'authentification pour la distribution des messages.|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](../../../../../docs/framework/wcf/diagnostics/etw/711-dispatchmessagebeforeauthorization.md)|Détaillé|Démarrer l'autorisation pour la distribution des messages.|ServiceModel|  
|[712 - DispatchMessageStop](../../../../../docs/framework/wcf/diagnostics/etw/712-dispatchmessagestop.md)|Information|Distribution des messages terminée.|ServiceModel|  
|[715 - ClientChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/715-clientchannelopenstart.md)|Information|Début de l'ouverture de ServiceChannel.|ServiceModel|  
|[716 - ClientChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/716-clientchannelopenstop.md)|Information|Arrêt de l'ouverture de ServiceChannel.|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/717-httpsendstreamedmessagestart.md)|Information|Message diffusé en continu par envoi HTTP démarré.|HTTP|  
|[1400 - ChannelInitializationTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1400-channelinitializationtimeout.md)|Error|1%|ServiceModel|  
|[1401 - CloseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1401-closetimeout.md)|Error|1%|ServiceModel|  
|[1402 - IdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1402-idletimeout.md)|Error|Clé de pool de connexion %1 : %2|ServiceModel|  
|[1403 - LeaseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1403-leasetimeout.md)|Information|Clé de pool de connexion %1 : %2|ServiceModel|  
|[1405 - OpenTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1405-opentimeout.md)|Error|%1|ServiceModel|  
|[1406 - ReceiveTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1406-receivetimeout.md)|Error|%1|ServiceModel|  
|[1407 - SendTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1407-sendtimeout.md)|Error|%1|ServiceModel|  
|[1409 - InactivityTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1409-inactivitytimeout.md)|Information|%1|ServiceModel|  
|[1416 - MaxReceivedMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1416-maxreceivedmessagesizeexceeded.md)|Error|%1|Quota|  
|[1417 - MaxSentMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1417-maxsentmessagesizeexceeded.md)|Error|%1|Quota|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1418-maxoutboundconnectionsperendpointexceeded.md)|Information|%1|Quota|  
|[1419 - MaxPendingConnectionsExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1419-maxpendingconnectionsexceeded.md)|Information|%1|Quota|  
|[1420 - ReaderQuotaExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1420-readerquotaexceeded.md)|Error|%1|Quota|  
|[1422 - NegotiateTokenAuthenticatorStateCacheExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Error|%1|Quota|  
|[1423 - NegotiateTokenAuthenticatorStateCacheRatio](../../../../../docs/framework/wcf/diagnostics/etw/1423-negotiatetokenauthenticatorstatecacheratio.md)|Détaillé|Ratio du cache de l'état de l'authentificateur de jetons Negotiate : %1/%2|Quota|  
|[1424 - SecuritySessionRatio](../../../../../docs/framework/wcf/diagnostics/etw/1424-securitysessionratio.md)|Détaillé|Ratio de la session de sécurité : %1/%2|Quota|  
|[1430 - PendingConnectionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1430-pendingconnectionsratio.md)|Détaillé|Ratio des connexions en attente : %1/%2|Quota|  
|[1431 - ConcurrentCallsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1431-concurrentcallsratio.md)|Détaillé|Ratio des sessions simultanées : %1/%2|Quota|  
|[1432 - ConcurrentSessionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1432-concurrentsessionsratio.md)|Détaillé|Ratio des sessions simultanées : %1/%2|Quota|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|Détaillé|Ratio des connexions sortantes par point de terminaison : %1/%2|Quota|  
|[1436 - PendingMessagesPerChannelRatio](../../../../../docs/framework/wcf/diagnostics/etw/1436-pendingmessagesperchannelratio.md)|Détaillé|Ratio des messages en attente par canal : %1/%2|Quota|  
|[1438 - ConcurrentInstancesRatio](../../../../../docs/framework/wcf/diagnostics/etw/1438-concurrentinstancesratio.md)|Détaillé|Ratio des instances simultanées : %1/%2|Quota|  
|[1439 - PendingAcceptsAtZero](../../../../../docs/framework/wcf/diagnostics/etw/1439-pendingacceptsatzero.md)|Information|Aucune acceptation en attente restante|Quota|  
|[1441 - MaxSessionSizeReached](../../../../../docs/framework/wcf/diagnostics/etw/1441-maxsessionsizereached.md)|Warning|1%|Quota|  
|[1442 - ReceiveRetryCountReached](../../../../../docs/framework/wcf/diagnostics/etw/1442-receiveretrycountreached.md)|Warning|Nombre de tentatives de réceptions atteint dans le message MSMQ avec l'ID « %1 »|Quota|  
|[1443 - MaxRetryCyclesExceededMsmq](../../../../../docs/framework/wcf/diagnostics/etw/1443-maxretrycyclesexceededmsmq.md)|Error|Nombre maximal de cycles de tentatives dépassé dans le message MSMQ avec l'ID « %1 »|Quota|  
|[1445 - ReadPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1445-readpoolmiss.md)|Détaillé|Création de « %1 »|Quota|  
|[1446 - WritePoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1446-writepoolmiss.md)|Détaillé|Création de « %1 »|Quota|  
|[1451 - MaxRetryCyclesExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1451-maxretrycyclesexceeded.md)|Error|1%|Quota|  
|[3300 - ReceiveContextCompleteFailed](../../../../../docs/framework/wcf/diagnostics/etw/3300-receivecontextcompletefailed.md)|Warning|Impossible de terminer %1.|Canal|  
|[3301 - ReceiveContextAbandonFailed](../../../../../docs/framework/wcf/diagnostics/etw/3301-receivecontextabandonfailed.md)|Warning|Impossible d'abandonner %1.|Canal|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Warning|Contexte de réception erroné.|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|Information|%1 a été abandonné avec l'exception %2.|Canal|  
|[3305 - ClientBaseCachedChannelFactoryCount](../../../../../docs/framework/wcf/diagnostics/etw/3305-clientbasecachedchannelfactorycount.md)|Information|Le nombre de fabriques de canaux mises en cache est de %1.  Seules «%2 » fabriques de canaux peuvent être mises en cache.|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](../../../../../docs/framework/wcf/diagnostics/etw/3306-clientbasechannelfactoryagedoutofcache.md)|Information|Une fabrique de canaux a été échue du cache, car le cache a atteint sa limite de « %1 ».|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](../../../../../docs/framework/wcf/diagnostics/etw/3307-clientbasechannelfactorycachehit.md)|Information|Une fabrique de canaux correspondante trouvée dans le cache a été utilisée.|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](../../../../../docs/framework/wcf/diagnostics/etw/3308-clientbaseusinglocalchannelfactory.md)|Information|N’utilise pas la fabrique de canaux à partir du cache, c.-à-d. la mise en cache est désactivée pour l’instance.|ServiceModel|  
|[3309 - QueryCompositionExecuted](../../../../../docs/framework/wcf/diagnostics/etw/3309-querycompositionexecuted.md)|Information|La composition de requête à l'aide de « %1 » a été exécutée sur l'URI de requête : « %2 ».|ServiceModel|  
|[3310 - DispatchFailed](../../../../../docs/framework/wcf/diagnostics/etw/3310-dispatchfailed.md)|Error|L'opération « %1 »' a été distribuée avec des erreurs.|ServiceModel|  
|[3311 - DispatchSuccessful](../../../../../docs/framework/wcf/diagnostics/etw/3311-dispatchsuccessful.md)|Information|L'opération « %1 » a été distribuée.|ServiceModel|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Information|Un message d'une taille de « %1 » octets a été lu par l'encodeur.|Canal|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|Information|Un message d'une taille de '%1' octets a été écrit par l'encodeur.|Canal|  
|[3314 - SessionIdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/3314-sessionidletimeout.md)|Error|Abandon de la session du canal inactif de l'URI : « %1 ».|ServiceModel|  
|[3319 - SocketAcceptEnqueued](../../../../../docs/framework/wcf/diagnostics/etw/3319-socketacceptenqueued.md)|Détaillé|Acceptation de la connexion commencée.|TCP|  
|[3320 - SocketAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3320-socketaccepted.md)|Détaillé|ListenerId : %1 a accepté SocketId : %2|TCP|  
|[3321 - ConnectionPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/3321-connectionpoolmiss.md)|Détaillé|Le pool de %1 ne dispose d'aucune connexion disponible et dispose de %2 connexions occupées.|Canal|  
|[3322 - DispatchFormatterDeserializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3322-dispatchformatterdeserializerequeststart.md)|Détaillé|Le répartiteur a démarré la désérialisation du message de requête.|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3323-dispatchformatterdeserializerequeststop.md)|Détaillé|Le répartiteur a terminé la désérialisation du message de requête.|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3324-dispatchformatterserializereplystart.md)|Détaillé|Le répartiteur a démarré la sérialisation du message de réponse.|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3325-dispatchformatterserializereplystop.md)|Détaillé|Le répartiteur a terminé la sérialisation du message de réponse.|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3326-clientformatterserializerequeststart.md)|Détaillé|La sérialisation de la requête du client a démarré.|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3327-clientformatterserializerequeststop.md)|Détaillé|Le client a terminé la sérialisation du message de requête.|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3328-clientformatterdeserializereplystart.md)|Détaillé|Le client a démarré la désérialisation du message de réponse.|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3329-clientformatterdeserializereplystop.md)|Détaillé|Le client a terminé la désérialisation du message de réponse.|ServiceModel|  
|[3330 - SecurityNegotiationStart](../../../../../docs/framework/wcf/diagnostics/etw/3330-securitynegotiationstart.md)|Détaillé|Démarrage de la négociation de sécurité.|Sécurité|  
|[3331 - SecurityNegotiationStop](../../../../../docs/framework/wcf/diagnostics/etw/3331-securitynegotiationstop.md)|Détaillé|Négociation de sécurité terminée.|Sécurité|  
|[3332 - SecurityTokenProviderOpened](../../../../../docs/framework/wcf/diagnostics/etw/3332-securitytokenprovideropened.md)|Détaillé|Ouverture de SecurityTokenProvider terminée.|Sécurité|  
|[3333 - OutgoingMessageSecured](../../../../../docs/framework/wcf/diagnostics/etw/3333-outgoingmessagesecured.md)|Détaillé|Le message sortant a été sécurisé.|Sécurité|  
|[3334 - IncomingMessageVerified](../../../../../docs/framework/wcf/diagnostics/etw/3334-incomingmessageverified.md)|Détaillé|Le message entrant a été vérifié.|ServiceModel de sécurité|  
|[3335 - GetServiceInstanceStart](../../../../../docs/framework/wcf/diagnostics/etw/3335-getserviceinstancestart.md)|Détaillé|Début de la récupération de l'instance de service.|ServiceModel|  
|[3336 - GetServiceInstanceStop](../../../../../docs/framework/wcf/diagnostics/etw/3336-getserviceinstancestop.md)|Détaillé|Instance de service récupérée.|ServiceModel|  
|[3337 - ChannelReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3337-channelreceivestart.md)|Détaillé|ChannelHandlerId : %1 - Début de la boucle de réception du message.|Canal|  
|[3338 - ChannelReceiveStop](../../../../../docs/framework/wcf/diagnostics/etw/3338-channelreceivestop.md)|Détaillé|ChannelHandlerId : %1 - Arrêt de la boucle de réception du message.|Canal|  
|[3339 - ChannelFactoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3339-channelfactorycreated.md)|Détaillé|ChannelFactory créé.|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3340-pipeconnectionacceptstart.md)|Détaillé|Début de l'acceptation de la connexion du canal sur %1.|Canal|  
|[3341 - PipeConnectionAcceptStop](../../../../../docs/framework/wcf/diagnostics/etw/3341-pipeconnectionacceptstop.md)|Détaillé|Connexion du canal acceptée.|Canal|  
|[3342 - EstablishConnectionStart](../../../../../docs/framework/wcf/diagnostics/etw/3342-establishconnectionstart.md)|Détaillé|Début de l'établissement de la connexion pour %1.|Canal|  
|[3343 - EstablishConnectionStop](../../../../../docs/framework/wcf/diagnostics/etw/3343-establishconnectionstop.md)|Détaillé|Connexion établie.|Canal|  
|[3345 - SessionPreambleUnderstood](../../../../../docs/framework/wcf/diagnostics/etw/3345-sessionpreambleunderstood.md)|Détaillé|Préambule de session pour « %1 » compris.|Canal|  
|[3346 - ConnectionReaderSendFault](../../../../../docs/framework/wcf/diagnostics/etw/3346-connectionreadersendfault.md)|Error|Envoi de l'erreur « %1 » par le lecteur de connexion.|Canal|  
|[3347 - SocketAcceptClosed](../../../../../docs/framework/wcf/diagnostics/etw/3347-socketacceptclosed.md)|Détaillé|Acceptation du socket fermée.|TCP|  
|[3348 - ServiceHostFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3348-servicehostfaulted.md)|Critique|L'hôte de service a rencontré une erreur.|TCP|  
|[3349 - ListenerOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/3349-listeneropenstart.md)|Détaillé|Ouverture de l'écouteur pour « %1 ».|Canal|  
|[3350 - ListenerOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/3350-listeneropenstop.md)|Détaillé|Ouverture de l'écouteur terminée.|Canal|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](../../../../../docs/framework/wcf/diagnostics/etw/3351-servermaxpooledconnectionsquotareached.md)|Détaillé|Le quota maximal de connexions regroupées du serveur a été atteint.|Quota|  
|[3352 - TcpConnectionTimedOut](../../../../../docs/framework/wcf/diagnostics/etw/3352-tcpconnectiontimedout.md)|Error|Le SocketId %1 à l'adresse distante %2 a expiré.|TCP|  
|[3353 - TcpConnectionResetError](../../../../../docs/framework/wcf/diagnostics/etw/3353-tcpconnectionreseterror.md)|Warning|Le SocketId %1 à l'adresse distante %2 a rencontré une erreur lors de la réinitialisation de la connexion.|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/3354-servicesecuritynegotiationcompleted.md)|Détaillé|Négociation de sécurité du service terminée.|Sécurité|  
|[3355 - SecurityNegotiationProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3355-securitynegotiationprocessingfailure.md)|Error|Échec du traitement de la négociation de sécurité.|Sécurité|  
|[3356 - SecurityIdentityVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3356-securityidentityverificationsuccess.md)|Détaillé|Vérification de sécurité effectuée.|Sécurité|  
|[3357 - SecurityIdentityVerificationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3357-securityidentityverificationfailure.md)|Error|Échec de la vérification de sécurité.|Sécurité|  
|[3358 - PortSharingDuplicatedSocket](../../../../../docs/framework/wcf/diagnostics/etw/3358-portsharingduplicatedsocket.md)|Détaillé|Socket dupliqué pour %1.|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3359-securityimpersonationsuccess.md)|Détaillé|Emprunt d'identité de sécurité effectué.|Sécurité|  
|[3360 - SecurityImpersonationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3360-securityimpersonationfailure.md)|Warning|Échec de l'emprunt d'identité de sécurité.|Sécurité|  
|[3361 - HttpChannelRequestAborted](../../../../../docs/framework/wcf/diagnostics/etw/3361-httpchannelrequestaborted.md)|Warning|Abandon de la requête de canal HTTP.|HTTP|  
|[3362 - HttpChannelResponseAborted](../../../../../docs/framework/wcf/diagnostics/etw/3362-httpchannelresponseaborted.md)|Warning|Abandon de la réponse de canal HTTP.|HTTP|  
|[3363 - HttpAuthFailed](../../../../../docs/framework/wcf/diagnostics/etw/3363-httpauthfailed.md)|Warning|Échec de l'authentification HTTP.|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/3364-sharedlistenerproxyregisterstart.md)|Détaillé|Début de l'inscription SharedListenerProxy pour l'URI « %1 ».|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](../../../../../docs/framework/wcf/diagnostics/etw/3365-sharedlistenerproxyregisterstop.md)|Détaillé|Arrêt de l'inscription SharedListenerProxy.|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/3366-sharedlistenerproxyregisterfailed.md)|Error|Échec de l'inscription SharedListenerProxy avec l'état « %1 ».|ActivationServices|  
|[3367 - ConnectionPoolPreambleFailed](../../../../../docs/framework/wcf/diagnostics/etw/3367-connectionpoolpreamblefailed.md)|Error|ConnectionPoolPreambleFailed.|Canal|  
|[3368 - SslOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3368-ssloninitiateupgrade.md)|Détaillé|SslOnAcceptUpgradeStart|Sécurité|  
|[3369 - SslOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3369-sslonacceptupgrade.md)|Détaillé|SslOnAcceptUpgradeStop|Sécurité|  
|[3370 - BinaryMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3370-binarymessageencodingstart.md)|Détaillé|BinaryMessageEncoder a démarré l'encodage du message.|Canal|  
|[3371 - MtomMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3371-mtommessageencodingstart.md)|Détaillé|MtomMessageEncoder a démarré l'encodage du message.|Canal|  
|[3372 - TextMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3372-textmessageencodingstart.md)|Détaillé|TextMessageEncoder a démarré l'encodage du message.|Canal|  
|[3373 - BinaryMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3373-binarymessagedecodingstart.md)|Détaillé|BinaryMessageEncoder a démarré le décodage du message.|Canal|  
|[3374 - MtomMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3374-mtommessagedecodingstart.md)|Détaillé|Mtommessageencoder a a démarré le décodage du message.|Canal|  
|[3375 - TextMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3375-textmessagedecodingstart.md)|Détaillé|TextMessageEncoder a démarré le décodage du message.|Canal|  
|[3376 - HttpResponseReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3376-httpresponsereceivestart.md)|Information|Début de la réception d'un message par le transport HTTP.|HTTP|  
|[3377 - SocketReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3377-socketreadstop.md)|Détaillé|L'élément SocketId %1 a lu « %2 » octets à partir de « %3 ».|TCP|  
|[3378 - SocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3378-socketasyncreadstop.md)|Détaillé|L'élément SocketId %1 a lu « %2 » octets à partir de « %3 ».|TCP|  
|[3379 - SocketWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3379-socketwritestart.md)|Détaillé|L'élément SocketId « %1 » a écrit « %2 » octets dans « %3 ».|TCP|  
|[3380 - SocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3380-socketasyncwritestart.md)|Détaillé|L'élément SocketId « %1 » a écrit « %2 » octets dans « %3 ».|TCP|  
|[3381 - SequenceAcknowledgementSent](../../../../../docs/framework/wcf/diagnostics/etw/3381-sequenceacknowledgementsent.md)|Détaillé|Accusé de réception SessionId : %1 envoyé.|Canal|  
|[3382 - ClientReliableSessionReconnect](../../../../../docs/framework/wcf/diagnostics/etw/3382-clientreliablesessionreconnect.md)|Information|SessionId : reconnexion de %1.|Canal|  
|[3383 - ReliableSessionChannelFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3383-reliablesessionchannelfaulted.md)|Information|SessionId %1 a rencontré une erreur.|Canal|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3384-windowsstreamsecurityoninitiateupgrade.md)|Détaillé|Début de la mise à niveau de sécurité par WindowsStreamSecurity.|Sécurité|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3385-windowsstreamsecurityonacceptupgrade.md)|Détaillé|Sécurité Windows relative à la diffusion en continu après acceptation de la mise à niveau.|Sécurité|  
|[3386 - SocketConnectionAbort](../../../../../docs/framework/wcf/diagnostics/etw/3386-socketconnectionabort.md)|Warning|Abandon de SocketId : %1.|TCP|  
|[3388 - HttpGetContextStart](../../../../../docs/framework/wcf/diagnostics/etw/3388-httpgetcontextstart.md)|Détaillé|Début de HttpGetContext.|HTTP|  
|[3389 - ClientSendPreambleStart](../../../../../docs/framework/wcf/diagnostics/etw/3389-clientsendpreamblestart.md)|Détaillé|Début du préambule d'envoi par le client.|Canal|  
|[3390 - ClientSendPreambleStop](../../../../../docs/framework/wcf/diagnostics/etw/3390-clientsendpreamblestop.md)|Détaillé|Arrêt du préambule d'envoi par le client.|Canal|  
|[3391 - HttpMessageReceiveFailed](../../../../../docs/framework/wcf/diagnostics/etw/3391-httpmessagereceivefailed.md)|Warning|Échec de la réception du message HTTP.|HTTP|  
|[3392 - TransactionScopeCreate](../../../../../docs/framework/wcf/diagnostics/etw/3392-transactionscopecreate.md)|Information|TransactionScope est en cours de création avec LocalIdentifier : « %1 » et DistributedIdentifier : « %2 ».|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3393-streamedmessagereadbyencoder.md)|Information|Un message diffusé en continu a été lu par l'encodeur.|Canal|  
|[3394 - StreamedMessageWrittenByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3394-streamedmessagewrittenbyencoder.md)|Information|Un message diffusé en continu a été écrit par l'encodeur.|Canal|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3395-messagewrittenasynchronouslybyencoder.md)|Information|Un message a été écrit de façon asynchrone par l'encodeur.|Canal|  
|[3396 - BufferedAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3396-bufferedasyncwritestart.md)|Information|L'élément BufferId %1 a terminé l'écriture de « %2 » octets dans le flux sous-jacent.|Canal|  
|[3397 - BufferedAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3397-bufferedasyncwritestop.md)|Information|Un message a été écrit de façon asynchrone par l'encodeur.|Canal|  
|[3398 - PipeSharedMemoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3398-pipesharedmemorycreated.md)|Détaillé|Mémoire partagée par les canaux créée à « %1 ».|Canal|  
|[3399 - NamedPipeCreated](../../../../../docs/framework/wcf/diagnostics/etw/3399-namedpipecreated.md)|Détaillé|NamedPipe « %1 » créé.|Canal|  
|[3401 - SignatureVerificationStart](../../../../../docs/framework/wcf/diagnostics/etw/3401-signatureverificationstart.md)|Détaillé|Début de la vérification de la signature.|Sécurité|  
|[3402 - SignatureVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3402-signatureverificationsuccess.md)|Détaillé|Vérification de la signature effectuée.|Sécurité|  
|[3403 - WrappedKeyDecryptionStart](../../../../../docs/framework/wcf/diagnostics/etw/3403-wrappedkeydecryptionstart.md)|Détaillé|Début du déchiffrement de la clé encapsulée.|Sécurité|  
|[3404 - WrappedKeyDecryptionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3404-wrappedkeydecryptionsuccess.md)|Détaillé|Déchiffrement de la clé encapsulée effectué.|Sécurité|  
|[3405 - EncryptedDataProcessingStart](../../../../../docs/framework/wcf/diagnostics/etw/3405-encrypteddataprocessingstart.md)|Détaillé|Début du traitement des données chiffrées.|Sécurité|  
|[3406 - EncryptedDataProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3406-encrypteddataprocessingsuccess.md)|Détaillé|Traitement des données chiffrées terminé.|Sécurité|  
|[3407 - HttpPipelineProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3407-httppipelineprocessinboundrequeststart.md)|Détaillé|Le gestionnaire de messages HTTP a commencé le traitement de la demande entrante.|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3408-httppipelinebeginprocessinboundrequeststart.md)|Détaillé|Le gestionnaire de messages HTTP a démarré le traitement asynchrone de la demande entrante.|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3409-httppipelineprocessinboundrequeststop.md)|Détaillé|Le gestionnaire de messages HTTP a terminé le traitement d'une demande entrante.|HTTP|  
|[3410 - HttpPipelineFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3410-httppipelinefaulted.md)|Warning|Le gestionnaire de messages HTTP est défectueux.|HTTP|  
|[3411 - HttpPipelineTimeoutException](../../../../../docs/framework/wcf/diagnostics/etw/3411-httppipelinetimeoutexception.md)|Error|La connexion WebSocket a expiré.|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3412-httppipelineprocessresponsestart.md)|Détaillé|Le gestionnaire de messages HTTP a démarré le traitement de la réponse.|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3413-httppipelinebeginprocessresponsestart.md)|Détaillé|Le gestionnaire de messages HTTP a démarré le traitement asynchrone de la réponse.|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](../../../../../docs/framework/wcf/diagnostics/etw/3414-httppipelineprocessresponsestop.md)|Détaillé|Le gestionnaire de messages HTTP a terminé le traitement de la réponse.|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](../../../../../docs/framework/wcf/diagnostics/etw/3415-websocketconnectionrequestsendstart.md)|Détaillé|Début de l'envoi de la demande de connexion WebSocket à « %1 ».|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](../../../../../docs/framework/wcf/diagnostics/etw/3416-websocketconnectionrequestsendstop.md)|Détaillé|Demande de connexion à l'élément WebSocketId %1 envoyée.|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3417-websocketconnectionacceptstart.md)|Détaillé|Début de l'acceptation de la connexion à l'élément WebSocket.|HTTP|  
|[3418 - WebSocketConnectionAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3418-websocketconnectionaccepted.md)|Détaillé|La connexion à l'élément WebSocketId %1 est acceptée.|HTTP|  
|[3419 - WebSocketConnectionDeclined](../../../../../docs/framework/wcf/diagnostics/etw/3419-websocketconnectiondeclined.md)|Error|Connexion à l'élément WebSocket refusée avec le code d'état « %1 »|HTTP|  
|[3420 - WebSocketConnectionFailed](../../../../../docs/framework/wcf/diagnostics/etw/3420-websocketconnectionfailed.md)|Error|Échec de la demande de connexion à l'élément WebSocket : « %1 »|HTTP|  
|[3421 - WebSocketConnectionAborted](../../../../../docs/framework/wcf/diagnostics/etw/3421-websocketconnectionaborted.md)|Error|La connexion à l'élément WebSocketId %1 est abandonnée.|HTTP|  
|[3422 - WebSocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3422-websocketasyncwritestart.md)|Détaillé|L'élément WebSocketId %1 a écrit « %2 » octets dans « %3 ».|HTTP|  
|[3423 - WebSocketAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3423-websocketasyncwritestop.md)|Détaillé|Arrêt de l'écriture asynchrone de l'élément WebSocketId %1.|HTTP|  
|[3424 - WebSocketAsyncReadStart](../../../../../docs/framework/wcf/diagnostics/etw/3424-websocketasyncreadstart.md)|Détaillé|Début de lecture de l'élément WebSocketId : %1.|HTTP|  
|[3425 - WebSocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3425-websocketasyncreadstop.md)|Détaillé|L'élément WebSocketId %1 a lu « %2 » octets à partir de « %3 ».|HTTP|  
|[3426 - WebSocketCloseSent](../../../../../docs/framework/wcf/diagnostics/etw/3426-websocketclosesent.md)|Détaillé|L'élément WebSocketId %1 a envoyé un message de fermeture à « %2 » avec l'état de fermeture « %3 ».|HTTP|  
|[3427 - WebSocketCloseOutputSent](../../../../../docs/framework/wcf/diagnostics/etw/3427-websocketcloseoutputsent.md)|Détaillé|L'élément WebSocketId %1 a envoyé un message en sortie de fermeture à « %2 » avec l'état de fermeture « %3 ».|HTTP|  
|[3428 - WebSocketConnectionClosed](../../../../../docs/framework/wcf/diagnostics/etw/3428-websocketconnectionclosed.md)|Détaillé|La connexion à l'élément WebSocketId %1 est fermée.|HTTP|  
|[3429 - WebSocketCloseStatusReceived](../../../../../docs/framework/wcf/diagnostics/etw/3429-websocketclosestatusreceived.md)|Détaillé|Message de fermeture de la connexion à l'élément WebSocketId %1 reçu avec l'état « %2 ».|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](../../../../../docs/framework/wcf/diagnostics/etw/3430-websocketuseversionfromclientwebsocketfactory.md)|Détaillé|Utilisation du WebSocketVersion d'une fabrique WebSocket cliente de type « %1 ».|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](../../../../../docs/framework/wcf/diagnostics/etw/3431-websocketcreateclientwebsocketwithfactory.md)|Détaillé|Création du WebSocket client avec une fabrique de type « %1 ».|HTTP|  
|[3553 - XamlServicesLoadStart](../../../../../docs/framework/wcf/diagnostics/etw/3553-xamlservicesloadstart.md)|Information|Début de XamlServicesLoad|WebHost|  
|[3554 - XamlServicesLoadStop](../../../../../docs/framework/wcf/diagnostics/etw/3554-xamlservicesloadstop.md)|Information|Arrêt de XamlServicesLoad|WebHost|  
|[3555 - CreateWorkflowServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/3555-createworkflowservicehoststart.md)|Information|Début de CreateWorkflowServiceHost|WebHost|  
|[3556 - CreateWorkflowServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/3556-createworkflowservicehoststop.md)|Information|Arrêt de CreateWorkflowServiceHost Stop|WebHost|  
|[3558 - ServiceActivationStart](../../../../../docs/framework/wcf/diagnostics/etw/3558-serviceactivationstart.md)|Information|Démarrage de l'activation du service|WebHost|  
|[3559 - ServiceActivationStop](../../../../../docs/framework/wcf/diagnostics/etw/3559-serviceactivationstop.md)|Information|Arrêt de l'activation du service|WebHost|  
|[3560 - ServiceActivationAvailableMemory](../../../../../docs/framework/wcf/diagnostics/etw/3560-serviceactivationavailablememory.md)|Détaillé|Mémoire disponible (en octets) : %1|Quota|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Information|Le service de routage ferme le client « %1 ».|RoutingServices|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|Warning|Le client de service de routage « %1 » a généré une erreur.|RoutingServices|  
|[3802 - RoutingServiceCompletingOneWay](../../../../../docs/framework/wcf/diagnostics/etw/3802-routingservicecompletingoneway.md)|Information|Fin du message unidirectionnel par le service de routage.|RoutingServices|  
|[3803 - RoutingServiceProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3803-routingserviceprocessingfailure.md)|Error|Échec du service de routage lors du traitement d'un message sur le point de terminaison avec l'adresse « %1 ».|RoutingServices|  
|[3804 - RoutingServiceCreatingClientForEndpoint](../../../../../docs/framework/wcf/diagnostics/etw/3804-routingservicecreatingclientforendpoint.md)|Information|Le service de routage crée un client pour le point de terminaison : « 1% ».|RoutingServices|  
|[3805 - RoutingServiceDisplayConfig](../../../../../docs/framework/wcf/diagnostics/etw/3805-routingservicedisplayconfig.md)|Détaillé|Le service de routage est configuré avec RouteOnHeadersOnly : %1, SoapProcessingEnabled : %2, EnsureOrderedDispatch : %3.|RoutingServices|  
|[3807 - RoutingServiceCompletingTwoWay](../../../../../docs/framework/wcf/diagnostics/etw/3807-routingservicecompletingtwoway.md)|Information|Fin du message de réponse à la demande du service de routage.|RoutingServices|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](../../../../../docs/framework/wcf/diagnostics/etw/3809-routingservicemessageroutedtoendpoints.md)|Détaillé|Message routé avec l'ID : « %1 » routé par le service de routage vers les listes de points de terminaison %2.|RoutingServices|  
|[3810 - RoutingServiceConfigurationApplied](../../../../../docs/framework/wcf/diagnostics/etw/3810-routingserviceconfigurationapplied.md)|Information|Une nouvelle RoutingConfiguration est appliquée au service de routage.|RoutingServices|  
|[3815 - RoutingServiceProcessingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3815-routingserviceprocessingmessage.md)|Information|Le service de routage traite un message avec l’ID : « %1 », action : « %2 », URL entrante : « %3 », Reçu dans la transaction : %4.|RoutingServices|  
|[3816 - RoutingServiceTransmittingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3816-routingservicetransmittingmessage.md)|Information|Le service de routage transmet le message avec l'ID « %1 » [opération %2] à « %3 ».|RoutingServices|  
|[3817 - RoutingServiceCommittingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3817-routingservicecommittingtransaction.md)|Information|Le service de routage valide la transaction avec l’ID « %1 ».|RoutingServices|  
|[3818 - RoutingServiceDuplexCallbackException](../../../../../docs/framework/wcf/diagnostics/etw/3818-routingserviceduplexcallbackexception.md)|Error|Le composant du service de routage %1 a rencontré une exception de rappel duplex.|RoutingServices|  
|[3819 - RoutingServiceMovedToBackup](../../../../../docs/framework/wcf/diagnostics/etw/3819-routingservicemovedtobackup.md)|Information|Message du service de routage avec l'ID %1 [opération %2] déplacé vers le point de terminaison de sauvegarde « %3 ».|RoutingServices|  
|[3820 - RoutingServiceCreatingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3820-routingservicecreatingtransaction.md)|Information|Le service de routage a créé une nouvelle transaction avec l’id « %1 »’ pour le traitement des messages.|RoutingServices|  
|[3821 - RoutingServiceCloseFailed](../../../../../docs/framework/wcf/diagnostics/etw/3821-routingserviceclosefailed.md)|Warning|Échec du service de routage lors de la fermeture du client sortant « %1 ».|RoutingServices|  
|[3822 - RoutingServiceSendingResponse](../../../../../docs/framework/wcf/diagnostics/etw/3822-routingservicesendingresponse.md)|Information|Le service de routage renvoie un message de réponse avec l'action « %1 ».|RoutingServices|  
|[3823 - RoutingServiceSendingFaultResponse](../../../../../docs/framework/wcf/diagnostics/etw/3823-routingservicesendingfaultresponse.md)|Warning|Le service de routage renvoie un message de réponse d'erreur avec l'action « %1 ».|RoutingServices|  
|[3824 - RoutingServiceCompletingReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3824-routingservicecompletingreceivecontext.md)|Détaillé|Le service de routage appelle ReceiveContext.Complete pour le message avec l'ID « %1 ».|RoutingServices|  
|[3825 - RoutingServiceAbandoningReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3825-routingserviceabandoningreceivecontext.md)|Warning|Le service de routage appelle ReceiveContext.Abandon pour le message d'ID : « %1 ».|RoutingServices|  
|[3826 - RoutingServiceUsingExistingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3826-routingserviceusingexistingtransaction.md)|Détaillé|Le service de routage enverra les messages à l’aide de la transaction « %1 » existante.|RoutingServices|  
|[3827 - RoutingServiceTransmitFailed](../../../../../docs/framework/wcf/diagnostics/etw/3827-routingservicetransmitfailed.md)|Warning|Échec du service de routage lors de l'envoi à « %1 ».|RoutingServices|  
|[3828 - RoutingServiceFilterTableMatchStart](../../../../../docs/framework/wcf/diagnostics/etw/3828-routingservicefiltertablematchstart.md)|Information|Début de la correspondance du service de routage MessageFilterTable.|RoutingServices|  
|[3829 - RoutingServiceFilterTableMatchStop](../../../../../docs/framework/wcf/diagnostics/etw/3829-routingservicefiltertablematchstop.md)|Information|Fin de la correspondance du service de routage MessageFilterTable.|RoutingServices|  
|[3830 - RoutingServiceAbortingChannel](../../../../../docs/framework/wcf/diagnostics/etw/3830-routingserviceabortingchannel.md)|Détaillé|Le service de routage appelle un abandon sur le canal : « %1 ».|RoutingServices|  
|[3831 - RoutingServiceHandledException](../../../../../docs/framework/wcf/diagnostics/etw/3831-routingservicehandledexception.md)|Détaillé|Le service de routage a géré une exception.|RoutingServices|  
|[3832 - RoutingServiceTransmitSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/3832-routingservicetransmitsucceeded.md)|Information|Le service de routage a correctement transmis le message avec l'ID « %1 » [opération %2] à « %3 ».|RoutingServices|  
|[4001 - TransportListenerSessionsReceived](../../../../../docs/framework/wcf/diagnostics/etw/4001-transportlistenersessionsreceived.md)|Détaillé|Session de l'écouteur de transport reçue via « %1 »|ActivationServices|  
|[4002 - FailFastException](../../../../../docs/framework/wcf/diagnostics/etw/4002-failfastexception.md)|Critique|FailFastException.|ActivationServices|  
|[4003 - ServiceStartPipeError](../../../../../docs/framework/wcf/diagnostics/etw/4003-servicestartpipeerror.md)|Error|Erreur de canal relative au démarrage du service.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Détaillé|Début de la distribution de sessions.|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|Warning|La distribution de sessions pour « %1 » a échoué, car la file d'attente des sessions en attente contient « %2 » éléments en attente, et est donc pleine.|ActivationServices|  
|[4011 - MessageQueueRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/4011-messagequeueregisterstart.md)|Détaillé|Début de l'inscription à la file d'attente des messages.|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](../../../../../docs/framework/wcf/diagnostics/etw/4012-messagequeueregisterabort.md)|Error|Abandon de l'inscription à la file d'attente des messages avec l'état : « %1 » pour l'URI : « %2 ».|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4013-messagequeueunregistersucceeded.md)|Détaillé|Désinscription de la file d'attente des messages effectuée pour l'URI : « %1 ».|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/4014-messagequeueregisterfailed.md)|Error|Échec de l'inscription à la file d'attente des messages pour l'URI « %1 » avec l'état « %2 ».|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4015-messagequeueregistercompleted.md)|Information|Inscription à la file d'attente des messages terminée pour l'URI « %1 ».|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](../../../../../docs/framework/wcf/diagnostics/etw/4016-messagequeueduplicatedsocketerror.md)|Error|Échec de la duplication de socket par la file d'attente des messages.|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](../../../../../docs/framework/wcf/diagnostics/etw/4019-messagequeueduplicatedsocketcomplete.md)|Détaillé|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4020-tcptransportlistenerlisteningstart.md)|Détaillé|Début de l'écoute de l'URI « %1 » par l'écouteur de transport TCP.|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4021-tcptransportlistenerlisteningstop.md)|Détaillé|Écouteur de transport TCP à l'écoute.|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](../../../../../docs/framework/wcf/diagnostics/etw/4022-webhostunregisterprotocolfailed.md)|Error|Code d'erreur : %1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4023-wasclosealllistenerchannelinstancescompleted.md)|Information|Fermeture de toutes les instances du canal de l'écouteur à l'aide de WAS terminée.|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](../../../../../docs/framework/wcf/diagnostics/etw/4024-wasclosealllistenerchannelinstancesfailed.md)|Error|Code d'erreur : %1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](../../../../../docs/framework/wcf/diagnostics/etw/4025-openlistenerchannelinstancefailed.md)|Error|Code d'erreur : %1|ActivationServices|  
|[4026 - WasConnected](../../../../../docs/framework/wcf/diagnostics/etw/4026-wasconnected.md)|Détaillé|WAS est connecté.|ActivationServices|  
|[4027 - WasDisconnected](../../../../../docs/framework/wcf/diagnostics/etw/4027-wasdisconnected.md)|Détaillé|WAS est déconnecté.|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4028-pipetransportlistenerlisteningstart.md)|Détaillé|Début de l'écoute de l'URI %1 par l'écouteur de transport du canal.|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4029-pipetransportlistenerlisteningstop.md)|Détaillé|Arrêt de l'écoute par l'écouteur de transport du canal.|ActivationServices|  
|[4030 - DispatchSessionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/4030-dispatchsessionsuccess.md)|Information|Distribution de sessions effectuée.|ActivationServices|  
|[4031 - DispatchSessionFailed](../../../../../docs/framework/wcf/diagnostics/etw/4031-dispatchsessionfailed.md)|Error|Échec de la distribution de sessions.|ActivationServices|  
|[4032 - WasConnectionTimedout](../../../../../docs/framework/wcf/diagnostics/etw/4032-wasconnectiontimedout.md)|Critique|Expiration de la connexion WAS.|ActivationServices|  
|[4033 - RoutingTableLookupStart](../../../../../docs/framework/wcf/diagnostics/etw/4033-routingtablelookupstart.md)|Détaillé|Début de la recherche dans la table de routage.|ActivationServices|  
|[4034 - RoutingTableLookupStop](../../../../../docs/framework/wcf/diagnostics/etw/4034-routingtablelookupstop.md)|Détaillé|Recherche dans la table de routage terminée.|ActivationServices|  
|[4035 - PendingSessionQueueRatio](../../../../../docs/framework/wcf/diagnostics/etw/4035-pendingsessionqueueratio.md)|Détaillé|Ratio des files d'attente des sessions en attente : %1/%2|Quota|  
|[4600 - MessageLogEventSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/4600-messagelogeventsizeexceeded.md)|Warning|Impossible de journaliser le message, car il dépasse la taille des événements ETW|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](../../../../../docs/framework/wcf/diagnostics/etw/4801-discoveryclientinclientchannelfailedtoclose.md)|Warning|Le DiscoveryClient créé dans DiscoveryClientChannel n'a pas pu se fermer et a par conséquent été abandonné.|découverte,|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](../../../../../docs/framework/wcf/diagnostics/etw/4802-discoveryclientprotocolexceptionsuppressed.md)|Information|ProtocolException a été supprimé lors de la fermeture de DiscoveryClient. Cela peut être dû à un DiscoveryService qui tente encore d'envoyer une réponse à DiscoveryClient.|découverte,|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](../../../../../docs/framework/wcf/diagnostics/etw/4803-discoveryclientreceivedmulticastsuppression.md)|Information|DiscoveryClient a reçu un message de suppression multidiffusion d'un DiscoveryProxy.|découverte,|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4804-discoverymessagereceivedafteroperationcompleted.md)|Information|Un message %1 avec messageId='%2' a été déposé par DiscoveryClient car l’opération correspondante %3 est terminée.|découverte,|  
|[4805 - DiscoveryMessageWithInvalidContent](../../../../../docs/framework/wcf/diagnostics/etw/4805-discoverymessagewithinvalidcontent.md)|Warning|Un message %1 avec messageId='%2' a été déposé, car son contenu n’était pas valide.|découverte,|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Warning|Un message %1 avec messageId='%2' et relatesTo='%3' a été supprimé par DiscoveryClient, car l'opération correspondante %4 est terminée ou la valeur relatesTo n'est pas valide.|découverte,|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4807-discoverymessagewithinvalidreplyto.md)|Warning|Un message de demande de découverte avec messageId='%1' a été supprimé, car son adresse de réponse ReplyTo n’était pas valide.|découverte,|  
|[4808 - DiscoveryMessageWithNoContent](../../../../../docs/framework/wcf/diagnostics/etw/4808-discoverymessagewithnocontent.md)|Warning|Un message %1 a été supprimé, car il n’avait aucun contenu.|découverte,|  
|[4809 - DiscoveryMessageWithNullMessageId](../../../../../docs/framework/wcf/diagnostics/etw/4809-discoverymessagewithnullmessageid.md)|Warning|Un message %1 a été supprimé car son en-tête ne contenait pas la propriété MessageId requise.|découverte,|  
|[4810 - DiscoveryMessageWithNullMessageSequence](../../../../../docs/framework/wcf/diagnostics/etw/4810-discoverymessagewithnullmessagesequence.md)|Warning|Un message %1 avec messageId='%2' a été supprimé par DiscoveryClient, car il n'avait pas la propriété DiscoveryMessageSequence.|découverte,|  
|[4811 - DiscoveryMessageWithNullRelatesTo](../../../../../docs/framework/wcf/diagnostics/etw/4811-discoverymessagewithnullrelatesto.md)|Warning|Un message %1 avec messageId='%2' a été supprimé par DiscoveryClient, car son en-tête ne contenait pas la propriété RelatesTo requise.|découverte,|  
|[4812 - DiscoveryMessageWithNullReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4812-discoverymessagewithnullreplyto.md)|Warning|Un message de demande de découverte avec messageId='%1' a été supprimé, car il n'avait pas d'adresse de réponse ReplyTo.|découverte,|  
|[4813 - DuplicateDiscoveryMessage](../../../../../docs/framework/wcf/diagnostics/etw/4813-duplicatediscoverymessage.md)|Warning|Un message %1 avec messageId='%2' a été supprimé, car il s'agissait d'un doublon.|découverte,|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Information|La fonctionnalité de découverte du point de terminaison avec EndpointAddress='%1' et ListenUri='%2' a été désactivée.|découverte,|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|Information|La fonctionnalité de découverte du point de terminaison avec EndpointAddress='%1' et ListenUri='%2' a été activée.|découverte,|  
|[4816 - FindInitiatedInDiscoveryClientChannel](../../../../../docs/framework/wcf/diagnostics/etw/4816-findinitiatedindiscoveryclientchannel.md)|Détaillé|Une opération Find a été initiée dans DiscoveryClientChannel pour découvrir des points de terminaison.|découverte,|  
|[4817 - InnerChannelCreationFailed](../../../../../docs/framework/wcf/diagnostics/etw/4817-innerchannelcreationfailed.md)|Warning|DiscoveryClientChannel n'a pas pu créer le canal avec un point de terminaison découvert avec EndpointAddress='%1' et Via='%2'. DiscoveryClientChannel va tenter d'utiliser le prochain point de terminaison découvert disponible.|découverte,|  
|[4818 - InnerChannelOpenFailed](../../../../../docs/framework/wcf/diagnostics/etw/4818-innerchannelopenfailed.md)|Warning|DiscoveryClientChannel n'a pas pu ouvrir le canal avec un point de terminaison découvert avec EndpointAddress='%1' et Via='%2'. DiscoveryClientChannel va tenter d'utiliser le prochain point de terminaison découvert disponible.|découverte,|  
|[4819 - InnerChannelOpenSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4819-innerchannelopensucceeded.md)|Information|DiscoveryClientChannel a correctement découvert un point de terminaison et ouvert le canal qui l'utilise. Le client est connecté à un service utilisant EndpointAddress='%1' et Via='%2'.|découverte,|  
|[4820 - SynchronizationContextReset](../../../../../docs/framework/wcf/diagnostics/etw/4820-synchronizationcontextreset.md)|Information|DiscoveryClientChannel a rétabli la valeur d'origine %1 de SynchronizationContext.|découverte,|  
|[4821 - SynchronizationContextSetToNull](../../../../../docs/framework/wcf/diagnostics/etw/4821-synchronizationcontextsettonull.md)|Information|DiscoveryClientChannel a attribué à SynchronizationContext la valeur Null avant le lancement de l’opération Find.|découverte,|  
|[5001 - DCSerializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5001-dcserializewithsurrogatestart.md)|Détaillé|Début de la sérialisation de %1 par DataContract avec substituts.|Sérialisation|  
|[5002 - DCSerializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5002-dcserializewithsurrogatestop.md)|Détaillé|Arrêt de la sérialisation DataContract avec substituts.|Sérialisation|  
|[5003 - DCDeserializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5003-dcdeserializewithsurrogatestart.md)|Détaillé|Début de la désérialisation de %1 par DataContract avec substituts.|Sérialisation|  
|[5004 - DCDeserializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5004-dcdeserializewithsurrogatestop.md)|Détaillé|Arrêt de la désérialisation DataContract avec substituts.|Sérialisation|  
|[5005 - ImportKnownTypesStart](../../../../../docs/framework/wcf/diagnostics/etw/5005-importknowntypesstart.md)|Détaillé|Démarrage des ImportKnownTypes.|Sérialisation|  
|[5006 - ImportKnownTypesStop](../../../../../docs/framework/wcf/diagnostics/etw/5006-importknowntypesstop.md)|Détaillé|Arrêt des ImportKnownTypes.|Sérialisation|  
|[5007 - DCResolverResolve](../../../../../docs/framework/wcf/diagnostics/etw/5007-dcresolverresolve.md)|Détaillé|Début de la résolution de %1 par le programme de résolution DataContract.|Sérialisation|  
|[5008 - DCGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5008-dcgenwriterstart.md)|Détaillé|Début de la génération de l'enregistreur %1 par DataContract pour %2.|Sérialisation|  
|[5009 - DCGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5009-dcgenwriterstop.md)|Détaillé|Arrêt de la génération de l'enregistreur par DataContract.|Sérialisation|  
|[5010 - DCGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5010-dcgenreaderstart.md)|Détaillé|Début de la génération du lecteur %1 par DataContract pour %2.|Sérialisation|  
|[5011 - DCGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5011-dcgenreaderstop.md)|Détaillé|Arrêt de la génération par DataContract.|Sérialisation|  
|[5012 - DCJsonGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5012-dcjsongenreaderstart.md)|Détaillé|Début de la génération du lecteur %1 par JSON pour %2.|Sérialisation|  
|[5013 - DCJsonGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5013-dcjsongenreaderstop.md)|Détaillé|Arrêt de la génération du lecteur par JSON.|Sérialisation|  
|[5014 - DCJsonGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5014-dcjsongenwriterstart.md)|Détaillé|Début de la génération de l'enregistreur %1 par JSON pour %2.|Sérialisation|  
|[5015 - DCJsonGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5015-dcjsongenwriterstop.md)|Détaillé|Arrêt de la génération de l'enregistreur par JSON.|Sérialisation|  
|[5016 - GenXmlSerializableStart](../../../../../docs/framework/wcf/diagnostics/etw/5016-genxmlserializablestart.md)|Détaillé|Début de la génération sérialisable xml pour « %1 ».|Sérialisation|  
|[5017 - GenXmlSerializableStop](../../../../../docs/framework/wcf/diagnostics/etw/5017-genxmlserializablestop.md)|Détaillé|Arrêt de la génération sérialisable xml.|Sérialisation|  
|[5203 - JsonMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5203-jsonmessagedecodingstart.md)|Détaillé|JsonMessageEncoder a démarré le décodage du message.|Canal|  
|[5204 - JsonMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5204-jsonmessageencodingstart.md)|Détaillé|JsonMessageEncoder a démarré le codage du message.|Canal|  
|[5402 - TokenValidationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5402-tokenvalidationstarted.md)|Détaillé|Début de la validation de SecurityToken (type « %1 » et ID « %2 »).|Sécurité|  
|[5403 - TokenValidationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5403-tokenvalidationsuccess.md)|Détaillé|Validation de SecurityToken (type « %1 » et ID « %2 ») effectuée.|Sécurité|  
|[5404 - TokenValidationFailure](../../../../../docs/framework/wcf/diagnostics/etw/5404-tokenvalidationfailure.md)|Error|Échec de la validation de SecurityToken (type « %1 » et ID « %2 »). %3|Sécurité|  
|[5405 - GetIssuerNameSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5405-getissuernamesuccess.md)|Détaillé|Récupération du nom de l'émetteur %1 à partir de tokenId %2 effectuée.|Sécurité|  
|[5406 - GetIssuerNameFailure](../../../../../docs/framework/wcf/diagnostics/etw/5406-getissuernamefailure.md)|Error|Échec de la récupération du nom de l'émetteur à partir de tokenId : %1.|Sécurité|  
|[5600 - FederationMessageProcessingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5600-federationmessageprocessingstarted.md)|Détaillé|Début du traitement du message de fédération.|Sécurité|  
|[5601 - FederationMessageProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5601-federationmessageprocessingsuccess.md)|Détaillé|Traitement du message de fédération effectué.|Sécurité|  
|[5602 - FederationMessageCreationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5602-federationmessagecreationstarted.md)|Détaillé|Début de la création d'un message de fédération à partir de la publication de formulaire.|Sécurité|  
|[5603 - FederationMessageCreationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5603-federationmessagecreationsuccess.md)|Détaillé|Création d'un message de fédération à partir de la publication de formulaire effectuée.|Sécurité|  
|[5604 - SessionCookieReadingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5604-sessioncookiereadingstarted.md)|Détaillé|Début de la lecture du jeton de session à partir du cookie de session.|Sécurité|  
|[5605 - SessionCookieReadingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5605-sessioncookiereadingsuccess.md)|Détaillé|Lecture du jeton de session à partir du cookie de session effectuée.|Sécurité|  
|[5606 - PrincipalSettingFromSessionTokenStarted](../../../../../docs/framework/wcf/diagnostics/etw/5606-principalsettingfromsessiontokenstarted.md)|Détaillé|Début du paramétrage du principal à partir du jeton de session.|Sécurité|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5607-principalsettingfromsessiontokensuccess.md)|Détaillé|Paramétrage du principal à partir du jeton de session effectué.|Sécurité|  
|[57393 - AppDomainUnload](../../../../../docs/framework/wcf/diagnostics/etw/57393-appdomainunload.md)|Information|Déchargement d'AppDomain. AppDomain.FriendlyName %1, ProcessName %2, ProcessId %3.|Infrastructure|  
|[57394 - HandledException](../../../../../docs/framework/wcf/diagnostics/etw/57394-handledexception.md)|Information|Traitement d'une exception.|Infrastructure|  
|[57395 - ShipAssertExceptionMessage](../../../../../docs/framework/wcf/diagnostics/etw/57395-shipassertexceptionmessage.md)|Error|Une erreur inattendue s'est produite. Les applications ne doivent pas essayer de gérer cette erreur. À des fins de diagnostic, ce message en anglais est associé à l'échec : %1.|Infrastructure|  
|[57396 - ThrowingException](../../../../../docs/framework/wcf/diagnostics/etw/57396-throwingexception.md)|Warning|Levée d'une exception. Source : %1.|Infrastructure|  
|[57397 - UnhandledException](../../../../../docs/framework/wcf/diagnostics/etw/57397-unhandledexception.md)|Critique|Exception non gérée.|Infrastructure|  
|[57399 - TraceCodeEventLogCritical](../../../../../docs/framework/wcf/diagnostics/etw/57399-tracecodeeventlogcritical.md)|Critique|Écriture dans le journal d'événements.|Infrastructure|  
|[57400 - TraceCodeEventLogError](../../../../../docs/framework/wcf/diagnostics/etw/57400-tracecodeeventlogerror.md)|Error|Écriture dans le journal d'événements.|Infrastructure|  
|[57401 - TraceCodeEventLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/57401-tracecodeeventloginfo.md)|Information|Écriture dans le journal d'événements.|Infrastructure|  
|[57402 - TraceCodeEventLogVerbose](../../../../../docs/framework/wcf/diagnostics/etw/57402-tracecodeeventlogverbose.md)|Détaillé|Écriture dans le journal d'événements.|Infrastructure|  
|[57403 - TraceCodeEventLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/57403-tracecodeeventlogwarning.md)|Warning|Écriture dans le journal d'événements.|Infrastructure|  
|[57404 - HandledExceptionWarning](../../../../../docs/framework/wcf/diagnostics/etw/57404-handledexceptionwarning.md)|Warning|Traitement d'une exception.|Infrastructure|  
|[62326 - HttpHandlerPickedForUrl](../../../../../docs/framework/wcf/diagnostics/etw/62326-httphandlerpickedforurl.md)|Information|L'URL « %1 » héberge un document XAML avec le type d'élément racine « %2 ». Le type de gestionnaire HTTP « %3 » est sélectionné pour traiter toutes les requêtes adressées à cette URL.|WebHost|
