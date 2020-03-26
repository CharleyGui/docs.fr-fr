---
title: Configuration simplifiée
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 4e316290c045b75896c61e36c1646440c18678e2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249628"
---
# <a name="simplified-configuration"></a>Configuration simplifiée
La configuration des services de la Windows Communication Foundation (WCF) peut être une tâche complexe. Il existe de nombreuses options différentes et il n'est pas toujours évident de déterminer les paramètres nécessaires. Bien que les fichiers de configuration augmentent la flexibilité des services WCF, ils sont également la source de nombreux problèmes difficiles à trouver. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] traite ces problèmes et permet de réduire la taille et la complexité de la configuration de service.  
  
## <a name="simplified-configuration"></a>Configuration simplifiée  
 Dans les fichiers de configuration de `system.serviceModel` service WCF, la section> `service` <contient un élément <> pour chaque service hébergé. L’élément `service` <> contient une collection d’éléments `endpoint` <> qui spécifient les points de terminaison exposés pour chaque service et un ensemble de comportements de service. Les éléments `endpoint` <> spécifient l’adresse, la liaison et le contrat exposés par le point de terminaison, ainsi que la configuration et les comportements de point de terminaison qui l’ont d’option. La section `system.serviceModel` <> contient également un élément `behaviors`> <qui vous permet de spécifier des comportements de service ou de point de terminaison. L’exemple suivant montre la `system.serviceModel` section <> d’un fichier de configuration.  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]facilite la configuration d’un service WCF en supprimant `service` l’exigence pour l’élément> <. Si vous n’ajoutez pas `service` de <> section ou n’ajoutez pas `service` de points de terminaison dans une section <> et que votre service ne définit pas de façon programmatique les paramètres de fin, un ensemble de paramètres par défaut est automatiquement ajouté à votre service, un pour chaque adresse de base de service et pour chaque contrat implémenté par votre service. Dans chacun de ces points de terminaison, l’adresse du point de terminaison correspond à l’adresse de base, la liaison est déterminée par le schéma d’adresse de base et le contrat est celui implémenté par votre service. Si vous n’avez pas besoin de spécifier de comportements de point de terminaison ou de service, ni de modifier un paramètre de liaison, il est inutile de spécifier un fichier de configuration de service. Si un service implémente deux contrats et que l'hôte active à la fois les transports HTTP et TCP, l'hôte de service crée quatre points de terminaison par défaut, un pour chaque contrat utilisant chaque transport. Pour créer des points de terminaison par défaut, l'hôte de service doit savoir quelles liaisons utiliser. Ces paramètres sont spécifiés dans `protocolMappings` une section <> dans `system.serviceModel` la section <>. La section `protocolMappings` <> contient une liste des protocoles de transport cartographiés aux types contraignants. L’hôte du service utilise les adresses de base qui lui sont transmises pour déterminer quelle liaison utiliser. L’exemple suivant utilise `protocolMappings` l’élément <>.  
  
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
  
 Chaque élément de la `protocolMappings` section> <doit spécifier un régime et une liaison. En option, il `bindingConfiguration` peut spécifier un attribut qui `bindings` spécifie une configuration de liaison dans la section <> du fichier de configuration. Si aucun attribut `bindingConfiguration` n’est spécifié, la configuration de liaison anonyme du type de liaison approprié est utilisée.  
  
 Les comportements de service sont configurés pour les `behavior` paramètres par défaut en utilisant des `serviceBehaviors` sections anonymes <> dans <sections>. Tout <sans nom `behavior`> éléments dans <`serviceBehaviors`> sont utilisés pour configurer les comportements de service. Par exemple, le fichier de configuration suivant permet la publication de métadonnées de service pour tous les services qui se trouvent dans l'hôte.  
  
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
  
 Les comportements de point de terminaison `behavior` sont configurés en utilisant des `serviceBehaviors` sections anonymes> <dans <sections>.  
  
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
> Cette fonctionnalité concerne uniquement la configuration du service WCF, non la configuration du client. La plupart de temps, la configuration cliente WCF est générée par un outil comme svcutil.exe ou en ajoutant une référence de service à partir de Visual Studio. Si vous configurez manuellement un client WCF, \<vous devrez ajouter un élément> client à la configuration et spécifier tous les paramètres que vous souhaitez appeler.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration des services à l'aide de fichiers de configuration](configuring-services-using-configuration-files.md)
- [Configuration de liaisons pour les services](configuring-bindings-for-wcf-services.md)
- [Configuration des liaisons fournies par le système](./feature-details/configuring-system-provided-bindings.md)
- [Configuration des services](configuring-services.md)
- [Configuration des services WCF](configuring-services.md)
- [Configuration des services WCF dans le code](configuring-wcf-services-in-code.md)
