---
title: Vulnérabilité de décryptage de LA SRC
description: Apprenez à détecter et à atténuer les vulnérabilités de synchronisation avec le décryptage symétrique du mode Cipher-Block-Chaining (CBC) à l’aide du rembourrage.
ms.date: 06/12/2018
author: blowdart
ms.openlocfilehash: 47520ea4c9c7d0ef4d79378c93c6ce1f2ba7dd6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186095"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>Vulnérabilités de temporisation avec le déchiffrement symétrique en mode CBC à l’aide du remplissage

Microsoft estime qu’il n’est plus sûr de déchiffrer les données cryptées avec le mode de chiffrement symétrique Cipher-Block-Chaining (CBC) lorsque le rembourrage vérifiable a été appliqué sans d’abord assurer l’intégrité du texte de chiffrement, à l’exception de très spécifiques Circonstances. Ce jugement est basé sur des recherches cryptographiques actuellement connues.

## <a name="introduction"></a>Introduction

Une attaque d’oracle de rembourrage est un type d’attaque contre les données chiffrées qui permet à l’attaquant de déchiffrer le contenu des données, sans connaître la clé.

Un oracle se réfère à un "dire" qui donne à un attaquant des informations sur si l’action qu’ils exécutent est correcte ou non. Imaginez jouer à un jeu de société ou de cartes avec un enfant. Quand leur visage s’illumine avec un grand sourire parce qu’ils pensent qu’ils sont sur le point de faire un bon mouvement, c’est un oracle. Vous, en tant qu’adversaire, pouvez utiliser cet oracle pour planifier votre prochain mouvement de manière appropriée.

Le rembourrage est un terme cryptographique spécifique. Certains chiffrements, qui sont les algorithmes utilisés pour chiffrer vos données, fonctionnent sur des blocs de données où chaque bloc est une taille fixe. Si les données que vous souhaitez chiffrer ne sont pas de la bonne taille pour remplir les blocs, vos données sont rembourrées jusqu’à ce qu’elles le soient. De nombreuses formes de rembourrage exigent que le rembourrage soit toujours présent, même si l’entrée originale était de la bonne taille. Cela permet au rembourrage d’être toujours retiré en toute sécurité lors du décryptage.

Mettre les deux choses ensemble, une implémentation logicielle avec un oracle rembourrage révèle si les données décryptées a rembourrage valide. L’oracle pourrait être quelque chose d’aussi simple que le retour d’une valeur qui dit "Rembourrage invalide" ou quelque chose de plus compliqué comme prendre un temps sensiblement différent pour traiter un bloc valide par opposition à un bloc invalide.

Les chiffrements à base de blocs ont une autre propriété, appelée le mode, qui détermine la relation des données dans le premier bloc aux données dans le deuxième bloc, et ainsi de suite. L’un des modes les plus couramment utilisés est CBC. CBC introduit un premier bloc aléatoire, connu sous le nom de vecteur d’initialisation (IV), et combine le bloc précédent avec le résultat du cryptage statique pour le rendre tel que le cryptage du même message avec la même clé ne produit pas toujours la même sortie cryptée.

Un attaquant peut utiliser un oracle rembourrage, en combinaison avec la façon dont les données de LA SRC est structurée, pour envoyer des messages légèrement modifiés au code qui expose l’oracle, et continuer à envoyer des données jusqu’à ce que l’oracle leur indique que les données sont correctes. De cette réponse, l’attaquant peut déchiffrer le message byte byte byte.

Les réseaux informatiques modernes sont d’une telle qualité qu’un attaquant peut détecter de très petites différences (moins de 0,1 ms) dans le temps d’exécution sur les systèmes distants.Les applications qui supposent qu’un décryptage réussi ne peut se produire que lorsque les données n’ont pas été altérées peuvent être vulnérables aux attaques à partir d’outils qui sont conçus pour observer les différences dans le décryptage réussi et infructueux. Bien que cette différence de calendrier puisse être plus importante dans certaines langues ou bibliothèques que dans d’autres, on croit maintenant qu’il s’agit d’une menace pratique pour toutes les langues et bibliothèques lorsque la réponse de l’application à l’échec est prise en compte.

Cette attaque repose sur la possibilité de modifier les données chiffrées et de tester le résultat avec l’oracle. La seule façon d’atténuer complètement l’attaque est de détecter les modifications apportées aux données chiffrées et de refuser d’effectuer des actions à ce sujet. La façon standard de le faire est de créer une signature pour les données et de valider cette signature avant toute opération est effectuée. La signature doit être vérifiable, elle ne peut pas être créée par l’attaquant, sinon ils modifieraient les données chiffrées, puis calculeraient une nouvelle signature basée sur les données modifiées. Un type commun de signature appropriée est connu sous le nom de code d’authentification des messages à clé (HMAC). Un HMAC diffère d’un checksum en ce qu’il prend une clé secrète, connue seulement de la personne qui produit le HMAC et de la personne qui la valide. Sans la possession de la clé, vous ne pouvez pas produire un HMAC correct. Lorsque vous recevez vos données, vous prenez les données chiffrées, calculez indépendamment le HMAC à l’aide de la clé secrète que vous et l’expéditeur partagez, puis comparez le HMAC qu’ils ont envoyé par rapport à celui que vous avez calculé. Cette comparaison doit être le temps constant, sinon vous avez ajouté un autre oracle détectable, permettant un autre type d’attaque.

En résumé, pour utiliser des chiffres rembourrés de blocs de CBC en toute sécurité, vous devez les combiner avec un HMAC (ou une autre vérification de l’intégrité des données) que vous validez à l’aide d’une comparaison de temps constante avant d’essayer de déchiffrer les données. Étant donné que tous les messages modifiés prennent le même temps de produire une réponse, l’attaque est empêchée.

## <a name="who-is-vulnerable"></a>Qui est vulnérable

Cette vulnérabilité s’applique à la fois aux applications gérées et natives qui exécutent leur propre cryptage et décryptage. Cela comprend, par exemple :

- Une application qui crypte un cookie pour le décryptage ultérieur sur le serveur.
- Une application de base de données qui permet aux utilisateurs d’insérer des données dans une table dont les colonnes sont plus tard décryptées.
- Une application de transfert de données qui repose sur le chiffrement à l’aide d’une clé partagée pour protéger les données en transit.
- Une application qui crypte et décrypte les messages "à l’intérieur" du tunnel TLS.

Notez que l’utilisation de TLS seul peut ne pas vous protéger dans ces scénarios.

Une application vulnérable :

- Décrypte les données à l’aide du mode chiffreur de la SRC avec un mode rembourrage vérifiable, comme PKCS-7 ou ANSI X.923.
- Effectue le décryptage sans avoir effectué de vérification de l’intégrité des données (via un MAC ou une signature numérique asymétrique).

Cela s’applique également aux applications construites au-dessus des abstractions au-dessus de ces primitifs, telles que la structure Cryptographic Message Syntax (PKCS-7/CMS) EnvelopedData.

## <a name="related-areas-of-concern"></a>Domaines de préoccupation connexes

La recherche a amené Microsoft à s’inquiéter davantage des messages de la SRC qui sont rembourrés par le rembourrage équivalent ISO 10126 lorsque le message a une structure de pied bien connue ou prévisible. Par exemple, le contenu préparé selon les règles de la syntaxe de chiffrement et de la recommandation de traitement W3C XML (xmlenc, EncryptedXml). Alors que les directives W3C pour signer le message puis chiffrer a été jugé approprié à l’époque, Microsoft recommande maintenant toujours faire chiffre-alors-signe.

Les développeurs d’applications doivent toujours être conscients de vérifier l’applicabilité d’une clé de signature asymétrique, car il n’y a pas de relation de confiance inhérente entre une clé asymétrique et un message arbitraire.

## <a name="details"></a>Détails

Historiquement, il y a eu consensus sur le fait qu’il est important de chiffrer et d’authentifier des données importantes, en utilisant des moyens tels que les signatures HMAC ou RSA. Cependant, il y a eu des conseils moins clairs quant à la façon de séquencer les opérations de cryptage et d’authentification. En raison de la vulnérabilité détaillée dans cet article, les conseils de Microsoft est maintenant d’utiliser toujours le paradigme "crypt-then-sign". C’est-à-dire, d’abord chiffrer les données à l’aide d’une clé symétrique, puis calculer un MAC ou une signature asymétrique sur le texte de chiffrement (données chiffrées). Lors du décryptage des données, effectuez l’inverse. Tout d’abord, confirmer le MAC ou la signature du texte de chiffrement, puis le déchiffrer.

Une classe de vulnérabilités connues sous le nom de « attaques d’oracle de rembourrage » existe depuis plus de 10 ans. Ces vulnérabilités permettent à un attaquant de déchiffrer les données cryptées par des algorithmes de blocs symétriques, tels que AES et 3DES, en utilisant pas plus de 4096 tentatives par bloc de données. Ces vulnérabilités utilisent le fait que les chiffres de bloc sont le plus souvent utilisés avec des données verifiables rembourrage à la fin. Il a été constaté que si un attaquant peut altérer le texte de chiffrement et savoir si la falsification a causé une erreur dans le format du rembourrage à l’extrémité, l’attaquant peut décrypter les données.

Initialement, les attaques pratiques étaient basées sur des services qui rendraient différents codes d’erreur basés sur la validité du rembourrage, comme la vulnérabilité ASP.NET [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070). Cependant, Microsoft estime maintenant qu’il est pratique de mener des attaques similaires en utilisant uniquement les différences dans le calendrier entre le traitement du rembourrage valide et invalide.

À condition que le système de cryptage utilise une signature et que la vérification de signature soit effectuée avec un délai d’exécution fixe pour une durée donnée de données (quel que soit le contenu), l’intégrité des données peut être vérifiée sans émettre d’informations à un attaquant via un [canal latéral](https://en.wikipedia.org/wiki/Side-channel_attack). Étant donné que la vérification de l’intégrité rejette tout message trafiqué, la menace d’oracle rembourrage est atténuée.

## <a name="guidance"></a>Assistance

Tout d’abord, Microsoft recommande que toutes les données qui ont la confidentialité doivent être transmises sur la sécurité des couches de transport (TLS), le successeur de Secure Sockets Layer (SSL).

Ensuite, analysez votre application pour :

- Comprendre précisément le chiffrement que vous effectuez et le chiffrement fourni par les plates-formes et les API que vous utilisez.
- Assurez-vous que chaque utilisation à chaque couche d’un algorithme de [chiffrement](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)de blocs symétriques, comme AES et 3DES, en mode CBC, intègre l’utilisation d’une vérification secrète de l’intégrité des données (une signature asymétrique, un HMAC, ou pour changer le mode chiffrement en mode [cryptage authentifié](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) comme GCM ou CCM).

Sur la base de la recherche actuelle, on croit généralement que lorsque les étapes d’authentification et de cryptage sont effectuées indépendamment pour les modes de cryptage non-AE, l’authentification du texte de chiffrement (crypt-puis-signe) est la meilleure option générale. Cependant, il n’y a pas de réponse unique à la cryptographie et cette généralisation n’est pas aussi bonne que les conseils dirigés d’un cryptographe professionnel.

Les applications qui ne sont pas en mesure de modifier leur format de messagerie mais qui effectuent un décryptage non authentique à la SRC sont encouragées à essayer d’intégrer des mesures d’atténuation telles que :

- Décrypter sans permettre au décrypteur de vérifier ou d’enlever le rembourrage :
  - Tout rembourrage qui a été appliqué doit encore être supprimé ou ignoré, vous déplacez le fardeau dans votre application.
  - L’avantage est que la vérification et la suppression du rembourrage peuvent être incorporées dans d’autres logiques de vérification des données d’application. Si la vérification du rembourrage et la vérification des données peuvent être effectuées en temps constant, la menace est réduite.
  - Étant donné que l’interprétation du rembourrage modifie la longueur du message perçu, il peut tout de même y avoir des renseignements sur le moment émis par cette approche.
- Modifier le mode rembourrage de décryptage pour ISO10126 :
  - Le rembourrage de décryptage ISO10126 est compatible avec le rembourrage de cryptage PKCS7 et le rembourrage de chiffrement ANSIX923.
  - Changer le mode réduit la connaissance de l’oracle rembourrage à 1 byte au lieu de l’ensemble du bloc. Toutefois, si le contenu a un pied bien connu, comme un élément XML de fermeture, les attaques connexes peuvent continuer à attaquer le reste du message.
  - Cela n’empêche pas non plus la récupération de texte clair dans les situations où l’attaquant peut contraindre le même texte clair à être crypté plusieurs fois avec un message différent compensé.
- Portez l’évaluation d’un appel de décryptage pour amortir le signal de synchronisation :
  - Le calcul du temps de retenue doit avoir un minimum de plus de temps que l’opération de décryptage prendrait pour tout segment de données contenant du rembourrage.
  - Les calculs de temps doivent être effectués selon les directives dans [l’acquisition de timbres-temps](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps)à haute résolution, et non en utilisant <xref:System.Environment.TickCount?displayProperty=nameWithType> (sous réserve de renversement/débordement) ou en soustrayant deux timetamps du système (sous réserve d’erreurs d’ajustement NTP).
  - Les calculs de temps doivent inclure l’opération de décryptage, y compris toutes les exceptions potentielles dans les applications gérées ou CMD, et pas seulement rembourrées à la fin.
  - Si le succès ou l’échec a été déterminé encore, la porte de synchronisation doit retourner l’échec quand il expire.
- Les services qui effectuent un décryptage non athénisé devraient avoir une surveillance en place pour détecter qu’un flot de messages « invalides » est passé.
  - Gardez à l’esprit que ce signal comporte à la fois de faux positifs (données légitimement corrompues) et de faux négatifs (étaler l’attaque sur une période suffisamment longue pour échapper à la détection).

## <a name="finding-vulnerable-code---native-applications"></a>Trouver un code vulnérable - applications natives

Pour les programmes conçus contre la bibliothèque Windows Cryptography: Next Generation (CNG) :

- L’appel de décryptage est à [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), spécifiant le `BCRYPT_BLOCK_PADDING` drapeau.
- La poignée de clé a été parascée [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) en appelant `BCRYPT_CHAIN_MODE_CBC` [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) avec BCRYPT_CHAINING_MODE réglé à .
  - Depuis `BCRYPT_CHAIN_MODE_CBC` la valeur par défaut, le code `BCRYPT_CHAINING_MODE`affecté peut ne pas avoir attribué de valeur pour .

Pour les programmes conçus contre l’ancienne API cryptographique Windows :

- L’appel de décryptage est `Final=TRUE`de [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) avec .
- La poignée de clé a été parascée [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) en appelant `CRYPT_MODE_CBC` [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) avec KP_MODE réglé à .
  - Depuis `CRYPT_MODE_CBC` la valeur par défaut, le code `KP_MODE`affecté peut ne pas avoir attribué de valeur pour .

## <a name="finding-vulnerable-code---managed-applications"></a>Trouver un code vulnérable - applications gérées

- L’appel de décryptage <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> est <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>à la ou des <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> méthodes sur .
  - Cela comprend les types dérivés suivants dans le .NET, mais peut également inclure des types tiers:
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
- La <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> propriété a <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>été <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>réglée à , , ou .
  - Depuis <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> la valeur par défaut, le <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> code affecté peut ne jamais avoir attribué la propriété.
- La <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> propriété a été fixée à<xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - Depuis <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> la valeur par défaut, le <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> code affecté peut ne jamais avoir attribué la propriété.

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>Trouver un code vulnérable - syntaxe de message cryptographique

Message non athénisé cmS EnvelopedData dont le contenu crypté utilise le mode SRC de l’AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) ou RC2 (1.2.840.113549.3.2) vulnérables, ainsi que les messages utilisant d’autres algorithmes de chiffrement de blocs en mode CBC.

Bien que les chiffres de flux ne soient pas sensibles à cette vulnérabilité particulière, Microsoft recommande toujours d’authentifier les données sur l’inspection de la valeur ContentEncryptionAlgorithm.

Pour les applications gérées, un blob CMS EnvelopedData peut <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>être détecté comme n’importe quelle valeur qui est passée à .

Pour les applications natives, un blob CMS EnvelopedData peut être détecté comme n’importe quelle [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) valeur fournie à `CMSG_ENVELOPED` une poignée CMS via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) dont le CMSG_TYPE_PARAM résultant est et / ou la poignée CMS est plus tard envoyé une `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).

## <a name="vulnerable-code-example---managed"></a>Exemple de code vulnérable - géré

Cette méthode lit un cookie et le décrypte et aucune vérification de l’intégrité des données n’est visible. Par conséquent, le contenu d’un cookie qui est lu par cette méthode peut être attaqué par l’utilisateur qui l’a reçu, ou par tout attaquant qui a obtenu la valeur de cookie crypté.

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

## <a name="example-code-following-recommended-practices---managed"></a>Exemple de code suivant les pratiques recommandées - géré

Le code d’échantillon suivant utilise un format de message non standard de

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

où `cipher_algorithm_id` `hmac_algorithm_id` les identificateurs et les algorithmes sont des représentations d’applications locales (non standard) de ces algorithmes. Ces identificateurs peuvent avoir un sens dans d’autres parties de votre protocole de messagerie existant au lieu d’un bytestream concatenated nu.

Cet exemple utilise également une seule clé principale pour dériver à la fois une clé de chiffrement et une clé HMAC. Ceci est fourni à la fois comme une commodité pour transformer une application à touches individuellement en une application à double clé, et pour encourager à garder les deux clés comme des valeurs différentes. Il garantit en outre que la clé HMAC et la clé de chiffrement ne peuvent pas sortir de la synchronisation.

Cet échantillon n’accepte <xref:System.IO.Stream> pas un chiffrement ou un décryptage. Le format de données actuel rend le `hmac_tag` chiffrement d’un passage difficile parce que la valeur précède le texte de chiffrement. Cependant, ce format a été choisi parce qu’il conserve tous les éléments de taille fixe au début pour garder le parser plus simple. Avec ce format de données, un décryptage d’un passage est possible, bien qu’un implémenteur soit averti d’appeler GetHashAndReset et de vérifier le résultat avant d’appeler TransformFinalBlock. Si le chiffrement en streaming est important, un mode AE différent peut être nécessaire.

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
