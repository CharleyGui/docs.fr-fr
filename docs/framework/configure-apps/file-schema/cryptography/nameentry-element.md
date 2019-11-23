---
title: Élément <nameEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: a339638587f8b544bbc1b0073553f6232ce09694
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699781"
---
# <a name="nameentry-element"></a>\<élément élément nameEntry >
Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings** >](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[ **cryptoNameMapping >** ](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<élément nameentry >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributes  
  
|Attribut|Description|  
|---------------|-----------------|  
|**name**|Attribut requis.<br /><br /> Spécifie le nom convivial de l’algorithme que la classe de chiffrement implémente.|  
|**classe**|Attribut requis.<br /><br /> Spécifie la valeur de l’attribut **Name** dans l’élément [\<cryptoClass >](cryptoclass-element.md) .|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucune.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.web`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
  
## <a name="remarks"></a>Remarques  
 L’attribut **Name** peut être le nom de l’une des classes abstraites se trouvant dans l’espace de noms <xref:System.Security.Cryptography>. Quand vous appelez la méthode **Create** sur une classe de chiffrement abstraite, le nom de la classe abstraite est passé à la méthode <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>. **CreateFromName** retourne une instance du type indiqué par l’attribut de **classe** . Si l’attribut **Name** est un nom abrégé, tel que RSA, vous pouvez utiliser ce nom lors de l’appel de la méthode **CreateFromName** .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l’élément **\<élément nameentry >** pour faire référence à une classe de chiffrement et configurer le Runtime. Vous pouvez ensuite passer la chaîne « RSA » à la méthode <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> et utiliser la méthode <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pour retourner un objet `MyCryptoRSAClass`.  
  
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

- [Schéma des fichiers de configuration](../index.md)
- [Schéma des paramètres de chiffrement](index.md)
- [Services de chiffrement](../../../../standard/security/cryptographic-services.md)
- [Configuration des classes de chiffrement](../../configure-cryptography-classes.md)
