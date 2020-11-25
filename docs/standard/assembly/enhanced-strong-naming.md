---
title: Amélioration de l’utilisation de noms forts
description: Les signatures de nom fort conventionnelles pour les assemblys dans .NET Framework présentent des limitations. En savoir plus sur les noms forts améliorés.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: b9c690c77dafc247f7282c3f56384481efe53399
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731525"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="a932b-104">Amélioration de l’utilisation de noms forts</span><span class="sxs-lookup"><span data-stu-id="a932b-104">Enhanced strong naming</span></span>

<span data-ttu-id="a932b-105">Une signature de nom fort est un mécanisme d’identité dans le .NET Framework permettant d’identifier des assemblys.</span><span class="sxs-lookup"><span data-stu-id="a932b-105">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="a932b-106">Il s’agit d’une signature numérique de clé publique qui sert généralement à vérifier l’intégrité des données transmises d’un expéditeur (signataire) vers un destinataire (vérificateur).</span><span class="sxs-lookup"><span data-stu-id="a932b-106">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="a932b-107">Cette signature est utilisée comme identité unique pour un assembly, et garantit que les références à l’assembly ne sont pas ambiguës.</span><span class="sxs-lookup"><span data-stu-id="a932b-107">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="a932b-108">L’assembly est signé dans le cadre du processus de génération, puis vérifié quand il est chargé.</span><span class="sxs-lookup"><span data-stu-id="a932b-108">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="a932b-109">Les signatures de nom fort empêchent des parties malveillantes de falsifier un assembly et de le resigner avec la clé du signataire d’origine.</span><span class="sxs-lookup"><span data-stu-id="a932b-109">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="a932b-110">Toutefois, les clés de nom fort ne contiennent pas d’informations fiables sur l’éditeur, ni de hiérarchie de certificats.</span><span class="sxs-lookup"><span data-stu-id="a932b-110">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="a932b-111">Une signature de nom fort ne garantit pas la fiabilité de la personne qui a signé l’assembly, et ne garantit pas non plus que cette personne était un propriétaire légitime de la clé ; elle indique uniquement que le propriétaire de la clé a signé l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a932b-111">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="a932b-112">Par conséquent, nous déconseillons d’utiliser une signature de nom fort comme validateur de sécurité pour approuver du code tiers.</span><span class="sxs-lookup"><span data-stu-id="a932b-112">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="a932b-113">Microsoft Authenticode est la méthode recommandée pour authentifier le code.</span><span class="sxs-lookup"><span data-stu-id="a932b-113">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="a932b-114">Limitations des noms forts conventionnels</span><span class="sxs-lookup"><span data-stu-id="a932b-114">Limitations of conventional strong names</span></span>  

 <span data-ttu-id="a932b-115">La technologie de nommage fort utilisée dans les versions antérieures à .NET Framework 4.5 présente les inconvénients suivants :</span><span class="sxs-lookup"><span data-stu-id="a932b-115">The strong naming technology used in versions before the .NET Framework 4.5 has the following shortcomings:</span></span>  
  
- <span data-ttu-id="a932b-116">Les clés subissent constamment des attaques, et le matériel et les techniques améliorés facilitent la déduction d’une clé privée à partir d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="a932b-116">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="a932b-117">Pour se protéger des attaques, de plus grandes clés sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="a932b-117">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="a932b-118">Les versions du .NET Framework antérieures à .NET Framework 4.5 permettent de signer avec n’importe quelle taille de clé (la taille par défaut étant de 1 024 bits), mais la signature d’un assembly avec une nouvelle clé brise tous les binaires qui référencent l’ancienne identité de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a932b-118">.NET Framework versions before the .NET Framework 4.5 provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="a932b-119">Par conséquent, il est extrêmement difficile de mettre à niveau la taille d’une clé de signature si vous voulez assurer la compatibilité.</span><span class="sxs-lookup"><span data-stu-id="a932b-119">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
- <span data-ttu-id="a932b-120">La signature de nom fort prend en charge uniquement l’algorithme SHA-1.</span><span class="sxs-lookup"><span data-stu-id="a932b-120">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="a932b-121">Il a été récemment observé que SHA-1 n’était pas adéquat pour les applications de hachage sécurisées.</span><span class="sxs-lookup"><span data-stu-id="a932b-121">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="a932b-122">Par conséquent, un algorithme plus fort (SHA-256 ou supérieur) est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a932b-122">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="a932b-123">Il est possible que SHA-1 perde sa position conforme FIPS, ce qui poserait des problèmes pour ceux qui choisissent d’utiliser uniquement des logiciels et des algorithmes conformes FIPS.</span><span class="sxs-lookup"><span data-stu-id="a932b-123">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="a932b-124">Avantages des noms forts améliorés</span><span class="sxs-lookup"><span data-stu-id="a932b-124">Advantages of enhanced strong names</span></span>  

 <span data-ttu-id="a932b-125">Les principaux avantages des noms forts améliorés sont la compatibilité avec les noms forts préexistants et la capacité à revendiquer qu’une identité est équivalente à une autre :</span><span class="sxs-lookup"><span data-stu-id="a932b-125">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
- <span data-ttu-id="a932b-126">Les développeurs qui ont des assemblys signés pré-existants peuvent migrer leurs identités vers les algorithmes SHA-2 tout en conservant la compatibilité avec les assemblys qui référencent les anciennes identités.</span><span class="sxs-lookup"><span data-stu-id="a932b-126">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
- <span data-ttu-id="a932b-127">Les développeurs qui créent de nouveaux assemblys et ne sont pas concernés par les signatures de nom fort préexistantes peuvent utiliser les algorithmes SHA-2 plus sécurisés et signer les assemblys comme ils l’ont toujours fait.</span><span class="sxs-lookup"><span data-stu-id="a932b-127">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="use-enhanced-strong-names"></a><span data-ttu-id="a932b-128">Utiliser des noms forts améliorés</span><span class="sxs-lookup"><span data-stu-id="a932b-128">Use enhanced strong names</span></span>  

 <span data-ttu-id="a932b-129">Les clés de nom fort se composent d’une clé de signature et d’une clé d’identité.</span><span class="sxs-lookup"><span data-stu-id="a932b-129">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="a932b-130">L’assembly est signé avec la clé de signature et est identifié par la clé d’identité.</span><span class="sxs-lookup"><span data-stu-id="a932b-130">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="a932b-131">Avant .NET Framework 4.5, ces deux clés étaient identiques.</span><span class="sxs-lookup"><span data-stu-id="a932b-131">Prior to the .NET Framework 4.5, these two keys were identical.</span></span> <span data-ttu-id="a932b-132">À partir de .NET Framework 4.5, la clé d’identité est la même que dans les versions antérieures du .NET Framework, mais la clé de signature est améliorée avec un algorithme de hachage plus fort.</span><span class="sxs-lookup"><span data-stu-id="a932b-132">Starting with the .NET Framework 4.5, the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="a932b-133">En outre, la clé de signature est signée avec la clé d’identité pour créer une contre-signature.</span><span class="sxs-lookup"><span data-stu-id="a932b-133">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="a932b-134">L’attribut <xref:System.Reflection.AssemblySignatureKeyAttribute> permet aux métadonnées de l’assembly d’utiliser la clé publique préexistante pour l’identité d’assembly, ce qui permet aux anciennes références d’assembly de continuer à fonctionner.</span><span class="sxs-lookup"><span data-stu-id="a932b-134">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="a932b-135">L’attribut <xref:System.Reflection.AssemblySignatureKeyAttribute> utilise la contre-signature pour garantir que le propriétaire de la nouvelle clé de signature est également le propriétaire de l’ancienne clé d’identité.</span><span class="sxs-lookup"><span data-stu-id="a932b-135">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="sign-with-sha-2-without-key-migration"></a><span data-ttu-id="a932b-136">Signer avec SHA-2, sans migration de clé</span><span class="sxs-lookup"><span data-stu-id="a932b-136">Sign with SHA-2, without key migration</span></span>  

 <span data-ttu-id="a932b-137">Exécutez les commandes suivantes à partir d’une invite de commandes pour signer un assembly sans migrer une signature de nom fort :</span><span class="sxs-lookup"><span data-stu-id="a932b-137">Run the following commands from a command prompt to sign an assembly without migrating a strong name signature:</span></span>  
  
1. <span data-ttu-id="a932b-138">Générez la nouvelle clé d’identité (si nécessaire).</span><span class="sxs-lookup"><span data-stu-id="a932b-138">Generate the new identity key (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. <span data-ttu-id="a932b-139">Extrayez la clé publique d’identité et indiquez qu’un algorithme SHA-2 doit être utilisé lors de la signature avec cette clé.</span><span class="sxs-lookup"><span data-stu-id="a932b-139">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="a932b-140">Signez en différé l’assembly avec le fichier de clé publique d’identité.</span><span class="sxs-lookup"><span data-stu-id="a932b-140">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. <span data-ttu-id="a932b-141">Resignez l’assembly avec la paire de clés d’identité complète.</span><span class="sxs-lookup"><span data-stu-id="a932b-141">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a><span data-ttu-id="a932b-142">Signature avec SHA-2, avec migration de clé</span><span class="sxs-lookup"><span data-stu-id="a932b-142">Sign with SHA-2, with key migration</span></span>  

 <span data-ttu-id="a932b-143">Exécutez les commandes suivantes à partir d’une invite de commandes pour signer un assembly avec une signature de nom fort migrée.</span><span class="sxs-lookup"><span data-stu-id="a932b-143">Run the following commands from a command prompt to sign an assembly with a migrated strong name signature.</span></span>  
  
1. <span data-ttu-id="a932b-144">Générez une paire de clés d’identité et de signature (si nécessaire).</span><span class="sxs-lookup"><span data-stu-id="a932b-144">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. <span data-ttu-id="a932b-145">Extrayez la clé publique de signature et indiquez qu’un algorithme SHA-2 doit être utilisé lors de la signature avec cette clé.</span><span class="sxs-lookup"><span data-stu-id="a932b-145">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="a932b-146">Extrayez la clé publique d’identité, qui détermine l’algorithme de hachage qui génère une contre-signature.</span><span class="sxs-lookup"><span data-stu-id="a932b-146">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. <span data-ttu-id="a932b-147">Générez les paramètres pour un attribut <xref:System.Reflection.AssemblySignatureKeyAttribute> et attachez l’attribut à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a932b-147">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="a932b-148">Cela produit une sortie similaire à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="a932b-148">This produces output similar to the following.</span></span>

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

    <span data-ttu-id="a932b-149">Cette sortie peut ensuite être transformée en AssemblySignatureKeyAttribute.</span><span class="sxs-lookup"><span data-stu-id="a932b-149">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```csharp
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. <span data-ttu-id="a932b-150">Signez en différé l’assembly avec la clé publique d’identité.</span><span class="sxs-lookup"><span data-stu-id="a932b-150">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. <span data-ttu-id="a932b-151">Signez complètement l’assembly avec la paire de clés de signature.</span><span class="sxs-lookup"><span data-stu-id="a932b-151">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a932b-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a932b-152">See also</span></span>

- [<span data-ttu-id="a932b-153">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="a932b-153">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
