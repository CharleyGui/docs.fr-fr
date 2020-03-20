---
title: Configuration de liaisons pour les services Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: e7ee1a8ce358c77e46db39af67bd9dc20114fb3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174821"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Configuration de liaisons pour les services Windows Communication Foundation
Lorsque vous créez une application, vous souhaitez souvent confier des décisions à l'administrateur après le déploiement de l'application. Par exemple, il n'existe souvent aucune façon de savoir à l'avance ce que sera une adresse de service ou un URI (Uniform Resource Identifier). Au lieu de d'encoder de manière irréversible une adresse, il est préférable de permettre à un administrateur de le faire après avoir créé un service. Cette souplesse est obtenue par le biais de la configuration.  
  
> [!NOTE]
> Utilisez [l’outil utilitaire de métadonnées De ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) avec le `/config` commutateur pour créer rapidement des fichiers de configuration.  
  
## <a name="major-sections"></a>Sections principales  
 Le système de configuration de la Windows Communication Foundation`serviceModel`(WCF) comprend les trois sections principales suivantes ( , `bindings`et `services`):  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a>Éléments ServiceModel  
 Vous pouvez utiliser la section `system.ServiceModel` délimitée par l’élément pour configurer un type de service avec un ou plusieurs paramètres, ainsi que des paramètres pour un service. Ensuite, chaque point de terminaison peut être configuré avec une adresse, un contrat et une liaison. Pour plus d’informations sur les points de terminaison, voir [Aperçu de la création de point final](endpoint-creation-overview.md). Si aucun point de terminaison n'est spécifié, le runtime ajoute des points de terminaison par défaut. Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [Configuration simplifiée](simplified-configuration.md) et [Configuration simplifiée pour les services WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
 Une liaison spécifie des transports (HTTP, TCP, canaux, Message Queuing ) et des protocoles (sécurité, fiabilité, flux de transaction) et se compose d’éléments de liaison, dont chacun spécifie un aspect de la manière dont un point de terminaison communique avec le monde.  
  
 Par exemple, spécifier [ \<l’élément de base de>dehttpBinding](../configure-apps/file-schema/wcf/basichttpbinding.md) indique utiliser HTTP comme transport pour un point de terminaison. Cela permet de rattacher le point de terminaison au moment de l'exécution lorsque le service qui utilise ce point de terminaison est ouvert.  
  
 Il existe deux types de liaisons : les liaisons prédéfinies et les liaisons personnalisées. Les liaisons prédéfinies contiennent des combinaisons utiles d’éléments utilisés dans des scénarios courants. Pour une liste de types de liaison prédéfinis que WCF fournit, voir [Liaisons fournies par le système](system-provided-bindings.md). Si aucune collection de liaison prédéfinie n’a la combinaison correcte de fonctionnalités dont une application de service a besoin, vous pouvez construire des liaisons personnalisées pour satisfaire les exigences de l’application. Pour plus d’informations sur les fixations personnalisées, voir [ \<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).  
  
 Les quatre exemples suivants illustrent les configurations de liaison les plus courantes utilisées pour la mise en place d’un service WCF.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Spécification d’un point de terminaison pour utiliser un type de liaison  
 Le premier exemple montre comment spécifier un point de terminaison configuré avec une adresse, un contrat et une liaison.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 Dans cet exemple, l'attribut `name` indique à quel type de service la configuration est destinée. Lorsque vous créez un service dans votre code avec le contrat `HelloWorld`, il est initialisé avec tous les points de terminaison définis dans l'exemple de configuration. Si l’assemblage ne met en `name` œuvre qu’un seul contrat de service, l’attribut peut être omis parce que le service utilise le seul type disponible. L'attribut utilise une chaîne, qui doit être dans le format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 L'attribut `address` spécifie l'URI que d'autres points de terminaison utilisent pour communiquer avec le service. L’URI peut être un chemin d’accès absolu ou relatif. Si une adresse relative est fournie, l’hôte est censé fournir une adresse de base appropriée au schéma de transport utilisé dans la liaison. Si une adresse n'est pas configurée, l'adresse de base est l'adresse pour ce point de terminaison.  
  
 L'attribut `contract` spécifie le contrat que ce point de terminaison expose. Le type d'implémentation de service doit implémenter le type de contrat. Si une implémentation de service implémente un seul type de contrat, cette propriété peut alors être omise.  
  
 L’attribut de `binding` sélectionne une liaison prédéfinie ou personnalisée à utiliser pour ce point de terminaison spécifique. Un point de terminaison qui ne sélectionne pas explicitement de liaison utilise la sélection de liaison par défaut, qui correspond à `BasicHttpBinding`.  
  
#### <a name="modifying-a-predefined-binding"></a>Modification d'une liaison prédéfinie  
 Dans l'exemple suivant, une liaison prédéfinie est modifiée. Elle peut alors être utilisée pour configurer tout point de terminaison dans le service. La liaison est modifiée en affectant 1 seconde à la valeur <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A>. Notez que la propriété retourne un objet <xref:System.TimeSpan>.  
  
 Cette liaison modifiée se trouve dans la section consacrée aux liaisons. Cette liaison modifiée peut maintenant être utilisée lors de la création de tout point de terminaison en définissant l'attribut `binding` dans l'élément `endpoint`.  
  
> [!NOTE]
> Si vous donnez un nom particulier à la liaison, le `bindingConfiguration` spécifié dans le point de terminaison du service doit lui correspondre.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a>Configuration d'un comportement à appliquer à un service  
 Dans l'exemple ci-dessous, un comportement spécifique est configuré pour le type de service. L’élément `ServiceMetadataBehavior` est utilisé pour permettre à [l’outil utilitaire De métadonnées (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) de Poser des questions sur le service et de générer des documents de langage de description des services Web (WSDL) à partir des métadonnées.  
  
> [!NOTE]
> Si vous donnez un nom particulier au comportement, le `behaviorConfiguration` spécifié dans la section du point de terminaison ou du service doit lui correspondre.  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />
    </behavior>  
</behaviors>  
<services>  
    <service
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 La configuration précédente permet à un client d'appeler et d'obtenir les métadonnées du service typé « HelloWorld ».  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Spécification d’un service avec deux points de terminaison qui utilisent des valeurs de liaison différentes  
 Dans ce dernier exemple, deux points de terminaison sont configurés pour le type de service `HelloWorld`. Chaque point de terminaison utilise un attribut personnalisé `bindingConfiguration` différent `basicHttpBinding`du même type de liaison (chacun modifie le ).  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding
        name="shortTimeout"  
        timeout="00:00:00:01"
     />  
     <basicHttpBinding
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 Vous pouvez obtenir le même comportement à l'aide de la configuration par défaut en ajoutant une section `protocolMapping` et en configurant les liaisons comme illustré dans l'exemple suivant.  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding
        name="shortTimeout"  
        timeout="00:00:00:01"
     />  
     <basicHttpBinding
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Configuration simplifiée](simplified-configuration.md)
- [Liaisons fournies par le système](system-provided-bindings.md)
- [Vue d'ensemble de la création de points de terminaison](endpoint-creation-overview.md)
- [Utilisation de liaisons pour configurer des services et des clients](using-bindings-to-configure-services-and-clients.md)
