---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399560"
---
# \<serviceThrottling>
Spécifie le mécanisme de limitation de requêtes d'un service Windows Communication Foundation (WCF).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|maxConcurrentCalls|Entier positif qui limite le nombre de messages actuellement traités dans <xref:System.ServiceModel.ServiceHost>. Les appels excédentaires sont mis en file d'attente. Affecter 0 à cette valeur équivaut à lui affecter la valeur Int32.MaxValue. La valeur par défaut est 16 * nombre de processeurs.|  
|maxConcurrentInstances|Entier positif qui limite le nombre d'objets <xref:System.ServiceModel.InstanceContext> exécutés à un moment donné sur <xref:System.ServiceModel.ServiceHost>. Les demandes de création d'instances supplémentaires sont mises en file d'attente et traitées lorsqu'un emplacement se libère. La valeur par défaut est la somme de maxConcurrentSessions et MaxConcurrentCalls.|  
|maxConcurrentSessions|Entier positif qui limite le nombre de sessions qu'un objet <xref:System.ServiceModel.ServiceHost> peut accepter.<br /><br /> Le service acceptera des connexions une fois la limite atteinte, mais seuls les canaux ne dépassant pas la limite seront actifs (les messages seront lus à partir du canal). Affecter 0 à cette valeur équivaut à lui affecter la valeur Int32.MaxValue. La valeur par défaut est 100 * nombre de processeurs.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## <a name="remarks"></a>Remarques  
 Les contrôles de limitation de requêtes limitent le nombre d'appels, d'instances ou de sessions simultanés pour empêcher une surconsommation des ressources.  
  
 Un suivi est écrit à chaque fois que la valeur des attributs est atteinte. Le premier suivi est écrit en tant qu'avertissement.  
  
## <a name="example"></a>Exemple  
 L'exemple de configuration suivant spécifie que le service restreint le nombre maximal d'appels simultanés à 2 et le nombre maximal d'instances simultanées à 10. Pour obtenir un exemple détaillé de l’exécution de cet exemple, consultez [limitation](../../../wcf/samples/throttling.md).  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [Utilisation de ServiceThrottlingBehavior pour contrôler les performances du service WCF](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
