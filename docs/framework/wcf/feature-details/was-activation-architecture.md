---
title: Architecture d'activation WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 01c30db1182ece6dd968b69cc4efcaa2d9fabd79
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737515"
---
# <a name="was-activation-architecture"></a>Architecture d'activation WAS
Cette rubrique détaille et décrit les composants du service d'activation des processus de Windows (également appelé WAS).  
  
## <a name="activation-components"></a>Composants d'activation  
 Le service WAS se compose de plusieurs composants architecturaux :  
  
- Adaptateurs d'écouteur. Services Windows qui reçoivent des messages sur des protocoles réseau spécifiques et communiquent avec WAS pour acheminer les messages entrants vers le processus de travail correct.  
  
- WAS. Service Windows qui gère la création et la durée de vie des processus de travail.  
  
- Fichier exécutable de processus de travail générique (w3wp.exe).  
  
- Gestionnaire d'application. Gère la création et la durée de vie des domaines d'application qui hébergent des applications dans le processus de travail.  
  
- Gestionnaires de protocoles. Composants spécifiques au protocole qui s'exécutent dans le processus de travail et gèrent les communications entre le processus de travail et les différents adaptateurs d'écouteur. Il existe deux types de gestionnaires de protocoles : les gestionnaires de protocoles de processus et les gestionnaires de protocoles de domaine d'application (AppDomain).  
  
 Lorsque le service WAS active une instance de processus de traitement, il charge les gestionnaires de protocoles de processus requis dans le processus de traitement et utilise le gestionnaire d'application pour créer un domaine d'application destiné à héberger l'application. Le domaine d'application charge le code de l'application ainsi que les gestionnaires de protocoles AppDomain requis par l'application.  
  
 ![Capture d’écran montrant l’architecture WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a>Adaptateurs d'écouteur  
 Les adaptateurs d'écouteur sont des services Windows individuels qui implémentent la logique de la communication réseau utilisée pour recevoir les messages à l'aide du protocole réseau sur lequel ils écoutent. Le tableau suivant répertorie les adaptateurs d’écouteur pour les protocoles Windows Communication Foundation (WCF).  
  
|Nom du service d'adaptateur de l'écouteur|Protocole|Remarques|  
|-----------------------------------|--------------|-----------|  
|W3SVC|http|Composant commun qui fournit l’activation HTTP pour IIS 7,0 et WCF.|  
|NetTcpActivator|net.tcp|Dépend du service NetTcpPortSharing.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|net.msmq|Pour une utilisation avec des applications Message Queuing basées sur WCF.|  
|NetMsmqActivator|msmq.formatname|Assure la compatibilité descendante avec les applications Message Queuing existantes.|  
  
 Les adaptateurs d'écouteur pour des protocoles spécifiques sont enregistrés lors de l'installation dans le fichier applicationHost.config, comme l'illustre l'exemple XML suivant.  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"   
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"   
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"   
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"   
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a>Gestionnaires de protocoles  
 Les gestionnaires de protocoles de processus et AppDomain pour des protocoles spécifiques sont enregistrés dans le fichier Web.config de l'ordinateur.  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Configuration du service WAS pour une utilisation avec WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
