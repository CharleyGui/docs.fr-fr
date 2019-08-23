---
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 032139b714aa11079c7ee8610c332e404b3981ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918996"
---
# <a name="exposedmethod"></a>\<exposedMethod>
Représente une méthode COM+ exposée lorsque l'interface sur un composant COM+ est exposée en tant que service Web.  
  
 \<system.ServiceModel>  
\<comContracts>  
\<comContract>  
\<methods>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Chaîne qui contient la méthode COM+ exposée lorsque l'interface sur un composant COM+ est exposée comme un service Web.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<exposedMethods>](exposedmethods.md)|Collection d' [ \<éléments > ExposedMethod](exposedmethod.md) .|  
  
## <a name="remarks"></a>Notes  
 Il est possible d'utiliser l'outil de configuration d'intégration COM+ (ComSvcConfig.exe) pour ajouter des méthodes spécifiques issues d'une interface COM afin qu'elles apparaissent sur le contrat de service généré.  
  
 Par exemple, vous pouvez utiliser la commande suivante pour ajouter les trois méthodes nommées issues de l'interface COM `IFinances` sur le composant financier `ItemOrders` au contrat de service généré.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 Quand vous exécutez également le fichier ComSvcConfig. exe, il génère le contrat de service suivant, qui répertorie les méthodes mentionnées précédemment comme [ \<ExposedMethod >](exposedmethod.md) Elements.  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 Au moment de l’initialisation du service, le runtime tente de générer un contrat de service en reflétant et en ajoutant uniquement les méthodes incluses dans la liste des éléments de [ \<> ExposedMethod](exposedmethod.md) . Une trace est produite pour chaque méthode d'interface qui n'est pas incluse sur le contrat de service.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [Intégration à des applications COM+](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Guide pratique pour Configurer les paramètres du service COM+](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
