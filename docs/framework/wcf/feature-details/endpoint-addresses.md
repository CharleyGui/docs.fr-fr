---
title: Adresses de point de terminaison
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: 71358ed1c16c3c9b490a41f74dd6319af8eb2e7b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593527"
---
# <a name="endpoint-addresses"></a>Adresses de point de terminaison
Chaque point de terminaison a une adresse qui lui est associée et qui est utilisé pour localiser et identifier le point de terminaison. Cette adresse se compose à l'origine d'un URI (Uniform Resource Identifier) qui spécifie l'emplacement du point de terminaison. L’adresse de point de terminaison est représentée dans le modèle de programmation Windows Communication Foundation (WCF) par la <xref:System.ServiceModel.EndpointAddress> classe, qui contient une <xref:System.ServiceModel.EndpointAddress.Identity%2A> propriété facultative qui active l’authentification du point de terminaison par les autres points de terminaison qui échangent des messages avec celui-ci, ainsi qu’un ensemble de propriétés facultatives <xref:System.ServiceModel.EndpointAddress.Headers%2A> , qui définissent tous les autres en-têtes SOAP requis pour atteindre le service. Les en-têtes facultatifs fournissent des données d'adressage plus détaillées supplémentaires pour identifier ou interagir avec le point de terminaison de service. L'adresse d'un point de terminaison est représentée sur le câble comme une référence de point de terminaison WS-Addressing (EPR).  
  
## <a name="uri-structure-of-an-address"></a>Structure URI d'une adresse  
 L'URI d'adresse de la plupart des transports se compose de quatre parties. Par exemple, les quatre parties de l’URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` peuvent être déprésentées comme suit :  
  
- Mode`http:`
  
- Usinage`www.fabrikam.com`  
  
- (facultatif) Port : 322  
  
- Chemin d’accès : /mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>Définition de l'adresse d'un service  
 L'adresse du point de terminaison pour un service peut être spécifiée de manière impérative en utilisant le code ou de façon déclarative par la configuration. La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service. En général, il est plus pratique de définir des points de terminaison de service à l'aide de la configuration plutôt que du code. Le fait de conserver les informations de liaison et d’adressage hors du code leur permet de changer sans nécessiter de recompilation et de redéploiement de l’application.  
  
### <a name="defining-an-address-in-configuration"></a>Définition d'une adresse dans la configuration  
 Pour définir un point de terminaison dans un fichier de configuration, utilisez l' [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) élément. Pour plus d’informations et pour obtenir un exemple, consultez [spécification d’une adresse de point de terminaison](../specifying-an-endpoint-address.md).  
  
### <a name="defining-an-address-in-code"></a>Définition d'une adresse dans le code  
 Une adresse de point de terminaison peut être créée dans le code avec la classe <xref:System.ServiceModel.EndpointAddress>. Pour plus d’informations et pour obtenir un exemple, consultez [spécification d’une adresse de point de terminaison](../specifying-an-endpoint-address.md).  
  
### <a name="endpoints-in-wsdl"></a>Points de terminaison dans WSDL  
 Une adresse de point de terminaison peut aussi être représentée dans WSDL sous la forme d'un élément EPR WS-Addressing à l'intérieur de l'élément `wsdl:port` du point de terminaison correspondant. L'EPR contient l'adresse du point de terminaison ainsi que toutes les propriétés d'adresse. Pour plus d’informations et pour obtenir un exemple, consultez [spécification d’une adresse de point de terminaison](../specifying-an-endpoint-address.md).  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>Prise en charge de plusieurs liaisons IIS dans .NET Framework 3,5  
 Les fournisseurs de services Internet hébergent souvent de nombreuses applications sur le même serveur et le même site pour augmenter la densité du site et réduire le coût total de possession. Ces applications sont liées en général à des adresses de base différentes. Un site web IIS (Internet Information Services) peut contenir plusieurs applications. Les applications dans un site sont accessibles par le biais d'une ou de plusieurs liaisons IIS.  
  
 Les liaisons IIS fournissent deux informations : un protocole de liaison et des informations de liaison. Le protocole de liaison définit la méthode selon laquelle la communication se produit, et les informations de liaison sont les informations utilisées pour accéder au site.  
  
 L’exemple suivant affiche les composants qui peuvent être présents dans une liaison IIS :  
  
- Protocole de liaison : HTTP  
  
- Informations de liaison : adresse IP, port, en-tête de l’hôte  
  
 IIS peut spécifier plusieurs liaisons pour chaque site, ce qui génère plusieurs adresses de base pour chaque méthode. Avant le .NET Framework 3,5, WCF ne prenait pas en charge plusieurs adresses pour un schéma et, s’ils étaient spécifiés, a levé une <xref:System.ArgumentException> lors de l’activation.  
  
 La .NET Framework 3,5 permet aux fournisseurs de services Internet d’héberger plusieurs applications avec différentes adresses de base pour le même schéma sur le même site.  
  
 Par exemple, un site pourrait contenir les adresses de base suivantes :  
  
- `http://payroll.myorg.com/Service.svc`
  
- `http://shipping.myorg.com/Service.svc`
  
 Avec .NET Framework 3,5, vous spécifiez un filtre de préfixe au niveau du AppDomain dans le fichier de configuration. Pour ce faire, vous devez utiliser l' [\<baseAddressPrefixFilters>](../../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) élément, qui contient une liste de préfixes. Les adresses de base entrantes, fournies par IIS, sont filtrées selon la liste de préfixes facultative. Par défaut, lorsqu'un préfixe n'est pas spécifié, toutes les adresses sont transmises. La spécification du préfixe entraîne uniquement la transmission de l'adresse de base correspondante pour ce schéma.  
  
 Les éléments suivants sont un exemple de code de configuration qui utilise les filtres de préfixe.  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://payroll.myorg.com:8000"/>  
        <add prefix="http://shipping.myorg.com:8000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Dans l’exemple précédent, `net.tcp://payroll.myorg.com:8000` et `http://shipping.myorg.com:8000` sont les seules adresses de base, pour leurs schémas respectifs, qui sont transmises.  
  
 Le `baseAddressPrefixFilter` ne prend pas en charge de caractères génériques.  
  
 Les adresses de base fournies par IIS peuvent avoir des adresses liées à d'autres méthodes non présentes dans la liste `baseAddressPrefixFilters`. Ces adresses ne sont pas éliminées par filtrage.  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>Prise en charge de plusieurs liaisons IIS dans .NET Framework 4 et version ultérieure  
 À partir du .NET 4, vous pouvez activer la prise en charge de plusieurs liaisons dans IIS sans avoir à récupérer une seule adresse de base, en affectant au paramètre <xref:System.ServiceModel.ServiceHostingEnvironment> de <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> la valeur true. Cette prise en charge est limitée aux schémas de protocole HTTP.  
  
 Voici un exemple de code de configuration qui utilise multipleSiteBindingsEnabled sur [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) .  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Tout paramètre baseAddressPrefixFilters est ignoré, à la fois pour les protocoles HTTP et non HTTP, lorsque plusieurs liaisons de site sont activées à l'aide de ce paramètre.  
  
 Pour plus d’informations et pour obtenir des exemples, consultez [prise en charge de plusieurs liaisons de site IIS](supporting-multiple-iis-site-bindings.md) et <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> .  
  
## <a name="extending-addressing-in-wcf-services"></a>Extension de l'adressage dans les services WCF  
 Le modèle d’adressage par défaut des services WCF utilise l’URI d’adresse de point de terminaison aux fins suivantes :  
  
- Pour spécifier l'adresse d'écoute du service, l'emplacement où le point de terminaison écoute les messages.  
  
- Pour spécifier le filtre d'adresse SOAP, l'adresse à laquelle s'attend un point de terminaison sous la forme d'un en-tête SOAP.  
  
 Les valeurs pour chacun de ces objectifs peuvent être spécifiées séparément, en permettant plusieurs extensions d’adressage qui représentent des scénarios utiles :  
  
- Intermédiaires SOAP : un message envoyé par un client traverse un ou plusieurs services supplémentaires qui traitent le message avant qu'il atteigne sa dernière destination. Les intermédiaires SOAP peuvent effectuer différentes tâches, telles que la mise en cache, le routage, l’équilibrage des charges, ou la validation de schéma sur les messages. Ce scénario s'accomplit en envoyant des messages à une adresse physique distincte (`via`) qui cible l'intermédiaire plutôt qu'une adresse logique (`wsa:To`) ciblant la destination finale.  
  
- L'adresse d'écoute du point de terminaison est un URI privé dont la valeur est différente de sa propriété `listenURI`.  
  
 L'adresse de transport spécifiée par `via` est l'emplacement auquel un message doit être initialement envoyé pour atteindre une autre adresse distante spécifiée par le paramètre `to` où est localisé le service. Dans la plupart des scénarios Internet, l'URI `via` est identique à la propriété <xref:System.ServiceModel.EndpointAddress.Uri%2A> de l'adresse `to` finale du service. Vous ne pouvez différencier ces deux adresses que lorsque vous devez effectuer un routage manuel.  
  
### <a name="addressing-headers"></a>En-têtes d'adressage  
 Un point de terminaison peut être adressé par un ou plusieurs en-têtes SOAP en plus de son URI de base. Le jeu de scénarios où cette opération est utile est un jeu de scénarios intermédiaires SOAP où un point de terminaison requiert que les clients de ce point de terminaison incluent des en-têtes SOAP destinés à des intermédiaires.  
  
 Vous pouvez définir des en-têtes d'adresse personnalisés de deux manières, à l'aide du code ou de la configuration :  
  
- Dans le code, vous créez des en-têtes d'adresse personnalisés à l'aide de la classe <xref:System.ServiceModel.Channels.AddressHeader>, que vous utilisez ensuite dans la construction d'un <xref:System.ServiceModel.EndpointAddress>.  
  
- Dans Configuration, Custom [\<headers>](../../configure-apps/file-schema/wcf/headers.md) est spécifié en tant qu’enfants de l' [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) élément.  
  
 La configuration est généralement préférable au code, car elle vous permet de modifier les en-têtes après le déploiement.  
  
### <a name="custom-listening-addresses"></a>Adresses d'écoute personnalisées  
 Vous pouvez affecter à l'adresse d'écoute une valeur différente de l'URI du point de terminaison. Ce procédé est utile dans les scénarios intermédiaires où l'adresse SOAP à exposer est celle d'un intermédiaire SOAP public, alors que l'adresse où le point de terminaison écoute réellement est une adresse de réseau privé.  
  
 Vous pouvez spécifier une adresse d'écoute personnalisée à l'aide du code ou de la configuration :  
  
- Dans le code, spécifiez une adresse d'écoute personnalisée en ajoutant une classe <xref:System.ServiceModel.Description.ClientViaBehavior> à la collection de comportements du point de terminaison.  
  
- Dans Configuration, spécifiez une adresse d’écoute personnalisée avec l' `ListenUri` attribut de l’élément de service [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) .  
  
### <a name="custom-soap-address-filter"></a>Filtre d'adresse SOAP personnalisé  
 L'<xref:System.ServiceModel.EndpointAddress.Uri%2A> est utilisé conjointement avec toute propriété <xref:System.ServiceModel.EndpointAddress.Headers%2A> pour définir le filtre d'adresse SOAP d'un point de terminaison (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>). Par défaut, ce filtre vérifie qu'un message entrant a un en-tête de message `To` qui correspond à l'URI du point de terminaison et que tous les en-têtes de point de terminaison requis sont présents dans le message.  
  
 Dans certains scénarios, un point de terminaison reçoit tous les messages qui arrivent sur le transport sous-jacent, et pas seulement ceux avec l'en-tête `To` approprié. Pour activer cette fonction, l'utilisateur peut utiliser la classe <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>.  
  
## <a name="see-also"></a>Voir aussi

- [Spécification d’une adresse de point de terminaison](../specifying-an-endpoint-address.md)
- [Identité du service et authentification](service-identity-and-authentication.md)
