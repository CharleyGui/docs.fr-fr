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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69912543"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a><span data-ttu-id="89dba-102">Mappage d'identificateurs d'objet à des algorithmes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="89dba-102">Mapping Object Identifiers to Cryptography Algorithms</span></span>
<span data-ttu-id="89dba-103">Les signatures numériques garantissent que les données ne sont pas falsifiées lorsqu’elles sont envoyées d’un programme à un autre.</span><span class="sxs-lookup"><span data-stu-id="89dba-103">Digital signatures ensure that data is not tampered with when it is sent from one program to another.</span></span> <span data-ttu-id="89dba-104">En général, la signature numérique est calculée en appliquant une fonction mathématique au hachage des données à signer.</span><span class="sxs-lookup"><span data-stu-id="89dba-104">Typically the digital signature is computed by applying a mathematical function to the hash of the data to be signed.</span></span> <span data-ttu-id="89dba-105">Lors de la mise en forme d’une valeur de hachage à signer, certains algorithmes de signature numérique ajoutent un identificateur d’objet (OID) ASN. 1 dans le cadre de l’opération de mise en forme.</span><span class="sxs-lookup"><span data-stu-id="89dba-105">When formatting a hash value to be signed, some digital signature algorithms append an ASN.1 Object Identifier (OID) as part of the formatting operation.</span></span> <span data-ttu-id="89dba-106">L’OID identifie l’algorithme utilisé pour calculer le hachage.</span><span class="sxs-lookup"><span data-stu-id="89dba-106">The OID identifies the algorithm that was used to compute the hash.</span></span> <span data-ttu-id="89dba-107">Vous pouvez mapper des algorithmes à des identificateurs d’objet pour étendre le mécanisme de chiffrement afin d’utiliser des algorithmes personnalisés.</span><span class="sxs-lookup"><span data-stu-id="89dba-107">You can map algorithms to object identifiers to extend the cryptography mechanism to use custom algorithms.</span></span> <span data-ttu-id="89dba-108">L’exemple suivant montre comment mapper un identificateur d’objet à un nouvel algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="89dba-108">The following example shows how to map an object identifier to a new hash algorithm.</span></span>  
  
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
  
 <span data-ttu-id="89dba-109">L' [ \<oidEntry> élément](./file-schema/cryptography/oidentry-element.md) contient deux attributs.</span><span class="sxs-lookup"><span data-stu-id="89dba-109">The [\<oidEntry> element](./file-schema/cryptography/oidentry-element.md) contains two attributes.</span></span> <span data-ttu-id="89dba-110">L’attribut **OID** est le numéro de l’identificateur d’objet.</span><span class="sxs-lookup"><span data-stu-id="89dba-110">The **OID** attribute is the object identifier number.</span></span> <span data-ttu-id="89dba-111">L’attribut **Name** est la valeur de l’attribut **Name** de l' [ \<nameEntry> élément](./file-schema/cryptography/nameentry-element.md).</span><span class="sxs-lookup"><span data-stu-id="89dba-111">The **name** attribute is the value of the **name** attribute from the [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md).</span></span> <span data-ttu-id="89dba-112">Il doit y avoir un mappage d’un nom d’algorithme à une classe avant qu’un identificateur d’objet puisse être mappé à un nom simple.</span><span class="sxs-lookup"><span data-stu-id="89dba-112">There must be a mapping from an algorithm name to a class before an object identifier can be mapped to a simple name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89dba-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89dba-113">See also</span></span>

- [<span data-ttu-id="89dba-114">Configuration de classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="89dba-114">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
- [<span data-ttu-id="89dba-115">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="89dba-115">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
