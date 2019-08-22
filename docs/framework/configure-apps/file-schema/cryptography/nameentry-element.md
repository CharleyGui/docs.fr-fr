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
ms.openlocfilehash: 9270552245b3867f0f09741ded3f9da6a8b6c135
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664266"
---
# <a name="nameentry-element"></a>\<Élément nameEntry >, élément
Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.  
  
 \<configuration>  
\<mscorlib>  
\<cryptographySettings>  
\<cryptoNameMapping>  
\<nameEntry>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**name**|Attribut requis.<br /><br /> Spécifie le nom convivial de l’algorithme que la classe de chiffrement implémente.|  
|**class**|Attribut requis.<br /><br /> Spécifie la valeur de l’attribut **Name** dans l' [ \<élément cryptoClass >](cryptoclass-element.md) .|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.web`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
  
## <a name="remarks"></a>Notes  
 L’attribut **Name** peut être le nom de l’une des classes abstraites trouvées dans <xref:System.Security.Cryptography> l’espace de noms. Quand vous appelez la méthode Create sur une classe de chiffrement abstraite, le nom de la <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> classe abstraite est passé à la méthode. **CreateFromName** retourne une instance du type indiqué par l’attribut de **classe** . Si l’attribut **Name** est un nom abrégé, tel que RSA, vous pouvez utiliser ce nom lors de l’appel de la méthode **CreateFromName** .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l'  **\<élément élément nameEntry >** pour référencer une classe de chiffrement et configurer le Runtime. Vous pouvez ensuite passer la chaîne «RSA» à la <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> méthode et utiliser la <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> méthode pour retourner un `MyCryptoRSAClass` objet.  
  
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
- [Cryptographic Services](../../../../../docs/standard/security/cryptographic-services.md)
- [Configuration des classes de chiffrement](../../configure-cryptography-classes.md)
