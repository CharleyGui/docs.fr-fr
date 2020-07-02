---
ms.openlocfilehash: abef47c64a7cfd99c5b50bf2100401a2d5fcc5c3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614494"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a><span data-ttu-id="3d5a1-101">X509CertificateClaimSet.FindClaims prend en compte tous les claimTypes</span><span class="sxs-lookup"><span data-stu-id="3d5a1-101">X509CertificateClaimSet.FindClaims Considers All claimTypes</span></span>

#### <a name="details"></a><span data-ttu-id="3d5a1-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3d5a1-102">Details</span></span>

<span data-ttu-id="3d5a1-103">Dans les applications qui ciblent .NET Framework 4.6.1, si un ensemble de revendications X509 est initialisé à partir d’un certificat dont le champ SAN a plusieurs entrées DNS, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> tente de faire correspondre l’argument claimType avec toutes les entrées DNS. Pour les applications qui ciblent des versions antérieures du .NET Framework, la méthode <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> tente de faire correspondre l’argument claimType uniquement avec la dernière entrée DNS.</span><span class="sxs-lookup"><span data-stu-id="3d5a1-103">In apps that target the .NET Framework 4.6.1, if an X509 claim set is initialized from a certificate that has multiple DNS entries in its SAN field, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument with all the DNS entries.For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=fullName> method attempts to match the claimType argument only with the last DNS entry.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3d5a1-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3d5a1-104">Suggestion</span></span>

<span data-ttu-id="3d5a1-105">Cette modification affecte uniquement les applications qui ciblent le .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="3d5a1-105">This change only affects applications targeting the .NET Framework 4.6.1.</span></span> <span data-ttu-id="3d5a1-106">Elle peut être désactivée (ou activée si vous ciblez une version antérieure à 4.6.1) avec le commutateur de compatibilité [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation).</span><span class="sxs-lookup"><span data-stu-id="3d5a1-106">This change may be disabled (or enabled if targeting pre-4.6.1) with the [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation) compatibility switch.</span></span>

| <span data-ttu-id="3d5a1-107">Nom</span><span class="sxs-lookup"><span data-stu-id="3d5a1-107">Name</span></span>    | <span data-ttu-id="3d5a1-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="3d5a1-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3d5a1-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="3d5a1-109">Scope</span></span>   | <span data-ttu-id="3d5a1-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="3d5a1-110">Minor</span></span>       |
| <span data-ttu-id="3d5a1-111">Version</span><span class="sxs-lookup"><span data-stu-id="3d5a1-111">Version</span></span> | <span data-ttu-id="3d5a1-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="3d5a1-112">4.6.1</span></span>       |
| <span data-ttu-id="3d5a1-113">Type</span><span class="sxs-lookup"><span data-stu-id="3d5a1-113">Type</span></span>    | <span data-ttu-id="3d5a1-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="3d5a1-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3d5a1-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="3d5a1-115">Affected APIs</span></span>

- <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType>
