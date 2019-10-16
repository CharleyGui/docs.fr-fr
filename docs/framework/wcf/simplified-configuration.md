---
title: Configuration simplifiée
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 567f03e8f35ed72ba7e2a602bf47257158741fb3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321153"
---
# <a name="simplified-configuration"></a>Configuration simplifiée
La configuration des services de Windows Communication Foundation (WCF) peut être une tâche complexe. Il existe de nombreuses options différentes et il n'est pas toujours évident de déterminer les paramètres nécessaires. Alors que les fichiers de configuration augmentent la flexibilité des services WCF, ils sont également la source de nombreux problèmes difficiles à détecter. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] traite ces problèmes et permet de réduire la taille et la complexité de la configuration de service.  
  
## <a name="simplified-configuration"></a>Configuration simplifiée  
 Dans les fichiers de configuration du service WCF, la section < `system.serviceModel` > contient un élément < `service` > pour chaque service hébergé. L’élément < `service` > contient une collection d’éléments de < `endpoint` > qui spécifient les points de terminaison exposés pour chaque service et éventuellement un ensemble de comportements de service. Les éléments de > < `endpoint` spécifient l’adresse, la liaison et le contrat exposés par le point de terminaison, et éventuellement la liaison des comportements de configuration et de point de terminaison. La section > < `system.serviceModel` contient également un élément < `behaviors` > qui vous permet de spécifier des comportements de service ou de point de terminaison. L’exemple suivant montre la section < `system.serviceModel` > d’un fichier de configuration.  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] facilite la configuration d’un service WCF en supprimant la nécessité de l’élément < `service` >. Si vous n’ajoutez pas de section < `service` > ou si vous ajoutez des points de terminaison dans une < `service` > section et que votre service ne définit aucun point de terminaison par programmation, un jeu de points de terminaison par défaut est automatiquement ajouté à votre service, un pour chaque adresse de base de service et pour chaque contrat implémenté par votre service. Dans chacun de ces points de terminaison, l’adresse du point de terminaison correspond à l’adresse de base, la liaison est déterminée par le schéma d’adresse de base et le contrat est celui implémenté par votre service. Si vous n’avez pas besoin de spécifier de comportements de point de terminaison ou de service, ni de modifier un paramètre de liaison, il est inutile de spécifier un fichier de configuration de service. Si un service implémente deux contrats et que l'hôte active à la fois les transports HTTP et TCP, l'hôte de service crée quatre points de terminaison par défaut, un pour chaque contrat utilisant chaque transport. Pour créer des points de terminaison par défaut, l'hôte de service doit savoir quelles liaisons utiliser. Ces paramètres sont spécifiés dans une section < `protocolMappings` > dans la section < `system.serviceModel` >. La section < `protocolMappings` > contient une liste de schémas de protocole de transport mappés aux types de liaison. L’hôte du service utilise les adresses de base qui lui sont transmises pour déterminer quelle liaison utiliser. L’exemple suivant utilise l’élément < `protocolMappings` >.  
  
> [!WARNING]
> Le fait de modifier les éléments de configuration par défaut, comme les liaisons ou les comportements, peut affecter les services définis dans les niveaux inférieurs de la hiérarchie de configuration, car ces derniers peuvent utiliser ces liaisons et comportements par défaut. C’est pourquoi, la personne qui modifie les liaisons et comportements par défaut doit savoir que ces changements peuvent affecter d’autres services dans la hiérarchie.  
  
> [!NOTE]
> Les services hébergés dans les services IIS (Internet Information Services) ou WAS (Windows Process Activation Service) utilisent le répertoire virtuel comme leur adresse de base.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 Dans l'exemple précédent, un point de terminaison avec une adresse de base commençant par le schéma « http » utilise la liaison <xref:System.ServiceModel.BasicHttpBinding>. Un point de terminaison avec une adresse de base commençant par le schéma « net.tcp » utilise la liaison <xref:System.ServiceModel.NetTcpBinding>. Vous pouvez remplacer des paramètres dans un fichier local App.config ou Web.config.  
  
 Chaque élément de la section < `protocolMappings` > doit spécifier un schéma et une liaison. Éventuellement, il peut spécifier un attribut `bindingConfiguration` qui spécifie une configuration de liaison dans la section < `bindings` > du fichier de configuration. Si aucun attribut `bindingConfiguration` n’est spécifié, la configuration de liaison anonyme du type de liaison approprié est utilisée.  
  
 Les comportements de service sont configurés pour les points de terminaison par défaut à l’aide des sections anonymes < `behavior` > dans < sections `serviceBehaviors` >. Tous les éléments sans nom < `behavior` > dans < `serviceBehaviors` > sont utilisés pour configurer les comportements de service. Par exemple, le fichier de configuration suivant permet la publication de métadonnées de service pour tous les services qui se trouvent dans l'hôte.  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 Les comportements de point de terminaison sont configurés à l’aide des sections anonyme < `behavior` > dans < sections `serviceBehaviors` >.  
  
 L'exemple suivant est un fichier de configuration équivalent à celui qui se trouve au début de cette rubrique. Il utilise le modèle de configuration simplifié.  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
> Cette fonctionnalité concerne uniquement la configuration du service WCF, non la configuration du client. La plupart de temps, la configuration cliente WCF est générée par un outil comme svcutil.exe ou en ajoutant une référence de service à partir de Visual Studio. Si vous configurez manuellement un client WCF, vous devez ajouter un élément \<client > à la configuration et spécifier tous les points de terminaison que vous souhaitez appeler.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration des services à l’aide de fichiers de configuration](configuring-services-using-configuration-files.md)
- [Configuration de liaisons pour les services](configuring-bindings-for-wcf-services.md)
- [Configuration des liaisons fournies par le système](./feature-details/configuring-system-provided-bindings.md)
- [Configuration des services](configuring-services.md)
- [Configuration des services WCF](configuring-services.md)
- [Configuration des services WCF dans le code](configuring-wcf-services-in-code.md)
