---
title: Configuration du service d'activation de processus de Windows pour son utilisation dans Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 2f84afba72e5260a44726dcc812401da5475679f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284093"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Configuration du service d'activation de processus de Windows pour son utilisation dans Windows Communication Foundation

Cette rubrique décrit les étapes requises pour configurer le service d’activation des processus Windows (également appelé WAS) dans Windows Vista pour héberger des services Windows Communication Foundation (WCF) qui ne communiquent pas sur des protocoles réseau HTTP. Les sections suivantes définissent les étapes pour cette configuration :  
  
- Installez (ou confirmez l’installation de) les composants d’activation WCF requis.  
  
- Créez un site WAS avec les liaisons de protocole réseau que vous souhaitez utiliser ou ajoutez un nouveau protocole qui crée une liaison vers un site existant.  
  
- Créez une application pour héberger vos services et permettre à cette application d'utiliser les protocoles réseau requis.  
  
- Générez un service WCF qui expose un point de terminaison non-HTTP.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Configuration d’un site avec des liaisons non HTTP  

 Pour utiliser une liaison non HTTP avec le service WAS, la liaison de site doit être ajoutée à la configuration WAS. Le magasin de configurations pour le service WAS est le fichier applicationHost.config situé dans le répertoire %windir%\system32\inetsrv\config. Ce magasin de configurations est partagé à la fois par le service WAS et le service IIS 7.0.  
  
 applicationHost.config est un fichier texte XML qui peut être ouvert avec un éditeur de texte standard (tel que le Bloc-notes). Toutefois, l’outil de configuration de ligne de commande IIS 7,0 (appcmd.exe) est la méthode recommandée pour ajouter des liaisons de site non-HTTP.  
  
 La commande suivante ajoute une liaison de site net.tcp au site Web par défaut à l'aide de appcmd.exe (cette commande est entrée comme une ligne unique).  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Cette commande ajoute la nouvelle liaison net.tcp au site web par défaut en ajoutant la ligne indiquée ci-dessous au fichier applicationHost.config.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Activation de l'utilisation des protocoles non HTTP par une application  

 Vous pouvez activer ou désactiver le protocolsat réseau individuel au niveau de l’application. La commande suivante montre comment activer à la fois les protocoles HTTP et net.tcp pour une application qui s'exécute dans le `Default Web Site`.  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 La liste des Protocoles activés peut également être définie dans l' \<applicationDefaults> élément de la configuration XML du site stocké dans ApplicationHost.config.  
  
 Le code XML suivant issu du fichier applicationHost.config illustre un site lié à la fois à des protocoles HTTP et non HTTP. La configuration supplémentaire requise pour la prise en charge de protocoles non HTTP est appelée avec des commentaires.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
      <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
      </application>  
      <bindings>  
            <!-- The following two lines are added by the command. -->
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults
      applicationPool="DefaultAppPool"
      <!-- The following line is inserted by the command. -->
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 Si vous tentez d'activer un service en utilisant WAS pour l'activation non-HTTP et vous n'avez pas installé et configuré WAS, l'erreur suivante s'affiche :  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Si cette erreur s'affiche, assurez-vous que WAS pour l'activation non HTTP est installé et configuré correctement. Pour plus d’informations, consultez [Comment : installer et configurer des composants d’activation WCF](how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Génération d'un service WCF qui utilise le service WAS pour l'activation non HTTP  

 Une fois que vous avez effectué les étapes d’installation et de configuration de WAS (voir [Comment : installer et configurer des composants d’activation WCF](how-to-install-and-configure-wcf-activation-components.md)), la configuration d’un service pour utiliser was pour l’activation est semblable à la configuration d’un service hébergé dans IIS.  
  
 Pour obtenir des instructions détaillées sur la création d’un service WCF activé par WAS, consultez [Comment : héberger un service WCF dans was](how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement dans le service d'activation de processus de Windows (WAS, Windows Process Activation Service)](hosting-in-windows-process-activation-service.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](/previous-versions/appfabric/ee677189(v=azure.10))
