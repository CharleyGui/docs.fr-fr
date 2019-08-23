---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 366def5d0f4cc82b0ff0a5127701b0b5a6adb6a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940502"
---
# <a name="webhttp"></a>\<webHttp>
Cet élément spécifie le <xref:System.ServiceModel.Description.WebHttpBehavior> d'un point de terminaison via la configuration. Ce comportement, lorsqu’il est utilisé conjointement avec [ \<WebHttpBinding >](webhttpbinding.md) la liaison standard, active le modèle de programmation Web pour un service Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<behaviors>  
\<endpointBehaviors>  
\<> de comportement  
\<webHttp>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Lorsque cette propriété a la valeur `true`, l'infrastructure WCF détermine le meilleur format à utiliser. La sélection automatique du format est désactivée par défaut à des fins de compatibilité descendante. La sélection automatique du format peut être activée par programme ou par configuration.|  
|defaultBodyStyle|Spécifie le style du corps par défaut des messages retournés. Pour plus d’informations, <xref:System.ServiceModel.Web.WebMessageBodyStyle> consultez et [mise en forme http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|Spécifie le format de réponse sortante par défaut des messages. Pour plus d’informations, consultez [mise en forme http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).|  
|faultExceptionEnabled|Obtient ou définit l’indicateur qui spécifie si FaultException est généré quand une erreur de serveur interne (code d’état HTTP : 500) se produit.|  
|helpEnabled|Obtient ou définit une valeur qui détermine si la page d'aide est activée.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Spécifie le jeu de comportements du point de terminaison.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Intégration d’AJAX et prise en charge de JSON](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
