---
ms.openlocfilehash: e2ae329d027d605e6331afe422e550990fab1042
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614539"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a><span data-ttu-id="fb653-101">Valeur par défaut des algorithmes SignedXML et SignedXMS remplacée par SHA256</span><span class="sxs-lookup"><span data-stu-id="fb653-101">Default SignedXML and SignedXMS algorithms changed to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="fb653-102">Détails</span><span class="sxs-lookup"><span data-stu-id="fb653-102">Details</span></span>

<span data-ttu-id="fb653-103">Dans .NET Framework 4.7 et les versions antérieures, SignedXML et SignedCMS utilisent par défaut SHA1 pour certaines opérations. À compter de .NET Framework 4.7.1, SHA256 est activé par défaut pour ces opérations.</span><span class="sxs-lookup"><span data-stu-id="fb653-103">In the .NET Framework 4.7 and earlier, SignedXML and SignedCMS default to SHA1 for some operations.Starting with the .NET Framework 4.7.1, SHA256 is enabled by default for these operations.</span></span> <span data-ttu-id="fb653-104">Ce changement est nécessaire car SHA1 n’est plus considérée comme sécurisé.</span><span class="sxs-lookup"><span data-stu-id="fb653-104">This change is necessary because SHA1 is no longer considered to be secure.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fb653-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="fb653-105">Suggestion</span></span>

<span data-ttu-id="fb653-106">Deux nouvelles valeurs de commutateur de contexte permettent de contrôler si SHA1 (non sécurisé) ou SHA256 est utilisé par défaut :</span><span class="sxs-lookup"><span data-stu-id="fb653-106">There are two new context switch values to control whether SHA1 (insecure) or SHA256 is used by default:</span></span>

- <span data-ttu-id="fb653-107">Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</span><span class="sxs-lookup"><span data-stu-id="fb653-107">Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</span></span>
- <span data-ttu-id="fb653-108">Switch.SysTEM. Security. Cryptography. Pkcs. UseInsecureHashAlgorithms pour les applications qui ciblent le .NET Framework 4.7.1 et versions ultérieures. si l’utilisation de SHA256 n’est pas souhaitable, vous pouvez restaurer la valeur par défaut SHA1 en ajoutant le commutateur de configuration suivant à la section [Runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="fb653-108">Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms For applications that target the .NET Framework 4.7.1 and later versions, if the use of SHA256 is undesirable, you can restore the default to SHA1 by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true" />
```

<span data-ttu-id="fb653-109">Pour les applications que ciblent .NET Framework 4.7 et les versions antérieures, vous pouvez accepter ce changement en ajoutant le commutateur de configuration suivant à la section [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="fb653-109">For applications that target the .NET Framework 4.7 and earlier versions, you can opt into this change by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false" />
```

| <span data-ttu-id="fb653-110">Nom</span><span class="sxs-lookup"><span data-stu-id="fb653-110">Name</span></span>    | <span data-ttu-id="fb653-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="fb653-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fb653-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="fb653-112">Scope</span></span>   | <span data-ttu-id="fb653-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="fb653-113">Minor</span></span>       |
| <span data-ttu-id="fb653-114">Version</span><span class="sxs-lookup"><span data-stu-id="fb653-114">Version</span></span> | <span data-ttu-id="fb653-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="fb653-115">4.7.1</span></span>       |
| <span data-ttu-id="fb653-116">Type</span><span class="sxs-lookup"><span data-stu-id="fb653-116">Type</span></span>    | <span data-ttu-id="fb653-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="fb653-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fb653-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="fb653-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType>
