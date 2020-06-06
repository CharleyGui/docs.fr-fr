---
title: <system.serviceModel>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 2125ce00b0e23f2e93ff251549f9c1276892b16b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399452"
---
# \<system.serviceModel>
Cette section de configuration contient tous les éléments de configuration de l’Windows Communication Foundation (WCF) ServiceModel.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <behaviors>
  </behaviors>
  <bindings>
  </bindings>
  <client>
  </client>
  <comContracts>
  </comContracts>
  <commonBehaviors>
  </commonBehaviors>
  <diagnostics>
  </diagnostics>
  <extensions>
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>
  <serviceHostingEnvironment>
  </serviceHostingEnvironment>
  <services>
  </services>
  <standardEndpoints>
  </standardEndpoints>
  <tracking>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucune  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|Cette section définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.  Chaque collection définit des éléments de comportement consommés respectivement par les points de terminaison et les services. Chaque élément de comportement est identifié par son attribut `name` unique.|  
|[\<bindings>](bindings.md)|Cette section contient une collection de liaisons standard et personnalisées. Chaque entrée est identifiée par son `name` unique. Les services utilisent les liaisons en les liant à l’aide de `name`.|  
|[\<client>](client.md)|Cette section contient la liste des points de terminaison utilisés par un client pour se connecter à un service.|  
|[\<comContracts>](comcontracts.md)|Cette section définit des contrats COM activés pour interagir avec WCF et COM.|  
|[\<commonBehaviors>](commonbehaviors.md)|Cette section peut uniquement être définie dans le fichier machine.config. Elle définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.  Chaque collection définit des éléments de comportement consommés respectivement par tous les services et points de terminaison WCF sur l’ordinateur.  Si un comportement est défini dans les sections `<commonBehaviors>` et `<behaviors>`, le comportement dans la section \<behaviors> a la préférence.|  
|[\<diagnostics>](diagnostics.md)|Cette section contient les paramètres des fonctionnalités de diagnostic de WCF. L'utilisateur peut activer/désactiver le suivi, les compteurs de performance et le fournisseur WMI et ajouter des filtres de messages personnalisés.|  
|[\<extensions>](extensions-section.md)|Cette section contient une collection d’extensions qui permettent à l’utilisateur de créer des liaisons, des comportements et d’autres aspects d’extensions définis par l’utilisateur.|  
|[\<protocolMapping>](protocolmapping.md)|Cette section définit un ensemble de mappages de protocole par défaut entre des schémas de protocole de transport (par exemple, http, net.tcp, net.pipe, etc.) et des liaisons WCF.|  
|[\<routing>](routing.md)|Cette section définit un ensemble de filtres de routage, qui déterminent le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu’un filtre correspond.|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Cette section définit le type instancié par l'environnement d'hébergement de service pour un transport particulier. Si cette section est vide, le type par défaut est utilisé.|  
|[\<services>](services.md)|Cette section contient une collection de services. Pour chaque service défini dans l'assembly, cet élément contient un élément `service` indiquant les paramètres du service.|  
|[\<standardEndpoints>](standardendpoints.md)|Cette section définit une collection de points de terminaison standard, qui sont des points de terminaison préconfigurés réutilisables. Un point de terminaison standard possède un ou plusieurs attributs d’adresse, de liaison et de contrat ayant une valeur fixe. Par exemple, dans le point de terminaison de découverte, le contrat est fixe. Vous pouvez également utiliser des points de terminaison standard pour étendre le point de terminaison de service avec de nouvelles propriétés, ce qui revient à définir des liaisons personnalisées.|
|[\<tracking>](tracking-of-wcf.md)|Cette section définit les paramètres de suivi d’un service de Workflow.|

### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|\<configuration>|Élément racine correspondant à tous les éléments de configuration qui se trouvent dans un fichier de configuration .NET.|  
  
## <a name="remarks"></a>Remarques  
 WCF n’ajoute pas d’éléments aux sections de configuration d’autres produits.  
  
 Les services WCF sont définis dans la `services` section du fichier de configuration. Un assembly peut contenir n'importe quel nombre de services. Chacun dispose de sa propre section de configuration de `service`. Cette section et son contenu définissent le contrat, le comportement et les points de terminaison du service en question.  
  
 Seul l'attribut `name` d'un service est requis.  Par défaut, le nom d'un service décrit le type CLR sous-jacent utilisé pour implémenter un service ; toutefois, vous pouvez modifier la propriété ConfigurationName d'un <xref:System.ServiceModel.ServiceContractAttribute> pour remplacer la spécification de type CLR.  
  
 L'attribut `behaviorConfiguration` est facultatif. Il identifie le comportement utilisé par un service. Le comportement spécifié par cet attribut doit être lié à un comportement de service défini dans l'étendue du même fichier de configuration (c'est-à-dire le même fichier ou un fichier parent).  
  
 Chaque service expose un ou plusieurs points de terminaison définis dans un élément `endpoint`. Chaque point de terminaison possède sa propre adresse et sa propre liaison. Toutes les liaisons utilisées dans le fichier de configuration doivent être définies dans l'étendue du fichier.  
  
 Les liaisons sont liées aux points de terminaison grâce à la combinaison des attributs `name` et `bindingConfiguration`. L’attribut `binding` définit la section dans laquelle la liaison est définie. L'attribut `bindingConfiguration` définit parmi les liaisons configurées figurant dans la section de liaison celle qui est utilisée. Une section de liaison peut définir plusieurs liaisons configurées.  
  
## <a name="example"></a>Exemple  
 Voici un exemple de fichier de configuration WCF.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <!-- List of Behaviors -->
    </behaviors>
    <client>
      <!-- List of Endpoints -->
    </client>
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
    </diagnostics>
    <serviceHostingEnvironment>
      <!-- List of entries -->
    </serviceHostingEnvironment>
    <comContracts>
      <!-- List of COM+ Contracts -->
    </comContracts>
    <services>
      <!-- List of Services -->
    </services>
    <bindings>
      <!-- List of Bindings -->
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
