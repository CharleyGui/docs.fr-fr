---
title: Référence d'événement de trace analytique
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: 28ae252d562b57df0553f0fd4370845e836ef537
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254842"
---
# <a name="analytic-trace-event-reference"></a>Référence d'événement de trace analytique

Le tableau suivant définit les niveaux d’événements, les identificateurs et les messages associés au suivi analytique WCF.  
  
## <a name="event-reference"></a>Référence d'événement  
  
|ID de l’événement|Niveau d'événement|Message d'événement.|Mots clés|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](131-bufferpoolallocation.md)|Commentaires|Le pool est en train d'allouer %1 octets.|Infrastructure|  
|[132 - BufferPoolChangeQuota](132-bufferpoolchangequota.md)|Commentaires|BufferPool de taille %1, modification du quota par %2.|Infrastructure|  
|[133 - ActionItemScheduled](133-actionitemscheduled.md)|Commentaires|Rappel du planificateur de threads d'E/S invoqué.|Infrastructure|  
|[134 - ActionItemCallbackInvoked](134-actionitemcallbackinvoked.md)|Commentaires|Rappel du planificateur de threads d'E/S invoqué.|Infrastructure|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](201-clientmessageinspectorafterreceiveinvoked.md)|Informations|Le répartiteur a appelé 'AfterReceiveReply' sur un ClientMessageInspector de type '%1.'|Dépannage, ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](202-clientmessageinspectorbeforesendinvoked.md)|Informations|Le répartiteur a appelé « BeforeSendRequest » sur un ClientMessageInspector de type « %1 ».|Dépannage, ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](203-clientparameterinspectoraftercallinvoked.md)|Informations|Le répartiteur a appelé « AfterCall » sur un ClientParameterInspector. de type « %1 ».|Dépannage, ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](204-clientparameterinspectorbeforecallinvoked.md)|Informations|Le répartiteur a appelé 'BeforeCall' sur un ClientParameterInspector de type '%1.'|Dépannage, ServiceModel|  
|[205 - OperationInvoked](205-operationinvoked.md)|Informations|Un OperationInvoker a appelé la méthode '%1'.|EndToEndMonitoring, Dépannage, ServiceModel|  
|[206 - ErrorHandlerInvoked](206-errorhandlerinvoked.md)|Informations|Le répartiteur a appelé un ErrorHandler de type '%1' avec une exception de type '%3'.  ErrorHandled == '%2.'|Dépannage, ServiceModel|  
|[207 - FaultProviderInvoked](207-faultproviderinvoked.md)|Informations|Le répartiteur a appelé un FaultProvider de type '%1' avec une exception de type '%2.'|Dépannage, ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](208-messageinspectorafterreceiveinvoked.md)|Informations|Le répartiteur a appelé 'AfterReceiveReply' sur un MessageInspector de type '%1'.|Dépannage, ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](209-messageinspectorbeforesendinvoked.md)|Informations|Le répartiteur a appelé 'BeforeSendRequest' sur un MessageInspector de type '%1'.|Dépannage, ServiceModel|  
|[210 - MessageThrottleExceeded](210-messagethrottleexceeded.md)|Avertissement|La valeur '%1' de la limitation '%2' a été atteinte.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[211 - ParameterInspectorAfterCallInvoked](211-parameterinspectoraftercallinvoked.md)|Informations|Le répartiteur a appelé 'AfterCall' sur un ParameterInspector de type '%1'.|Dépannage, ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](212-parameterinspectorbeforecallinvoked.md)|Informations|Le répartiteur a appelé 'BeforeCall' sur un ParameterInspector de type '%1.'|Dépannage, ServiceModel|  
|[213 - ServiceHostStarted](213-servicehoststarted.md)|LogAlways|ServiceHost a démarré : '%1'.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[214 - OperationCompleted](214-operationcompleted.md)|Informations|OperationInvoker a terminé l'appel de la méthode '%1'.  Durée de l'appel de méthode : '%2' ms.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[215 - MessageReceivedByTransport](215-messagereceivedbytransport.md)|Informations|Le transport a reçu un message de '%1'.|Dépannage, ServiceModel|  
|[216 - MessageSentByTransport](216-messagesentbytransport.md)|Informations|Le transport a envoyé un message à '%1.'|Dépannage, ServiceModel|  
|[217 - ClientOperationPrepared](217-clientoperationprepared.md)|Informations|Le client exécute l'opération '%1' définie dans le contrat '%2'. Le message sera envoyé à '%3'.|Dépannage, ServiceModel|  
|[218 - ClientOperationCompleted](218-clientoperationcompleted.md)|Informations|Le client a terminé l'exécution de l'opération '%1' définie dans le contrat '%2'. Le message a été envoyé à '%3'.|Dépannage, ServiceModel|  
|[219 - ServiceException](219-serviceexception.md)|Error|Une exception non gérée de type '%2' s'est produite lors du traitement du message.  Exception totale ToString : %1.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[220 - MessageSentToTransport](220-messagesenttotransport.md)|Informations|Le répartiteur a envoyé un message au transport. ID de corrélation == '%1.'|EndToEndMonitoring, Dépannage, ServiceModel|  
|[221 - MessageReceivedFromTransport](221-messagereceivedfromtransport.md)|Informations|Le répartiteur a reçu un message du transport. ID de corrélation == '%1.'|EndToEndMonitoring, Dépannage, ServiceModel|  
|[222 - OperationFailed](222-operationfailed.md)|Avertissement|La méthode '%1' a levé une exception non gérée lors de l'appel effectué par l'OperationInvoker. Durée de l'appel de méthode : '%2' ms.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[223 - OperationFaulted](223-operationfaulted.md)|Avertissement|La méthode '%1' a levé un FaultException lors de l'appel effectué par l'OperationInvoker. Durée de l'appel de méthode : '%2' ms.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[224 - MessageThrottleAtSeventyPercent](224-messagethrottleatseventypercent.md)|Avertissement|La valeur de la limitation '%1' de '%2' est à 70%.|HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[226 - IdleServicesClosed](226-idleservicesclosed.md)|LogAlways|%1 services inactifs sur un total de %2 services activés ont été fermés.|HealthMonitoring WebHost|  
|[301 - UserDefinedErrorOccurred](301-userdefinederroroccurred.md)|Error|Nom : '%1', Référence : '%2', Charge : %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[302 - UserDefinedWarningOccurred](302-userdefinedwarningoccurred.md)|Avertissement|Nom : '%1', Référence : '%2', Charge : %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[303 - UserDefinedInformationEventOccured](303-userdefinedinformationeventoccured.md)|Informations|Nom : '%1', Référence : '%2', Charge : %3.|UserEvents, HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel|  
|[401 - StopSignPostEvent](401-stopsignpostevent.md)|Informations|Limite d'activité.|Dépannage|  
|[402 - StartSignpostEvent](402-startsignpostevent.md)|Informations|Limite d'activité.|Dépannage|  
|[403 - SuspendSignpostEvent](403-suspendsignpostevent.md)|Informations|Limite d'activité.|Dépannage|  
|[404 - ResumeSignpostEvent](404-resumesignpostevent.md)|Informations|Limite d'activité.|Dépannage|  
|[451 - MessageLogInfo](451-messageloginfo.md)|Informations|%1|Dépannage, WCFMessageLogging|  
|[452 - MessageLogWarning](452-messagelogwarning.md)|Avertissement|%1|Dépannage, WCFMessageLogging|  
|[499 - TransferEmitted](499-transferemitted.md)|LogAlways|Événement Transfer émis.|Dépannage, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging|  
|[501 - CompilationStart](501-compilationstart.md)|Informations|Démarrer la compilation.|WebHost|  
|[502 - CompilationStop](502-compilationstop.md)|Informations|Terminez la compilation.|WebHost|  
|[503 - ServiceHostFactoryCreationStart](503-servicehostfactorycreationstart.md)|Informations|Début de la création de ServiceHostFactory.|WebHost|  
|[504 - ServiceHostFactoryCreationStop](504-servicehostfactorycreationstop.md)|Informations|Fin de la création de ServiceHostFactory.|WebHost|  
|[505 - CreateServiceHostStart](505-createservicehoststart.md)|Informations|Démarrer CreateServiceHost.|WebHost|  
|[506 - CreateServiceHostStop](506-createservicehoststop.md)|Informations|Arrêter CreateServiceHost.|WebHost|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](507-hostedtransportconfigurationmanagerconfiginitstart.md)|Informations|Initialisation du début de la configuration HostedTransportConfigurationManager.|WebHost|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](508-hostedtransportconfigurationmanagerconfiginitstop.md)|Informations|Initialisation de la fin de la configuration HostedTransportConfigurationManager.|WebHost|  
|[509 - ServiceHostOpenStart](509-servicehostopenstart.md)|Informations|Initialisation de la fin de la configuration HostedTransportConfigurationManager.|ServiceHost|  
|[510 - ServiceHostOpenStop](510-servicehostopenstop.md)|Informations|Ouverture de ServiceHost terminée.|ServiceHost|  
|[513 - WebHostRequestStart](513-webhostrequeststart.md)|Informations|Réception d'une requête avec le chemin d'accès virtuel « %2 » en provenance de l'AppDomain « %1 ».|WebHost|  
|[514 - WebHostRequestStop](514-webhostrequeststop.md)|Informations|Arrêt de WebHostRequest.|WebHost|  
|[601 - CBAEntryRead](601-cbaentryread.md)|Commentaires|Adresse relative de l'élément ServiceActivation traitée : « %1 », adresse relative normalisée : « %2 ».||  
|[602 - CBAMatchFound](602-cbamatchfound.md)|Commentaires|La demande entrante correspond à un élément ServiceActivation avec l'adresse « %1 ».||  
|[603 - AspNetRoutingService](603-aspnetroutingservice.md)|Commentaires|La demande entrante correspond à un service WCF défini dans ASP.NET route avec l’adresse %1.|RoutingServices|  
|[604 - AspNetRoute](604-aspnetroute.md)|Commentaires|Un nouvel itinéraire ASP.NET « %1 » avec serviceType « %2 » et serviceHostFactoryType « %3 » est ajouté.|RoutingServices|  
|[605 - IncrementBusyCount](605-incrementbusycount.md)|Commentaires|IncrementBusyCount appelé. Source : %1|WebHost|  
|[606 - DecrementBusyCount](606-decrementbusycount.md)|Commentaires|DecrementBusyCount appelé. Source : %1|WebHost|  
|[701 - ServiceChannelOpenStart](701-servicechannelopenstart.md)|Commentaires|ServiceChannelOpen démarré.|WebHost|  
|[702 - ServiceChannelOpenStop](702-servicechannelopenstop.md)|Informations|ServiceChannelOpen terminé.|ServiceModel|  
|[703 - ServiceChannelCallStart](703-servicechannelcallstart.md)|Informations|ServiceChannelCall démarré.|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](704-servicechannelbegincallstart.md)|Informations|Appels asynchrones ServiceChannel démarrés.|ServiceModel|  
|[706 - HttpSendMessageStart](706-httpsendmessagestart.md)|Commentaires|Début de la requête d'envoi HTTP.|HTTP|  
|[707 - HttpSendStop](707-httpsendstop.md)|Commentaires|Arrêt de la requête d'envoi HTTP.|HTTP|  
|[708 - HttpMessageReceiveStart](708-httpmessagereceivestart.md)|Commentaires|Message reçu via transport HTTP.|HTTP|  
|[709 - DispatchMessageStart](709-dispatchmessagestart.md)|Informations|Distribution des messages démarrée.|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](710-httpcontextbeforeprocessauthentication.md)|Commentaires|Démarrer l'authentification pour la distribution des messages.|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](711-dispatchmessagebeforeauthorization.md)|Commentaires|Démarrer l'autorisation pour la distribution des messages.|ServiceModel|  
|[712 - DispatchMessageStop](712-dispatchmessagestop.md)|Informations|Distribution des messages terminée.|ServiceModel|  
|[715 - ClientChannelOpenStart](715-clientchannelopenstart.md)|Informations|Début de l'ouverture de ServiceChannel.|ServiceModel|  
|[716 - ClientChannelOpenStop](716-clientchannelopenstop.md)|Informations|Arrêt de l'ouverture de ServiceChannel.|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](717-httpsendstreamedmessagestart.md)|Informations|Message diffusé en continu par envoi HTTP démarré.|HTTP|  
|[1400 - ChannelInitializationTimeout](1400-channelinitializationtimeout.md)|Error|1%|ServiceModel|  
|[1401 - CloseTimeout](1401-closetimeout.md)|Error|1%|ServiceModel|  
|[1402 - IdleTimeout](1402-idletimeout.md)|Error|Clé de pool de connexion %1 : %2|ServiceModel|  
|[1403 - LeaseTimeout](1403-leasetimeout.md)|Informations|Clé de pool de connexion %1 : %2|ServiceModel|  
|[1405 - OpenTimeout](1405-opentimeout.md)|Error|%1|ServiceModel|  
|[1406 - ReceiveTimeout](1406-receivetimeout.md)|Error|%1|ServiceModel|  
|[1407 - SendTimeout](1407-sendtimeout.md)|Error|%1|ServiceModel|  
|[1409 - InactivityTimeout](1409-inactivitytimeout.md)|Informations|%1|ServiceModel|  
|[1416 - MaxReceivedMessageSizeExceeded](1416-maxreceivedmessagesizeexceeded.md)|Error|%1|Quota|  
|[1417 - MaxSentMessageSizeExceeded](1417-maxsentmessagesizeexceeded.md)|Error|%1|Quota|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](1418-maxoutboundconnectionsperendpointexceeded.md)|Informations|%1|Quota|  
|[1419 - MaxPendingConnectionsExceeded](1419-maxpendingconnectionsexceeded.md)|Informations|%1|Quota|  
|[1420 - ReaderQuotaExceeded](1420-readerquotaexceeded.md)|Error|%1|Quota|  
|[1422 - NegotiateTokenAuthenticatorStateCacheExceeded](1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Error|%1|Quota|  
|[1423 - NegotiateTokenAuthenticatorStateCacheRatio](1423-negotiatetokenauthenticatorstatecacheratio.md)|Commentaires|Ratio du cache de l'état de l'authentificateur de jetons Negotiate : %1/%2|Quota|  
|[1424 - SecuritySessionRatio](1424-securitysessionratio.md)|Commentaires|Ratio de la session de sécurité : %1/%2|Quota|  
|[1430 - PendingConnectionsRatio](1430-pendingconnectionsratio.md)|Commentaires|Ratio des connexions en attente : %1/%2|Quota|  
|[1431 - ConcurrentCallsRatio](1431-concurrentcallsratio.md)|Commentaires|Ratio des sessions simultanées : %1/%2|Quota|  
|[1432 - ConcurrentSessionsRatio](1432-concurrentsessionsratio.md)|Commentaires|Ratio des sessions simultanées : %1/%2|Quota|  
|[1433 - OutboundConnectionsPerEndpointRatio](1433-outboundconnectionsperendpointratio.md)|Commentaires|Ratio des connexions sortantes par point de terminaison : %1/%2|Quota|  
|[1436 - PendingMessagesPerChannelRatio](1436-pendingmessagesperchannelratio.md)|Commentaires|Ratio des messages en attente par canal : %1/%2|Quota|  
|[1438 - ConcurrentInstancesRatio](1438-concurrentinstancesratio.md)|Commentaires|Ratio des instances simultanées : %1/%2|Quota|  
|[1439 - PendingAcceptsAtZero](1439-pendingacceptsatzero.md)|Informations|Aucune acceptation en attente restante|Quota|  
|[1441 - MaxSessionSizeReached](1441-maxsessionsizereached.md)|Avertissement|1%|Quota|  
|[1442 - ReceiveRetryCountReached](1442-receiveretrycountreached.md)|Avertissement|Nombre de tentatives de réceptions atteint dans le message MSMQ avec l'ID « %1 »|Quota|  
|[1443 - MaxRetryCyclesExceededMsmq](1443-maxretrycyclesexceededmsmq.md)|Error|Nombre maximal de cycles de tentatives dépassé dans le message MSMQ avec l'ID « %1 »|Quota|  
|[1445 - ReadPoolMiss](1445-readpoolmiss.md)|Commentaires|Création de « %1 »|Quota|  
|[1446 - WritePoolMiss](1446-writepoolmiss.md)|Commentaires|Création de « %1 »|Quota|  
|[1451 - MaxRetryCyclesExceeded](1451-maxretrycyclesexceeded.md)|Error|1%|Quota|  
|[3300 - ReceiveContextCompleteFailed](3300-receivecontextcompletefailed.md)|Avertissement|Impossible de terminer %1.|Channel|  
|[3301 - ReceiveContextAbandonFailed](3301-receivecontextabandonfailed.md)|Avertissement|Impossible d'abandonner %1.|Channel|  
|[3303 - ReceiveContextAbandonWithException](3303-receivecontextabandonwithexception.md)|Avertissement|Contexte de réception erroné.|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](3303-receivecontextabandonwithexception.md)|Informations|%1 a été abandonné avec l'exception %2.|Channel|  
|[3305 - ClientBaseCachedChannelFactoryCount](3305-clientbasecachedchannelfactorycount.md)|Informations|Le nombre de fabriques de canaux mises en cache est de %1.  Seules «%2 » fabriques de canaux peuvent être mises en cache.|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](3306-clientbasechannelfactoryagedoutofcache.md)|Informations|Une fabrique de canaux a été échue du cache, car le cache a atteint sa limite de « %1 ».|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](3307-clientbasechannelfactorycachehit.md)|Informations|Une fabrique de canaux correspondante trouvée dans le cache a été utilisée.|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](3308-clientbaseusinglocalchannelfactory.md)|Informations|N’utilise pas la fabrique de canaux à partir du cache, c.-à-d. la mise en cache est désactivée pour l’instance.|ServiceModel|  
|[3309 - QueryCompositionExecuted](3309-querycompositionexecuted.md)|Informations|La composition de requête à l'aide de « %1 » a été exécutée sur l'URI de requête : « %2 ».|ServiceModel|  
|[3310 - DispatchFailed](3310-dispatchfailed.md)|Error|L'opération « %1 »' a été distribuée avec des erreurs.|ServiceModel|  
|[3311 - DispatchSuccessful](3311-dispatchsuccessful.md)|Informations|L'opération « %1 » a été distribuée.|ServiceModel|  
|[3312 - MessageReadByEncoder](3312-messagereadbyencoder.md)|Informations|Un message d'une taille de « %1 » octets a été lu par l'encodeur.|Channel|  
|[3312 - MessageReadByEncoder](3312-messagereadbyencoder.md)|Informations|Un message d'une taille de '%1' octets a été écrit par l'encodeur.|Channel|  
|[3314 - SessionIdleTimeout](3314-sessionidletimeout.md)|Error|Abandon de la session du canal inactif de l'URI : « %1 ».|ServiceModel|  
|[3319 - SocketAcceptEnqueued](3319-socketacceptenqueued.md)|Commentaires|Acceptation de la connexion commencée.|TCP|  
|[3320 - SocketAccepted](3320-socketaccepted.md)|Commentaires|ListenerId : %1 a accepté SocketId : %2|TCP|  
|[3321 - ConnectionPoolMiss](3321-connectionpoolmiss.md)|Commentaires|Le pool de %1 ne dispose d'aucune connexion disponible et dispose de %2 connexions occupées.|Channel|  
|[3322 - DispatchFormatterDeserializeRequestStart](3322-dispatchformatterdeserializerequeststart.md)|Commentaires|Le répartiteur a démarré la désérialisation du message de requête.|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](3323-dispatchformatterdeserializerequeststop.md)|Commentaires|Le répartiteur a terminé la désérialisation du message de requête.|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](3324-dispatchformatterserializereplystart.md)|Commentaires|Le répartiteur a démarré la sérialisation du message de réponse.|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](3325-dispatchformatterserializereplystop.md)|Commentaires|Le répartiteur a terminé la sérialisation du message de réponse.|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](3326-clientformatterserializerequeststart.md)|Commentaires|La sérialisation de la requête du client a démarré.|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](3327-clientformatterserializerequeststop.md)|Commentaires|Le client a terminé la sérialisation du message de requête.|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](3328-clientformatterdeserializereplystart.md)|Commentaires|Le client a démarré la désérialisation du message de réponse.|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](3329-clientformatterdeserializereplystop.md)|Commentaires|Le client a terminé la désérialisation du message de réponse.|ServiceModel|  
|[3330 - SecurityNegotiationStart](3330-securitynegotiationstart.md)|Commentaires|Démarrage de la négociation de sécurité.|Sécurité|  
|[3331 - SecurityNegotiationStop](3331-securitynegotiationstop.md)|Commentaires|Négociation de sécurité terminée.|Sécurité|  
|[3332 - SecurityTokenProviderOpened](3332-securitytokenprovideropened.md)|Commentaires|Ouverture de SecurityTokenProvider terminée.|Sécurité|  
|[3333 - OutgoingMessageSecured](3333-outgoingmessagesecured.md)|Commentaires|Le message sortant a été sécurisé.|Sécurité|  
|[3334 - IncomingMessageVerified](3334-incomingmessageverified.md)|Commentaires|Le message entrant a été vérifié.|ServiceModel de sécurité|  
|[3335 - GetServiceInstanceStart](3335-getserviceinstancestart.md)|Commentaires|Début de la récupération de l'instance de service.|ServiceModel|  
|[3336 - GetServiceInstanceStop](3336-getserviceinstancestop.md)|Commentaires|Instance de service récupérée.|ServiceModel|  
|[3337 - ChannelReceiveStart](3337-channelreceivestart.md)|Commentaires|ChannelHandlerId : %1 - Début de la boucle de réception du message.|Channel|  
|[3338 - ChannelReceiveStop](3338-channelreceivestop.md)|Commentaires|ChannelHandlerId : %1 - Arrêt de la boucle de réception du message.|Channel|  
|[3339 - ChannelFactoryCreated](3339-channelfactorycreated.md)|Commentaires|ChannelFactory créé.|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](3340-pipeconnectionacceptstart.md)|Commentaires|Début de l'acceptation de la connexion du canal sur %1.|Channel|  
|[3341 - PipeConnectionAcceptStop](3341-pipeconnectionacceptstop.md)|Commentaires|Connexion du canal acceptée.|Channel|  
|[3342 - EstablishConnectionStart](3342-establishconnectionstart.md)|Commentaires|Début de l'établissement de la connexion pour %1.|Channel|  
|[3343 - EstablishConnectionStop](3343-establishconnectionstop.md)|Commentaires|Connexion établie.|Channel|  
|[3345 - SessionPreambleUnderstood](3345-sessionpreambleunderstood.md)|Commentaires|Préambule de session pour « %1 » compris.|Channel|  
|[3346 - ConnectionReaderSendFault](3346-connectionreadersendfault.md)|Error|Envoi de l'erreur « %1 » par le lecteur de connexion.|Channel|  
|[3347 - SocketAcceptClosed](3347-socketacceptclosed.md)|Commentaires|Acceptation du socket fermée.|TCP|  
|[3348 - ServiceHostFaulted](3348-servicehostfaulted.md)|Critique|L'hôte de service a rencontré une erreur.|TCP|  
|[3349 - ListenerOpenStart](3349-listeneropenstart.md)|Commentaires|Ouverture de l'écouteur pour « %1 ».|Channel|  
|[3350 - ListenerOpenStop](3350-listeneropenstop.md)|Commentaires|Ouverture de l'écouteur terminée.|Channel|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](3351-servermaxpooledconnectionsquotareached.md)|Commentaires|Le quota maximal de connexions regroupées du serveur a été atteint.|Quota|  
|[3352 - TcpConnectionTimedOut](3352-tcpconnectiontimedout.md)|Error|Le SocketId %1 à l'adresse distante %2 a expiré.|TCP|  
|[3353 - TcpConnectionResetError](3353-tcpconnectionreseterror.md)|Avertissement|Le SocketId %1 à l'adresse distante %2 a rencontré une erreur lors de la réinitialisation de la connexion.|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](3354-servicesecuritynegotiationcompleted.md)|Commentaires|Négociation de sécurité du service terminée.|Sécurité|  
|[3355 - SecurityNegotiationProcessingFailure](3355-securitynegotiationprocessingfailure.md)|Error|Échec du traitement de la négociation de sécurité.|Sécurité|  
|[3356 - SecurityIdentityVerificationSuccess](3356-securityidentityverificationsuccess.md)|Commentaires|Vérification de sécurité effectuée.|Sécurité|  
|[3357 - SecurityIdentityVerificationFailure](3357-securityidentityverificationfailure.md)|Error|Échec de la vérification de sécurité.|Sécurité|  
|[3358 - PortSharingDuplicatedSocket](3358-portsharingduplicatedsocket.md)|Commentaires|Socket dupliqué pour %1.|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](3359-securityimpersonationsuccess.md)|Commentaires|Emprunt d'identité de sécurité effectué.|Sécurité|  
|[3360 - SecurityImpersonationFailure](3360-securityimpersonationfailure.md)|Avertissement|Échec de l'emprunt d'identité de sécurité.|Sécurité|  
|[3361 - HttpChannelRequestAborted](3361-httpchannelrequestaborted.md)|Avertissement|Abandon de la requête de canal HTTP.|HTTP|  
|[3362 - HttpChannelResponseAborted](3362-httpchannelresponseaborted.md)|Avertissement|Abandon de la réponse de canal HTTP.|HTTP|  
|[3363 - HttpAuthFailed](3363-httpauthfailed.md)|Avertissement|Échec de l'authentification HTTP.|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](3364-sharedlistenerproxyregisterstart.md)|Commentaires|Début de l'inscription SharedListenerProxy pour l'URI « %1 ».|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](3365-sharedlistenerproxyregisterstop.md)|Commentaires|Arrêt de l'inscription SharedListenerProxy.|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](3366-sharedlistenerproxyregisterfailed.md)|Error|Échec de l'inscription SharedListenerProxy avec l'état « %1 ».|ActivationServices|  
|[3367 - ConnectionPoolPreambleFailed](3367-connectionpoolpreamblefailed.md)|Error|ConnectionPoolPreambleFailed.|Channel|  
|[3368 - SslOnInitiateUpgrade](3368-ssloninitiateupgrade.md)|Commentaires|SslOnAcceptUpgradeStart|Sécurité|  
|[3369 - SslOnAcceptUpgrade](3369-sslonacceptupgrade.md)|Commentaires|SslOnAcceptUpgradeStop|Sécurité|  
|[3370 - BinaryMessageEncodingStart](3370-binarymessageencodingstart.md)|Commentaires|BinaryMessageEncoder a démarré l'encodage du message.|Channel|  
|[3371 - MtomMessageEncodingStart](3371-mtommessageencodingstart.md)|Commentaires|MtomMessageEncoder a démarré l'encodage du message.|Channel|  
|[3372 - TextMessageEncodingStart](3372-textmessageencodingstart.md)|Commentaires|TextMessageEncoder a démarré l'encodage du message.|Channel|  
|[3373 - BinaryMessageDecodingStart](3373-binarymessagedecodingstart.md)|Commentaires|BinaryMessageEncoder a démarré le décodage du message.|Channel|  
|[3374 - MtomMessageDecodingStart](3374-mtommessagedecodingstart.md)|Commentaires|MtomMessageEncoder a démarré le décodage du message.|Channel|  
|[3375 - TextMessageDecodingStart](3375-textmessagedecodingstart.md)|Commentaires|TextMessageEncoder a démarré le décodage du message.|Channel|  
|[3376 - HttpResponseReceiveStart](3376-httpresponsereceivestart.md)|Informations|Début de la réception d'un message par le transport HTTP.|HTTP|  
|[3377 - SocketReadStop](3377-socketreadstop.md)|Commentaires|L'élément SocketId %1 a lu « %2 » octets à partir de « %3 ».|TCP|  
|[3378 - SocketAsyncReadStop](3378-socketasyncreadstop.md)|Commentaires|L'élément SocketId %1 a lu « %2 » octets à partir de « %3 ».|TCP|  
|[3379 - SocketWriteStart](3379-socketwritestart.md)|Commentaires|L'élément SocketId « %1 » a écrit « %2 » octets dans « %3 ».|TCP|  
|[3380 - SocketAsyncWriteStart](3380-socketasyncwritestart.md)|Commentaires|L'élément SocketId « %1 » a écrit « %2 » octets dans « %3 ».|TCP|  
|[3381 - SequenceAcknowledgementSent](3381-sequenceacknowledgementsent.md)|Commentaires|Accusé de réception SessionId : %1 envoyé.|Channel|  
|[3382 - ClientReliableSessionReconnect](3382-clientreliablesessionreconnect.md)|Informations|SessionId : reconnexion de %1.|Channel|  
|[3383 - ReliableSessionChannelFaulted](3383-reliablesessionchannelfaulted.md)|Informations|SessionId %1 a rencontré une erreur.|Channel|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](3384-windowsstreamsecurityoninitiateupgrade.md)|Commentaires|Début de la mise à niveau de sécurité par WindowsStreamSecurity.|Sécurité|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](3385-windowsstreamsecurityonacceptupgrade.md)|Commentaires|Sécurité Windows relative à la diffusion en continu après acceptation de la mise à niveau.|Sécurité|  
|[3386 - SocketConnectionAbort](3386-socketconnectionabort.md)|Avertissement|Abandon de SocketId : %1.|TCP|  
|[3388 - HttpGetContextStart](3388-httpgetcontextstart.md)|Commentaires|Début de HttpGetContext.|HTTP|  
|[3389 - ClientSendPreambleStart](3389-clientsendpreamblestart.md)|Commentaires|Début du préambule d'envoi par le client.|Channel|  
|[3390 - ClientSendPreambleStop](3390-clientsendpreamblestop.md)|Commentaires|Arrêt du préambule d'envoi par le client.|Channel|  
|[3391 - HttpMessageReceiveFailed](3391-httpmessagereceivefailed.md)|Avertissement|Échec de la réception du message HTTP.|HTTP|  
|[3392 - TransactionScopeCreate](3392-transactionscopecreate.md)|Informations|TransactionScope est en cours de création avec LocalIdentifier : « %1 » et DistributedIdentifier : « %2 ».|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](3393-streamedmessagereadbyencoder.md)|Informations|Un message diffusé en continu a été lu par l'encodeur.|Channel|  
|[3394 - StreamedMessageWrittenByEncoder](3394-streamedmessagewrittenbyencoder.md)|Informations|Un message diffusé en continu a été écrit par l'encodeur.|Channel|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](3395-messagewrittenasynchronouslybyencoder.md)|Informations|Un message a été écrit de façon asynchrone par l'encodeur.|Channel|  
|[3396 - BufferedAsyncWriteStart](3396-bufferedasyncwritestart.md)|Informations|L'élément BufferId %1 a terminé l'écriture de « %2 » octets dans le flux sous-jacent.|Channel|  
|[3397 - BufferedAsyncWriteStop](3397-bufferedasyncwritestop.md)|Informations|Un message a été écrit de façon asynchrone par l'encodeur.|Channel|  
|[3398 - PipeSharedMemoryCreated](3398-pipesharedmemorycreated.md)|Commentaires|Mémoire partagée par les canaux créée à « %1 ».|Channel|  
|[3399 - NamedPipeCreated](3399-namedpipecreated.md)|Commentaires|NamedPipe « %1 » créé.|Channel|  
|[3401 - SignatureVerificationStart](3401-signatureverificationstart.md)|Commentaires|Début de la vérification de la signature.|Sécurité|  
|[3402 - SignatureVerificationSuccess](3402-signatureverificationsuccess.md)|Commentaires|Vérification de la signature effectuée.|Sécurité|  
|[3403 - WrappedKeyDecryptionStart](3403-wrappedkeydecryptionstart.md)|Commentaires|Début du déchiffrement de la clé encapsulée.|Sécurité|  
|[3404 - WrappedKeyDecryptionSuccess](3404-wrappedkeydecryptionsuccess.md)|Commentaires|Déchiffrement de la clé encapsulée effectué.|Sécurité|  
|[3405 - EncryptedDataProcessingStart](3405-encrypteddataprocessingstart.md)|Commentaires|Début du traitement des données chiffrées.|Sécurité|  
|[3406 - EncryptedDataProcessingSuccess](3406-encrypteddataprocessingsuccess.md)|Commentaires|Traitement des données chiffrées terminé.|Sécurité|  
|[3407 - HttpPipelineProcessInboundRequestStart](3407-httppipelineprocessinboundrequeststart.md)|Commentaires|Le gestionnaire de messages HTTP a commencé le traitement de la demande entrante.|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](3408-httppipelinebeginprocessinboundrequeststart.md)|Commentaires|Le gestionnaire de messages HTTP a démarré le traitement asynchrone de la demande entrante.|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](3409-httppipelineprocessinboundrequeststop.md)|Commentaires|Le gestionnaire de messages HTTP a terminé le traitement d'une demande entrante.|HTTP|  
|[3410 - HttpPipelineFaulted](3410-httppipelinefaulted.md)|Avertissement|Le gestionnaire de messages HTTP est défectueux.|HTTP|  
|[3411 - HttpPipelineTimeoutException](3411-httppipelinetimeoutexception.md)|Error|La connexion WebSocket a expiré.|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](3412-httppipelineprocessresponsestart.md)|Commentaires|Le gestionnaire de messages HTTP a démarré le traitement de la réponse.|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](3413-httppipelinebeginprocessresponsestart.md)|Commentaires|Le gestionnaire de messages HTTP a démarré le traitement asynchrone de la réponse.|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](3414-httppipelineprocessresponsestop.md)|Commentaires|Le gestionnaire de messages HTTP a terminé le traitement de la réponse.|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](3415-websocketconnectionrequestsendstart.md)|Commentaires|Début de l'envoi de la demande de connexion WebSocket à « %1 ».|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](3416-websocketconnectionrequestsendstop.md)|Commentaires|Demande de connexion à l'élément WebSocketId %1 envoyée.|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](3417-websocketconnectionacceptstart.md)|Commentaires|Début de l'acceptation de la connexion à l'élément WebSocket.|HTTP|  
|[3418 - WebSocketConnectionAccepted](3418-websocketconnectionaccepted.md)|Commentaires|La connexion à l'élément WebSocketId %1 est acceptée.|HTTP|  
|[3419 - WebSocketConnectionDeclined](3419-websocketconnectiondeclined.md)|Error|Connexion à l'élément WebSocket refusée avec le code d'état « %1 »|HTTP|  
|[3420 - WebSocketConnectionFailed](3420-websocketconnectionfailed.md)|Error|Échec de la demande de connexion à l'élément WebSocket : « %1 »|HTTP|  
|[3421 - WebSocketConnectionAborted](3421-websocketconnectionaborted.md)|Error|La connexion à l'élément WebSocketId %1 est abandonnée.|HTTP|  
|[3422 - WebSocketAsyncWriteStart](3422-websocketasyncwritestart.md)|Commentaires|L'élément WebSocketId %1 a écrit « %2 » octets dans « %3 ».|HTTP|  
|[3423 - WebSocketAsyncWriteStop](3423-websocketasyncwritestop.md)|Commentaires|Arrêt de l'écriture asynchrone de l'élément WebSocketId %1.|HTTP|  
|[3424 - WebSocketAsyncReadStart](3424-websocketasyncreadstart.md)|Commentaires|Début de lecture de l'élément WebSocketId : %1.|HTTP|  
|[3425 - WebSocketAsyncReadStop](3425-websocketasyncreadstop.md)|Commentaires|L'élément WebSocketId %1 a lu « %2 » octets à partir de « %3 ».|HTTP|  
|[3426 - WebSocketCloseSent](3426-websocketclosesent.md)|Commentaires|L'élément WebSocketId %1 a envoyé un message de fermeture à « %2 » avec l'état de fermeture « %3 ».|HTTP|  
|[3427 - WebSocketCloseOutputSent](3427-websocketcloseoutputsent.md)|Commentaires|L'élément WebSocketId %1 a envoyé un message en sortie de fermeture à « %2 » avec l'état de fermeture « %3 ».|HTTP|  
|[3428 - WebSocketConnectionClosed](3428-websocketconnectionclosed.md)|Commentaires|La connexion à l'élément WebSocketId %1 est fermée.|HTTP|  
|[3429 - WebSocketCloseStatusReceived](3429-websocketclosestatusreceived.md)|Commentaires|Message de fermeture de la connexion à l'élément WebSocketId %1 reçu avec l'état « %2 ».|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](3430-websocketuseversionfromclientwebsocketfactory.md)|Commentaires|Utilisation du WebSocketVersion d'une fabrique WebSocket cliente de type « %1 ».|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](3431-websocketcreateclientwebsocketwithfactory.md)|Commentaires|Création du WebSocket client avec une fabrique de type « %1 ».|HTTP|  
|[3553 - XamlServicesLoadStart](3553-xamlservicesloadstart.md)|Informations|Début de XamlServicesLoad|WebHost|  
|[3554 - XamlServicesLoadStop](3554-xamlservicesloadstop.md)|Informations|Arrêt de XamlServicesLoad|WebHost|  
|[3555 - CreateWorkflowServiceHostStart](3555-createworkflowservicehoststart.md)|Informations|Début de CreateWorkflowServiceHost|WebHost|  
|[3556 - CreateWorkflowServiceHostStop](3556-createworkflowservicehoststop.md)|Informations|Arrêt de CreateWorkflowServiceHost Stop|WebHost|  
|[3558 - ServiceActivationStart](3558-serviceactivationstart.md)|Informations|Démarrage de l'activation du service|WebHost|  
|[3559 - ServiceActivationStop](3559-serviceactivationstop.md)|Informations|Arrêt de l'activation du service|WebHost|  
|[3560 - ServiceActivationAvailableMemory](3560-serviceactivationavailablememory.md)|Commentaires|Mémoire disponible (en octets) : %1|Quota|  
|[3800 - RoutingServiceClosingClient](3800-routingserviceclosingclient.md)|Informations|Le service de routage ferme le client « %1 ».|RoutingServices|  
|[3800 - RoutingServiceClosingClient](3800-routingserviceclosingclient.md)|Avertissement|Le client de service de routage « %1 » a généré une erreur.|RoutingServices|  
|[3802 - RoutingServiceCompletingOneWay](3802-routingservicecompletingoneway.md)|Informations|Fin du message unidirectionnel par le service de routage.|RoutingServices|  
|[3803 - RoutingServiceProcessingFailure](3803-routingserviceprocessingfailure.md)|Error|Échec du service de routage lors du traitement d'un message sur le point de terminaison avec l'adresse « %1 ».|RoutingServices|  
|[3804 - RoutingServiceCreatingClientForEndpoint](3804-routingservicecreatingclientforendpoint.md)|Informations|Le service de routage crée un client pour le point de terminaison : « 1% ».|RoutingServices|  
|[3805 - RoutingServiceDisplayConfig](3805-routingservicedisplayconfig.md)|Commentaires|Le service de routage est configuré avec RouteOnHeadersOnly : %1, SoapProcessingEnabled : %2, EnsureOrderedDispatch : %3.|RoutingServices|  
|[3807 - RoutingServiceCompletingTwoWay](3807-routingservicecompletingtwoway.md)|Informations|Fin du message de réponse à la demande du service de routage.|RoutingServices|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](3809-routingservicemessageroutedtoendpoints.md)|Commentaires|Message routé avec l'ID : « %1 » routé par le service de routage vers les listes de points de terminaison %2.|RoutingServices|  
|[3810 - RoutingServiceConfigurationApplied](3810-routingserviceconfigurationapplied.md)|Informations|Une nouvelle RoutingConfiguration est appliquée au service de routage.|RoutingServices|  
|[3815 - RoutingServiceProcessingMessage](3815-routingserviceprocessingmessage.md)|Informations|Le service de routage traite un message avec l’ID : « %1 », action : « %2 », URL entrante : « %3 », Reçu dans la transaction : %4.|RoutingServices|  
|[3816 - RoutingServiceTransmittingMessage](3816-routingservicetransmittingmessage.md)|Informations|Le service de routage transmet le message avec l'ID « %1 » [opération %2] à « %3 ».|RoutingServices|  
|[3817 - RoutingServiceCommittingTransaction](3817-routingservicecommittingtransaction.md)|Informations|Le service de routage valide la transaction avec l’ID « %1 ».|RoutingServices|  
|[3818 - RoutingServiceDuplexCallbackException](3818-routingserviceduplexcallbackexception.md)|Error|Le composant du service de routage %1 a rencontré une exception de rappel duplex.|RoutingServices|  
|[3819 - RoutingServiceMovedToBackup](3819-routingservicemovedtobackup.md)|Informations|Message du service de routage avec l'ID %1 [opération %2] déplacé vers le point de terminaison de sauvegarde « %3 ».|RoutingServices|  
|[3820 - RoutingServiceCreatingTransaction](3820-routingservicecreatingtransaction.md)|Informations|Le service de routage a créé une nouvelle transaction avec l’id « %1 »’ pour le traitement des messages.|RoutingServices|  
|[3821 - RoutingServiceCloseFailed](3821-routingserviceclosefailed.md)|Avertissement|Échec du service de routage lors de la fermeture du client sortant « %1 ».|RoutingServices|  
|[3822 - RoutingServiceSendingResponse](3822-routingservicesendingresponse.md)|Informations|Le service de routage renvoie un message de réponse avec l'action « %1 ».|RoutingServices|  
|[3823 - RoutingServiceSendingFaultResponse](3823-routingservicesendingfaultresponse.md)|Avertissement|Le service de routage renvoie un message de réponse d'erreur avec l'action « %1 ».|RoutingServices|  
|[3824 - RoutingServiceCompletingReceiveContext](3824-routingservicecompletingreceivecontext.md)|Commentaires|Le service de routage appelle ReceiveContext.Complete pour le message avec l'ID « %1 ».|RoutingServices|  
|[3825 - RoutingServiceAbandoningReceiveContext](3825-routingserviceabandoningreceivecontext.md)|Avertissement|Le service de routage appelle ReceiveContext.Abandon pour le message d'ID : « %1 ».|RoutingServices|  
|[3826 - RoutingServiceUsingExistingTransaction](3826-routingserviceusingexistingtransaction.md)|Commentaires|Le service de routage enverra les messages à l’aide de la transaction « %1 » existante.|RoutingServices|  
|[3827 - RoutingServiceTransmitFailed](3827-routingservicetransmitfailed.md)|Avertissement|Échec du service de routage lors de l'envoi à « %1 ».|RoutingServices|  
|[3828 - RoutingServiceFilterTableMatchStart](3828-routingservicefiltertablematchstart.md)|Informations|Début de la correspondance du service de routage MessageFilterTable.|RoutingServices|  
|[3829 - RoutingServiceFilterTableMatchStop](3829-routingservicefiltertablematchstop.md)|Informations|Fin de la correspondance du service de routage MessageFilterTable.|RoutingServices|  
|[3830 - RoutingServiceAbortingChannel](3830-routingserviceabortingchannel.md)|Commentaires|Le service de routage appelle un abandon sur le canal : « %1 ».|RoutingServices|  
|[3831 - RoutingServiceHandledException](3831-routingservicehandledexception.md)|Commentaires|Le service de routage a géré une exception.|RoutingServices|  
|[3832 - RoutingServiceTransmitSucceeded](3832-routingservicetransmitsucceeded.md)|Informations|Le service de routage a correctement transmis le message avec l'ID « %1 » [opération %2] à « %3 ».|RoutingServices|  
|[4001 - TransportListenerSessionsReceived](4001-transportlistenersessionsreceived.md)|Commentaires|Session de l'écouteur de transport reçue via « %1 »|ActivationServices|  
|[4002 - FailFastException](4002-failfastexception.md)|Critique|FailFastException.|ActivationServices|  
|[4003 - ServiceStartPipeError](4003-servicestartpipeerror.md)|Error|Erreur de canal relative au démarrage du service.|ActivationServices|  
|[4008 - DispatchSessionStart](4008-dispatchsessionstart.md)|Commentaires|Début de la distribution de sessions.|ActivationServices|  
|[4008 - DispatchSessionStart](4008-dispatchsessionstart.md)|Avertissement|La distribution de sessions pour « %1 » a échoué, car la file d'attente des sessions en attente contient « %2 » éléments en attente, et est donc pleine.|ActivationServices|  
|[4011 - MessageQueueRegisterStart](4011-messagequeueregisterstart.md)|Commentaires|Début de l'inscription à la file d'attente des messages.|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](4012-messagequeueregisterabort.md)|Error|Abandon de l'inscription à la file d'attente des messages avec l'état : « %1 » pour l'URI : « %2 ».|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](4013-messagequeueunregistersucceeded.md)|Commentaires|Désinscription de la file d'attente des messages effectuée pour l'URI : « %1 ».|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](4014-messagequeueregisterfailed.md)|Error|Échec de l'inscription à la file d'attente des messages pour l'URI « %1 » avec l'état « %2 ».|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](4015-messagequeueregistercompleted.md)|Informations|Inscription à la file d'attente des messages terminée pour l'URI « %1 ».|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](4016-messagequeueduplicatedsocketerror.md)|Error|Échec de la duplication de socket par la file d'attente des messages.|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](4019-messagequeueduplicatedsocketcomplete.md)|Commentaires|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](4020-tcptransportlistenerlisteningstart.md)|Commentaires|Début de l'écoute de l'URI « %1 » par l'écouteur de transport TCP.|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](4021-tcptransportlistenerlisteningstop.md)|Commentaires|Écouteur de transport TCP à l'écoute.|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](4022-webhostunregisterprotocolfailed.md)|Error|Code d'erreur : %1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](4023-wasclosealllistenerchannelinstancescompleted.md)|Informations|Fermeture de toutes les instances du canal de l'écouteur à l'aide de WAS terminée.|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](4024-wasclosealllistenerchannelinstancesfailed.md)|Error|Code d'erreur : %1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](4025-openlistenerchannelinstancefailed.md)|Error|Code d'erreur : %1|ActivationServices|  
|[4026 - WasConnected](4026-wasconnected.md)|Commentaires|WAS est connecté.|ActivationServices|  
|[4027 - WasDisconnected](4027-wasdisconnected.md)|Commentaires|WAS est déconnecté.|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](4028-pipetransportlistenerlisteningstart.md)|Commentaires|Début de l'écoute de l'URI %1 par l'écouteur de transport du canal.|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](4029-pipetransportlistenerlisteningstop.md)|Commentaires|Arrêt de l'écoute par l'écouteur de transport du canal.|ActivationServices|  
|[4030 - DispatchSessionSuccess](4030-dispatchsessionsuccess.md)|Informations|Distribution de sessions effectuée.|ActivationServices|  
|[4031 - DispatchSessionFailed](4031-dispatchsessionfailed.md)|Error|Échec de la distribution de sessions.|ActivationServices|  
|[4032 - WasConnectionTimedout](4032-wasconnectiontimedout.md)|Critique|Expiration de la connexion WAS.|ActivationServices|  
|[4033 - RoutingTableLookupStart](4033-routingtablelookupstart.md)|Commentaires|Début de la recherche dans la table de routage.|ActivationServices|  
|[4034 - RoutingTableLookupStop](4034-routingtablelookupstop.md)|Commentaires|Recherche dans la table de routage terminée.|ActivationServices|  
|[4035 - PendingSessionQueueRatio](4035-pendingsessionqueueratio.md)|Commentaires|Ratio des files d'attente des sessions en attente : %1/%2|Quota|  
|[4600 - MessageLogEventSizeExceeded](4600-messagelogeventsizeexceeded.md)|Avertissement|Impossible de journaliser le message, car il dépasse la taille des événements ETW|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](4801-discoveryclientinclientchannelfailedtoclose.md)|Avertissement|Le DiscoveryClient créé dans DiscoveryClientChannel n'a pas pu se fermer et a par conséquent été abandonné.|Découverte|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](4802-discoveryclientprotocolexceptionsuppressed.md)|Informations|ProtocolException a été supprimé lors de la fermeture de DiscoveryClient. Cela peut être dû à un DiscoveryService qui tente encore d'envoyer une réponse à DiscoveryClient.|Découverte|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](4803-discoveryclientreceivedmulticastsuppression.md)|Informations|DiscoveryClient a reçu un message de suppression multidiffusion d'un DiscoveryProxy.|Découverte|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](4804-discoverymessagereceivedafteroperationcompleted.md)|Informations|Un message %1 avec messageId='%2' a été déposé par DiscoveryClient car l’opération correspondante %3 est terminée.|Découverte|  
|[4805 - DiscoveryMessageWithInvalidContent](4805-discoverymessagewithinvalidcontent.md)|Avertissement|Un message %1 avec messageId='%2' a été déposé, car son contenu n’était pas valide.|Découverte|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|Avertissement|Un message %1 avec messageId='%2' et relatesTo='%3' a été supprimé par DiscoveryClient, car l'opération correspondante %4 est terminée ou la valeur relatesTo n'est pas valide.|Découverte|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](4807-discoverymessagewithinvalidreplyto.md)|Avertissement|Un message de demande de découverte avec messageId='%1' a été supprimé, car son adresse de réponse ReplyTo n’était pas valide.|Découverte|  
|[4808 - DiscoveryMessageWithNoContent](4808-discoverymessagewithnocontent.md)|Avertissement|Un message %1 a été supprimé, car il n’avait aucun contenu.|Découverte|  
|[4809 - DiscoveryMessageWithNullMessageId](4809-discoverymessagewithnullmessageid.md)|Avertissement|Un message %1 a été supprimé car son en-tête ne contenait pas la propriété MessageId requise.|Découverte|  
|[4810 - DiscoveryMessageWithNullMessageSequence](4810-discoverymessagewithnullmessagesequence.md)|Avertissement|Un message %1 avec messageId='%2' a été supprimé par DiscoveryClient, car il n'avait pas la propriété DiscoveryMessageSequence.|Découverte|  
|[4811 - DiscoveryMessageWithNullRelatesTo](4811-discoverymessagewithnullrelatesto.md)|Avertissement|Un message %1 avec messageId='%2' a été supprimé par DiscoveryClient, car son en-tête ne contenait pas la propriété RelatesTo requise.|Découverte|  
|[4812 - DiscoveryMessageWithNullReplyTo](4812-discoverymessagewithnullreplyto.md)|Avertissement|Un message de demande de découverte avec messageId='%1' a été supprimé, car il n'avait pas d'adresse de réponse ReplyTo.|Découverte|  
|[4813 - DuplicateDiscoveryMessage](4813-duplicatediscoverymessage.md)|Avertissement|Un message %1 avec messageId='%2' a été supprimé, car il s'agissait d'un doublon.|Découverte|  
|[4814 - EndpointDiscoverabilityDisabled](4814-endpointdiscoverabilitydisabled.md)|Informations|La fonctionnalité de découverte du point de terminaison avec EndpointAddress='%1' et ListenUri='%2' a été désactivée.|Découverte|  
|[4814 - EndpointDiscoverabilityDisabled](4814-endpointdiscoverabilitydisabled.md)|Informations|La fonctionnalité de découverte du point de terminaison avec EndpointAddress='%1' et ListenUri='%2' a été activée.|Découverte|  
|[4816 - FindInitiatedInDiscoveryClientChannel](4816-findinitiatedindiscoveryclientchannel.md)|Commentaires|Une opération Find a été initiée dans DiscoveryClientChannel pour découvrir des points de terminaison.|Découverte|  
|[4817 - InnerChannelCreationFailed](4817-innerchannelcreationfailed.md)|Avertissement|DiscoveryClientChannel n'a pas pu créer le canal avec un point de terminaison découvert avec EndpointAddress='%1' et Via='%2'. DiscoveryClientChannel va tenter d'utiliser le prochain point de terminaison découvert disponible.|Découverte|  
|[4818 - InnerChannelOpenFailed](4818-innerchannelopenfailed.md)|Avertissement|DiscoveryClientChannel n'a pas pu ouvrir le canal avec un point de terminaison découvert avec EndpointAddress='%1' et Via='%2'. DiscoveryClientChannel va tenter d'utiliser le prochain point de terminaison découvert disponible.|Découverte|  
|[4819 - InnerChannelOpenSucceeded](4819-innerchannelopensucceeded.md)|Informations|DiscoveryClientChannel a correctement découvert un point de terminaison et ouvert le canal qui l'utilise. Le client est connecté à un service utilisant EndpointAddress='%1' et Via='%2'.|Découverte|  
|[4820 - SynchronizationContextReset](4820-synchronizationcontextreset.md)|Informations|DiscoveryClientChannel a rétabli la valeur d'origine %1 de SynchronizationContext.|Découverte|  
|[4821 - SynchronizationContextSetToNull](4821-synchronizationcontextsettonull.md)|Informations|DiscoveryClientChannel a attribué à SynchronizationContext la valeur Null avant le lancement de l’opération Find.|Découverte|  
|[5001 - DCSerializeWithSurrogateStart](5001-dcserializewithsurrogatestart.md)|Commentaires|Début de la sérialisation de %1 par DataContract avec substituts.|Sérialisation|  
|[5002 - DCSerializeWithSurrogateStop](5002-dcserializewithsurrogatestop.md)|Commentaires|Arrêt de la sérialisation DataContract avec substituts.|Sérialisation|  
|[5003 - DCDeserializeWithSurrogateStart](5003-dcdeserializewithsurrogatestart.md)|Commentaires|Début de la désérialisation de %1 par DataContract avec substituts.|Sérialisation|  
|[5004 - DCDeserializeWithSurrogateStop](5004-dcdeserializewithsurrogatestop.md)|Commentaires|Arrêt de la désérialisation DataContract avec substituts.|Sérialisation|  
|[5005 - ImportKnownTypesStart](5005-importknowntypesstart.md)|Commentaires|Démarrage des ImportKnownTypes.|Sérialisation|  
|[5006 - ImportKnownTypesStop](5006-importknowntypesstop.md)|Commentaires|Arrêt des ImportKnownTypes.|Sérialisation|  
|[5007 - DCResolverResolve](5007-dcresolverresolve.md)|Commentaires|Début de la résolution de %1 par le programme de résolution DataContract.|Sérialisation|  
|[5008 - DCGenWriterStart](5008-dcgenwriterstart.md)|Commentaires|Début de la génération de l'enregistreur %1 par DataContract pour %2.|Sérialisation|  
|[5009 - DCGenWriterStop](5009-dcgenwriterstop.md)|Commentaires|Arrêt de la génération de l'enregistreur par DataContract.|Sérialisation|  
|[5010 - DCGenReaderStart](5010-dcgenreaderstart.md)|Commentaires|Début de la génération du lecteur %1 par DataContract pour %2.|Sérialisation|  
|[5011 - DCGenReaderStop](5011-dcgenreaderstop.md)|Commentaires|Arrêt de la génération par DataContract.|Sérialisation|  
|[5012 - DCJsonGenReaderStart](5012-dcjsongenreaderstart.md)|Commentaires|Début de la génération du lecteur %1 par JSON pour %2.|Sérialisation|  
|[5013 - DCJsonGenReaderStop](5013-dcjsongenreaderstop.md)|Commentaires|Arrêt de la génération du lecteur par JSON.|Sérialisation|  
|[5014 - DCJsonGenWriterStart](5014-dcjsongenwriterstart.md)|Commentaires|Début de la génération de l'enregistreur %1 par JSON pour %2.|Sérialisation|  
|[5015 - DCJsonGenWriterStop](5015-dcjsongenwriterstop.md)|Commentaires|Arrêt de la génération de l'enregistreur par JSON.|Sérialisation|  
|[5016 - GenXmlSerializableStart](5016-genxmlserializablestart.md)|Commentaires|Début de la génération sérialisable xml pour « %1 ».|Sérialisation|  
|[5017 - GenXmlSerializableStop](5017-genxmlserializablestop.md)|Commentaires|Arrêt de la génération sérialisable xml.|Sérialisation|  
|[5203 - JsonMessageDecodingStart](5203-jsonmessagedecodingstart.md)|Commentaires|JsonMessageEncoder a démarré le décodage du message.|Channel|  
|[5204 - JsonMessageEncodingStart](5204-jsonmessageencodingstart.md)|Commentaires|JsonMessageEncoder a démarré le codage du message.|Channel|  
|[5402 - TokenValidationStarted](5402-tokenvalidationstarted.md)|Commentaires|Début de la validation de SecurityToken (type « %1 » et ID « %2 »).|Sécurité|  
|[5403 - TokenValidationSuccess](5403-tokenvalidationsuccess.md)|Commentaires|Validation de SecurityToken (type « %1 » et ID « %2 ») effectuée.|Sécurité|  
|[5404 - TokenValidationFailure](5404-tokenvalidationfailure.md)|Error|Échec de la validation de SecurityToken (type « %1 » et ID « %2 »). %3|Sécurité|  
|[5405 - GetIssuerNameSuccess](5405-getissuernamesuccess.md)|Commentaires|Récupération du nom de l'émetteur %1 à partir de tokenId %2 effectuée.|Sécurité|  
|[5406 - GetIssuerNameFailure](5406-getissuernamefailure.md)|Error|Échec de la récupération du nom de l'émetteur à partir de tokenId : %1.|Sécurité|  
|[5600 - FederationMessageProcessingStarted](5600-federationmessageprocessingstarted.md)|Commentaires|Début du traitement du message de fédération.|Sécurité|  
|[5601 - FederationMessageProcessingSuccess](5601-federationmessageprocessingsuccess.md)|Commentaires|Traitement du message de fédération effectué.|Sécurité|  
|[5602 - FederationMessageCreationStarted](5602-federationmessagecreationstarted.md)|Commentaires|Début de la création d'un message de fédération à partir de la publication de formulaire.|Sécurité|  
|[5603 - FederationMessageCreationSuccess](5603-federationmessagecreationsuccess.md)|Commentaires|Création d'un message de fédération à partir de la publication de formulaire effectuée.|Sécurité|  
|[5604 - SessionCookieReadingStarted](5604-sessioncookiereadingstarted.md)|Commentaires|Début de la lecture du jeton de session à partir du cookie de session.|Sécurité|  
|[5605 - SessionCookieReadingSuccess](5605-sessioncookiereadingsuccess.md)|Commentaires|Lecture du jeton de session à partir du cookie de session effectuée.|Sécurité|  
|[5606 - PrincipalSettingFromSessionTokenStarted](5606-principalsettingfromsessiontokenstarted.md)|Commentaires|Début du paramétrage du principal à partir du jeton de session.|Sécurité|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](5607-principalsettingfromsessiontokensuccess.md)|Commentaires|Paramétrage du principal à partir du jeton de session effectué.|Sécurité|  
|[57393 - AppDomainUnload](57393-appdomainunload.md)|Informations|Déchargement d'AppDomain. AppDomain.FriendlyName %1, ProcessName %2, ProcessId %3.|Infrastructure|  
|[57394 - HandledException](57394-handledexception.md)|Informations|Traitement d'une exception.|Infrastructure|  
|[57395 - ShipAssertExceptionMessage](57395-shipassertexceptionmessage.md)|Error|Une défaillance inattendue s'est produite. Les applications ne doivent pas essayer de gérer cette erreur. À des fins de diagnostic, ce message en anglais est associé à l'échec : %1.|Infrastructure|  
|[57396 - ThrowingException](57396-throwingexception.md)|Avertissement|Levée d'une exception. Source : %1.|Infrastructure|  
|[57397 - UnhandledException](57397-unhandledexception.md)|Critique|Exception non gérée.|Infrastructure|  
|[57399 - TraceCodeEventLogCritical](57399-tracecodeeventlogcritical.md)|Critique|Écriture dans le journal d'événements.|Infrastructure|  
|[57400 - TraceCodeEventLogError](57400-tracecodeeventlogerror.md)|Error|Écriture dans le journal d'événements.|Infrastructure|  
|[57401 - TraceCodeEventLogInfo](57401-tracecodeeventloginfo.md)|Informations|Écriture dans le journal d'événements.|Infrastructure|  
|[57402 - TraceCodeEventLogVerbose](57402-tracecodeeventlogverbose.md)|Commentaires|Écriture dans le journal d'événements.|Infrastructure|  
|[57403 - TraceCodeEventLogWarning](57403-tracecodeeventlogwarning.md)|Avertissement|Écriture dans le journal d'événements.|Infrastructure|  
|[57404 - HandledExceptionWarning](57404-handledexceptionwarning.md)|Avertissement|Traitement d'une exception.|Infrastructure|  
|[62326 - HttpHandlerPickedForUrl](62326-httphandlerpickedforurl.md)|Informations|L'URL « %1 » héberge un document XAML avec le type d'élément racine « %2 ». Le type de gestionnaire HTTP « %3 » est sélectionné pour traiter toutes les requêtes adressées à cette URL.|WebHost|
