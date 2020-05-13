---
title: Amélioration de l’utilisation de noms forts
description: Les signatures de nom fort conventionnelles pour les assemblys dans .NET Framework présentent des limitations. En savoir plus sur les noms forts améliorés.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: 720eda86ef0555127da422b2f44a414e8bbfb1b7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378956"
---
# <a name="enhanced-strong-naming"></a>Amélioration de l’utilisation de noms forts
Une signature de nom fort est un mécanisme d’identité dans le .NET Framework permettant d’identifier des assemblys. Il s’agit d’une signature numérique de clé publique qui sert généralement à vérifier l’intégrité des données transmises d’un expéditeur (signataire) vers un destinataire (vérificateur). Cette signature est utilisée comme identité unique pour un assembly, et garantit que les références à l’assembly ne sont pas ambiguës. L’assembly est signé dans le cadre du processus de génération, puis vérifié quand il est chargé.  
  
 Les signatures de nom fort empêchent des parties malveillantes de falsifier un assembly et de le resigner avec la clé du signataire d’origine. Toutefois, les clés de nom fort ne contiennent pas d’informations fiables sur l’éditeur, ni de hiérarchie de certificats. Une signature de nom fort ne garantit pas la fiabilité de la personne qui a signé l’assembly, et ne garantit pas non plus que cette personne était un propriétaire légitime de la clé ; elle indique uniquement que le propriétaire de la clé a signé l’assembly. Par conséquent, nous déconseillons d’utiliser une signature de nom fort comme validateur de sécurité pour approuver du code tiers. Microsoft Authenticode est la méthode recommandée pour authentifier le code.  
  
## <a name="limitations-of-conventional-strong-names"></a>Limitations des noms forts conventionnels  
 La technologie de nommage fort utilisée dans les versions antérieures à .NET Framework 4.5 présente les inconvénients suivants :  
  
- Les clés subissent constamment des attaques, et le matériel et les techniques améliorés facilitent la déduction d’une clé privée à partir d’une clé publique. Pour se protéger des attaques, de plus grandes clés sont nécessaires. Les versions du .NET Framework antérieures à .NET Framework 4.5 permettent de signer avec n’importe quelle taille de clé (la taille par défaut étant de 1 024 bits), mais la signature d’un assembly avec une nouvelle clé brise tous les binaires qui référencent l’ancienne identité de l’assembly. Par conséquent, il est extrêmement difficile de mettre à niveau la taille d’une clé de signature si vous voulez assurer la compatibilité.  
  
- La signature de nom fort prend en charge uniquement l’algorithme SHA-1. Il a été récemment observé que SHA-1 n’était pas adéquat pour les applications de hachage sécurisées. Par conséquent, un algorithme plus fort (SHA-256 ou supérieur) est nécessaire. Il est possible que SHA-1 perde sa position conforme FIPS, ce qui poserait des problèmes pour ceux qui choisissent d’utiliser uniquement des logiciels et des algorithmes conformes FIPS.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Avantages des noms forts améliorés  
 Les principaux avantages des noms forts améliorés sont la compatibilité avec les noms forts préexistants et la capacité à revendiquer qu’une identité est équivalente à une autre :  
  
- Les développeurs qui ont des assemblys signés pré-existants peuvent migrer leurs identités vers les algorithmes SHA-2 tout en conservant la compatibilité avec les assemblys qui référencent les anciennes identités.  
  
- Les développeurs qui créent de nouveaux assemblys et ne sont pas concernés par les signatures de nom fort préexistantes peuvent utiliser les algorithmes SHA-2 plus sécurisés et signer les assemblys comme ils l’ont toujours fait.  
  
## <a name="use-enhanced-strong-names"></a>Utiliser des noms forts améliorés  
 Les clés de nom fort se composent d’une clé de signature et d’une clé d’identité. L’assembly est signé avec la clé de signature et est identifié par la clé d’identité. Avant .NET Framework 4.5, ces deux clés étaient identiques. À partir de .NET Framework 4.5, la clé d’identité est la même que dans les versions antérieures du .NET Framework, mais la clé de signature est améliorée avec un algorithme de hachage plus fort. En outre, la clé de signature est signée avec la clé d’identité pour créer une contre-signature.  
  
 L’attribut <xref:System.Reflection.AssemblySignatureKeyAttribute> permet aux métadonnées de l’assembly d’utiliser la clé publique préexistante pour l’identité d’assembly, ce qui permet aux anciennes références d’assembly de continuer à fonctionner.  L’attribut <xref:System.Reflection.AssemblySignatureKeyAttribute> utilise la contre-signature pour garantir que le propriétaire de la nouvelle clé de signature est également le propriétaire de l’ancienne clé d’identité.  
  
### <a name="sign-with-sha-2-without-key-migration"></a>Signer avec SHA-2, sans migration de clé  
 Exécutez les commandes suivantes à partir d’une invite de commandes pour signer un assembly sans migrer une signature de nom fort :  
  
1. Générez la nouvelle clé d’identité (si nécessaire).  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. Extrayez la clé publique d’identité et indiquez qu’un algorithme SHA-2 doit être utilisé lors de la signature avec cette clé.  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. Signez en différé l’assembly avec le fichier de clé publique d’identité.  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. Resignez l’assembly avec la paire de clés d’identité complète.  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a>Signature avec SHA-2, avec migration de clé  
 Exécutez les commandes suivantes à partir d’une invite de commandes pour signer un assembly avec une signature de nom fort migrée.  
  
1. Générez une paire de clés d’identité et de signature (si nécessaire).  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. Extrayez la clé publique de signature et indiquez qu’un algorithme SHA-2 doit être utilisé lors de la signature avec cette clé.  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. Extrayez la clé publique d’identité, qui détermine l’algorithme de hachage qui génère une contre-signature.  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. Générez les paramètres pour un attribut <xref:System.Reflection.AssemblySignatureKeyAttribute> et attachez l’attribut à l’assembly.  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    Cela produit une sortie similaire à ce qui suit.

    ```output
    Information for key migration attribute.
    (System.Reflection.AssemblySignatureKeyAttribute):
    publicKey=
    002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519
    d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936
    e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b4
    3893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a3
    4d153cdd

    counterSignature=
    e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91eb
    e1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8
    ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3
    ae5fec2c682e57b7442738
    ```

    Cette sortie peut ensuite être transformée en AssemblySignatureKeyAttribute.

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. Signez en différé l’assembly avec la clé publique d’identité.  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. Signez complètement l’assembly avec la paire de clés de signature.  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Créer et utiliser des assemblys avec nom fort](create-use-strong-named.md)
