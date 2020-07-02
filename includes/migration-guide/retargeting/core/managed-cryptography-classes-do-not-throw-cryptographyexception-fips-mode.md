---
ms.openlocfilehash: 0b62eff8d70873293aafa539f40bf032672df57a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616245"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a><span data-ttu-id="ad1f7-101">Les classes de chiffrement managées ne lèvent pas d’exception de chiffrement en mode FIPS</span><span class="sxs-lookup"><span data-stu-id="ad1f7-101">Managed cryptography classes do not throw a CryptographyException in FIPS mode</span></span>

#### <a name="details"></a><span data-ttu-id="ad1f7-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ad1f7-102">Details</span></span>

<span data-ttu-id="ad1f7-103">Dans .NET Framework 4.7.2 et versions antérieures, les classes de fournisseur de chiffrement managées comme <xref:System.Security.Cryptography.SHA256Managed> lèvent une <xref:System.Security.Cryptography.CryptographicException> quand les bibliothèques de chiffrement système sont configurées en mode FIPS.</span><span class="sxs-lookup"><span data-stu-id="ad1f7-103">In .NET Framework 4.7.2 and earlier versions, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in FIPS mode.</span></span> <span data-ttu-id="ad1f7-104">Ces exceptions sont levées parce que les versions managées ne sont pas sous la certification 140-2 FIPS (Federal Information Processing Standards), et dans le but de bloquer les algorithmes de chiffrement qui n’étaient pas considérés comme approuvés selon les règles FIPS.</span><span class="sxs-lookup"><span data-stu-id="ad1f7-104">These exceptions are thrown because the managed versions have not undergone FIPS (Federal Information Processing Standards) 140-2 certification, as well as to block cryptographic algorithms that were not considered to be approved based on the FIPS rules.</span></span>  <span data-ttu-id="ad1f7-105">Étant donné que peu de développeurs ont leurs ordinateurs de développement en mode FIPS, ces exceptions sont fréquemment levées sur les systèmes de production uniquement. Les applications qui ciblent .NET Framework 4.8 et versions ultérieures basculent automatiquement vers la stratégie plus récente et plus souple afin qu’une <xref:System.Security.Cryptography.CryptographicException> ne soit plus levée par défaut dans ces cas précis.</span><span class="sxs-lookup"><span data-stu-id="ad1f7-105">Because few developers have their development machines in FIPS mode, these exceptions are frequently thrown only on production systems.Applications that target .NET Framework 4.8 and later versions automatically switch to the newer, relaxed policy, so that a <xref:System.Security.Cryptography.CryptographicException> is no longer thrown by default in such cases.</span></span> <span data-ttu-id="ad1f7-106">Les classes de chiffrement managées redirigent plutôt les opérations de chiffrement vers une bibliothèque de chiffrement système.</span><span class="sxs-lookup"><span data-stu-id="ad1f7-106">Instead, the managed cryptography classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="ad1f7-107">Ce changement de stratégie supprime efficacement une différence pouvant potentiellement prêter à confusion entre les environnements de développement et les environnements de production, et permet d’exécuter les composants natifs et les composants managés sous la même stratégie de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="ad1f7-107">This policy change effectively removes a potentially confusing difference between developer environments and the production environments and makes native components and managed components operate under the same cryptographic policy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ad1f7-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ad1f7-108">Suggestion</span></span>

<span data-ttu-id="ad1f7-109">Si ce comportement est indésirable, vous pouvez choisir de ne plus y adhérer et restaurer le comportement précédent pour qu’une <xref:System.Security.Cryptography.CryptographicException> soit levée en mode FIPS en ajoutant le paramètre de configuration [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant dans la section [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="ad1f7-109">If this behavior is undesirable, you can opt out of it and restore the previous behavior so that a <xref:System.Security.Cryptography.CryptographicException> is thrown in FIPS mode by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=true" />
</runtime>
```

<span data-ttu-id="ad1f7-110">Si votre application cible .NET Framework 4.7.2 ou antérieur, vous pouvez aussi choisir d’adhérer à ce changement en ajoutant le paramètre de configuration [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant dans la section [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="ad1f7-110">If your application targets .NET Framework 4.7.2 or earlier, you can also opt in to this change by adding the following [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=false" />
</runtime>
```

| <span data-ttu-id="ad1f7-111">Nom</span><span class="sxs-lookup"><span data-stu-id="ad1f7-111">Name</span></span>    | <span data-ttu-id="ad1f7-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="ad1f7-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ad1f7-113">Étendue</span><span class="sxs-lookup"><span data-stu-id="ad1f7-113">Scope</span></span>   | <span data-ttu-id="ad1f7-114">Edge</span><span class="sxs-lookup"><span data-stu-id="ad1f7-114">Edge</span></span>        |
| <span data-ttu-id="ad1f7-115">Version</span><span class="sxs-lookup"><span data-stu-id="ad1f7-115">Version</span></span> | <span data-ttu-id="ad1f7-116">4.8</span><span class="sxs-lookup"><span data-stu-id="ad1f7-116">4.8</span></span>         |
| <span data-ttu-id="ad1f7-117">Type</span><span class="sxs-lookup"><span data-stu-id="ad1f7-117">Type</span></span>    | <span data-ttu-id="ad1f7-118">Reciblage</span><span class="sxs-lookup"><span data-stu-id="ad1f7-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ad1f7-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="ad1f7-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType>
