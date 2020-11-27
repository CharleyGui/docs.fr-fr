---
title: Configuration des services à l'aide de fichiers de configuration
description: Découvrez comment un fichier de configuration pour un service WCF vous donne la possibilité de fournir des données de comportement de point de terminaison et de service pendant le déploiement.
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 25a6891564054878e7bdf7f43d431547ea1dee6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253347"
---
# <a name="configuring-services-using-configuration-files"></a>Configuration des services à l'aide de fichiers de configuration

La configuration d’un service Windows Communication Foundation (WCF) avec un fichier de configuration vous donne la possibilité de fournir des données sur le point de terminaison et le comportement de service au point de déploiement au lieu de le faire au moment de la conception. Cette rubrique esquisse les principales techniques disponibles.  
  
 Un service WCF peut être configuré à l’aide de la technologie de configuration .NET Framework. Le plus souvent, les éléments XML sont ajoutés au fichier Web.config pour un site Internet Information Services (IIS) qui héberge un service WCF. Les éléments vous permettent de modifier des détails, tels que les adresses de point de terminaison (les adresses réelles qui communiquent avec le service) à partir de chaque ordinateur individuel. En outre, WCF comprend plusieurs éléments fournis par le système qui vous permettent de sélectionner rapidement les fonctionnalités les plus basiques pour un service. À partir de .NET Framework 4, WCF est fourni avec un nouveau modèle de configuration par défaut qui simplifie les exigences de configuration WCF. Si vous ne fournissez aucune configuration WCF pour un service particulier, le runtime configure automatiquement votre service avec certains points de terminaison standard et la liaison/comportement par défaut. Dans la pratique, l’écriture de la configuration est une partie importante de la programmation des applications WCF.  
  
 Pour plus d’informations, consultez [Configuration des liaisons pour les services](configuring-bindings-for-wcf-services.md). Pour obtenir la liste des éléments les plus couramment utilisés, consultez [liaisons fournies](system-provided-bindings.md)par le système. Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [Configuration simplifiée](simplified-configuration.md) et [Configuration simplifiée pour les services WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
> Si vous déployez des scénarios côte à côte où deux versions différentes d'un service sont déployées, vous devez spécifier les noms partiels des assemblys référencés dans les fichiers de configuration. En effet, le fichier de configuration est partagé entre toutes les versions d'un service et elles peuvent s'exécuter sous différentes versions du .NET Framework.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration : Web.config et App.config  

 WCF utilise le système de configuration System.Configfiguration du .NET Framework.  
  
 Quand vous configurez un service dans Visual Studio, utilisez un fichier Web.config ou un fichier App.config pour spécifier les paramètres. Le choix du nom de fichier de configuration est déterminé par l'environnement d'hébergement que vous choisissez pour le service. Si vous utilisez IIS pour héberger votre service, utilisez un fichier Web.config. Si vous utilisez tout autre environnement d'hébergement, utilisez un fichier App.config.  
  
 Dans Visual Studio, le fichier nommé App.config est utilisé pour créer le fichier de configuration final. Le nom final réellement utilisé pour la configuration dépend du nom de l'assembly. Par exemple, un assembly nommé "Cohowinery.exe" porte le nom de fichier de configuration final "Cohowinery.exe.config". Toutefois, vous devez seulement modifier le fichier App.config. Les modifications apportées à ce fichier sont automatiquement répercutées dans le fichier final de configuration de l'application, à la compilation.  
  
 Pour utiliser un fichier App.config, le système de configuration fusionne le fichier App.config avec le contenu du fichier Machine.config lorsque l'application démarre et la configuration est appliquée. Ce mécanisme autorise la définition de paramètres à l'échelle de l'ordinateur dans le fichier Machine.config. Le fichier App.config peut être utilisé pour substituer les paramètres du fichier Machine.config ; vous pouvez également verrouiller les paramètres dans le fichier Machine.config afin qu'ils soient utilisés. Dans le cas de Web.config, le système de configuration fusionne les fichiers Web.config dans tous les répertoires qui mènent au répertoire de l'application dans la configuration qui est appliquée. Pour plus d’informations sur la configuration et les priorités de paramètres, consultez les rubriques de l' <xref:System.Configuration> espace de noms.  
  
## <a name="major-sections-of-the-configuration-file"></a>Sections majeures du fichier de configuration  

 Les sections principales dans le fichier de configuration incluent les éléments suivants.  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
> Les sections de liaison et de comportement sont facultatives et sont incluses uniquement si besoin est.  
  
### <a name="the-services-element"></a>\<services>Élément  

 L'élément `services` contient les caractéristiques pour tous les services que l'application héberge. À partir du modèle de configuration simplifié dans .NET Framework 4, cette section est facultative.  
  
 [\<services>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>\<service>Élément  

 Chaque service a les attributs suivants :  
  
- `name`. Spécifie le type qui fournit une implémentation d'un contrat de service. Il s'agit d'un nom complet composé de l'espace de noms, d'un point et du nom du type. Par exemple, `"MyNameSpace.myServiceType"`.  
  
- `behaviorConfiguration`. Spécifie le nom de l'un des éléments `behavior` recherché dans l'élément `behaviors` . Le comportement spécifié gouverne des actions comme l'autorisation de l'emprunt d'identité par le service. Si sa valeur correspond au nom vide ou qu'aucun `behaviorConfiguration` n'est fourni, l'ensemble de comportements de service par défaut est ajouté au service.  
  
- [\<service>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>\<endpoint>Élément  

 Chaque point de terminaison requiert une adresse, une liaison et un contrat, représentés par les attributs suivants :  
  
- `address`. Spécifie l'URI (Uniform Resource Identifier) du service, qui peut être une adresse absolue ou une adresse donnée relativement à l'adresse de base du service. Si l'attribut a une valeur de chaîne vide, il indique que le point de terminaison est disponible à l'adresse de base spécifiée lors de la création de <xref:System.ServiceModel.ServiceHost> pour le service.  
  
- `binding`. En général, spécifie une liaison fournie par le système comme <xref:System.ServiceModel.WSHttpBinding>, mais peut également spécifier une liaison définie par l'utilisateur. La liaison spécifiée détermine le type de transport, de sécurité et d'encodage utilisé, et si des sessions fiables, des transactions ou la diffusion en continu sont pris en charge ou activés.  
  
- `bindingConfiguration`. Si les valeurs par défaut d'une liaison doivent être modifiées, cela peut être fait en configurant l'élément `binding` approprié dans l'élément `bindings` . Cet attribut doit avoir la même valeur que l'attribut `name` de l'élément `binding` utilisé pour modifier les valeurs par défaut. Si aucun nom n'est donné ou qu'aucun `bindingConfiguration` n'est spécifié dans la liaison, la liaison par défaut du type de liaison est utilisée dans le point de terminaison.  
  
- `contract`. Spécifie l'interface qui définit le contrat. C'est l'interface implémentée dans le type Common Language Runtime (CLR) spécifié par l'attribut `name` de l'élément `service` .  
  
- [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a>\<bindings>Élément  

 L'élément `bindings` contient les caractéristiques pour toutes les liaisons qui peuvent être utilisées par tout point de terminaison défini dans un service.  
  
 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>\<binding>Élément  

 L'élément `binding` contenus dans l'élément `bindings` peuvent être une des liaisons fournies par le système (consultez [System-Provided Bindings](system-provided-bindings.md)) ou une liaison personnalisée (consultez [Custom Bindings](./extending/custom-bindings.md)). L'élément `binding` a un attribut `name` qui correspond la liaison avec le point de terminaison spécifié dans l'attribut `bindingConfiguration` de l'élément `endpoint` . Si aucun nom n'est spécifié, cette liaison correspond à la valeur par défaut de ce type de liaison.  
  
Pour plus d’informations sur la configuration des services et des clients, consultez [Configuration des services WCF](configuring-services.md).
  
 [\<binding>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a>\<behaviors>Élément  

 C'est un élément conteneur des éléments `behavior` qui définissent les comportements pour un service.  
  
 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>\<behavior>Élément  

 Chaque `behavior` élément est identifié par un `name` attribut et fournit un comportement fourni par le système, tel que <`throttling`> ou un comportement personnalisé. Si aucun nom n'est donné, cet élément behavior correspond au service par défaut ou au comportement du point de terminaison.  
  
 [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Comment : utiliser les configurations de liaison et de comportement  

 WCF facilite le partage des configurations entre des points de terminaison à l’aide d’un système de référence dans la configuration. Plutôt qu'assigner directement des valeurs de configuration à un point de terminaison, les valeurs de configuration connexes à la liaison sont groupées dans les éléments `bindingConfiguration` dans la section `<binding>` . Une configuration de liaison est un groupe nommé de paramètres sur une liaison. Les points de terminaison peuvent référencer ensuite l'élément `bindingConfiguration` par nom.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint
          address="myAddress" binding="basicHttpBinding"
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint
          address="myAddress2" binding="basicHttpBinding"
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint
          address="myAddress3" binding="basicHttpBinding"
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 L'attribut `name` de l'élément `bindingConfiguration` est défini dans l'élément `<binding>` . `name`Doit être une chaîne unique dans l’étendue du type de liaison (dans ce cas, le [<BasicHttpBinding \> ](../configure-apps/file-schema/wcf/basichttpbinding.md)ou une valeur vide pour faire référence à la liaison par défaut). Le point de terminaison est relié à la configuration en affectant l'attribut `bindingConfiguration` à cette chaîne.  
  
 Un attribut `behaviorConfiguration` est implémenté de la même façon, comme illustré dans l'exemple suivant.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 Notez que l'ensemble par défaut des comportements de service est ajouté au service. Ce système permet aux points de terminaison de partager des configurations communes sans redéfinir les paramètres. Si une étendue à l’échelle de l’ordinateur est requise, créez la liaison ou la configuration du comportement dans Machine.config. Les paramètres de configuration sont disponibles dans tous les fichiers de App.config. L' [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) facilite la création des configurations.  
  
## <a name="behavior-merge"></a>Fusion des comportements  

 La fonctionnalité de fusion des comportements facilite la gestion des comportements lorsque vous souhaitez définir des comportements communs à utiliser régulièrement. Elle vous permet de spécifier des comportements à différents niveaux de la hiérarchie de configuration et d'hériter les comportements de service de plusieurs niveaux de la hiérarchie de configuration. Pour illustrer le fonctionnement, supposons que vous disposez de la structure de répertoires virtuels suivante dans IIS :  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 Et votre `~\Web.config` fichier présente le contenu suivant :  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Votre fichier Web.config enfant qui se trouve à l'emplacement ~\Child\Web.config a le contenu suivant :  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Le service situé à l'emplacement ~\Child\Service.svc se comportera comme s'il contenait les comportements serviceDebug et serviceMetadata. Le service qui se trouve à l'emplacement ~\Service.svc aura uniquement le comportement serviceDebug. Les deux collections de comportements portant le même nom (dans ce cas la chaîne vide) sont fusionnées.  
  
 Vous pouvez également effacer les collections de comportements à l’aide de la \<clear> balise et supprimer des comportements individuels de la collection à l’aide de la \<remove> balise. Par exemple, les deux configurations suivantes provoquent uniquement le comportement serviceMetadata du service enfant :  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 La fusion des comportements est effectuée pour les collections de comportements sans nom, tel qu'illustré ci-dessus, ainsi que pour les collections de comportements nommées.  
  
 La fusion de comportement fonctionne dans l’environnement d’hébergement IIS, dans lequel Web.config fichiers sont fusionnés hiérarchiquement avec le fichier Web.config racine et machine.config. Mais il fonctionne également dans l’environnement d’application, où machine.config pouvez fusionner avec le fichier App.config.  
  
 La fusion des comportements s'applique à la fois aux comportements de points de terminaison et aux comportements de services dans une configuration.  
  
 Si une collection de comportements enfants contient un comportement qui est déjà présent dans la collection de comportements parents, le comportement enfant remplace le comportement parent. Par conséquent, si une collection de comportements parente avait `<serviceMetadata httpGetEnabled="False" />` et une collection de comportements enfants avait `<serviceMetadata httpGetEnabled="True" />` , le comportement enfant remplace le comportement parent dans la collection de comportements et httpGetEnabled serait « true ».  
  
## <a name="see-also"></a>Voir aussi

- [Configuration simplifiée](simplified-configuration.md)
- [Configuration des services WCF](configuring-services.md)
- [\<service>](../configure-apps/file-schema/wcf/service.md)
- [\<binding>](../configure-apps/file-schema/wcf/bindings.md)
