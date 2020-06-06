---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 7a76e5a90fe3218bc0302501b71daa9de0b098bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854834"
---
# \<userDefinedType>
Représente un type défini par l'utilisateur (UDT) à inclure dans le contrat de service.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<userDefinedTypes>**](userdefinedtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userDefinedType>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<comContracts>
  <comContract>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`name`|Attribut facultatif qui contient une chaîne fournissant le nom de type lisible. Il n'est pas utilisé par l'exécution mais aide le lecteur à distinguer les types.|  
|`TypeDefID`|Chaîne GUID qui identifie le type UDT spécifique dans la bibliothèque de types inscrite.|  
|`TypeLibID`|Chaîne GUID qui identifie la bibliothèque de types inscrite définissant le type.|  
|`TypeLibVersion`|Chaîne qui identifie la version de la bibliothèque de types définissant le type.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`userDefinedTypes`|Collection d'éléments `userDefinedType`.|  
  
## <a name="remarks"></a>Remarques  
 Le runtime d'intégration COM+ crée des services en inspectant la bibliothèque de types. Lorsqu'un composant COM+ contient des méthodes qui passent un VARIANT, le système ne peut pas déterminer les types réels à passer avant l'exécution. Par conséquent, le passage d'un UDT dans un VARIANT échoue car ce n'est pas un type connu pour la sérialisation.  
  
 Pour contourner ce problème, vous pouvez ajouter les UDT au fichier de configuration afin qu'ils puissent être inclus comme types connus sur le contrat de service approprié. Pour ce faire, vous devez identifier de manière unique l'UDT et le ou les contrats, autrement dit, le ou les interfaces COM d'origine qui les utilisent.  
  
 L'exemple suivant décrit l'ajout à cette fin de deux UDT spécifiques à la section <`userDefinedTypes`> du fichier de configuration.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <userDefinedTypes>
      <userDefinedType name="CustomerType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">
      </userDefinedType>
      <userDefinedType name="AddressType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">
      </userDefinedType>
    </userDefinedTypes>
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 Lorsque le service est initialisé, le runtime d'intégration recherche les types spécifiés et les ajoute à la collection de types connus pour les contrats spécifiés.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [\<comContracts>](comcontracts.md)
- [Intégration à des applications COM+](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Comment : configurer des paramètres de service COM+](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
