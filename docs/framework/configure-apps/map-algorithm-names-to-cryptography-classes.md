---
title: Mappage de noms d'algorithmes à des classes de chiffrement
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 513000169504473aa6dd46feaca214f58502ffd0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69912865"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>Mappage de noms d'algorithmes à des classes de chiffrement
Un développeur peut créer un objet de chiffrement à l’aide de l’SDK Windows de quatre façons :  
  
- Créez un objet à l’aide de l’opérateur **New** .  
  
- Créez un objet qui implémente un algorithme de chiffrement particulier en appelant la méthode **Create** sur la classe abstraite pour cet algorithme.  
  
- Créez un objet qui implémente un algorithme de chiffrement particulier en appelant la <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> méthode.  
  
- Créez un objet qui implémente une classe d’algorithmes de chiffrement (par exemple, un chiffrement par bloc symétrique) en appelant la méthode **Create** sur la classe abstraite pour ce type d’algorithme (tel que <xref:System.Security.Cryptography.SymmetricAlgorithm> ).  
  
 Par exemple, supposons qu’un développeur souhaite calculer le hachage SHA1 d’un ensemble d’octets. L' <xref:System.Security.Cryptography> espace de noms contient deux implémentations de l’algorithme SHA1, une implémentation purement managée et une implémentation qui encapsule CryptoAPI. Le développeur peut choisir d’instancier une implémentation SHA1 particulière (telle que <xref:System.Security.Cryptography.SHA1Managed> ) en appelant l’opérateur **New** . Toutefois, s’il importe peu la classe que le common language runtime charge, tant que la classe implémente l’algorithme de hachage SHA1, le développeur peut créer un objet en appelant la <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> méthode. Cette méthode appelle **System. Security. Cryptography. CryptoConfig. CreateFromName ("System. Security. Cryptography. SHA1")**, qui doit retourner une implémentation de l’algorithme de hachage SHA1.  
  
 Le développeur peut également appeler **System. Security. Cryptography. CryptoConfig. CreateFromName ("SHA1")** car, par défaut, la configuration du chiffrement comprend des noms courts pour les algorithmes fournis dans le .NET Framework.  
  
 Si l’algorithme de hachage utilisé n’a pas d’importance, le développeur peut appeler la <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> méthode, qui retourne un objet qui implémente une transformation de hachage.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>Mappage des noms d’algorithmes dans les fichiers de configuration  
 Par défaut, le runtime retourne un <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> objet pour les quatre scénarios. Toutefois, un administrateur d’ordinateur peut modifier le type d’objet retourné par les méthodes dans les deux derniers scénarios. Pour ce faire, vous devez mapper un nom d’algorithme convivial à la classe que vous souhaitez utiliser dans le fichier de configuration de l’ordinateur (machine. config).  
  
 L’exemple suivant montre comment configurer le runtime afin que **System. Security. Cryptography. SHA1. Create**, **System. Security. CryptoConfig. CREATEFROMNAME ("SHA1")** et **System. Security. Cryptography. HashAlgorithm. Create** retournent un `MySHA1HashClass` objet.  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 Vous pouvez spécifier le nom de l’attribut dans l' [ \> élément<cryptoClass](./file-schema/cryptography/cryptoclass-element.md) (l’exemple précédent nomme l’attribut `MySHA1Hash` ). La valeur de l’attribut dans l' **\<cryptoClass>** élément est une chaîne que l’Common Language Runtime utilise pour rechercher la classe. Vous pouvez utiliser n’importe quelle chaîne conforme aux exigences spécifiées dans [spécification de noms de types qualifiés complets](../reflection-and-codedom/specifying-fully-qualified-type-names.md).  
  
 De nombreux noms d’algorithmes peuvent être mappés à la même classe. L' [ \<nameEntry> élément](./file-schema/cryptography/nameentry-element.md) mappe une classe à un nom d’algorithme convivial. L’attribut **Name** peut être soit une chaîne utilisée lors de l’appel de la méthode **System. Security. Cryptography. CryptoConfig. CreateFromName** , soit le nom d’une classe de chiffrement abstraite dans l' <xref:System.Security.Cryptography> espace de noms. La valeur de l’attribut de **classe** est le nom de l’attribut dans l' **\<cryptoClass>** élément.  
  
> [!NOTE]
> Vous pouvez récupérer un algorithme SHA1 en appelant la <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> méthode ou la méthode **Security. CryptoConfig. CreateFromName ("SHA1")** . Chaque méthode garantit uniquement qu’elle retourne un objet qui implémente l’algorithme SHA1. Vous n’avez pas besoin de mapper chaque nom convivial d’un algorithme à la même classe dans le fichier de configuration.  
  
 Pour obtenir la liste des noms par défaut et des classes avec lesquelles ils sont mappés, consultez <xref:System.Security.Cryptography.CryptoConfig> .  
  
## <a name="see-also"></a>Voir aussi

- [Services de chiffrement](../../standard/security/cryptographic-services.md)
- [Configuration de classes de chiffrement](configure-cryptography-classes.md)
