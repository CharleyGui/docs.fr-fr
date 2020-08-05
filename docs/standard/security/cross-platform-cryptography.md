---
title: Chiffrement multiplateforme dans .NET Core et .NET 5
description: Découvrez les fonctionnalités de chiffrement sur les plateformes prises en charge par .NET.
ms.date: 06/19/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- cryptography, cross-platform
- encryption, cross-platform
ms.openlocfilehash: 61fd49e53761deac278b770003eb97241b6c2be9
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557149"
---
# <a name="cross-platform-cryptography-in-net-core-and-net-5"></a>Chiffrement multiplateforme dans .NET Core et .NET 5

Les opérations de chiffrement dans .NET Core et .NET 5 sont effectuées par les bibliothèques du système d’exploitation. Cette dépendance présente des avantages :

* Les applications .NET bénéficient de la fiabilité du système d’exploitation. La sécurisation des bibliothèques de chiffrement contre les vulnérabilités est une priorité élevée pour les fournisseurs de systèmes d’exploitation. Pour ce faire, ils fournissent des mises à jour que les administrateurs système doivent appliquer.
* Les applications .NET ont accès aux algorithmes validés par FIPS si les bibliothèques du système d’exploitation sont validées FIPS.

La dépendance sur les bibliothèques du système d’exploitation signifie également que les applications .NET peuvent uniquement utiliser les fonctionnalités de chiffrement prises en charge par le système d’exploitation. Bien que toutes les plateformes prennent en charge certaines fonctionnalités de base, certaines fonctionnalités prises en charge par .NET ne peuvent pas être utilisées sur certaines plateformes. Cet article identifie les fonctionnalités prises en charge sur chaque plateforme.

Cet article suppose que vous avez une bonne connaissance du chiffrement dans .NET. Pour plus d’informations, consultez [modèle de chiffrement .net](cryptography-model.md) et [services de chiffrement .net](cryptographic-services.md).

## <a name="hash-algorithms"></a>Algorithmes de hachage

Toutes les classes d’algorithme de hachage et d’authentification de message basé sur le hachage (HMAC), y compris les `*Managed` classes, diffèrent les bibliothèques du système d’exploitation. Bien que les performances des différentes bibliothèques du système d’exploitation diffèrent, elles doivent être compatibles.

## <a name="symmetric-encryption"></a>Chiffrement symétrique

Les chiffrements et le chaînage sous-jacents sont effectués par les bibliothèques système, et tous sont pris en charge par toutes les plateformes.

| Mode de chiffrement + | Windows | Linux | macOS |
|---------------|---------|-------|-------|
| AES-CBC       | ✔️     | ✔️    | ✔️   |
| AES-BCE       | ✔️     | ✔️    | ✔️   |
| 3DES-CBC      | ✔️     | ✔️    | ✔️   |
| 3DES-BCE      | ✔️     | ✔️    | ✔️   |
| DES-CBC       | ✔️     | ✔️    | ✔️   |
| DES-BCE       | ✔️     | ✔️    | ✔️   |

## <a name="authenticated-encryption"></a>Chiffrement authentifié

La prise en charge du chiffrement authentifié (AE) est fournie pour AES-CCM et AES-GCM via les <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName> <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName> classes et.

Sur Windows et Linux, les implémentations d’AES-CCM et AES-GCM sont fournies par les bibliothèques du système d’exploitation.

### <a name="aes-ccm-and-aes-gcm-on-macos"></a>AES-CCM et AES-GCM sur macOS

Sur macOS, les bibliothèques système ne prennent pas en charge AES-CCM ou AES-GCM pour le code tiers. par conséquent, les <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm> classes et utilisent OpenSSL pour la prise en charge. Les utilisateurs de macOS doivent obtenir une copie appropriée d’OpenSSL (libénigmatique) pour que ces types fonctionnent, et il doit se trouver dans un chemin d’accès auquel le système chargera une bibliothèque par défaut. Nous vous recommandons d’installer OpenSSL à partir d’un gestionnaire de package tel que homebrew.

Les `libcrypto.0.9.7.dylib` `libcrypto.0.9.8.dylib` bibliothèques et incluses dans MacOS proviennent de versions antérieures d’OpenSSL et ne seront pas utilisées. Les `libcrypto.35.dylib` `libcrypto.41.dylib` bibliothèques, et `libcrypto.42.dylib` sont issues de LibreSSL et ne seront pas utilisées.

### <a name="aes-ccm-keys-nonces-and-tags"></a>Clés AES-CCM, pointeurs et balises

* Tailles de clé

  AES-CCM fonctionne avec les clés 128, 192 et 256 bits.

* Tailles de nonce

  La <xref:System.Security.Cryptography.AesCcm> classe prend en charge les pointeurs 56, 64, 72, 80, 88, 96 et 104 bits (7, 8, 9, 10, 11, 12 et 13 octets).

* Tailles des balises

  La <xref:System.Security.Cryptography.AesCcm> classe prend en charge la création ou le traitement des balises 32, 48, 64, 80, 96, 112 et 128 bits (4, 8, 10, 12, 14 et 16 octets).

### <a name="aes-gcm-keys-nonces-and-tags"></a>AES-GCM, clés, pointeurs et balises

* Tailles de clé

  AES-GCM fonctionne avec les clés 128, 192 et 256 bits.

* Tailles de nonce

  La <xref:System.Security.Cryptography.AesGcm> classe prend en charge uniquement les pointeurss 96 bits (12 octets).

* Tailles des balises

  La <xref:System.Security.Cryptography.AesGcm> classe prend en charge la création ou le traitement de balises 96, 104, 112, 120 et 128 bits (12, 13, 14, 15 et 16 octets).

## <a name="asymmetric-cryptography"></a>Chiffrement asymétrique

Cette section comprend les sous-sections suivantes :

* [RSA](#rsa)
* [ECDSA](#ecdsa)
* [ECDH](#ecdh)
* [DSA](#dsa)

### <a name="rsa"></a>RSA

La génération de clés RSA (Rivest-Shamir-Adleman) est effectuée par les bibliothèques du système d’exploitation et est soumise à leurs limitations de taille et caractéristiques de performances.

Les opérations de clé RSA sont effectuées par les bibliothèques du système d’exploitation, et les types de clé qui peuvent être chargés sont soumis aux exigences du système d’exploitation.

.NET n’expose pas les opérations RSA « brutes » (sans remplissage).

Les bibliothèques du système d’exploitation sont utilisées pour le chiffrement et le remplissage du déchiffrement. Toutes les plateformes ne prennent pas en charge les mêmes options de marge intérieure :

| Mode de remplissage                          | Windows (CNG) | Linux (OpenSSL) | macOS | Windows (CAPI) |
|---------------------------------------|---------------|-----------------|-------|----------------|
| Chiffrement PKCS1                      | ✔️           | ✔️              | ✔️   | ✔️             |
| OAEP-SHA-1                          | ✔️           | ✔️              | ✔️   | ✔️             |
| OAEP-SHA-2 (SHA256, SHA384, SHA512) | ✔️           | ✔️              | ✔️   | ❌             |
| Signature PKCS1 (MD5, SHA-1)          | ✔️           | ✔️              | ✔️   | ✔️             |
| Signature PKCS1 (SHA-2)               | ✔️           | ✔️              | ✔️   | ⚠️\*           |
| PSS                                   | ✔️           | ✔️              | ✔️   | ❌             |

\*Windows CryptoAPI (CAPI) est en charge de la signature PKCS1 avec un algorithme SHA-2. Toutefois, l’objet RSA individuel peut être chargé dans un fournisseur de services de chiffrement (CSP) qui ne le prend pas en charge.

#### <a name="rsa-on-windows"></a>RSA sur Windows

* Windows CryptoAPI (CAPI) est utilisé chaque fois que [`new RSACryptoServiceProvider()`](xref:System.Security.Cryptography.RSACryptoServiceProvider) est utilisé.
* L’API de chiffrement nouvelle génération (CNG) Windows est utilisée chaque fois que [`new RSACng()`](xref:System.Security.Cryptography.RSACng) est utilisé.
* L’objet retourné par <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> est alimenté en interne par le CNG Windows. Cette utilisation de Windows CNG est un détail d’implémentation qui peut faire l’objet de modifications.
* La <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A> méthode d’extension pour <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> retourne une <xref:System.Security.Cryptography.RSACng> instance de. Cette utilisation de <xref:System.Security.Cryptography.RSACng> est un détail d’implémentation et peut faire l’objet de modifications.
* La <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A> méthode d’extension pour <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> utilise actuellement une <xref:System.Security.Cryptography.RSACng> instance, mais si <xref:System.Security.Cryptography.RSACng> ne peut pas ouvrir la clé, <xref:System.Security.Cryptography.RSACryptoServiceProvider> sera tentée. Le fournisseur préféré est un détail d’implémentation et peut faire l’objet de modifications.

#### <a name="rsa-native-interop"></a>Interop Native RSA

.NET expose des types pour permettre aux programmes d’interagir avec les bibliothèques du système d’exploitation que le code de chiffrement .NET utilise. Les types impliqués ne traduisent pas entre les plateformes et doivent être utilisés directement uniquement lorsque cela est nécessaire.

| Type                                                         | Windows | Linux         | macOS         |
|--------------------------------------------------------------|---------|---------------|---------------|
| <xref:System.Security.Cryptography.RSACryptoServiceProvider> | ✔️     | ⚠️<sup>1</sup>| ⚠️<sup>1</sup> |
| <xref:System.Security.Cryptography.RSACng>                   | ✔️     | ❌            | ❌            |
| <xref:System.Security.Cryptography.RSAOpenSsl>               | ❌     | ✔️            | ⚠️<sup>2</sup> |

<sup>1</sup> sur MacOS et Linux, <xref:System.Security.Cryptography.RSACryptoServiceProvider> peut être utilisé pour la compatibilité avec les programmes existants. Dans ce cas, toute méthode nécessitant l’interopérabilité du système d’exploitation, telle que l’ouverture d’une clé nommée, lève une <xref:System.PlatformNotSupportedException> .

<sup>2</sup> sur MacOS, <xref:System.Security.Cryptography.RSAOpenSsl> fonctionne si OpenSSL est installé et qu’un libénigmatiqueo dylib approprié peut être trouvé via le chargement de la bibliothèque dynamique. Si une bibliothèque appropriée est introuvable, les exceptions sont levées.

### <a name="ecdsa"></a>ECDSA

La génération de clés ECDSA (Elliptic Curve Digital Signature Algorithm) est effectuée par les bibliothèques du système d’exploitation et est soumise à leurs limitations de taille et caractéristiques de performances.

Les courbes de clé ECDSA sont définies par les bibliothèques du système d’exploitation et sont soumises à leurs limitations.

| Courbe elliptique                     | Windows 10    | Windows 7-8,1 | Linux         | macOS         |
|------------------------------------|---------------|-----------------|---------------|---------------|
| NIST P-256 (secp256r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-384 (secp384r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-521 (secp521r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| Courbes Brainpool (sous forme de courbes nommées) | ✔️           | ❌              | ⚠️<sup>1</sup>| ❌           |
| Autres courbes nommées                 | ⚠️<sup>2</sup>| ❌             | ⚠️<sup>1</sup>| ❌           |
| Courbes explicites                    | ✔️           | ❌              | ✔️           | ❌            |
| Exporter ou importer comme Explicit       | ✔️           | ❌<sup>1,3</sup>  | ✔️           | ❌<sup>1,3</sup>|

<sup>1</sup> les distributions Linux ne prennent pas toutes en charge les mêmes courbes nommées.

<sup>2</sup> la prise en charge des courbes nommées a été ajoutée au CNG Windows dans Windows 10. Pour plus d’informations, consultez [CNG named](https://msdn.microsoft.com/library/windows/desktop/mt632245(v=vs.85).aspx)Curves. Les courbes nommées ne sont pas disponibles dans les versions antérieures de Windows, à l’exception de trois courbes dans Windows 7.

<sup>3</sup> l’exportation avec des paramètres de courbe explicite requiert la prise en charge de la bibliothèque de système d’exploitation, qui n’est pas disponible sur MacOS ou les versions antérieures de Windows.

#### <a name="ecdsa-native-interop"></a>Interopérabilité native ECDSA

.NET expose des types pour permettre aux programmes d’interagir avec les bibliothèques du système d’exploitation que le code de chiffrement .NET utilise. Les types impliqués ne sont pas traduits entre les plateformes et doivent être utilisés directement uniquement lorsque cela est nécessaire.

| Type                                             | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| <xref:System.Security.Cryptography.ECDsaCng>     | ✔️     | ❌    | ❌    |
| <xref:System.Security.Cryptography.ECDsaOpenSsl> | ❌     | ✔️    | ⚠️\*  |

\*Sur macOS, <xref:System.Security.Cryptography.ECDsaOpenSsl> fonctionne si OpenSSL est installé dans le système et qu’un libénigmatiqueo dylib approprié peut être trouvé via le chargement de la bibliothèque dynamique. Si une bibliothèque appropriée est introuvable, les exceptions sont levées.

### <a name="ecdh"></a>ECDH

La génération de la clé ECDH (Elliptic Curve Diffie-Hellman) est effectuée par les bibliothèques du système d’exploitation et est soumise à leurs limitations de taille et caractéristiques de performances.

La <xref:System.Security.Cryptography.ECDiffieHellman> classe ne retourne pas la valeur « brute » du calcul ECDH. Toutes les données retournées sont en termes de fonctions de dérivation de clés :

* HASH (Z)
* HASH (précéder | | Z | | parenthèse
* HMAC (clé, Z)
* HMAC (clé, précéder | | Z | | parenthèse
* HMAC (Z, Z)
* HMAC (Z, précéder | | Z | | parenthèse
* Tls11Prf (étiquette, valeur initiale)

Les courbes de clé ECDH sont définies par les bibliothèques du système d’exploitation et sont soumises à leurs limitations.

| Courbe elliptique                     | Windows 10    | Windows 7-8,1 | Linux         | macOS         |
|------------------------------------|---------------|-----------------|---------------|---------------|
| NIST P-256 (secp256r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-384 (secp384r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| NIST P-521 (secp521r1)             | ✔️           | ✔️              | ✔️           | ✔️            |
| courbes Brainpool (sous forme de courbes nommées) | ✔️           | ❌              | ⚠️<sup>1</sup>| ❌           |
| autres courbes nommées                 | ⚠️<sup>2</sup>| ❌             | ⚠️<sup>1</sup>| ❌           |
| courbes explicites                    | ✔️           | ❌              | ✔️           | ❌            |
| Exporter ou importer comme Explicit       | ✔️           | ❌<sup>1,3</sup>  | ✔️           | ❌<sup>1,3</sup>|

<sup>1</sup> les distributions Linux ne prennent pas toutes en charge les mêmes courbes nommées.

<sup>2</sup> la prise en charge des courbes nommées a été ajoutée au CNG Windows dans Windows 10. Pour plus d’informations, consultez [CNG named](https://msdn.microsoft.com/library/windows/desktop/mt632245(v=vs.85).aspx)Curves. Les courbes nommées ne sont pas disponibles dans les versions antérieures de Windows, à l’exception de trois courbes dans Windows 7.

<sup>3</sup> l’exportation avec des paramètres de courbe explicite requiert la prise en charge de la bibliothèque de système d’exploitation, qui n’est pas disponible sur MacOS ou les versions antérieures de Windows.

#### <a name="ecdh-native-interop"></a>Interopérabilité native ECDH

.NET expose des types pour permettre aux programmes d’interagir avec les bibliothèques du système d’exploitation que .NET utilise. Les types impliqués ne sont pas traduits entre les plateformes et doivent être utilisés directement uniquement lorsque cela est nécessaire.

| Type                                                       | Windows | Linux | macOS |
|------------------------------------------------------------|---------|-------|-------|
| <xref:System.Security.Cryptography.ECDiffieHellmanCng>     | ✔️     | ❌    | ❌   |
| <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> | ❌     | ✔️    | ⚠️\* |

\*Sur macOS, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> fonctionne si OpenSSL est installé et qu’une libénigmatiqueo dylib appropriée peut être trouvée via le chargement de la bibliothèque dynamique. Si une bibliothèque appropriée est introuvable, les exceptions sont levées.

### <a name="dsa"></a>DSA

La génération de clés DSA (Digital Signature Algorithm) est effectuée par les bibliothèques système et est soumise à leurs limitations de taille et caractéristiques de performances.

| Fonction                      | CNG Windows | Linux | macOS         | CAPI Windows |
|-------------------------------|-------------|-------|---------------|--------------|
| Création de la clé (<= 1024 bits)   | ✔️         | ✔️    | ❌            | ✔️           |
| Création de la clé (> 1024 bits)    | ✔️         | ✔️    | ❌            | ❌            |
| Chargement des clés (<= 1024 bits)   | ✔️         | ✔️    | ✔️            | ✔️           |
| Chargement des clés (> 1024 bits)    | ✔️         | ✔️    | ⚠️\*          | ❌            |
| FIPS 186-2                    | ✔️         | ✔️    | ✔️            | ✔️           |
| FIPS 186-3 (signatures SHA-2) | ✔️         | ✔️    | ❌            | ❌            |

\*macOS charge des clés DSA supérieures à 1024 bits, mais le comportement de ces clés n’est pas défini. Ils ne se comportent pas d’après la norme FIPS 186-3.

#### <a name="dsa-on-windows"></a>DSA sur Windows

* Windows CryptoAPI (CAPI) est utilisé chaque fois que [`new DSACryptoServiceProvider()`](xref:System.Security.Cryptography.DSACryptoServiceProvider) est utilisé.
* L’API de chiffrement nouvelle génération (CNG) Windows est utilisée chaque fois que [`new DSACng()`](xref:System.Security.Cryptography.DSACng) est utilisé.
* L’objet retourné par <xref:System.Security.Cryptography.DSA.Create%2A?displayProperty=nameWithType> est alimenté en interne par le CNG Windows. Cette utilisation de Windows CNG est un détail d’implémentation qui peut faire l’objet de modifications.
* La <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A> méthode d’extension pour <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> retourne une <xref:System.Security.Cryptography.DSACng> instance de. Cette utilisation de <xref:System.Security.Cryptography.DSACng> est un détail d’implémentation et peut faire l’objet de modifications.
* La <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A> méthode d’extension pour <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> préfère une <xref:System.Security.Cryptography.DSACng> instance, mais si <xref:System.Security.Cryptography.DSACng> ne peut pas ouvrir la clé, <xref:System.Security.Cryptography.DSACryptoServiceProvider> sera tentée.  Le fournisseur préféré est un détail d’implémentation et peut faire l’objet de modifications.

#### <a name="dsa-native-interop"></a>Interopérabilité native DSA

.NET expose des types pour permettre aux programmes d’interagir avec les bibliothèques du système d’exploitation que le code de chiffrement .NET utilise. Les types impliqués ne sont pas traduits entre les plateformes et doivent être utilisés directement uniquement lorsque cela est nécessaire.

| Type                                                         | Windows | Linux         | macOS         |
|--------------------------------------------------------------|---------|---------------|---------------|
| <xref:System.Security.Cryptography.DSACryptoServiceProvider> | ✔️     | ⚠️<sup>1</sup> | ⚠️<sup>1</sup> |
| <xref:System.Security.Cryptography.DSACng>                   | ✔️     | ❌             | ❌            |
| <xref:System.Security.Cryptography.DSAOpenSsl>               | ❌      | ✔️            | ⚠️<sup>2</sup> |

<sup>1</sup> sur MacOS et Linux, <xref:System.Security.Cryptography.DSACryptoServiceProvider> peut être utilisé pour la compatibilité avec les programmes existants. Dans ce cas, toute méthode nécessitant l’interopérabilité du système, telle que l’ouverture d’une clé nommée, lève une exception <xref:System.PlatformNotSupportedException> .

<sup>2</sup> sur MacOS, <xref:System.Security.Cryptography.DSAOpenSsl> fonctionne si OpenSSL est installé et qu’un libénigmatiqueo dylib approprié peut être trouvé via le chargement de la bibliothèque dynamique. Si une bibliothèque appropriée est introuvable, les exceptions sont levées.

## <a name="x509-certificates"></a>Certificats X.509

La majeure partie de la prise en charge des certificats X. 509 dans .NET provient des bibliothèques du système d’exploitation. Pour charger un certificat dans une <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> <xref:System.Security.Cryptography.X509Certificates.X509Certificate> instance ou dans .net, le certificat doit être chargé par la bibliothèque du système d’exploitation sous-jacente.

### <a name="read-a-pkcs12pfx"></a>Lire un fichier PKCS12/PFX

| Scénario                                     | Windows | Linux | macOS |
|----------------------------------------------|---------|-------|-------|
| Vide                                        | ✔️     | ✔️    | ✔️   |
| Un certificat, aucune clé privée              | ✔️     | ✔️    | ✔️   |
| Un certificat avec une clé privée            | ✔️     | ✔️    | ✔️   |
| Certificats multiples, aucune clé privée       | ✔️     | ✔️    | ✔️   |
| Plusieurs certificats, une clé privée       | ✔️     | ✔️    | ✔️   |
| Plusieurs certificats, plusieurs clés privées | ✔️     | ⚠️\*  | ✔️   |

\*Disponible dans les versions préliminaires de .NET 5.

### <a name="write-a-pkcs12pfx"></a>Écrire un PKCS12/PFX

| Scénario                                     | Windows | Linux | macOS |
|----------------------------------------------|---------|-------|-------|
| Vide                                        | ✔️     | ✔️    | ⚠️\* |
| Un certificat, aucune clé privée              | ✔️     | ✔️    | ⚠️\* |
| Un certificat avec une clé privée            | ✔️     | ✔️    | ✔️   |
| Certificats multiples, aucune clé privée       | ✔️     | ✔️    | ⚠️\* |
| Plusieurs certificats, une clé privée       | ✔️     | ✔️    | ✔️   |
| Plusieurs certificats, plusieurs clés privées | ✔️     | ⚠️\*  | ✔️   |
| Chargement éphémère                            | ✔️     | ✔️    | ⚠️\* |

\*Disponible dans les versions préliminaires de .NET 5.

macOS ne peut pas charger les clés privées de certificat sans objet de trousseau, qui requiert l’écriture sur le disque. Les trousseau sont créés automatiquement pour le chargement PFX et sont supprimés lorsqu’ils ne sont plus utilisés. Étant donné que l' <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> option signifie que la clé privée ne doit pas être écrite sur le disque, l’assertion de cet indicateur sur MacOS produit un <xref:System.PlatformNotSupportedException> .

### <a name="write-a-pkcs7-certificate-collection"></a>Écrire une collection de certificats PKCS7

Windows et Linux émettent tous deux des objets BLOB PKCS7 codés DER. macOS émet des objets BLOB PKCS7 encodés en longueur illimitée-CER.

### <a name="x509store"></a>X509Store

Sur Windows, la <xref:System.Security.Cryptography.X509Certificates.X509Store> classe est une représentation des API du magasin de certificats Windows. Ces API fonctionnent de la même manière dans .NET Core et dans .NET 5, comme c’est le cas dans .NET Framework.

Sur Linux, la <xref:System.Security.Cryptography.X509Certificates.X509Store> classe est une projection de décisions d’approbation du système (lecture seule), de décisions d’approbation des utilisateurs (lecture-écriture) et de stockage de clés utilisateur (lecture-écriture).

Sur macOS, la <xref:System.Security.Cryptography.X509Certificates.X509Store> classe est une projection de décisions d’approbation du système (en lecture seule), de décisions d’approbation des utilisateurs (lecture seule) et de stockage de clés utilisateur (lecture-écriture).

Les tableaux suivants indiquent les scénarios pris en charge dans chaque plateforme. Pour les scénarios non pris en charge ( ❌ dans les tables), une <xref:System.Security.Cryptography.CryptographicException> exception est levée.

#### <a name="the-my-store"></a>Mon magasin

| Scénario                                         | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| Ouvrir CurrentUser\My (ReadOnly)                   | ✔️     | ✔️    | ✔️   |
| Ouvrir CurrentUser\My (ReadWrite)                  | ✔️     | ✔️    | ✔️   |
| Ouvrir CurrentUser\My (ExistingOnly)               | ✔️     | ⚠️    | ✔️   |
| Ouvrir LocalMachine\My                             | ✔️     | ❌    | ✔️   |

Sur Linux, les magasins sont créés lors de la première écriture, et aucun magasin d’utilisateur n’existe par défaut. l’ouverture `CurrentUser\My` de avec `ExistingOnly` peut échouer.

Sur macOS, le `CurrentUser\My` magasin est le trousseau par défaut de l’utilisateur, qui est `login.keychain` par défaut. Le `LocalMachine\My` magasin est `System.keychain` .

#### <a name="the-root-store"></a>Le magasin racine

| Scénario                              | Windows | Linux | macOS           |
|---------------------------------------|---------|-------|-----------------|
| Ouvrir CurrentUser\Root (ReadOnly)      | ✔️     | ✔️    | ✔️             |
| Ouvrir CurrentUser\Root (ReadWrite)     | ✔️     | ✔️    | ❌              |
| Ouvrir CurrentUser\Root (ExistingOnly)  | ✔️     | ⚠️    | ✔️ (en lecture seule) |
| Ouvrir Localmachine\root. (ReadOnly)     | ✔️     | ✔️    | ✔️             |
| Ouvrir Localmachine\root. (ReadWrite)    | ✔️     | ❌    | ❌              |
| Ouvrir Localmachine\root. (ExistingOnly) | ✔️     | ⚠️    | ✔️ (en lecture seule) |

Sur Linux, le `LocalMachine\Root` magasin est une interprétation de l’offre groupée de l’autorité de certification dans le chemin d’accès par défaut pour OpenSSL.

Sur macOS, le `CurrentUser\Root` magasin est une interprétation des `SecTrustSettings` résultats pour le domaine de confiance de l’utilisateur. Le `LocalMachine\Root` magasin est une interprétation des `SecTrustSettings` résultats pour les domaines de confiance de l’administrateur et du système.

#### <a name="the-intermediate-store"></a>Le magasin intermédiaire

| Scénario                                      | Windows | Linux | macOS           |
|-----------------------------------------------|---------|-------|-----------------|
| Ouvrir CurrentUser\Intermediate (ReadOnly)      | ✔️     | ✔️    | ✔️             |
| Ouvrir CurrentUser\Intermediate (ReadWrite)     | ✔️     | ✔️    | ❌              |
| Ouvrir CurrentUser\Intermediate (ExistingOnly)  | ✔️     | ⚠️    | ✔️ (en lecture seule) |
| Ouvrir LocalMachine\Intermediate (ReadOnly)     | ✔️     | ✔️    | ✔️             |
| Ouvrir LocalMachine\Intermediate (ReadWrite)    | ✔️     | ❌    | ❌              |
| Ouvrir LocalMachine\Intermediate (ExistingOnly) | ✔️     | ⚠️    | ✔️ (en lecture seule) |

Sur Linux, le `CurrentUser\Intermediate` magasin est utilisé en tant que cache lors du téléchargement d’autorités de certification intermédiaires par les enregistrements d’accès aux informations de l’autorité sur les builds X509Chain réussies. Le `LocalMachine\Intermediate` magasin est une interprétation de l’offre groupée de l’autorité de certification dans le chemin d’accès par défaut pour OpenSSL.

#### <a name="the-disallowed-store"></a>Le magasin non autorisé

| Scénario                                    | Windows | Linux | macOS           |
|---------------------------------------------|---------|-------|-----------------|
| Ouvrir CurrentUser\Disallowed (ReadOnly)      | ✔️     | ⚠️    | ✔️             |
| Ouvrir CurrentUser\Disallowed (ReadWrite)     | ✔️     | ⚠️    | ❌              |
| Ouvrir CurrentUser\Disallowed (ExistingOnly)  | ✔️     | ⚠️    | ✔️ (en lecture seule) |
| Ouvrir LocalMachine\Disallowed (ReadOnly)     | ✔️     | ❌    | ✔️             |
| Ouvrir LocalMachine\Disallowed (ReadWrite)    | ✔️     | ❌    | ❌              |
| Ouvrir LocalMachine\Disallowed (ExistingOnly) | ✔️     | ❌    | ✔️ (en lecture seule) |

Sur Linux, le `Disallowed` magasin n’est pas utilisé dans la création de chaînes, et toute tentative d’ajout de contenu à ce dernier produit un <xref:System.Security.Cryptography.CryptographicException> . Une <xref:System.Security.Cryptography.CryptographicException> exception est levée lors de l’ouverture du `Disallowed` magasin si elle a déjà acquis le contenu.

Sur macOS, les magasins CurrentUser\Disallowed et LocalMachine\Disallowed sont des interprétations des résultats SecTrustSettings appropriés pour les certificats dont l’approbation est définie sur `Always Deny` .

#### <a name="nonexistent-store"></a>Magasin inexistant

| Scénario                                         | Windows | Linux | macOS |
|--------------------------------------------------|---------|-------|-------|
| Ouvrir le magasin inexistant (ExistingOnly)           | ❌     | ❌     | ❌    |
| Ouvrir le magasin inexistant CurrentUser (ReadWrite)  | ✔️     | ✔️     | ⚠️   |
| Ouvrir le magasin inexistant LocalMachine (ReadWrite) | ✔️     | ❌     | ❌    |

Sur macOS, la création d’un magasin personnalisé avec l’API X509Store est prise en charge uniquement pour l' `CurrentUser` emplacement. Il créera un nouveau trousseau sans mot de passe dans le répertoire de trousseau de l’utilisateur (*~/Library/Keychains*). Pour créer un trousseau avec mot de passe, vous pouvez utiliser un appel P/Invoke `SecKeychainCreate` . De même, `SecKeychainOpen` peut être utilisé pour ouvrir des trousseau dans différents emplacements. Le résultant `IntPtr` peut être passé à [`new X509Store(IntPtr)`](xref:System.Security.Cryptography.X509Certificates.X509Store.%23ctor(System.IntPtr)) pour obtenir un magasin de lecture/écriture, sous réserve des autorisations de l’utilisateur actuel.

### <a name="x509chain"></a>X509Chain

macOS ne prend pas en charge l’utilisation de la liste de révocation de certificats hors connexion `X509RevocationMode.Offline` `X509RevocationMode.Online` .

macOS ne prend pas en charge le délai d’expiration initié par l’utilisateur sur le téléchargement de la liste de révocation de certificats/OCSP (Online Certificate Status Protocol)/AIA (accès aux informations de l’autorité) `X509ChainPolicy.UrlRetrievalTimeout` . il est donc ignoré.

## <a name="additional-resources"></a>Ressources supplémentaires

* [Modèle de chiffrement .NET](cryptography-model.md)
* [Services de chiffrement .NET](cryptographic-services.md)
* [Vulnérabilités de temporisation avec le déchiffrement symétrique en mode CBC à l’aide du remplissage](vulnerabilities-cbc-mode.md)
* [Protection des données ASP.NET Core](/aspnet/core/security/data-protection/introduction)
