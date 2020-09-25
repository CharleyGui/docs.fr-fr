---
title: Mappage d'identificateurs d'objet à des algorithmes de chiffrement
description: Consultez comment mapper un identificateur d’objet (OID) à un algorithme de chiffrement dans .NET à l’aide des éléments oidEntry et élément nameEntry dans un fichier de configuration XML.
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: 5416ddbb766dfde56fa28a3853ed448cc73f25a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189381"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>Mappage d'identificateurs d'objet à des algorithmes de chiffrement

Les signatures numériques garantissent que les données ne sont pas falsifiées lorsqu’elles sont envoyées d’un programme à un autre. En général, la signature numérique est calculée en appliquant une fonction mathématique au hachage des données à signer. Lors de la mise en forme d’une valeur de hachage à signer, certains algorithmes de signature numérique ajoutent un identificateur d’objet (OID) ASN. 1 dans le cadre de l’opération de mise en forme. L’OID identifie l’algorithme utilisé pour calculer le hachage. Vous pouvez mapper des algorithmes à des identificateurs d’objet pour étendre le mécanisme de chiffrement afin d’utiliser des algorithmes personnalisés. L’exemple suivant montre comment mapper un identificateur d’objet à un nouvel algorithme de hachage.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 L' [ \<oidEntry> élément](./file-schema/cryptography/oidentry-element.md) contient deux attributs. L’attribut **OID** est le numéro de l’identificateur d’objet. L’attribut **Name** est la valeur de l’attribut **Name** de l' [ \<nameEntry> élément](./file-schema/cryptography/nameentry-element.md). Il doit y avoir un mappage d’un nom d’algorithme à une classe avant qu’un identificateur d’objet puisse être mappé à un nom simple.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration de classes de chiffrement](configure-cryptography-classes.md)
- [services de chiffrement](../../standard/security/cryptographic-services.md)
