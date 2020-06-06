---
title: Élément <oidEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: 4564cf59e3b6cfbdcd9dca06cd0f966d524834de
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088547"
---
# <a name="oidentry-element"></a>Élément \<oidEntry>
Mappe un identificateur d’objet (OID) ASN.1 à un nom convivial.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**OID**|Attribut requis.<br /><br /> Spécifie l’OID ASN. 1 correspondant à l’algorithme implémenté par votre classe.|  
|**name**|Attribut requis.<br /><br /> Spécifie la valeur de l’attribut **Name** dans la [\<nameEntry>](nameentry-element.md) balise.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`cryptographySettings`|Contient des paramètres de chiffrement.|  
|`mscorlib`|Contient l' `cryptographySettings` élément.|  
|`oidMap`|Contient les mappages de l’identificateur d’objet (OID) ASN. 1 aux classes.|  
  
## <a name="remarks"></a>Remarques  
 Les identificateurs d’objets ASN. 1 identifient les algorithmes dans certains formats de chiffrement. Mappez les identificateurs d’objet à des noms conviviaux pour les algorithmes que vous souhaitez identifier.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l' **\<oidEntry>** élément pour mapper un identificateur d’objet pour l’algorithme de hachage RIPEMD-160 à une implémentation de cet algorithme de hachage.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des fichiers de configuration](../index.md)
- [Schéma des paramètres de chiffrement](index.md)
- [Services de chiffrement](../../../../standard/security/cryptographic-services.md)
- [Configuration de classes de chiffrement](../../configure-cryptography-classes.md)
- [Mappage d'identificateurs d'objet à des algorithmes de chiffrement](../../map-object-identifiers-to-cryptography-algorithms.md)
