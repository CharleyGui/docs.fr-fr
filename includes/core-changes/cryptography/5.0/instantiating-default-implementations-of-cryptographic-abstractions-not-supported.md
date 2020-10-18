---
ms.openlocfilehash: 8198eca5b9c63d9717260b71ac6687dbf7245f35
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159550"
---
### <a name="instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported"></a><span data-ttu-id="6b206-101">L’instanciation des implémentations par défaut des abstractions de chiffrement n’est pas prise en charge</span><span class="sxs-lookup"><span data-stu-id="6b206-101">Instantiating default implementations of cryptographic abstractions is not supported</span></span>

<span data-ttu-id="6b206-102">Les `Create()` surcharges sans paramètre sur les abstractions de chiffrement sont obsolètes en tant qu’avertissement en tant que .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="6b206-102">The parameterless `Create()` overloads on cryptographic abstractions are obsolete as warning as of .NET 5.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6b206-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="6b206-103">Change description</span></span>

<span data-ttu-id="6b206-104">Dans .NET Framework 2,0-4,8, les fabriques de primitives de chiffrement abstraites telles que <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> peuvent être configurées pour retourner des algorithmes différents.</span><span class="sxs-lookup"><span data-stu-id="6b206-104">In .NET Framework 2.0 - 4.8, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> can be configured to return different algorithms.</span></span> <span data-ttu-id="6b206-105">Par exemple, dans le cas d’une installation par défaut de .NET Framework 4,8, la méthode statique sans paramètre <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> retourne une instance de l’algorithme SHA1, comme illustré dans l’extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="6b206-105">For example, on a default install of .NET Framework 4.8, the parameterless, static method <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> returns an instance of the SHA1 algorithm, as shown in the following snippet.</span></span>

<span data-ttu-id="6b206-106">**.NET Framework uniquement**</span><span class="sxs-lookup"><span data-stu-id="6b206-106">**.NET Framework only**</span></span>

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

<span data-ttu-id="6b206-107">Vous pouvez également utiliser la configuration à l’intérieur de l' [ordinateur](../../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) pour modifier l’algorithme par défaut sans avoir à appeler par `CryptoConfig` programme.</span><span class="sxs-lookup"><span data-stu-id="6b206-107">You can also use [machine-wide configuration](../../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md) to change the default algorithm without needing to call into `CryptoConfig` programmatically.</span></span>

<span data-ttu-id="6b206-108">Dans .NET Core 2,0-3,1, les fabriques de primitives de chiffrement abstraites telles que <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> lèvent toujours un <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="6b206-108">In .NET Core 2.0 - 3.1, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> always throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException on .NET Core.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="6b206-109">Dans .NET 5,0 et versions ultérieures, les fabriques de primitives de chiffrement abstraites telles que <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> sont marquées comme obsolètes et produisent un avertissement au moment de la compilation avec l’ID `SYSLIB0007` .</span><span class="sxs-lookup"><span data-stu-id="6b206-109">In .NET 5.0 and later versions, abstract cryptographic primitive factories such as <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> are marked obsolete and produce a compile-time warning with ID `SYSLIB0007`.</span></span> <span data-ttu-id="6b206-110">Au moment de l’exécution, ces méthodes continuent à lever une <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="6b206-110">At run time, these methods continue to throw a <xref:System.PlatformNotSupportedException>.</span></span>

```csharp
// Throws PlatformNotSupportedException.
// Also produces compile-time warning SYSLIB0007 on .NET 5+.
HashAlgorithm alg = HashAlgorithm.Create();
```

<span data-ttu-id="6b206-111">Il s’agit d’une modification uniquement au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="6b206-111">This is a compile-time only change.</span></span> <span data-ttu-id="6b206-112">Il n’existe aucun changement au moment de l’exécution par rapport aux versions précédentes de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b206-112">There is no run-time change from previous versions of .NET Core.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="6b206-113">Seules les surcharges sans paramètre des `Create()` méthodes sont obsolètes.</span><span class="sxs-lookup"><span data-stu-id="6b206-113">Only the parameterless overloads of the `Create()` methods are obsolete.</span></span> <span data-ttu-id="6b206-114">Les surcharges paramétrables ne sont pas obsolètes et continuent de fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="6b206-114">Parameterized overloads are not obsolete and still function as expected.</span></span>
>
>   ```csharp
>   // Call Create(string), providing an explicit algorithm family name.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   HashAlgorithm hashAlg = HashAlgorithm.Create("SHA256");
>   ```
>
> - <span data-ttu-id="6b206-115">Les surcharges sans paramètre de familles d’algorithmes *spécifiques* (pas d’abstractions) ne sont pas obsolètes et continuent de fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="6b206-115">Parameterless overloads of *specific* algorithm families (not abstractions) are not obsolete, and will continue to function as expected.</span></span>
>
>   ```csharp
>   // Call a specific algorithm family's parameterless Create() ctor.
>   // Works in .NET Framework, .NET Core, and .NET 5.0+.
>   Aes aesAlg = Aes.Create();
>   ```

#### <a name="reason-for-change"></a><span data-ttu-id="6b206-116">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="6b206-116">Reason for change</span></span>

<span data-ttu-id="6b206-117">Le système de configuration de chiffrement présent dans .NET Framework n’est plus présent dans .NET Core et .NET 5.0 +, car ce système hérité n’autorise pas l’agilité de chiffrement appropriée.</span><span class="sxs-lookup"><span data-stu-id="6b206-117">The cryptographic configuration system present in .NET Framework is no longer present in .NET Core and .NET 5.0+, since that legacy system doesn't allow for proper cryptographic agility.</span></span> <span data-ttu-id="6b206-118">. Les exigences de compatibilité descendante de .net empêchent également l’infrastructure de mettre à jour certaines API de chiffrement pour suivre les avancées du chiffrement.</span><span class="sxs-lookup"><span data-stu-id="6b206-118">.NET's backward-compatibility requirements also prohibit the framework from updating certain cryptographic APIs to keep up with advances in cryptography.</span></span> <span data-ttu-id="6b206-119">Par exemple, la <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> méthode a été introduite dans .NET Framework 1,0, lorsque l’algorithme de hachage SHA-1 était de pointe.</span><span class="sxs-lookup"><span data-stu-id="6b206-119">For example, the <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> method was introduced in .NET Framework 1.0, when the SHA-1 hash algorithm was state-of-the-art.</span></span> <span data-ttu-id="6b206-120">Vingt ans ont passé, et désormais SHA-1 est considéré comme cassé, mais nous ne pouvons pas modifier <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> pour retourner un algorithme différent.</span><span class="sxs-lookup"><span data-stu-id="6b206-120">Twenty years have passed, and now SHA-1 is considered broken, but we cannot change <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> to return a different algorithm.</span></span> <span data-ttu-id="6b206-121">Cela introduirait une modification avec rupture inacceptable dans les applications consommatrices.</span><span class="sxs-lookup"><span data-stu-id="6b206-121">Doing so would introduce an unacceptable breaking change in consuming applications.</span></span>

<span data-ttu-id="6b206-122">La meilleure pratique consiste à ce que les bibliothèques qui utilisent des primitives de chiffrement (par exemple, AES, SHA-\* et RSA) aient un contrôle total sur la façon dont elles consomment ces Primitives.</span><span class="sxs-lookup"><span data-stu-id="6b206-122">Best practice dictates that libraries that consume cryptographic primitives (such as AES, SHA-\*, and RSA) should be in full control over how they consume these primitives.</span></span> <span data-ttu-id="6b206-123">Les applications qui requièrent une vérification ultérieure doivent utiliser des bibliothèques de niveau supérieur qui encapsulent ces primitives et ajoutent des fonctionnalités de gestion de clés et d’agilité de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="6b206-123">Applications that require future-proofing should utilize higher-level libraries that wrap these primitives and add key management and cryptographic agility capabilities.</span></span> <span data-ttu-id="6b206-124">Ces bibliothèques sont souvent fournies par l’environnement d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="6b206-124">These libraries are often provided by the hosting environment.</span></span> <span data-ttu-id="6b206-125">ASP en est un exemple [. La bibliothèque de protection des données du réseau](/aspnet/core/security/data-protection/), qui gère ces problèmes pour le compte de l’application appelante.</span><span class="sxs-lookup"><span data-stu-id="6b206-125">One example is [ASP.NET's Data Protection library](/aspnet/core/security/data-protection/), which handles these concerns on behalf of the calling application.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6b206-126">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6b206-126">Version introduced</span></span>

<span data-ttu-id="6b206-127">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="6b206-127">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6b206-128">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6b206-128">Recommended action</span></span>

- <span data-ttu-id="6b206-129">La procédure recommandée consiste à remplacer les appels aux API désormais obsolètes par des appels aux méthodes de fabrique pour des algorithmes spécifiques, par exemple, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6b206-129">The recommended course of action is to replace calls to the now-obsolete APIs with calls to factory methods for specific algorithms, for example, <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6b206-130">Cela vous donne un contrôle total sur les algorithmes qui sont instanciés.</span><span class="sxs-lookup"><span data-stu-id="6b206-130">This gives you full control over which algorithms are instantiated.</span></span>

- <span data-ttu-id="6b206-131">Si vous avez besoin de maintenir la compatibilité avec les charges utiles existantes générées par .NET Framework les applications qui utilisent les API désormais obsolètes, utilisez les remplacements suggérés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="6b206-131">If you need to maintain compatibility with existing payloads generated by .NET Framework apps that use the now-obsolete APIs, use the replacements suggested in the following table.</span></span> <span data-ttu-id="6b206-132">La table fournit un mappage de .NET Framework les algorithmes par défaut à leurs équivalents .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="6b206-132">The table provides a mapping from .NET Framework default algorithms to their .NET 5+ equivalents.</span></span>

  | <span data-ttu-id="6b206-133">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="6b206-133">.NET Framework</span></span> | <span data-ttu-id="6b206-134">.NET Core/.NET 5.0 + remplacement compatible</span><span class="sxs-lookup"><span data-stu-id="6b206-134">.NET Core / .NET 5.0+ compatible replacement</span></span> | <span data-ttu-id="6b206-135">Notes </span><span class="sxs-lookup"><span data-stu-id="6b206-135">Remarks</span></span> |
  | - | - | - |
  | <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.RSA.Create?displayProperty=nameWithType> | |
  | <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.SHA1.Create?displayProperty=nameWithType> | <span data-ttu-id="6b206-136">L’algorithme SHA-1 est considéré comme cassé.</span><span class="sxs-lookup"><span data-stu-id="6b206-136">The SHA-1 algorithm is considered broken.</span></span> <span data-ttu-id="6b206-137">Envisagez d’utiliser un algorithme plus fort si possible.</span><span class="sxs-lookup"><span data-stu-id="6b206-137">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="6b206-138">Pour plus d’informations, consultez votre conseiller en sécurité.</span><span class="sxs-lookup"><span data-stu-id="6b206-138">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="6b206-139">L’algorithme HMACSHA1 est déconseillé pour la plupart des applications modernes.</span><span class="sxs-lookup"><span data-stu-id="6b206-139">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="6b206-140">Envisagez d’utiliser un algorithme plus fort si possible.</span><span class="sxs-lookup"><span data-stu-id="6b206-140">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="6b206-141">Pour plus d’informations, consultez votre conseiller en sécurité.</span><span class="sxs-lookup"><span data-stu-id="6b206-141">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.HMACSHA1.%23ctor> | <span data-ttu-id="6b206-142">L’algorithme HMACSHA1 est déconseillé pour la plupart des applications modernes.</span><span class="sxs-lookup"><span data-stu-id="6b206-142">The HMACSHA1 algorithm is discouraged for most modern applications.</span></span> <span data-ttu-id="6b206-143">Envisagez d’utiliser un algorithme plus fort si possible.</span><span class="sxs-lookup"><span data-stu-id="6b206-143">Consider using a stronger algorithm if possible.</span></span> <span data-ttu-id="6b206-144">Pour plus d’informations, consultez votre conseiller en sécurité.</span><span class="sxs-lookup"><span data-stu-id="6b206-144">Consult your security advisor for further guidance.</span></span> |
  | <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <xref:System.Security.Cryptography.Aes.Create?displayProperty=nameWithType> |

- <span data-ttu-id="6b206-145">Si vous devez continuer à appeler les surcharges sans paramètre obsolètes `Create()` , vous pouvez supprimer l' `SYSLIB0007` avertissement dans le code.</span><span class="sxs-lookup"><span data-stu-id="6b206-145">If you must continue to call the obsolete parameterless `Create()` overloads, you can suppress the `SYSLIB0007` warning in code.</span></span>

  ```csharp
  #pragma warning disable SYSLIB0007 // Disable the warning.
  HashAlgorithm alg = HashAlgorithm.Create(); // Still throws PNSE.
  #pragma warning restore SYSLIB0007 // Re-enable the warning.
  ```

  <span data-ttu-id="6b206-146">Vous pouvez également supprimer l’avertissement dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6b206-146">You can also suppress the warning in your project file.</span></span> <span data-ttu-id="6b206-147">Cela désactive l’avertissement pour tous les fichiers sources dans le projet.</span><span class="sxs-lookup"><span data-stu-id="6b206-147">Doing so disables the warning for all source files within the project.</span></span>

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
  > <span data-ttu-id="6b206-148">La suppression `SYSLIB0007` désactive uniquement les avertissements obsoletion pour les API de chiffrement répertoriées ici.</span><span class="sxs-lookup"><span data-stu-id="6b206-148">Suppressing `SYSLIB0007` disables only the obsoletion warnings for the cryptography APIs listed here.</span></span> <span data-ttu-id="6b206-149">Il ne désactive pas les autres avertissements.</span><span class="sxs-lookup"><span data-stu-id="6b206-149">It does not disable any other warnings.</span></span> <span data-ttu-id="6b206-150">En outre, même si vous supprimez l’avertissement, ces API obsolètes lèvent toujours une <xref:System.PlatformNotSupportedException> au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="6b206-150">Additionally, even if you suppress the warning, these obsoleted APIs will still throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

#### <a name="category"></a><span data-ttu-id="6b206-151">Category</span><span class="sxs-lookup"><span data-stu-id="6b206-151">Category</span></span>

- <span data-ttu-id="6b206-152">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="6b206-152">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6b206-153">API affectées</span><span class="sxs-lookup"><span data-stu-id="6b206-153">Affected APIs</span></span>

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
