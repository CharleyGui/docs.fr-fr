---
title: Vulnérabilité de déchiffrement CBC
description: Découvrez comment détecter et atténuer les vulnérabilités de temporisation avec le déchiffrement symétrique en mode CBC (Cipher-Block-chaînage) à l’aide du remplissage.
ms.date: 06/12/2018
author: blowdart
ms.openlocfilehash: 4616ef9015b47ff232a17f058c7a0f1449f42e81
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159960"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Vulnérabilités de temporisation avec le déchiffrement symétrique en mode CBC à l’aide du remplissage

Microsoft est convaincu qu’il n’est plus sûr de déchiffrer les données chiffrées à l’aide du mode de chiffrement symétrique (CBC) du chiffrement symétrique lorsque le remplissage vérifiable a été appliqué sans assurer d’abord l’intégrité du texte chiffré, à l’exception des propres. Ce jugement est basé sur la recherche chiffrée actuellement connue.

## <a name="introduction"></a>Introduction

Une attaque Oracle de remplissage est un type d’attaque contre les données chiffrées qui permet à l’attaquant de déchiffrer le contenu des données, sans connaître la clé.

Oracle fait référence à un « Tell » qui donne à une personne malveillante des informations indiquant si l’action qu’elle exécute est correcte ou non. Imaginez que vous jouez à une carte ou à un jeu de cartes avec un enfant. Quand son visage s’illumine avec un grand sourire car il pense qu’il est sur le fait d’effectuer un bon déplacement, c’est un Oracle. En tant qu’adversaire, vous pouvez utiliser cet Oracle pour planifier votre prochain déplacement.

Le remplissage est un terme de chiffrement spécifique. Certains chiffrements, qui sont les algorithmes utilisés pour chiffrer vos données, fonctionnent sur des blocs de données où chaque bloc a une taille fixe. Si les données que vous souhaitez chiffrer ne sont pas de la bonne taille pour remplir les blocs, vos données sont complétées jusqu’à ce qu’elles soient remplies. De nombreuses formes de remplissage nécessitent que le remplissage soit toujours présent, même si l’entrée d’origine était de la taille appropriée. Cela permet à la marge de remplissage d’être toujours supprimée en toute sécurité lors du déchiffrement.

En regroupant les deux éléments, une implémentation logicielle avec un remplissage Oracle révèle que les données déchiffrées ont un remplissage valide. Oracle peut être aussi simple que de retourner une valeur qui indique « remplissage non valide » ou un point plus complexe, comme le temps de traitement d’un bloc valide, par opposition à un bloc non valide.

Les chiffrements basés sur les blocs ont une autre propriété, appelée mode, qui détermine la relation des données dans le premier bloc avec les données du deuxième bloc, et ainsi de suite. CBC est l’un des modes les plus couramment utilisés. CBC introduit un bloc aléatoire initial, connu sous le nom de vecteur d’initialisation (IV), et combine le bloc précédent avec le résultat du chiffrement statique pour le rendre tel que le chiffrement du même message avec la même clé ne produit pas toujours la même sortie chiffrée.

Une personne malveillante peut utiliser un remplissage Oracle, en association avec la façon dont les données CBC sont structurées, envoyer des messages légèrement modifiés au code qui expose l’Oracle et continuer à envoyer des données jusqu’à ce que Oracle leur indique que les données sont correctes. À partir de cette réponse, l’attaquant peut déchiffrer le message octet par octet.

Les réseaux informatiques modernes sont de qualité telle qu’une personne malveillante peut détecter des différences très petites (moins de 0,1 ms) dans le temps d’exécution sur les systèmes distants.Les applications qui supposent qu’un déchiffrement réussi ne peut se produire que lorsque les données n’ont pas été falsifiées peuvent être vulnérables aux attaques d’outils conçus pour observer les différences de déchiffrement réussi et infructueuse. Bien que cette différence de synchronisation puisse être plus significative dans certains langages ou bibliothèques que d’autres, il est maintenant supposé qu’il s’agit d’une menace pratique pour tous les langages et bibliothèques lorsque la réponse de l’application aux défaillances est prise en compte.

Cette attaque repose sur la possibilité de modifier les données chiffrées et de tester le résultat avec Oracle. La seule façon d’atténuer l’attaque consiste à détecter les modifications apportées aux données chiffrées et à refuser d’effectuer des actions sur celui-ci. La méthode standard pour effectuer cette opération consiste à créer une signature pour les données et à valider cette signature avant l’exécution des opérations. La signature doit être vérifiable, elle ne peut pas être créée par l’attaquant, sinon elle modifie les données chiffrées, puis calcule une nouvelle signature en fonction des données modifiées. Un type commun de signature appropriée est appelé code d’authentification de message à hachage par clé (HMAC). Un HMAC diffère d’une somme de contrôle en ce qu’il prend une clé secrète, connue uniquement de la personne qui produit le code HMAC et à la personne qui le valide. Sans possession de la clé, vous ne pouvez pas produire un HMAC correct. Lorsque vous recevez vos données, vous pouvez utiliser les données chiffrées, calculer indépendamment le HMAC à l’aide de la clé secrète que vous et le partage de l’expéditeur, puis comparer le HMAC qu’il a envoyé à celui que vous avez calculé. Cette comparaison doit être en temps constant, sinon vous avez ajouté une autre solution de détection d’Oracle, ce qui permet un type d’attaque différent.

En résumé, pour utiliser les chiffrements par bloc CBC remplis en toute sécurité, vous devez les associer à un code HMAC (ou à une autre vérification de l’intégrité des données) que vous validez à l’aide d’une comparaison de temps constant avant de tenter de déchiffrer les données. Étant donné que tous les messages modifiés prennent le même temps pour produire une réponse, l’attaque est empêchée.

## <a name="who-is-vulnerable"></a>Qui est vulnérable

Cette vulnérabilité s’applique aux applications gérées et natives qui effectuent leur propre chiffrement et déchiffrement. Cela comprend, par exemple :

- Application qui chiffre un cookie pour un déchiffrement ultérieur sur le serveur.
- Application de base de données qui offre aux utilisateurs la possibilité d’insérer des données dans une table dont les colonnes sont déchiffrées ultérieurement.
- Application de transfert de données qui s’appuie sur le chiffrement à l’aide d’une clé partagée pour protéger les données en transit.
- Application qui chiffre et déchiffre les messages « à l’intérieur » du tunnel TLS.

Notez que l’utilisation de TLS seul peut ne pas vous protéger dans ces scénarios.

Une application vulnérable :

- Déchiffre les données à l’aide du mode de chiffrement CBC avec un mode de remplissage vérifiable, tel que PKCS # 7 ou ANSI X. 923.
- Effectue le déchiffrement sans avoir effectué une vérification de l’intégrité des données (via un MAC ou une signature numérique asymétrique).

Cela s’applique également aux applications basées sur des abstractions au-dessus de ces primitives, telles que la structure EnvelopedData de la syntaxe de message de chiffrement (PKCS # 7/CMS).

## <a name="related-areas-of-concern"></a>Domaines de préoccupation associés

La recherche a conduit Microsoft à se préoccuper des messages CBC remplis avec une marge intérieure ISO 10126 équivalente lorsque le message a une structure de pied de page bien connue ou prévisible. Par exemple, le contenu préparé dans le cadre des règles de la recommandation du W3C sur la syntaxe et le traitement du chiffrement XML (xmlenc, EncryptedXml). Tandis que le Guide du W3C pour signer le message a été jugé approprié à ce moment-là, Microsoft recommande de toujours effectuer le chiffrement-Then-Sign.

Les développeurs d’applications doivent toujours être attentifs à la vérification de l’applicabilité d’une clé de signature asymétrique, car il n’existe aucune relation d’approbation inhérente entre une clé asymétrique et un message arbitraire.

## <a name="details"></a>Détails

Historiquement, il y a eu un consensus sur le chiffrement et l’authentification des données importantes, à l’aide de moyens tels que HMAC ou les signatures RSA. Toutefois, il y a eu des conseils moins clairs quant au mode de séquencement des opérations de chiffrement et d’authentification. En raison de la vulnérabilité détaillée dans cet article, l’aide de Microsoft consiste à toujours utiliser le paradigme « chiffrement-Then-signe ». Autrement dit, chiffrez d’abord les données à l’aide d’une clé symétrique, puis calculez une signature MAC ou asymétrique sur le texte chiffré (données chiffrées). Lors du déchiffrement des données, effectuez l’inverse. Tout d’abord, confirmez le MAC ou la signature du texte chiffré, puis déchiffrez-le.

Une classe de vulnérabilités connue sous le nom de « attaques Oracle de remplissage » a été réputée exister depuis plus de 10 ans. Ces vulnérabilités permettent à une personne malveillante de déchiffrer les données chiffrées par des algorithmes de bloc symétriques, tels que AES et 3DES, en n’utilisant pas plus de 4096 tentatives par bloc de données. Ces vulnérabilités font appel au fait que les chiffrements par bloc sont utilisés le plus fréquemment avec les données de remplissage vérifiables à la fin. Il a été constaté que si une personne malveillante peut falsifier le texte chiffré et savoir si la falsification a provoqué une erreur dans le format de remplissage à la fin, l’attaquant peut déchiffrer les données.

Initialement, les attaques pratiques étaient basées sur des services qui renvoient des codes d’erreur différents selon que le remplissage était valide, par exemple la vulnérabilité ASP.NET [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070). Toutefois, Microsoft pense qu’il est pratique d’effectuer des attaques similaires en utilisant uniquement les différences de synchronisation entre le traitement des remplissages valides et non valides.

À condition que le schéma de chiffrement utilise une signature et que la vérification de la signature soit effectuée avec un Runtime fixe pour une longueur de données donnée (quel que soit le contenu), l’intégrité des données peut être vérifiée sans émettre d’informations à une personne malveillante via un [canal latéral](https://en.wikipedia.org/wiki/Side-channel_attack). Étant donné que le contrôle d’intégrité rejette les messages falsifiés, la menace Oracle de remplissage est atténuée.

## <a name="guidance"></a>Aide

Tout d’abord, Microsoft recommande que toutes les données qui ont des besoins de confidentialité soient transmises sur le protocole TLS (Transport Layer Security), le successeur de protocole SSL (SSL).

Ensuite, analysez votre application pour :

- Comprenez précisément le chiffrement que vous effectuez et le chiffrement fourni par les plateformes et les API que vous utilisez.
- Veillez à ce que chaque utilisation de chaque couche d’un [algorithme de chiffrement par bloc](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)symétrique, comme AES et 3DES, en mode CBC incorpore l’utilisation d’une vérification de l’intégrité des données à clé secrète (une signature asymétrique, un code HMAC ou pour modifier le mode de chiffrement en mode de [chiffrement authentifié](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE), tel que GCM ou CCM).

En se basant sur la recherche actuelle, il est généralement supposé que lorsque les étapes d’authentification et de chiffrement sont effectuées indépendamment pour les modes de chiffrement non-AE, l’authentification du texte chiffré (chiffre-Then-Sign) est la meilleure option générale. Toutefois, il n’y a aucune réponse correcte à une seule taille pour le chiffrement et cette généralisation n’est pas aussi efficace que les conseils dirigés d’un cryptographe professionnel.

Les applications qui ne peuvent pas modifier leur format de messagerie mais effectuent un déchiffrement CBC non authentifié sont encouragées à essayer d’incorporer des atténuations telles que :

- Déchiffrer sans autoriser le déchiffreur à vérifier ou supprimer le remplissage :
  - Tout remplissage qui a été appliqué doit toujours être supprimé ou ignoré, vous déplacez la charge dans votre application.
  - L’avantage est que la vérification et la suppression du remplissage peuvent être incorporées dans d’autres logiques de vérification des données d’application. Si la vérification de la marge intérieure et la vérification des données peuvent être effectuées en temps constant, la menace est réduite.
  - Étant donné que l’interprétation du remplissage change la longueur de message perçue, il se peut qu’il y ait toujours des informations de minutage émises à partir de cette approche.
- Modifiez le mode de remplissage de déchiffrement en ISO10126 :
  - Le remplissage de déchiffrement ISO10126 est compatible avec le remplissage de chiffrement PKCS7 et le remplissage de chiffrement ANSIX923.
  - La modification du mode réduit la connaissance Oracle de remplissage à 1 octet au lieu du bloc entier. Toutefois, si le contenu a un pied de page bien connu, tel qu’un élément XML de fermeture, les attaques connexes peuvent continuer à attaquer le reste du message.
  - Cela n’empêche pas non plus la récupération en texte clair dans les situations où l’attaquant peut forcer le même texte en clair à être chiffré plusieurs fois avec un décalage de message différent.
- Portez l’évaluation d’un appel de déchiffrement pour amortir le signal de minutage :
  - Le calcul de la durée de conservation doit avoir un minimum de temps pour l’opération de déchiffrement pour un segment de données qui contient le remplissage.
  - Les calculs de temps doivent être effectués conformément aux instructions fournies dans [acquisition d’horodatages haute résolution](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), et non à l’aide de <xref:System.Environment.TickCount?displayProperty=nameWithType> (sous réserve de basculement/débordement) ou de la soustraction de deux horodateurs système (soumis à des erreurs d’ajustement NTP).
  - Les calculs de temps doivent être inclus dans l’opération de déchiffrement, y compris toutes C++ les exceptions potentielles dans les applications ou managées, et non simplement complétées à la fin.
  - En cas de réussite ou d’échec, la porte de synchronisation doit retourner une erreur lorsqu’elle expire.
- Les services qui effectuent un déchiffrement non authentifié doivent avoir une analyse en place pour détecter qu’un flux de messages « non valides » est arrivé.
  - Gardez à l’esprit que ce signal contient à la fois des faux positifs (données endommagées de manière légitime) et des faux négatifs (en étalant l’attaque sur une durée suffisamment longue pour échapper à la détection).

## <a name="finding-vulnerable-code---native-applications"></a>Recherche de code vulnérable-applications natives

Pour les programmes basés sur la bibliothèque Windows Cryptography : Next Generation (CNG) :

- L’appel de déchiffrement est [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), en spécifiant l’indicateur `BCRYPT_BLOCK_PADDING`.
- Le handle de clé a été initialisé en appelant [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) avec [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) défini sur `BCRYPT_CHAIN_MODE_CBC`.
  - Étant donné que `BCRYPT_CHAIN_MODE_CBC` est la valeur par défaut, le code affecté n’a peut-être pas affecté de valeur pour `BCRYPT_CHAINING_MODE`.

Pour les programmes basés sur l’ancienne API de chiffrement Windows :

- L’appel de déchiffrement consiste à [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) avec `Final=TRUE`.
- Le handle de clé a été initialisé en appelant [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) avec [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) défini sur `CRYPT_MODE_CBC`.
  - Étant donné que `CRYPT_MODE_CBC` est la valeur par défaut, le code affecté n’a peut-être pas affecté de valeur pour `KP_MODE`.

## <a name="finding-vulnerable-code---managed-applications"></a>Recherche d’applications gérées par code vulnérables

- L’appel de déchiffrement concerne les méthodes <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> ou <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> sur <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.
  - Cela inclut les types dérivés suivants dans .NET, mais peut également inclure des types tiers :
    - <xref:System.Security.Cryptography.Aes>
    - <xref:System.Security.Cryptography.AesCng>
    - <xref:System.Security.Cryptography.AesCryptoServiceProvider>
    - <xref:System.Security.Cryptography.AesManaged>
    - <xref:System.Security.Cryptography.DES>
    - <xref:System.Security.Cryptography.DESCryptoServiceProvider>
    - <xref:System.Security.Cryptography.RC2>
    - <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
    - <xref:System.Security.Cryptography.Rijndael>
    - <xref:System.Security.Cryptography.RijndaelManaged>
    - <xref:System.Security.Cryptography.TripleDES>
    - <xref:System.Security.Cryptography.TripleDESCng>
    - <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>
- La propriété <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> a été définie sur <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>ou <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.
  - Étant donné que <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> est la valeur par défaut, le code affecté n’a peut-être jamais affecté la propriété <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>.
- La propriété <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> a été définie sur <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Étant donné que <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> est la valeur par défaut, le code affecté n’a peut-être jamais affecté la propriété <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Recherche de code vulnérable-syntaxe de message cryptographique

Un message CMS EnvelopedData non authentifié dont le contenu chiffré utilise le mode CBC AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) ou RC2 (1.2.840.113549.3.2) est vulnérable, ainsi que des messages utilisant d’autres algorithmes de chiffrement par bloc en mode CBC.

Alors que les chiffrements de flux ne sont pas sensibles à cette vulnérabilité particulière, Microsoft recommande de toujours authentifier les données par le biais de l’inspection de la valeur ContentEncryptionAlgorithm.

Pour les applications managées, un objet BLOB EnvelopedData CMS peut être détecté comme n’importe quelle valeur transmise à <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.

Pour les applications natives, un objet BLOB CMS EnvelopedData peut être détecté comme n’importe quelle valeur fournie à un descripteur CMS via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) dont le [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) résultant est `CMSG_ENVELOPED` et/ou le descripteur CMS reçoit ultérieurement une instruction `CMSG_CTRL_DECRYPT` via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).

## <a name="vulnerable-code-example---managed"></a>Exemple de code vulnérable-géré

Cette méthode lit un cookie et le déchiffre et aucune vérification de l’intégrité des données n’est visible. Par conséquent, le contenu d’un cookie lu par cette méthode peut être attaqué par l’utilisateur qui l’a reçu, ou par tout attaquant qui a obtenu la valeur du cookie chiffré.

```csharp
private byte[] DecryptCookie(string cookieName)
{
    HttpCookie cookie = Request.Cookies[cookieName];

    if (cookie == null)
    {
        return null;
    }

    using (ICryptoTransform decryptor = _aes.CreateDecryptor())
    using (MemoryStream memoryStream = new MemoryStream())
    using (CryptoStream cryptoStream =
        new CryptoStream(memoryStream, decryptor, CryptoStreamMode.Write))
    {
        byte[] readCookie = Convert.FromBase64String(cookie.Value);
        cryptoStream.Write(readCookie, 0, readCookie.Length);
        cryptoStream.FlushFinalBlock();
        return memoryStream.ToArray();
    }
}
```

## <a name="example-code-following-recommended-practices---managed"></a>Exemple de code suivant les pratiques recommandées-géré

L’exemple de code suivant utilise un format de message non standard de

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

où les identificateurs d’algorithme `cipher_algorithm_id` et `hmac_algorithm_id` sont des représentations propres à l’application (non standard) de ces algorithmes. Ces identificateurs peuvent être logiques dans d’autres parties de votre protocole de messagerie existant plutôt que sous la forme d’un ByteStream non-concaténé.

Cet exemple utilise également une clé principale unique pour dériver une clé de chiffrement et une clé HMAC. Cela est fourni pour faciliter la conversion d’une application à clé unique en application à double clé et pour encourager la conservation des deux clés en tant que valeurs différentes. Il garantit également que la clé et la clé de chiffrement HMAC ne peuvent pas être désynchronisées.

Cet exemple n’accepte pas de <xref:System.IO.Stream> pour le chiffrement ou le déchiffrement. Le format de données actuel rend le chiffrement à un passage difficile, car la valeur de `hmac_tag` précède le texte chiffré. Toutefois, ce format a été choisi, car il conserve tous les éléments de taille fixe au début afin de simplifier l’analyseur. Avec ce format de données, le déchiffrement à un passage est possible, bien qu’un implémenteur soit vigilant pour appeler GetHashAndReset et vérifier le résultat avant d’appeler TransformFinalBlock. Si le chiffrement de la diffusion en continu est important, un autre mode AE peut être nécessaire.

```csharp
// ==++==
//
//   Copyright (c) Microsoft Corporation.  All rights reserved.
//
//   Shared under the terms of the Microsoft Public License,
//   https://opensource.org/licenses/MS-PL
//
// ==--==

using System;
using System.Diagnostics;
using System.IO;
using System.Runtime.CompilerServices;
using System.Security.Cryptography;

namespace Microsoft.Examples.Cryptography
{
    public enum AeCipher : byte
    {
        Unknown,
        Aes256CbcPkcs7,
    }

    public enum AeMac : byte
    {
        Unknown,
        HMACSHA256,
        HMACSHA384,
    }

    /// <summary>
    /// Provides extension methods to make HashAlgorithm look like .NET Core's
    /// IncrementalHash
    /// </summary>
    internal static class IncrementalHashExtensions
    {
        public static void AppendData(this HashAlgorithm hash, byte[] data)
        {
            hash.TransformBlock(data, 0, data.Length, null, 0);
        }

        public static void AppendData(
            this HashAlgorithm hash,
            byte[] data,
            int offset,
            int length)
        {
            hash.TransformBlock(data, offset, length, null, 0);
        }

        public static byte[] GetHashAndReset(this HashAlgorithm hash)
        {
            hash.TransformFinalBlock(Array.Empty<byte>(), 0, 0);
            return hash.Hash;
        }
    }

    public static partial class AuthenticatedEncryption
    {
        /// <summary>
        /// Use <paramref name="masterKey"/> to derive two keys (one cipher, one HMAC)
        /// to provide authenticated encryption for <paramref name="message"/>.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="message">The message to encrypt</param>
        /// <returns>
        /// A concatenation of
        /// [cipher algorithm+chainmode+padding][mac algorithm][authtag][IV][ciphertext],
        /// suitable to be passed to <see cref="Decrypt"/>.
        /// </returns>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or bigger) value generated
        /// by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>.
        /// This implementation chooses to block deficient inputs by length, but does not
        /// make any attempt at discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase)
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Encrypt(byte[] masterKey, byte[] message)
        {
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (message == null)
                throw new ArgumentNullException(nameof(message));

            // First, choose an encryption scheme.
            AeCipher aeCipher = AeCipher.Aes256CbcPkcs7;

            // Second, choose an authentication (message integrity) scheme.
            //
            // In this example we use the master key length to change from HMACSHA256 to
            // HMACSHA384, but that is completely arbitrary. This mostly represents a
            // "cryptographic needs change over time" scenario.
            AeMac aeMac = masterKey.Length < 48 ? AeMac.HMACSHA256 : AeMac.HMACSHA384;

            // It's good to be able to identify what choices were made when a message was
            // encrypted, so that the message can later be decrypted. This allows for
            // future versions to add support for new encryption schemes, but still be
            // able to read old data. A practice known as "cryptographic agility".
            //
            // This is similar in practice to PKCS#7 messaging, but this uses a
            // private-scoped byte rather than a public-scoped Object IDentifier (OID).
            // Please note that the scheme in this example adheres to no particular
            // standard, and is unlikely to survive to a more complete implementation in
            // the .NET Framework.
            //
            // You may be well-served by prepending a version number byte to this
            // message, but may want to avoid the value 0x30 (the leading byte value for
            // DER-encoded structures such as X.509 certificates and PKCS#7 messages).
            byte[] algorithmChoices = { (byte)aeCipher, (byte)aeMac };
            byte[] iv;
            byte[] cipherText;
            byte[] tag;

            // Using our algorithm choices, open an HMAC (as an authentication tag
            // generator) and a SymmetricAlgorithm which use different keys each derived
            // from the same master key.
            //
            // A custom implementation may very well have distinctly managed secret keys
            // for the MAC and cipher, this example merely demonstrates the master to
            // derived key methodology to encourage key separation from the MAC and
            // cipher keys.
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
                using (ICryptoTransform encryptor = cipher.CreateEncryptor())
                {
                    // Since no IV was provided, a random one has been generated
                    // during the call to CreateEncryptor.
                    //
                    // But note that it only does the auto-generation once. If the cipher
                    // object were used again, a call to GenerateIV would have been
                    // required.
                    iv = cipher.IV;

                    cipherText = Transform(encryptor, message, 0, message.Length);
                }

                // The IV and ciphertest both need to be included in the MAC to prevent
                // tampering.
                //
                // By including the algorithm identifiers, we have technically moved from
                // simple Authenticated Encryption (AE) to Authenticated Encryption with
                // Additional Data (AEAD). By including the algorithm identifiers in the
                // MAC, it becomes harder for an attacker to change them as an attempt to
                // perform a downgrade attack.
                //
                // If you've added a data format version field, it can also be included
                // in the MAC to further inhibit an attacker's options for confusing the
                // data processor into believing the tampered message is valid.
                tagGenerator.AppendData(algorithmChoices);
                tagGenerator.AppendData(iv);
                tagGenerator.AppendData(cipherText);
                tag = tagGenerator.GetHashAndReset();
            }

            // Build the final result as the concatenation of everything except the keys.
            int totalLength =
                algorithmChoices.Length +
                tag.Length +
                iv.Length +
                cipherText.Length;

            byte[] output = new byte[totalLength];
            int outputOffset = 0;

            Append(algorithmChoices, output, ref outputOffset);
            Append(tag, output, ref outputOffset);
            Append(iv, output, ref outputOffset);
            Append(cipherText, output, ref outputOffset);

            Debug.Assert(outputOffset == output.Length);
            return output;
        }

        /// <summary>
        /// Reads a message produced by <see cref="Encrypt"/> after verifying it hasn't
        /// been tampered with.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="cipherText">
        /// The output of <see cref="Encrypt"/>: a concatenation of a cipher ID, mac ID,
        /// authTag, IV, and cipherText.
        /// </param>
        /// <returns>The decrypted content.</returns>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="masterKey"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="cipherText"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="CryptographicException">
        /// <paramref name="cipherText"/> identifies unknown algorithms, is not long
        /// enough, fails a data integrity check, or fails to decrypt.
        /// </exception>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or larger) value
        /// generated by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>. This implementation chooses to
        /// block deficient inputs by length, but doesn't make any attempt at
        /// discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase),
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Decrypt(byte[] masterKey, byte[] cipherText)
        {
            // This example continues the .NET practice of throwing exceptions for
            // failures. If you consider message tampering to be normal (and thus
            // "not exceptional") behavior, you may like the signature
            // bool Decrypt(byte[] messageKey, byte[] cipherText, out byte[] message)
            // better.
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (cipherText == null)
                throw new ArgumentNullException(nameof(cipherText));

            // The format of this message is assumed to be public, so there's no harm in
            // saying ahead of time that the message makes no sense.
            if (cipherText.Length < 2)
            {
                throw new CryptographicException();
            }

            // Use the message algorithm headers to determine what cipher algorithm and
            // MAC algorithm are going to be used. Since the same Key Derivation
            // Functions (KDFs) are being used in Decrypt as Encrypt, the keys are also
            // the same.
            AeCipher aeCipher = (AeCipher)cipherText[0];
            AeMac aeMac = (AeMac)cipherText[1];

            using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                int blockSizeInBytes = cipher.BlockSize / 8;
                int tagSizeInBytes = tagGenerator.HashSize / 8;
                int headerSizeInBytes = 2;
                int tagOffset = headerSizeInBytes;
                int ivOffset = tagOffset + tagSizeInBytes;
                int cipherTextOffset = ivOffset + blockSizeInBytes;
                int cipherTextLength = cipherText.Length - cipherTextOffset;
                int minLen = cipherTextOffset + blockSizeInBytes;

                // Again, the minimum length is still assumed to be public knowledge,
                // nothing has leaked out yet. The minimum length couldn't just be calculated
                // without reading the header.
                if (cipherText.Length < minLen)
                {
                    throw new CryptographicException();
                }

                // It's very important that the MAC be calculated and verified before
                // proceeding to decrypt the ciphertext, as this prevents any sort of
                // information leaking out to an attacker.
                //
                // Don't include the tag in the calculation, though.

                // First, everything before the tag (the cipher and MAC algorithm ids)
                tagGenerator.AppendData(cipherText, 0, tagOffset);

                // Skip the data before the tag and the tag, then read everything that
                // remains.
                tagGenerator.AppendData(
                    cipherText,
                    tagOffset + tagSizeInBytes,
                    cipherText.Length - tagSizeInBytes - tagOffset);

                byte[] generatedTag = tagGenerator.GetHashAndReset();

                // The time it took to get to this point has so far been a function only
                // of the length of the data, or of non-encrypted values (e.g. it could
                // take longer to prepare the *key* for the HMACSHA384 MAC than the
                // HMACSHA256 MAC, but the algorithm choice wasn't a secret).
                //
                // If the verification of the authentication tag aborts as soon as a
                // difference is found in the byte arrays then your program may be
                // acting as a timing oracle which helps an attacker to brute-force the
                // right answer for the MAC. So, it's very important that every possible
                // "no" (2^256-1 of them for HMACSHA256) be evaluated in as close to the
                // same amount of time as possible. For this, we call CryptographicEquals
                if (!CryptographicEquals(
                    generatedTag,
                    0,
                    cipherText,
                    tagOffset,
                    tagSizeInBytes))
                {
                    // Assuming every tampered message (of the same length) took the same
                    // amount of time to process, we can now safely say
                    // "this data makes no sense" without giving anything away.
                    throw new CryptographicException();
                }

                // Restore the IV into the symmetricAlgorithm instance.
                byte[] iv = new byte[blockSizeInBytes];
                Buffer.BlockCopy(cipherText, ivOffset, iv, 0, iv.Length);
                cipher.IV = iv;

                using (ICryptoTransform decryptor = cipher.CreateDecryptor())
                {
                    return Transform(
                        decryptor,
                        cipherText,
                        cipherTextOffset,
                        cipherTextLength);
                }
            }
        }

        private static byte[] Transform(
            ICryptoTransform transform,
            byte[] input,
            int inputOffset,
            int inputLength)
        {
            // Many of the implementations of ICryptoTransform report true for
            // CanTransformMultipleBlocks, and when the entire message is available in
            // one shot this saves on the allocation of the CryptoStream and the
            // intermediate structures it needs to properly chunk the message into blocks
            // (since the underlying stream won't always return the number of bytes
            // needed).
            if (transform.CanTransformMultipleBlocks)
            {
                return transform.TransformFinalBlock(input, inputOffset, inputLength);
            }

            // If our transform couldn't do multiple blocks at once, let CryptoStream
            // handle the chunking.
            using (MemoryStream messageStream = new MemoryStream())
            using (CryptoStream cryptoStream =
                new CryptoStream(messageStream, transform, CryptoStreamMode.Write))
            {
                cryptoStream.Write(input, inputOffset, inputLength);
                cryptoStream.FlushFinalBlock();
                return messageStream.ToArray();
            }
        }

        /// <summary>
        /// Open a properly configured <see cref="SymmetricAlgorithm"/> conforming to the
        /// scheme identified by <paramref name="aeCipher"/>.
        /// </summary>
        /// <param name="aeCipher">The cipher mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// A SymmetricAlgorithm object with the right key, cipher mode, and padding
        /// mode; or <c>null</c> on unknown algorithms.
        /// </returns>
        private static SymmetricAlgorithm GetCipher(AeCipher aeCipher, byte[] masterKey)
        {
            SymmetricAlgorithm symmetricAlgorithm;

            switch (aeCipher)
            {
                case AeCipher.Aes256CbcPkcs7:
                    symmetricAlgorithm = Aes.Create();
                    // While 256-bit, CBC, and PKCS7 are all the default values for these
                    // properties, being explicit helps comprehension more than it hurts
                    // performance.
                    symmetricAlgorithm.KeySize = 256;
                    symmetricAlgorithm.Mode = CipherMode.CBC;
                    symmetricAlgorithm.Padding = PaddingMode.PKCS7;
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            //
            // Since none of the symmetric encryption algorithms currently in .NET
            // support key sizes greater than 256-bit, we can use HMACSHA256 with
            // NIST SP 800-108 5.1 (Counter Mode KDF) to derive a value that is
            // no smaller than the key size, then Array.Resize to trim it down as
            // needed.

            using (HMAC hmac = new HMACSHA256(masterKey))
            {
                // i=1, Label=ASCII(cipher)
                byte[] cipherKey = hmac.ComputeHash(
                    new byte[] { 1, 99, 105, 112, 104, 101, 114 });

                // Resize the array to the desired keysize. KeySize is in bits,
                // and Array.Resize wants the length in bytes.
                Array.Resize(ref cipherKey, symmetricAlgorithm.KeySize / 8);

                symmetricAlgorithm.Key = cipherKey;
            }

            return symmetricAlgorithm;
        }

        /// <summary>
        /// Open a properly configured <see cref="HMAC"/> conforming to the scheme
        /// identified by <paramref name="aeMac"/>.
        /// </summary>
        /// <param name="aeMac">The message authentication mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// An HMAC object with the proper key, or <c>null</c> on unknown algorithms.
        /// </returns>
        private static HMAC GetMac(AeMac aeMac, byte[] masterKey)
        {
            HMAC hmac;

            switch (aeMac)
            {
                case AeMac.HMACSHA256:
                    hmac = new HMACSHA256();
                    break;
                case AeMac.HMACSHA384:
                    hmac = new HMACSHA384();
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            // Since the output size of the HMAC is the same as the ideal key size for
            // the HMAC, we can use the master key over a fixed input once to perform
            // NIST SP 800-108 5.1 (Counter Mode KDF):
            hmac.Key = masterKey;

            // i=1, Context=ASCII(MAC)
            byte[] newKey = hmac.ComputeHash(new byte[] { 1, 77, 65, 67 });

            hmac.Key = newKey;
            return hmac;
        }

        // A simple helper method to ensure that the offset (writePos) always moves
        // forward with new data.
        private static void Append(byte[] newData, byte[] combinedData, ref int writePos)
        {
            Buffer.BlockCopy(newData, 0, combinedData, writePos, newData.Length);
            writePos += newData.Length;
        }

        /// <summary>
        /// Compare the contents of two arrays in an amount of time which is only
        /// dependent on <paramref name="length"/>.
        /// </summary>
        /// <param name="a">An array to compare to <paramref name="b"/>.</param>
        /// <param name="aOffset">
        /// The starting position within <paramref name="a"/> for comparison.
        /// </param>
        /// <param name="b">An array to compare to <paramref name="a"/>.</param>
        /// <param name="bOffset">
        /// The starting position within <paramref name="b"/> for comparison.
        /// </param>
        /// <param name="length">
        /// The number of bytes to compare between <paramref name="a"/> and
        /// <paramref name="b"/>.</param>
        /// <returns>
        /// <c>true</c> if both <paramref name="a"/> and <paramref name="b"/> have
        /// sufficient length for the comparison and all of the applicable values are the
        /// same in both arrays; <c>false</c> otherwise.
        /// </returns>
        /// <remarks>
        /// An "insufficient data" <c>false</c> response can happen early, but otherwise
        /// a <c>true</c> or <c>false</c> response take the same amount of time.
        /// </remarks>
        [MethodImpl(MethodImplOptions.NoInlining | MethodImplOptions.NoOptimization)]
        private static bool CryptographicEquals(
            byte[] a,
            int aOffset,
            byte[] b,
            int bOffset,
            int length)
        {
            Debug.Assert(a != null);
            Debug.Assert(b != null);
            Debug.Assert(length >= 0);

            int result = 0;

            if (a.Length - aOffset < length || b.Length - bOffset < length)
            {
                return false;
            }

            unchecked
            {
                for (int i = 0; i < length; i++)
                {
                    // Bitwise-OR of subtraction has been found to have the most
                    // stable execution time.
                    //
                    // This cannot overflow because bytes are 1 byte in length, and
                    // result is 4 bytes.
                    // The OR propagates all set bytes, so the differences are only
                    // present in the lowest byte.
                    result = result | (a[i + aOffset] - b[i + bOffset]);
                }
            }

            return result == 0;
        }
    }
}
```
