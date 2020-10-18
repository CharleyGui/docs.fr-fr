---
ms.openlocfilehash: 8198eca5b9c63d9717260b71ac6687dbf7245f35
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159550"
---
### <a name="instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported"></a>L’instanciation des implémentations par défaut des abstractions de chiffrement n’est pas prise en charge

Les `Create()` surcharges sans paramètre sur les abstractions de chiffrement sont obsolètes en tant qu’avertissement en tant que .net 5,0.

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework 2,0-4,8, les fabriques de primitives de chiffrement abstraites telles que <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> peuvent être configurées pour retourner des algorithmes différents. Par exemple, dans le cas d’une installation par défaut de .NET Framework 4,8, la méthode statique sans paramètre <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> retourne une instance de l’algorithme SHA1, comme illustré dans l’extrait de code suivant.

**.NET Framework uniquement**

```csharp
// Return an instance of the default hash algorithm (SHA1).
HashAlgorithm alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA1CryptoServiceProvider'.
Console.WriteLine(alg.GetType());

// Change the default algorithm to be SHA256, not SHA1.
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), typeof(HashAlgorithm).FullName);
alg = HashAlgorithm.Create();
// Prints 'System.Security.Cryptography.SHA256CryptoServiceProvider'.
Console.WriteLine(alg.GetType());
```

Vous pouvez également utiliser la configuration à l’intérieur de l' [ordinateur](../../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) pour modifier l’algorithme par défaut sans avoir à appeler par `CryptoConfig` programme.

Dans .NET Core 2,0-3,1, les fabriques de primitives de chiffrement abstraites telles que <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> lèvent toujours un <xref:System.PlatformNotSupportedException> .

```csharp
// Throws PlatformNotSupportedException on .NET Core.
HashAlgorithm alg = HashAlgorithm.Create();
```

Dans .NET 5,0 et versions ultérieures, les fabriques de primitives de chiffrement abstraites telles que <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> sont marquées comme obsolètes et produisent un avertissement au moment de la compilation avec l’ID `SYSLIB0007` . Au moment de l’exécution, ces méthodes continuent à lever une <xref:System.PlatformNotSupportedException> .

```csharp
// Throws PlatformNotSupportedException.
// Also produces compile-time warning SYSLIB0007 on .NET 5+.
HashAlgorithm alg = HashAlgorithm.Create();
```

Il s’agit d’une modification uniquement au moment de la compilation. Il n’existe aucun changement au moment de l’exécution par rapport aux versions précédentes de .NET Core.

> [!NOTE]
>
> - Seules les surcharges sans paramètre des `Create()` méthodes sont obsolètes. Les surcharges paramétrables ne sont pas obsolètes et continuent de fonctionner comme prévu.
>
>   ```csharp
>   // Call Create(string), providing an explicit algorithm family name.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   HashAlgorithm hashAlg = HashAlgorithm.Create("SHA256");
>   ```
>
> - Les surcharges sans paramètre de familles d’algorithmes *spécifiques* (pas d’abstractions) ne sont pas obsolètes et continuent de fonctionner comme prévu.
>
>   ```csharp
>   // Call a specific algorithm family's parameterless Create() ctor.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   Aes aesAlg = Aes.Create();
>   ```

#### <a name="reason-for-change"></a>Motif de modification

Le système de configuration de chiffrement présent dans .NET Framework n’est plus présent dans .NET Core et .NET 5.0 +, car ce système hérité n’autorise pas l’agilité de chiffrement appropriée. . Les exigences de compatibilité descendante de .net empêchent également l’infrastructure de mettre à jour certaines API de chiffrement pour suivre les avancées du chiffrement. Par exemple, la <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> méthode a été introduite dans .NET Framework 1,0, lorsque l’algorithme de hachage SHA-1 était de pointe. Vingt ans ont passé, et désormais SHA-1 est considéré comme cassé, mais nous ne pouvons pas modifier <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> pour retourner un algorithme différent. Cela introduirait une modification avec rupture inacceptable dans les applications consommatrices.

La meilleure pratique consiste à ce que les bibliothèques qui utilisent des primitives de chiffrement (par exemple, AES, SHA-* et RSA) aient un contrôle total sur la façon dont elles consomment ces Primitives. Les applications qui requièrent une vérification ultérieure doivent utiliser des bibliothèques de niveau supérieur qui encapsulent ces primitives et ajoutent des fonctionnalités de gestion de clés et d’agilité de chiffrement. Ces bibliothèques sont souvent fournies par l’environnement d’hébergement. ASP en est un exemple [. La bibliothèque de protection des données du réseau](/aspnet/core/security/data-protection/), qui gère ces problèmes pour le compte de l’application appelante.

#### <a name="version-introduced"></a>Version introduite

5,0 RC1

#### <a name="recommended-action"></a>Action recommandée

- La procédure recommandée consiste à remplacer les appels aux API désormais obsolètes par des appels aux méthodes de fabrique pour des algorithmes spécifiques, par exemple, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> . Cela vous donne un contrôle total sur les algorithmes qui sont instanciés.

- Si vous avez besoin de maintenir la compatibilité avec les charges utiles existantes générées par .NET Framework les applications qui utilisent les API désormais obsolètes, utilisez les remplacements suggérés dans le tableau suivant. La table fournit un mappage de .NET Framework les algorithmes par défaut à leurs équivalents .NET 5 +.

  | .NET Framework | .NET Core/.NET 5.0 + remplacement compatible | Notes  |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | L’algorithme SHA-1 est considéré comme cassé. Envisagez d’utiliser un algorithme plus fort si possible. Pour plus d’informations, consultez votre conseiller en sécurité. |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | L’algorithme HMACSHA1 est déconseillé pour la plupart des applications modernes. Envisagez d’utiliser un algorithme plus fort si possible. Pour plus d’informations, consultez votre conseiller en sécurité. |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | L’algorithme HMACSHA1 est déconseillé pour la plupart des applications modernes. Envisagez d’utiliser un algorithme plus fort si possible. Pour plus d’informations, consultez votre conseiller en sécurité. |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

- Si vous devez continuer à appeler les surcharges sans paramètre obsolètes `Create()` , vous pouvez supprimer l' `SYSLIB0007` avertissement dans le code.

  ```csharp
  #pragma warning disable SYSLIB0007 // Disable the warning.
  HashAlgorithm alg = HashAlgorithm.Create(); // Still throws PNSE.
  #pragma warning restore SYSLIB0007 // Re-enable the warning.
  ```

  Vous pouvez également supprimer l’avertissement dans votre fichier projet. Cela désactive l’avertissement pour tous les fichiers sources dans le projet.

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0007 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0007</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > La suppression `SYSLIB0007` désactive uniquement les avertissements obsoletion pour les API de chiffrement répertoriées ici. Il ne désactive pas les autres avertissements. En outre, même si vous supprimez l’avertissement, ces API obsolètes lèvent toujours une <xref:System.PlatformNotSupportedException> au moment de l’exécution.

#### <a name="category"></a>Category

- Chiffrement

#### <a name="affected-apis"></a>API affectées

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.HMAC.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.AsymmetricAlgorithm.Create`
- `M:System.Security.Cryptography.HashAlgorithm.Create`
- `M:System.Security.Cryptography.HMAC.Create`
- `M:System.Security.Cryptography.KeyedHashAlgorithm.Create`
- `M:System.Security.Cryptography.SymmetricAlgorithm.Create`

-->
