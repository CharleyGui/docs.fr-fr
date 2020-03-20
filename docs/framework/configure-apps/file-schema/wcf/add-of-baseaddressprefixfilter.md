---
title: <add> de <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 8fdae02b558708a9b3f4535123752dce12dd5cf5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153138"
---
# <a name="add-of-baseaddressprefixfilter"></a>\<ajouter> de \<baseAddressPrefixFilter>
Représente un élément de configuration qui spécifie un filtre de passage, qui fournit un mécanisme pour choisir les liaisons appropriées des services d’information Internet (IIS) lors de l’hébergement d’une application de la Fondation de communication Windows (WCF) dans l’IIS.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ajouter>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|prefix|URI utilisé pour correspondre à une partie d'une adresse de base.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|Une collection d’éléments de configuration qui spécifient les filtres de passage, qui fournissent un mécanisme pour choisir les liaisons IIS appropriées lors de l’hébergement d’une application De la Fondation de communication Windows (WCF) dans l’IIS.|  
  
## <a name="remarks"></a>Notes   
 Un filtre de préfixe permet aux fournisseurs d'hébergement partagé de spécifier les URI que le service doit utiliser. Il permet aux hôtes partagés d'héberger plusieurs applications avec différentes adresses de base pour la même méthode sur le même site.  
  
 Les sites Web IIS sont des conteneurs d'applications virtuelles qui contiennent des répertoires virtuels. L’application dans un site est accessible par le biais d’une ou de plusieurs liaisons IIS. Les liaisons IIS fournissent deux informations : un protocole de liaison et des informations de liaison. Le protocole de liaison (par exemple, HTTP) définit le modèle sur lequel la communication se produit, tandis que les informations de liaison (par exemple, adresse IP, port, en-tête de l'hôte) contiennent les données servant à accéder au site.  
  
 IIS prend en charge la spécification de plusieurs liaisons IIS pour chaque site, ce qui génère plusieurs adresses de base pour chaque méthode. Étant donné qu’un service WCF hébergé sous un site permet de lier une seule adresse de base pour chaque schéma, vous pouvez utiliser la fonction de filtre préfixe pour choisir l’adresse de base requise du service hébergé. Les adresses de base entrantes, fournies par IIS, sont filtrées selon le filtre de la liste de préfixes facultative.  
  
 Par exemple, votre site peut contenir les adresses de base suivantes :
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Vous pouvez utiliser le fichier de configuration suivant pour spécifier un filtre de préfixe au niveau AppDomain.  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 Dans cet exemple, `net.tcp://test1.fabrikam.com:8000` et `http://test2.fabrikam.com:9000` sont les seules adresses de base pouvant être transmises pour leur modèle respectif.  
  
 Par défaut, si aucun préfixe n'est spécifié, toutes les adresses sont transmises. La spécification du préfixe autorise uniquement la transmission de l'adresse de base correspondante pour ce modèle.  
  
> [!NOTE]
> Le filtre ne prend pas en charge les caractères génériques. En outre, les adresses de base fournies par IIS peuvent avoir des adresses liées à d'autres modèles non présents dans la liste `baseAddressPrefixFilters`. Ces adresses ne sont pas éliminées par filtrage.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hébergement](../../../wcf/feature-details/hosting.md)
