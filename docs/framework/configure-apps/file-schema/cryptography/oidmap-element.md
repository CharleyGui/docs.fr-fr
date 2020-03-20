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
ms.openlocfilehash: a28eaf68fe1e6ab3f26592eee5ae2d0f2e7a3256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155165"
---
# <a name="oidmap-element"></a>\<oidMap> Element
Contient des cartographies ASN.1 d’identifiant d’objet (OID) aux classes.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>mscorlib**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographieSettings>**](cryptographysettings-element.md)\
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
|[\<oidEntry>](oidentry-element.md)|Cartes d’un ASN.1 OID à un nom amical.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`cryptographySettings`|Contient des paramètres de chiffrement.|  
|`mscorlib`|Contient `cryptographySettings` l’élément.|  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser ** \<l’élément oidMap>** pour contenir une cartographie d’un OID pour l’algorithme de hachage RIPEMD-160 à une implémentation de cet algorithme de hachage.  
  
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

- [Configuration Fichier Schema](../index.md)
- [Paramètres de cryptographie Schema](index.md)
- [Cryptographic Services](../../../../standard/security/cryptographic-services.md)
- [Configuration de classes de chiffrement](../../configure-cryptography-classes.md)
- [Mappage d'identificateurs d'objet à des algorithmes de chiffrement](../../map-object-identifiers-to-cryptography-algorithms.md)
