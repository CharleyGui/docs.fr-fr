---
title: Windows Service Host
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: ab1effe93a1572f5d4ce5296bba99dad24f9cbca
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094785"
---
# <a name="windows-service-host"></a>Windows Service Host
Cet exemple illustre un service Windows Communication Foundation (WCF) hébergé dans un service Windows managé. Les services Windows sont contrôlés à l’aide de l’applet services du **panneau** de configuration et peuvent être configurés pour démarrer automatiquement après un redémarrage du système. L'exemple se compose d'un programme client et d'un programme de service Windows. Le service est implémenté en tant que programme .exe et contient son propre code d'hébergement. Dans d'autres environnements d'hébergement, tels que WAS (Windows Process Activation Services) ou IIS (Internet Information Services), vous n'avez pas besoin d'écrire le code d'hébergement.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Après avoir généré ce service, il doit être installé avec l'utilitaire Installutil.exe comme tout autre service Windows. Si vous voulez apporter des modifications au service, vous devez d'abord le désinstaller avec `installutil /u`. Les fichiers Setup.bat et Cleanup.bat inclus dans cet exemple sont les commandes pour installer et démarrer le service Windows, et pour fermer et désinstaller le service Windows. Le service WCF ne peut répondre aux clients que si le service Windows est en cours d’exécution. Si vous arrêtez le service Windows à l’aide de l’applet services du **panneau de configuration** et que vous exécutez le client, une exception <xref:System.ServiceModel.EndpointNotFoundException> se produit lorsqu’un client tente d’accéder au service. Si vous redémarrez le service Windows et exécutez à nouveau le client, la communication réussit.  
  
 Le code de service comprend une classe installer, une classe d’implémentation de service WCF qui implémente le contrat ICalculator et une classe de service Windows qui agit comme hôte au moment de l’exécution. La classe Installer, qui hérite de <xref:System.Configuration.Install.Installer>, permet à l'outil Installutil.exe d'installer le programme comme un service NT. La classe d’implémentation de service, `WcfCalculatorService`, est un service WCF qui implémente un contrat de service de base. Ce service WCF est hébergé dans une classe de service Windows appelée `WindowsCalculatorService`. Pour prétendre au titre de service Windows, la classe hérite de <xref:System.ServiceProcess.ServiceBase> et implémente les méthodes <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> et <xref:System.ServiceProcess.ServiceBase.OnStop>. Dans <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, un objet <xref:System.ServiceModel.ServiceHost> est créé pour le type `WcfCalculatorService` et ouvert. Dans <xref:System.ServiceProcess.ServiceBase.OnStop>, le ServiceHost est fermé en appelant la méthode <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> de l'objet <xref:System.ServiceModel.ServiceHost>. L’adresse de base de l’hôte est configurée à l’aide de l’élément [\<add >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) , qui est un enfant de [\<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), qui est un enfant de l’élément\<[Host >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) , qui est un enfant de l’élément\<[service >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) .  
  
 Le point de terminaison défini utilise l’adresse de base et une [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). L'exemple suivant illustre la configuration de l'adresse de base ainsi que le point de terminaison qui expose le CalculatorService.  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Une fois la solution générée, exécutez Setup. bat à partir d’une invite de commandes Visual Studio 2012 avec élévation de privilèges pour installer le service Windows à l’aide de l’outil installutil. exe. Le service doit apparaître dans Services.  
  
4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement AppFabric et exemples de persistance](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
