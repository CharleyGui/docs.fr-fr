---
title: <endpoint>, élément
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 71ddb3b860870ee8feeeb36c3f64fa7bfebb0f10
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925825"
---
# <a name="endpoint-element"></a>\<élément de > de point de terminaison
Spécifie la liaison, le contrat et les propriétés d’adresse d’un point de terminaison de service, utilisé pour exposer des services.  
  
 \<system.ServiceModel>  
\<service>  
\<endpoint>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|adresse|Chaîne qui contient l'adresse du point de terminaison. L'adresse peut être spécifiée comme une adresse absolue ou relative. Si une adresse relative est fournie, l’hôte doit fournir une adresse de base appropriée au schéma de transport utilisé dans la liaison. Si une adresse n'est pas configurée, l'adresse de base est l'adresse pour ce point de terminaison.<br /><br /> La valeur par défaut est une chaîne vide.|  
|behaviorConfiguration|Chaîne qui contient le nom du comportement à utiliser au point de terminaison.|  
|liaison|Attribut de chaîne requis indiquant le type de liaison à utiliser. Ce type doit posséder une section de configuration inscrite pour pouvoir être référencé. Il est inscrit en fonction du nom de la section et non en fonction du nom du type de la liaison.|  
|bindingConfiguration|Chaîne qui spécifie le nom de la liaison à utiliser lorsque le point de terminaison est instancié. Le nom de liaison doit être dans la portée, au niveau où le point de terminaison est défini. La valeur par défaut est une chaîne vide.<br /><br /> Cet attribut est utilisé conjointement à `binding` pour référencer une configuration de liaison spécifique dans le fichier de configuration. Définissez cet attribut si vous essayez d’utiliser une liaison personnalisée. Sinon, une exception peut être levée.|  
|bindingName|Chaîne qui spécifie le nom qualifié unique de la liaison pour l’exportation de définition à travers WSDL. La valeur par défaut est une chaîne vide.|  
|bindingNamespace|Chaîne qui spécifie le nom qualifié de l’espace de noms de la liaison pour l’exportation de définition à travers WSDL. La valeur par défaut est une chaîne vide.|  
|contrat|Chaîne qui indique le contrat exposé par ce point de terminaison. L'assembly doit implémenter le type de contrat. Si une implémentation de service implémente un seul type de contrat, cette propriété peut alors être omise. La valeur par défaut est une chaîne vide.|  
|endpointConfiguration|Chaîne qui spécifie le nom du point de terminaison standard défini par l'attribut `kind`, qui fait référence aux informations de configuration supplémentaires de ce point de terminaison standard. Le même nom doit être défini dans la section `<standardEndpoints>`.|  
|isSystemEndpoint|Valeur booléenne qui spécifie si un point de terminaison est un point de terminaison d'infrastructure.|  
|kind|Chaîne qui spécifie le type de point de terminaison standard appliqué. Le type doit être inscrit dans la section `<extensions>` ou dans machine.config. Si rien n'est spécifié, un point de terminaison de service commun est créé.|  
|listenUriMode|Spécifie la manière dont le transport traite le `ListenUri` fourni sur lequel le service effectue son écoute. Les valeurs valides sont les suivantes :<br /><br /> -Explicit<br />-Unique<br /><br /> La valeur par défaut est Explicit.|  
|listenUri|Chaîne qui spécifie l'URI au niveau duquel le point de terminaison de service effectue son écoute. La valeur par défaut est une chaîne vide.|  
|name|Attribut facultatif. Chaîne qui spécifie le nom du point de terminaison du service. La valeur par défaut correspond à la concaténation du nom de la liaison et de celui de la description du contrat. Les services peuvent disposer de plusieurs points de terminaison, l'attribut `name` du point de terminaison est donc différent du nom du service.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<headers>](headers.md)|Collection d'en-têtes d'adresses.|  
|[\<identity>](identity.md)|Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<service>](service.md)|Section de configuration qui définit une liste des points de terminaison auxquels un client peut se connecter.|  
  
## <a name="example"></a>Exemples  
 Il s'agit d'un exemple de configuration de point de terminaison de service.  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [Terminaison Adresses, liaisons et contrats](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Guide pratique : Créer un point de terminaison de service dans la configuration](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
