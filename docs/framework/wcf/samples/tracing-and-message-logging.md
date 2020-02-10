---
title: Tracing and Message Logging
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 448eef6ea147b725600b774026155acc1fca6d36
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094863"
---
# <a name="tracing-and-message-logging"></a>Tracing and Message Logging
Cet exemple illustre comment activer l'enregistrement des suivis et des messages. Les journaux de suivi et de message résultants sont affichés à l’aide de l' [outil Service Trace Viewer (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
## <a name="tracing"></a>Traçage  
 Windows Communication Foundation (WCF) utilise le mécanisme de suivi défini dans l’espace de noms <xref:System.Diagnostics>. Dans ce modèle de suivi, les données de suivi sont générées par les sources de suivi implémentées par les applications. Chacune de ces sources est identifiée à l'aide d'un nom. Les consommateurs de suivis créent des écouteurs pour les sources de suivi à partir desquelles ils souhaitent récupérer des informations. Pour recevoir des données de suivi d'une source, vous devez créer un écouteur pour cette source. Dans WCF, vous pouvez effectuer cette opération en ajoutant le code suivant au fichier de configuration du client ou du service en définissant la source de suivi du modèle de service `switchValue`:  
  
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
  
 Pour plus d’informations sur les sources de suivi, consultez la section source de suivi dans la rubrique [configuration du suivi](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) .  
  
## <a name="activity-tracing-and-propagation"></a>Suivi et propagation d'activité  
 Si `ActivityTracing` est activé et `propagateActivity` défini sur `true` dans les sources de suivi `system.ServiceModel` pour le client et le service, il fournit la corrélation des traces au sein d’unités logiques de traitement (activités), entre les activités au sein des points de terminaison (via les transferts d’activité) et entre les activités couvrant plusieurs points de terminaison (par le biais de la propagation d’ID d’activité).  
  
 Ces trois mécanismes (activités, transfert et propagation) peuvent vous permettre de localiser plus facilement la cause racine d’une erreur, notamment en utilisant l’outil Service Trace Viewer. Pour plus d’informations, consultez [utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Il est possible d'étendre le suivi fourni par le ServiceModel en créant des suivis d'activité définis par l'utilisateur. Les suivis d'activité définis par l'utilisateur permettent :  
  
- De regrouper les suivis dans des unités logiques de travail.  
  
- De mettre en relation les activités à l'aide du transfert et de la propagation.  
  
- Réduire le coût de performance du suivi WCF (par exemple, le coût d’espace disque d’un fichier journal).  
  
 Pour plus d’informations sur la trace d’activité définie par l’utilisateur, consultez l’exemple [extension du traçage](../../../../docs/framework/wcf/samples/extending-tracing.md) .  
  
## <a name="message-logging"></a>Journalisation des messages  
 L’enregistrement des messages peut être activé à la fois sur le client et le service d’une application WCF. Pour activer l'enregistrement des messages, vous devez ajouter le code suivant au client ou au service :  
  
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
  
 Pour plus d’informations sur la journalisation des messages, consultez la rubrique Configuration de l' [enregistrement des messages](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) .  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Avant d'exécuter l'exemple Tracing and Message Logging, créez le répertoire C:\logs\ dans lequel le service stockera les fichiers .svclog. Le nom de ce répertoire est défini dans le fichier de configuration sous la forme d’un chemin d’accès indiquant où les suivis et les messages doivent être enregistrés. Ce chemin peut être modifié. Accordez à l'utilisateur des droits d'accès en écriture de service réseau au répertoire des journaux.  
  
3. Pour générer C#, C++ou Visual Basic Édition .net de la solution, suivez les instructions de la création des exemples de [Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Exemples de surveillance AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
