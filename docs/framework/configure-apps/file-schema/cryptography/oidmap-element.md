---
title: Élément <oidMap>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: 6c57810389acbd58e6d2e05277a6f26fa0aac8c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149515"
---
# <a name="oidmap-element"></a>Élément \<oidMap>

Contient les mappages de l’identificateur d’objet (OID) ASN. 1 aux classes.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  

 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|Mappe un OID ASN. 1 à un nom convivial.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`cryptographySettings`|Contient des paramètres de chiffrement.|  
|`mscorlib`|Contient l' `cryptographySettings` élément.|  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment utiliser l' **\<oidMap>** élément pour contenir un mappage d’un OID pour l’algorithme de hachage RIPEMD-160 à une implémentation de cet algorithme de hachage.  
  
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
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma du fichier de configuration](../index.md)
- [Schéma des paramètres de chiffrement](index.md)
- [services de chiffrement](../../../../standard/security/cryptographic-services.md)
- [Configuration de classes de chiffrement](../../configure-cryptography-classes.md)
- [Mappage d'identificateurs d'objet à des algorithmes de chiffrement](../../map-object-identifiers-to-cryptography-algorithms.md)
