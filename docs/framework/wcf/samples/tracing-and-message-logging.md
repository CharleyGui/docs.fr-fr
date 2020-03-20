---
title: Tracing and Message Logging
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 9ffb7a99540b953fc93a22d2296caf86f294d25d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143822"
---
# <a name="tracing-and-message-logging"></a>Tracing and Message Logging
Cet exemple illustre comment activer l'enregistrement des suivis et des messages. Les traces et les journaux de messages qui en résultent sont visualisés à l’aide de [l’outil de visionneuse de traces de service (SvcTraceViewer.exe).](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) Cet échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
## <a name="tracing"></a>Traçage  
 Windows Communication Foundation (WCF) utilise le <xref:System.Diagnostics> mécanisme de traçage défini dans l’espace de nom. Dans ce modèle de suivi, les données de suivi sont générées par les sources de suivi implémentées par les applications. Chacune de ces sources est identifiée à l'aide d'un nom. Les consommateurs de suivis créent des écouteurs pour les sources de suivi à partir desquelles ils souhaitent récupérer des informations. Pour recevoir des données de suivi d'une source, vous devez créer un écouteur pour cette source. Dans WCF, cela peut se faire en ajoutant le code suivant au fichier de configuration `switchValue`du service ou du client en définissant la source de traces du modèle de service :  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 Pour plus d’informations sur les sources de traces, consultez la section Trace Source dans le sujet [Configuring Tracing.](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
## <a name="activity-tracing-and-propagation"></a>Suivi et propagation d'activité  
 Le `ActivityTracing` fait `propagateActivity` d’avoir permis et placé `true` dans les sources de traces pour le client et le service fournit une corrélation des traces au sein des unités logiques de traitement (activités), entre les activités dans les `system.ServiceModel` points de terminaison (par le biais de transferts d’activités), et entre les activités couvrant plusieurs critères de terminaison (par la propagation d’ID d’activité).  
  
 Ces trois mécanismes (activités, transfert et propagation) peuvent vous permettre de localiser plus facilement la cause racine d’une erreur, notamment en utilisant l’outil Service Trace Viewer. Pour plus d’informations, voir [Using Service Trace Viewer pour afficher des traces corrélées et dépannage](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Il est possible d'étendre le suivi fourni par le ServiceModel en créant des suivis d'activité définis par l'utilisateur. Les suivis d'activité définis par l'utilisateur permettent :  
  
- De regrouper les suivis dans des unités logiques de travail.  
  
- De mettre en relation les activités à l'aide du transfert et de la propagation.  
  
- Réduire le coût de performance du traçage WCF (par exemple, le coût de l’espace disque d’un fichier journal).  
  
 Pour plus d’informations sur la trace d’activité définie par l’utilisateur, veuillez consulter l’échantillon [de traçage.](../../../../docs/framework/wcf/samples/extending-tracing.md)  
  
## <a name="message-logging"></a>Journalisation des messages  
 L’enregistrement des messages peut être activé à la fois sur le client et le service de n’importe quelle application WCF. Pour activer l'enregistrement des messages, vous devez ajouter le code suivant au client ou au service :  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 Lorsqu'un message est enregistré, le type de suivi généré pour ce message n'est pas le même si ce message est suivi au niveau du client ou du serveur. Par exemple, le suivi du message « Add » est assuré dans la catégorie « TransportWrite », au niveau du client alors que son suivi est assuré dans la catégorie « TransportRead », au niveau du service.  
  
 Configurez l'écouteur de suivi en ajoutant le code suivant à la section <xref:System.Diagnostics> du fichier App.config du client ou du fichier Web.config du service :  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 Les messages sont enregistrés au format XML dans le fichier de configuration stocké dans le répertoire cible spécifié.  
  
> [!NOTE]
> Les fichiers de suivi ne peuvent pas être créés si un répertoire de journal n'est pas créé auparavant. Assurez-vous que le répertoire C:\logs\ existe ou définissez un autre répertoire d'enregistrement dans la configuration de l'écouteur. Consultez les instructions initiales de configuration figurant en fin de rubrique pour plus d'informations.  
  
 Pour plus d’informations sur l’enregistrement des messages, consultez le sujet [Configuring Message Logging.](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Avant d'exécuter l'exemple Tracing and Message Logging, créez le répertoire C:\logs\ dans lequel le service stockera les fichiers .svclog. Le nom de ce répertoire est défini dans le fichier de configuration sous la forme d’un chemin d’accès indiquant où les suivis et les messages doivent être enregistrés. Ce chemin peut être modifié. Accordez à l'utilisateur des droits d'accès en écriture de service réseau au répertoire des journaux.  
  
3. Pour construire l’édition C, C OU Visual Basic .NET de la solution, suivez les instructions dans [La construction des échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Pour exécuter l’échantillon dans une configuration mono-ou cross-computer, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Voir aussi

- [Traçage](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
