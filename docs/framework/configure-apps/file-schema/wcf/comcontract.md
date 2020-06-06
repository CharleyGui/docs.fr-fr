---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: b499294af71ba230dcf985d4af1d013b1ca260cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850029"
---
# \<comContract>
Spécifie un contrat de service d'intégration COM+.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|contract|Chaîne qui contient le type de contrat.|  
|name|Chaîne qui contient le type de nom.|  
|espace de noms|Chaîne qui contient l'espace de noms du contrat.|  
|requiresSession|Valeur booléenne qui spécifie si le contrat ne peut être utilisé que sur des liaisons de session. Lorsque le service est initialisé, l’exécution d’intégration garantit que ce paramètre est cohérent avec le type de liaison à utiliser. Une exception est générée en cas de conflit avec une ou plusieurs liaisons du contrat. Si cette propriété a la valeur `false`, qu'un canal unidirectionnel est utilisé et qu'un paramètre [out] est présent, une exception est également levée.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|persistableTypes|Tous les types persistants.|  
|userDefinedTypes|Collection de types définis par l'utilisateur (UDT) à inclure dans le contrat de service.|  
|exposedMethods|Collection de méthodes COM+ exposées lorsque l’interface sur un composant COM+ est exposée en tant que service Web.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|comContracts|Contient une collection d’éléments `comContract`.|  
  
## <a name="remarks"></a>Remarques  
 Les contrats de service d’intégration COM+ sont actuellement restreints à l' `http://tempuri.org` espace de noms et le nom de contrat est dérivé de l’interface com de prise en charge. Toutefois, vous pouvez spécifier des alternatives à l'aide de la section `comContracts`, ainsi que l'élément `comContract` dans le fichier de configuration. Par exemple, vous pouvez utiliser la configuration suivante pour spécifier l'espace de noms, le nom de contrat et les types définis par l'utilisateur à inclure, ainsi que d'autres paramètres pour un contrat de service.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 Lorsque le service est initialisé, les espaces de noms et les noms de contrat spécifiés sont appliqués aux descriptions de service générées.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](comcontracts.md)
- [Intégration à des applications COM+](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Comment : configurer des paramètres de service COM+](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
