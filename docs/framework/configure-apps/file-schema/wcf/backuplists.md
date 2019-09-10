---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5f2bb030d13389e15cb44f1ddff3b8168b4f2140
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850259"
---
# <a name="backuplists"></a>\<backupLists>
Représente une section de configuration pour la définition d'un ensemble de services de sauvegarde utilisés dans la gestion des erreurs. Chaque élément enfant est une liste de sauvegarde qui énumère un ensemble de points de terminaison que vous souhaitez que le service de routage utilise si le point de terminaison principal est inaccessible. Si le premier point de terminaison de la liste est inactif, le service de routage bascule automatiquement sur le suivant dans la liste.  Vous disposez ainsi d’une méthode rapide pour renforcer la fiabilité de votre application sans avoir à apprendre à votre application cliente à gérer des modèles complexes ou à rechercher l’emplacement de tous vos services déployés.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de routage**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<backupLists >**  
  
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
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<filter>](filter.md)|Contient une liste de points de terminaison que vous souhaitez que le service de routage utilise si le point de terminaison principal n’est pas accessible. .|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<routing>](routing.md)|Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles Envoyer des messages à lorsqu’un filtre correspond.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
