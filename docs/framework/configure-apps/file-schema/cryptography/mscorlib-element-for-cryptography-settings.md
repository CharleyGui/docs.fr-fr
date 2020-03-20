---
title: Élément <mscorlib> pour les paramètres de chiffrement
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: d1d805f7154c18dba2dcd4eb7228cc200d8da811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155179"
---
# <a name="mscorlib-element-for-cryptography-settings"></a>\<hcorlib> Élément pour les paramètres de cryptographie
Contient la [ \<cryptographieSettings> élément](cryptographysettings-element.md).  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<>mscorlib**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`cryptographySettings`|Contient des paramètres de chiffrement.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre comment utiliser le ** \<mscorlib>** élément pour référencer une classe de cryptographie et configurer le temps d’exécution. Vous pouvez ensuite passer la chaîne <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> "RSA" <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> à la `MyCryptoRSAClass` méthode et utiliser la méthode pour retourner un objet.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [Configuration Fichier Schema](../index.md)
- [Paramètres de cryptographie Schema](index.md)
- [Cryptographic Services](../../../../standard/security/cryptographic-services.md)
- [Configuration de classes de chiffrement](../../configure-cryptography-classes.md)
