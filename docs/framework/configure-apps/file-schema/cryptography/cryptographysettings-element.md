---
title: Élément <cryptographySettings>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: fe6de09213c6f980e8eb205a318aae50033b2a84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155230"
---
# <a name="cryptographysettings-element"></a>\<cryptographieSettings> Element
Contient des paramètres de chiffrement.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>mscorlib**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographieSettings>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<cryptoNameMapping>](cryptonamemapping-element.md)|Contient des mappages de classes à des noms conviviaux.|  
|[\<oidMap>](oidmap-element.md)|Contient des cartographies ASN.1 d’identifiant d’objet (OID) aux classes.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`mscorlib`|Contient `cryptographySettings` l’élément.|  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser les ** \<cryptographieSettings>** élément pour contenir des cartographies nominographies et des cartographies OID. Cet exemple configure le temps <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> d’exécution de sorte que renvoie un `MyHashClass` objet et les `MyCryptoClass` cartes de classe à l’identifiant d’objet 1.3.36.2.1.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Configuration Fichier Schema](../index.md)
- [Paramètres de cryptographie Schema](index.md)
- [Cryptographic Services](../../../../standard/security/cryptographic-services.md)
