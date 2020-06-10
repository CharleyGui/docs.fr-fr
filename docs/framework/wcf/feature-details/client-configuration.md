---
title: Configuration client
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 2d17438095e65ccf922061c03e406bab35b07c5d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593657"
---
# <a name="client-configuration"></a>Configuration client
Vous pouvez utiliser la configuration du client Windows Communication Foundation (WCF) pour spécifier l’adresse, la liaison, le comportement et le contrat, les propriétés « ABC » du point de terminaison client, que les clients utilisent pour se connecter aux points de terminaison de service. L' [\<client>](../../configure-apps/file-schema/wcf/client.md) élément a un [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) élément dont les attributs sont utilisés pour configurer le point de terminaison ABC. Ces attributs sont décrits dans la section [Configuration des points de terminaison](#configuring-endpoints) .  
  
 L' [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) élément contient également un [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) élément qui est utilisé pour spécifier les paramètres d’importation et d’exportation des métadonnées, un [\<headers>](../../configure-apps/file-schema/wcf/headers.md) élément qui contient une collection d’en-têtes d’adresse personnalisés et un [\<identity>](../../configure-apps/file-schema/wcf/identity.md) élément qui permet l’authentification d’un point de terminaison par d’autres points de terminaison qui échangent des messages avec lui. Les [\<headers>](../../configure-apps/file-schema/wcf/headers.md) [\<identity>](../../configure-apps/file-schema/wcf/identity.md) éléments et font partie de <xref:System.ServiceModel.EndpointAddress> et sont décrits dans l’article [adresses](endpoint-addresses.md) . Des liens vers des rubriques qui expliquent l’utilisation des extensions de métadonnées sont fournis dans la section [Configuration des métadonnées](#configuring-metadata) .  
  
## <a name="configuring-endpoints"></a>Configuration des points de terminaison  
 La configuration client est conçue pour permettre au client de spécifier un ou plusieurs points de terminaison, chacun avec son propre nom, adresse et contrat, avec chacun référençant [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) les [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) éléments et dans la configuration client à utiliser pour configurer ce point de terminaison. Le fichier de configuration client doit être nommé « App. config », car il s’agit du nom attendu par le runtime WCF. L'exemple suivant illustre un fichier de configuration client.  
  
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
  
 L'attribut `name` facultatif identifie de manière unique un point de terminaison pour un contrat donné. Il est utilisé par le <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> ou par le <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> pour spécifier quel point de terminaison est visé dans la configuration client et doit être chargé lorsqu'un canal est créé pour le desservir. Un nom de configuration de point de terminaison générique « \* » est disponible et indique à la <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> méthode qu’il doit charger toute configuration de point de terminaison dans le fichier, à condition qu’il y ait précisément un disponible et lève une exception. Si cet attribut est omis, le point de terminaison correspondant est utilisé comme point de terminaison par défaut associé au type de contrat spécifié. La valeur par défaut pour l'attribut `name` est une chaîne vide qui est mise en correspondance comme tout autre nom.  
  
 Chaque point de terminaison doit avoir une adresse qui lui est associée pour pouvoir être localisé et identifié. L'attribut `address` peut être utilisé pour spécifier l'URL qui fournit l'emplacement du point de terminaison. Mais l'adresse d'un point de terminaison de service peut également être spécifiée dans du code en créant un URI et en l'ajoutant à <xref:System.ServiceModel.ServiceHost> qui utilise l'une des méthodes <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>. Pour plus d’informations, consultez la rubrique [adresses](endpoint-addresses.md). Comme l’indique la présentation, [\<headers>](../../configure-apps/file-schema/wcf/headers.md) les [\<identity>](../../configure-apps/file-schema/wcf/identity.md) éléments et font partie de <xref:System.ServiceModel.EndpointAddress> et sont également traités dans la rubrique [adresses](endpoint-addresses.md) .  
  
 L’attribut `binding` indique le type de liaison que le point de terminaison s’attend à utiliser lors de la connexion à un service. Ce type doit posséder une section de configuration inscrite s'il doit être référencé. Dans l’exemple précédent, il s’agit de la [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) section, qui indique que le point de terminaison utilise un <xref:System.ServiceModel.WSHttpBinding> . Mais il peut y avoir plusieurs liaisons d’un type donné utilisables par le point de terminaison. Chacun de ces éléments a son propre [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément dans l’élément de type (Binding). L’attribut `bindingconfiguration` est utilisé pour distinguer plusieurs liaisons du même type. Sa valeur est mise en correspondance avec l' `name` attribut de l' [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément. Pour plus d’informations sur la configuration d’une liaison cliente à l’aide de la configuration, consultez [Comment : spécifier une liaison cliente dans la configuration](../how-to-specify-a-client-binding-in-configuration.md).  
  
 L' `behaviorConfiguration` attribut est utilisé pour spécifier le [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) point de [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) terminaison à utiliser. Sa valeur est mise en correspondance avec l' `name` attribut de l' [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) élément. Pour obtenir un exemple d’utilisation de la configuration pour spécifier les comportements des clients, consultez [Configuration des comportements des clients](../configuring-client-behaviors.md).  
  
 L'attribut `contract` spécifie quel contrat le point de terminaison expose. Cette valeur correspond au <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> de <xref:System.ServiceModel.ServiceContractAttribute>. La valeur par défaut est le nom de type complet de la classe qui implémente le service.  
  
### <a name="configuring-metadata"></a>Configuration des métadonnées  
 L' [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) élément est utilisé pour spécifier les paramètres utilisés pour enregistrer des extensions d’importation de métadonnées. Pour plus d’informations sur l’extension du système de métadonnées, consultez [extension du système de métadonnées](../extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Voir aussi

- [Points de terminaison : adresses, liaisons et contrats](endpoints-addresses-bindings-and-contracts.md)
- [Configuration des comportements clients](../configuring-client-behaviors.md)
