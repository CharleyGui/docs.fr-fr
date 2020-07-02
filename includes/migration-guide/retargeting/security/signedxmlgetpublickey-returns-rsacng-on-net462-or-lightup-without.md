---
ms.openlocfilehash: 23e278d38d6904d8afe927e6b54c388d443e41f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616053"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a><span data-ttu-id="fe5f1-101">SignedXml.GetPublicKey retourne RSACng sur net462 (ou lightup) sans changement de reciblage</span><span class="sxs-lookup"><span data-stu-id="fe5f1-101">SignedXml.GetPublicKey returns RSACng on net462 (or lightup) without retargeting change</span></span>

#### <a name="details"></a><span data-ttu-id="fe5f1-102">Détails</span><span class="sxs-lookup"><span data-stu-id="fe5f1-102">Details</span></span>

<span data-ttu-id="fe5f1-103">À compter de .NET Framework 4.6.2, le type concret de l’objet retourné par la méthode <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> est passé (sans coïncidence) d’une implémentation CryptoServiceProvider à une implémentation Cng.</span><span class="sxs-lookup"><span data-stu-id="fe5f1-103">Starting with the .NET Framework 4.6.2, the concrete type of the object returned by the <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> method changed (without a quirk) from a CryptoServiceProvider implementation to a Cng implementation.</span></span> <span data-ttu-id="fe5f1-104">La raison en est que l’implémentation est passée de l’utilisation de `certificate.PublicKey.Key` à l’utilisation du `certificate.GetAnyPublicKey` interne qu’elle transfère à <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe5f1-104">This is because the implementation changed from using `certificate.PublicKey.Key` to using the internal `certificate.GetAnyPublicKey` which forwards to <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fe5f1-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="fe5f1-105">Suggestion</span></span>

<span data-ttu-id="fe5f1-106">À partir des applications qui s’exécutent sur .NET Framework 4.7.1, vous pouvez utiliser l’implémentation CryptoServiceProvider utilisée par défaut dans .NET Framework 4.6.1 et les versions antérieures en ajoutant le commutateur de configuration suivant à la section [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :</span><span class="sxs-lookup"><span data-stu-id="fe5f1-106">Starting with apps running on the .NET Framework 4.7.1, you can use the CryptoServiceProvider implementation used by default in the .NET Framework 4.6.1 and earlier versions by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true" />
```

| <span data-ttu-id="fe5f1-107">Nom</span><span class="sxs-lookup"><span data-stu-id="fe5f1-107">Name</span></span>    | <span data-ttu-id="fe5f1-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="fe5f1-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fe5f1-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="fe5f1-109">Scope</span></span>   | <span data-ttu-id="fe5f1-110">Edge</span><span class="sxs-lookup"><span data-stu-id="fe5f1-110">Edge</span></span>        |
| <span data-ttu-id="fe5f1-111">Version</span><span class="sxs-lookup"><span data-stu-id="fe5f1-111">Version</span></span> | <span data-ttu-id="fe5f1-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="fe5f1-112">4.6.2</span></span>       |
| <span data-ttu-id="fe5f1-113">Type</span><span class="sxs-lookup"><span data-stu-id="fe5f1-113">Type</span></span>    | <span data-ttu-id="fe5f1-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="fe5f1-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fe5f1-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="fe5f1-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType>
