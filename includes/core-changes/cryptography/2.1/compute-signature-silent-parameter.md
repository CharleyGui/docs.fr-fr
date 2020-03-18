---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449214"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="7de70-101">Boolean paramètre de SignedCms.ComputeSignature est respecté</span><span class="sxs-lookup"><span data-stu-id="7de70-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="7de70-102">Dans .NET Core, `silent` le paramètre Boolean de la <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> méthode est respecté.</span><span class="sxs-lookup"><span data-stu-id="7de70-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="7de70-103">Une invite NIP n’est pas `true`indiquée si ce paramètre est défini pour .</span><span class="sxs-lookup"><span data-stu-id="7de70-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7de70-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="7de70-104">Change description</span></span>

<span data-ttu-id="7de70-105">Dans .NET Framework, `silent` le <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> paramètre de la méthode est ignoré, et une invite NIP est toujours affichée si nécessaire par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="7de70-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="7de70-106">Dans .NET Core, le `silent` paramètre est `true`respecté, et si défini à , une invite NIP n’est jamais montré, même si elle est requise par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="7de70-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="7de70-107">La prise en charge des messages #7 CMS/PKCS a été introduite dans .NET Core dans la version 2.1.</span><span class="sxs-lookup"><span data-stu-id="7de70-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7de70-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7de70-108">Version introduced</span></span>

<span data-ttu-id="7de70-109">2.1</span><span class="sxs-lookup"><span data-stu-id="7de70-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7de70-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7de70-110">Recommended action</span></span>

<span data-ttu-id="7de70-111">Pour s’assurer qu’une invite NIP apparaît si nécessaire, les applications de bureau doivent appeler <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> et définir le paramètre Boolean à `false`.</span><span class="sxs-lookup"><span data-stu-id="7de70-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="7de70-112">Le comportement qui en résulte est le même que sur .NET Framework indépendamment du fait que le contexte silencieux y est désactivé.</span><span class="sxs-lookup"><span data-stu-id="7de70-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

### <a name="category"></a><span data-ttu-id="7de70-113">Category</span><span class="sxs-lookup"><span data-stu-id="7de70-113">Category</span></span>

<span data-ttu-id="7de70-114">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="7de70-114">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="7de70-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="7de70-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
