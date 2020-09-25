---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 8f4dcf8f7d71cfa2ed9944822d7cce974e7f1979
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201562"
---
# \<backupList>

Représente une section de configuration permettant de définir une liste de sauvegarde qui énumère un ensemble de points de terminaison que le service de routage doit utiliser au cas où il est impossible d'atteindre le point de terminaison primaire. Si le premier point de terminaison de la liste est inactif, le service de routage bascule automatiquement sur le suivant dans la liste.  Vous disposez ainsi d’une méthode rapide pour renforcer la fiabilité de votre application sans avoir à apprendre à votre application cliente à gérer des modèles complexes ou à rechercher l’emplacement de tous vos services déployés.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Chaîne qui spécifie le nom permettant d'identifier la liste de points de terminaison.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filter>](filter.md)||  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<routing>](routing.md)|Liste de points de terminaison de sauvegarde.|  
  
## <a name="remarks"></a>Notes  

 Cette section contient une collection ordonnée de points de terminaison auxquels un message sera transmis si une exception de communication se produit lors de l'envoi au point de terminaison primaire.  
  
 Si un envoi au point de terminaison principal listé dans l' `endpointName` attribut de [\<add>](add-of-entries.md) échoue avec une exception de communication, le service de routage tente d’envoyer le message au premier point de terminaison de cette section de configuration. Si l’opération échoue également avec une exception de communication, le service de routage essaie d’envoyer le message au point de terminaison suivant contenu dans cette section jusqu’à ce que la tentative d’envoi aboutisse, retourne une erreur autre qu’une exception de communication, ou que tous les points de terminaison de la collection retournent une erreur.  
  
 Dans l’exemple suivant, si un envoi au point de terminaison principal nommé « destination » retourne une exception de communication, le service tente d’envoyer le message à « alternateServiceQueue ». Si cette tentative retourne également une exception de communication, le service de routage essaiera d’envoyer le message au point de terminaison suivant dans la collection.  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
