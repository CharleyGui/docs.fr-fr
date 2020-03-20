---
title: Élément <cryptoClasses>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: c93fadf51297d59ab499e25de283700364903049
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155244"
---
# <a name="cryptoclasses-element"></a>\<cryptoClasses> Element
Contient une liste de classes de cryptographie qui ont une cartographie à un nom amical dans le [ \<nomEntry>](nameentry-element.md) élément.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<>mscorlib**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographieSettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<cryptoClass>](cryptoclass-element.md)|Contient un cours de cryptographie qui a une cartographie à un nom amical dans le ** \<nomEntry>** élément.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`cryptographySettings`|Contient des paramètres de chiffrement.|  
|`cryptoNameMapping`|Contient des mappages de classes à des noms conviviaux.|  
|`mscorlib`|Contient `cryptographySettings` l’élément.|  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser l’élément ** \<cryptoClass>** pour référencer une classe de cryptographie et configurer l’heure d’exécution. Vous pouvez ensuite passer la chaîne <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> "RSA" <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> à la `MyCryptoRSAClass` méthode et utiliser la méthode pour retourner un objet.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Cryptography>
- [Configuration Fichier Schema](../index.md)
- [Paramètres de cryptographie Schema](index.md)
- [Cryptographic Services](../../../../standard/security/cryptographic-services.md)
- [System.Security.Cryptography.CryptoConfig.CreateDeName](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [Configuration de classes de chiffrement](../../configure-cryptography-classes.md)
