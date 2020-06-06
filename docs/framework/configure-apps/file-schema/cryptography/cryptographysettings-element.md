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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155230"
---
# <a name="cryptographysettings-element"></a>Élément \<cryptographySettings>
Contient des paramètres de chiffrement.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**

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
|[\<oidMap>](oidmap-element.md)|Contient les mappages de l’identificateur d’objet (OID) ASN. 1 aux classes.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`mscorlib`|Contient l' `cryptographySettings` élément.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l' **\<cryptographySettings>** élément pour contenir des mappages de noms de chiffrement et des mappages OID. Cet exemple configure le runtime afin que <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> retourne un `MyHashClass` objet et que la `MyCryptoClass` classe soit mappée à l’identificateur d’objet 1.3.36.2.1.  
  
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

- [Schéma des fichiers de configuration](../index.md)
- [Schéma des paramètres de chiffrement](index.md)
- [Services de chiffrement](../../../../standard/security/cryptographic-services.md)
