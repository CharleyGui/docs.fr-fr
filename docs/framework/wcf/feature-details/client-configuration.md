---
title: Configuration client
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 141b7f7fc04f98f267ce520544fb89451beac7b6
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463865"
---
# <a name="client-configuration"></a>Configuration client
Vous pouvez utiliser la configuration client de la Windows Communication Foundation (WCF) pour spécifier l’adresse, la liaison, le comportement et le contrat, les propriétés « ABC » du point de terminaison client, que les clients utilisent pour se connecter aux paramètres de service. [ \<L’élément>client](../../configure-apps/file-schema/wcf/client.md) a un [ \<critère de terminaison>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) élément dont les attributs sont utilisés pour configurer le point final ABC. Ces attributs sont discutés dans la section [Configuring Endpoints.](#configuring-endpoints)  
  
 Le [ \<critère d’évaluation>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) élément contient également une [ \<métadonnée>](../../configure-apps/file-schema/wcf/metadata.md) élément qui est utilisé pour spécifier les paramètres d’importation et d’exportation de métadonnées, un [ \<en-tête>](../../configure-apps/file-schema/wcf/headers.md) élément qui contient une collection d’en-têtes d’adresse personnalisé, et un [ \<élément>d’identité](../../configure-apps/file-schema/wcf/identity.md) qui permet l’authentification d’un point de terminaison par d’autres points d’évaluation échangeant des messages avec elle. Les [ \<en-têtes>](../../configure-apps/file-schema/wcf/headers.md) et [ \<l’identité>](../../configure-apps/file-schema/wcf/identity.md) éléments <xref:System.ServiceModel.EndpointAddress> font partie de l’article et sont discutés dans l’article [Adresses.](../../wcf/feature-details/endpoint-addresses.md) Des liens vers des sujets qui expliquent l’utilisation d’extensions de métadonnées sont fournis dans la section [Configuring Metadata.](#configuring-metadata)  
  
## <a name="configuring-endpoints"></a>Configuration des points de terminaison  
 La configuration du client est conçue pour permettre au client de spécifier un ou plusieurs points de terminaison, [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) chacun avec son propre nom, adresse et contrat, chacun faisant référence aux [ \<fixations>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) et les comportements>éléments de la configuration client à configurer ce critère d’évaluation. Le fichier de configuration client doit être nommé "App.config" parce que c’est le nom que le temps d’exécution WCF s’attend. L'exemple suivant illustre un fichier de configuration client.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
            <!-- Add another endpoint by adding another <endpoint> element. -->
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"
                 bypassProxyOnLocal="false"
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
          <!-- Configure this binding here. -->  
        </binding>  
          </wsHttpBinding>  
     </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 L'attribut `name` facultatif identifie de manière unique un point de terminaison pour un contrat donné. Il est utilisé par le <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> ou par le <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> pour spécifier quel point de terminaison est visé dans la configuration client et doit être chargé lorsqu'un canal est créé pour le desservir. Un nom de configuration\*de point de terminaison wildcard " est disponible et indique à la <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> méthode qu’il devrait charger n’importe quelle configuration de point de terminaison dans le fichier, à condition qu’il y ait précisément un disponible, et jette autrement une exception. Si cet attribut est omis, le point de terminaison correspondant est utilisé comme point de terminaison par défaut associé au type de contrat spécifié. La valeur par défaut pour l'attribut `name` est une chaîne vide qui est mise en correspondance comme tout autre nom.  
  
 Chaque point de terminaison doit avoir une adresse qui lui est associée pour pouvoir être localisé et identifié. L'attribut `address` peut être utilisé pour spécifier l'URL qui fournit l'emplacement du point de terminaison. Mais l'adresse d'un point de terminaison de service peut également être spécifiée dans du code en créant un URI et en l'ajoutant à <xref:System.ServiceModel.ServiceHost> qui utilise l'une des méthodes <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>. Pour plus d’informations, voir [Adresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Comme l’introduction l’indique, <xref:System.ServiceModel.EndpointAddress> les [ \<en-têtes>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) et [ \<l’identité>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) éléments font partie de la et sont également discutés dans le sujet [Adresses.](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
  
 L’attribut `binding` indique le type de liaison que le point de terminaison s’attend à utiliser lors de la connexion à un service. Ce type doit posséder une section de configuration inscrite s'il doit être référencé. Dans l’exemple précédent, il s’agit de la <xref:System.ServiceModel.WSHttpBinding> [ \<section wsHttpBinding>,](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) qui indique que le point final utilise un . Mais il peut y avoir plusieurs liaisons d’un type donné utilisables par le point de terminaison. Chacun d’eux [ \<](../../configure-apps/file-schema/wcf/bindings.md) a son propre élément de liaison>dans l’élément de type (contraignant). L’attribut `bindingconfiguration` est utilisé pour distinguer plusieurs liaisons du même type. Sa valeur est `name` assortie à l’attribut de [ \<l’élément>de liaison.](../../configure-apps/file-schema/wcf/bindings.md) Pour plus d’informations sur la façon de configurer une liaison client à l’aide de la configuration, voir [comment : Spécifier une liaison client dans la configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 L’attribut `behaviorConfiguration` est utilisé [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) pour spécifier quel comportement>de [ \<l’endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) le point de terminaison doit utiliser. Sa valeur est `name` assortie à l’attribut du [ \<comportement>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) élément. Pour un exemple d’utilisation de la configuration pour spécifier les comportements des clients, voir [Configurer les comportements des clients](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 L'attribut `contract` spécifie quel contrat le point de terminaison expose. Cette valeur correspond au <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> de <xref:System.ServiceModel.ServiceContractAttribute>. La valeur par défaut est le nom de type complet de la classe qui implémente le service.  
  
### <a name="configuring-metadata"></a>Configuration des métadonnées  
 Les [ \<métadonnées>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) élément est utilisée pour spécifier les paramètres utilisés pour enregistrer les extensions d’importation de métadonnées. Pour plus d’informations sur l’extension du système de métadonnées, voir [Extension du système de métadonnées](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Voir aussi

- [Points de terminaison : adresses, liaisons et contrats](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Configuration des comportements clients](../../../../docs/framework/wcf/configuring-client-behaviors.md)
