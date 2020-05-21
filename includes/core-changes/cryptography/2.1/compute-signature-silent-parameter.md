---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721708"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="ecd69-101">Le paramètre booléen de SignedCms. ComputeSignature est respecté</span><span class="sxs-lookup"><span data-stu-id="ecd69-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="ecd69-102">Dans .NET Core, le `silent` paramètre booléen de la <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> méthode est respecté.</span><span class="sxs-lookup"><span data-stu-id="ecd69-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="ecd69-103">Aucune invite de code confidentiel n’est affichée si ce paramètre a la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="ecd69-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ecd69-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="ecd69-104">Change description</span></span>

<span data-ttu-id="ecd69-105">Dans .NET Framework, le `silent` paramètre de la <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> méthode est ignoré et une invite de code confidentiel est toujours affichée si le fournisseur l’exige.</span><span class="sxs-lookup"><span data-stu-id="ecd69-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="ecd69-106">Dans .NET Core, le `silent` paramètre est respecté et, s’il a la valeur `true` , une invite de code pin n’est jamais affichée, même si elle est requise par le fournisseur.</span><span class="sxs-lookup"><span data-stu-id="ecd69-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="ecd69-107">La prise en charge des messages de #7 CMS/PKCS a été introduite dans .NET Core dans la version 2,1.</span><span class="sxs-lookup"><span data-stu-id="ecd69-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ecd69-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ecd69-108">Version introduced</span></span>

<span data-ttu-id="ecd69-109">2.1</span><span class="sxs-lookup"><span data-stu-id="ecd69-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ecd69-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ecd69-110">Recommended action</span></span>

<span data-ttu-id="ecd69-111">Pour vous assurer qu’une invite de code confidentiel s’affiche si nécessaire, les applications de bureau doivent appeler <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> et définir le paramètre booléen sur `false` .</span><span class="sxs-lookup"><span data-stu-id="ecd69-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="ecd69-112">Le comportement résultant est le même que sur .NET Framework que le contexte silencieux soit désactivé ou non.</span><span class="sxs-lookup"><span data-stu-id="ecd69-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

#### <a name="category"></a><span data-ttu-id="ecd69-113">Category</span><span class="sxs-lookup"><span data-stu-id="ecd69-113">Category</span></span>

<span data-ttu-id="ecd69-114">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="ecd69-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ecd69-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="ecd69-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
