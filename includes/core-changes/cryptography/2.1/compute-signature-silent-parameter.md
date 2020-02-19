---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449214"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="5aab8-101">Le paramètre booléen de SignedCms. ComputeSignature est respecté</span><span class="sxs-lookup"><span data-stu-id="5aab8-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="5aab8-102">Dans .NET Core, le paramètre booléen `silent` de la méthode <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> est respecté.</span><span class="sxs-lookup"><span data-stu-id="5aab8-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="5aab8-103">Aucune invite de code confidentiel n’est affichée si ce paramètre est défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="5aab8-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5aab8-104">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="5aab8-104">Change description</span></span>

<span data-ttu-id="5aab8-105">Dans .NET Framework, le paramètre `silent` de la méthode <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> est ignoré, et une invite de code PIN est toujours affichée si le fournisseur l’exige.</span><span class="sxs-lookup"><span data-stu-id="5aab8-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="5aab8-106">Dans .NET Core, le paramètre `silent` est respecté et, s’il est défini sur `true`, une invite de code PIN n’est jamais affichée, même si elle est requise par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="5aab8-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="5aab8-107">La prise en charge des messages de #7 CMS/PKCS a été introduite dans .NET Core dans la version 2,1.</span><span class="sxs-lookup"><span data-stu-id="5aab8-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5aab8-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="5aab8-108">Version introduced</span></span>

<span data-ttu-id="5aab8-109">2.1</span><span class="sxs-lookup"><span data-stu-id="5aab8-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5aab8-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="5aab8-110">Recommended action</span></span>

<span data-ttu-id="5aab8-111">Pour vous assurer qu’une invite de code confidentiel s’affiche si nécessaire, les applications de bureau doivent appeler <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> et définir le paramètre booléen sur `false`.</span><span class="sxs-lookup"><span data-stu-id="5aab8-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="5aab8-112">Le comportement résultant est le même que sur .NET Framework que le contexte silencieux soit désactivé ou non.</span><span class="sxs-lookup"><span data-stu-id="5aab8-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

### <a name="category"></a><span data-ttu-id="5aab8-113">Category</span><span class="sxs-lookup"><span data-stu-id="5aab8-113">Category</span></span>

<span data-ttu-id="5aab8-114">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="5aab8-114">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="5aab8-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="5aab8-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
