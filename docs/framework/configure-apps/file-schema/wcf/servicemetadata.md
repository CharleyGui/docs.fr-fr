---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: c421273d1d08db047a51f1f1e4f9d6c908f12986
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84201782"
---
# \<serviceMetadata>
Spécifie la publication de métadonnées de service et des informations associées.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceMetadata>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceMetadata externalMetadataLocation="String"
                 httpGetBinding="String"
                 httpGetBindingConfiguration="String"
                 httpGetEnabled="Boolean"
                 httpGetUrl="String"
                 httpsGetBinding="String"
                 httpsGetBindingConfiguration="String"
                 httpsGetEnabled="Boolean"
                 httpsGetUrl="String"
                 policyVersion="Policy12/Policy15" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|externalMetadataLocation|Uri contenant l'emplacement d'un fichier WSDL renvoyé à l'utilisateur en réponse aux demandes WSDL et MEX au lieu du WSDL généré automatiquement. Lorsque cet attribut n'est pas défini, le WSDL par défaut est renvoyé. La valeur par défaut est une chaîne vide.|  
|httpGetBinding|Chaîne qui spécifie le type de la liaison qui sera utilisée pour la récupération de métadonnées via HTTP GET. Ce paramètre est facultatif. En l'absence de spécification, les liaisons par défaut seront utilisées.<br /><br /> La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>. En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpGetBindingConfiguration|Chaîne qui définit le nom de la liaison spécifiée dans l’attribut `httpGetBinding`, qui fait référence aux informations de configuration supplémentaires de cette liaison. Le même nom doit être défini dans la section `<bindings>`.|  
|httpGetEnabled|Valeur booléenne indiquant si les métadonnées de service correspondant à la récupération doivent être publiées à l'aide d'une demande HTTP/Get. Par défaut, il s’agit de `false`.<br /><br /> Si l'attribut httpGetUrl n'est pas spécifié, l'adresse utilisée pour publier les métadonnées est celle du service à laquelle est ajouté le suffixe « ? wsdl ». Par exemple, si l’adresse du service est `http://localhost:8080/CalculatorService` , l’adresse de métadonnées http/obtenir est `http://localhost:8080/CalculatorService?wsdl` .<br /><br /> Si cette propriété est `false` , ou si l’adresse du service n’est pas basée sur http ou HTTPS, «  ? WSDL » est ignoré.|  
|httpGetUrl|URI indiquant l'adresse utilisée pour publier les métadonnées correspondant à la récupération à l'aide d'une demande HTTP/Get. Si l'URI relatif est spécifié, il sera traité comme étant relatif à l'adresse de base du service.|  
|httpsGetBinding|Chaîne qui spécifie le type de la liaison qui sera utilisée pour la récupération de métadonnées via HTTPS GET. Ce paramètre est facultatif. En l'absence de spécification, les liaisons par défaut seront utilisées.<br /><br /> La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>. En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpsGetBindingConfiguration|Chaîne qui définit le nom de la liaison spécifiée dans l’attribut `httpsGetBinding`, qui fait référence aux informations de configuration supplémentaires de cette liaison. Le même nom doit être défini dans la section `<bindings>`.|  
|httpsGetEnabled|Valeur booléenne indiquant si les métadonnées de service correspondant à la récupération doivent être publiées à l'aide d'une demande HTTPS/Get. Par défaut, il s’agit de `false`.<br /><br /> Si l'attribut httpsGetUrl n'est pas spécifié, l'adresse utilisée pour publier les métadonnées est celle du service à laquelle est ajouté le suffixe « ? wsdl ». Par exemple, si l’adresse du service est « https://localhost:8080/CalculatorService », l’adresse des métadonnées http/obtenir est « https://localhost:8080/CalculatorService?wsdl ».<br /><br /> Si cette propriété est `false` , ou si l’adresse du service n’est pas basée sur http ou HTTPS, «  ? WSDL » est ignoré.|  
|httpsGetUrl|URI indiquant l'adresse utilisée pour publier les métadonnées afin d'effectuer une récupération à l'aide d'une demande HTTPS/Get.|  
|policyVersion|Chaîne indiquant la version de la spécification WS-Policy utilisée. Cet attribut est de type <xref:System.ServiceModel.Description.PolicyVersion>.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucune  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## <a name="remarks"></a>Remarques  
 Cet élément de configuration permet de contrôler les métadonnées qui publient les fonctionnalités d’un service. Pour empêcher la divulgation non intentionnelle de métadonnées de service potentiellement sensibles, la configuration par défaut pour les services Windows Communication Foundation (WCF) désactive la publication de métadonnées. Ce comportement est sécurisé par défaut, mais il signifie également que vous ne pouvez pas utiliser d'outil d'importation de métadonnées (tel que Svcutil.exe) pour générer le code client requis pour appeler le service, à moins que le comportement de publication des métadonnées du service soit activé explicitement dans la configuration. À l'aide de cet élément de configuration, vous pouvez activer ce comportement de publication pour votre service.  
  
 Pour obtenir un exemple détaillé de la configuration de ce comportement, consultez [comportement de publication des métadonnées](../../../wcf/samples/metadata-publishing-behavior.md).  
  
 Les attributs facultatifs `httpGetBinding` et `httpsGetBinding` vous permettent de configurer les liaisons utilisées pour la récupération de métadonnées via HTTP GET (ou HTTPS GET). S’ils ne sont pas spécifiés, les liaisons par défaut (`HttpTransportBindingElement` dans le cas de HTTP et `HttpsTransportBindingElement` dans le cas de HTTPS) sont utilisées pour la récupération des métadonnées. Notez que vous ne pouvez pas utiliser ces attributs avec les liaisons WCF intégrées. La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>. En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
 Pour éviter l'exposition d'un service aux utilisateurs malveillants, il est possible de sécuriser le transfert à l'aide du mécanisme HTTPS (SSL over HTTP). Pour ce faire, vous devez d'abord lier un certificat X.509 approprié à un port spécifique sur l'ordinateur qui héberge le service. (Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).) Ensuite, ajoutez cet élément à la configuration du service et affectez à l’attribut la valeur `httpsGetEnabled` `true` . Enfin, affectez l'URL du point de terminaison des métadonnées du service à l'attribut `httpsGetUrl`, comme indiqué dans l'exemple suivant.  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="NewBehavior">
      <serviceMetadata httpsGetEnabled="true"
                       httpsGetUrl="https://myComputerName/myEndpoint" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant configure un service pour exposer des métadonnées à l’aide de l' \<serviceMetadata> élément. Il configure également un point de terminaison afin d'exposer le contrat `IMetadataExchange` comme implémentation d'un protocole WS-MetadataExchange (MEX). L’exemple utilise `mexHttpBinding`, qui est une liaison standard équivalente à `wsHttpBinding` dans laquelle le mode de sécurité a la valeur `None`. Une adresse relative de « MEX » est utilisée dans le point de terminaison, qui, lorsqu’elle est résolue par rapport à l’adresse de base des services, se traduit par une adresse de point de terminaison `http://localhost/servicemodelsamples/service.svc/mex` .  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <!-- The serviceMetadata behavior publishes metadata through the IMetadataExchange contract. When this behavior is
               present, you can expose this contract through an endpoint as shown above. Setting httpGetEnabled to true publishes
               the service's WSDL at the <baseaddress>?wsdl eg. http://localhost/servicemodelsamples/service.svc?wsdl -->
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Comportements de sécurité](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Metadata Publishing Behavior](../../../wcf/samples/metadata-publishing-behavior.md)
