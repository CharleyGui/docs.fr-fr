---
title: Mappage d'identificateurs d'objet à des algorithmes de chiffrement
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: a5aebac2d392d4540581dfe7c7afff0819968ac0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912543"
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
  
 [ L'\<élément oidEntry >](./file-schema/cryptography/oidentry-element.md) contient deux attributs. L’attribut **OID** est le numéro de l’identificateur d’objet. L’attribut **Name** est la valeur de l’attribut **Name** de l' [ \<élément élément nameEntry >](./file-schema/cryptography/nameentry-element.md). Il doit y avoir un mappage d’un nom d’algorithme à une classe avant qu’un identificateur d’objet puisse être mappé à un nom simple.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration des classes de chiffrement](configure-cryptography-classes.md)
- [Cryptographic Services](../../standard/security/cryptographic-services.md)
