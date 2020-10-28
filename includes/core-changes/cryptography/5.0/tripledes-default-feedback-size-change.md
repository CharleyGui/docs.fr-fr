---
ms.openlocfilehash: 2599e1f65720c25695f1fb5cfa39cabb842efc1d
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888610"
---
### <a name="default-feedbacksize-value-for-instances-created-by-tripledescreate-changed"></a><span data-ttu-id="d35a7-101">Valeur FeedbackSize par défaut pour les instances créées par TripleDES. Create Changed</span><span class="sxs-lookup"><span data-stu-id="d35a7-101">Default FeedbackSize value for instances created by TripleDES.Create changed</span></span>

<span data-ttu-id="d35a7-102">La valeur par défaut de la <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType> propriété sur l' <xref:System.Security.Cryptography.TripleDES> instance retournée de <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> est passée de 64 à 8 pour faciliter la migration à partir de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d35a7-102">The default value for the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType> property on the <xref:System.Security.Cryptography.TripleDES> instance returned from <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> has changed from 64 to 8 to make migration from .NET Framework easier.</span></span> <span data-ttu-id="d35a7-103">Cette propriété, sauf si elle est utilisée directement dans le code de l’appelant, est utilisée uniquement lorsque la <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> propriété est <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d35a7-103">This property, unless used directly in caller code, is used only when the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> property is <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d35a7-104">La prise en charge du <xref:System.Security.Cryptography.CipherMode.CFB> mode a été ajoutée à .net pour la version 5,0 RC1. par conséquent, seules les applications .net 5,0 RC1 et .net 5,0 RC2 doivent être affectées par cette modification.</span><span class="sxs-lookup"><span data-stu-id="d35a7-104">Support for the <xref:System.Security.Cryptography.CipherMode.CFB> mode was first added to .NET for the 5.0 RC1 release, so only .NET 5.0 RC1 and .NET 5.0 RC2 applications should be impacted by this change.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d35a7-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="d35a7-105">Change description</span></span>

<span data-ttu-id="d35a7-106">Dans .NET Core et les versions antérieures à la version préliminaire de .NET 5,0, `TripleDES.Create().FeedbackSize` a une valeur par défaut de 64.</span><span class="sxs-lookup"><span data-stu-id="d35a7-106">In .NET Core and previous pre-release versions of .NET 5.0, `TripleDES.Create().FeedbackSize` has a default value of 64.</span></span> <span data-ttu-id="d35a7-107">À partir de la version RTM de .NET 5,0, `TripleDES.Create().FeedbackSize` a une valeur par défaut de 8.</span><span class="sxs-lookup"><span data-stu-id="d35a7-107">Starting in the RTM version of .NET 5.0, `TripleDES.Create().FeedbackSize` has a default value of 8.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d35a7-108">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="d35a7-108">Reason for change</span></span>

<span data-ttu-id="d35a7-109">Dans .NET Framework, la <xref:System.Security.Cryptography.TripleDES> classe de base a par défaut la valeur <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 64, mais la <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> classe remplace la valeur par défaut par 8.</span><span class="sxs-lookup"><span data-stu-id="d35a7-109">In .NET Framework, the <xref:System.Security.Cryptography.TripleDES> base class defaults the value of <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> to 64, but the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class overwrites the default to 8.</span></span> <span data-ttu-id="d35a7-110">Lorsque la <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> propriété a été introduite dans .net core dans la version 2,0, ce même comportement a été préservé.</span><span class="sxs-lookup"><span data-stu-id="d35a7-110">When the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property was introduced to .NET Core in version 2.0, this same behavior was preserved.</span></span> <span data-ttu-id="d35a7-111">Toutefois, dans .NET Framework, <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> retourne une instance de <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> , donc la valeur par défaut de la fabrique d’algorithme est 8.</span><span class="sxs-lookup"><span data-stu-id="d35a7-111">However, in .NET Framework, <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> returns an instance of <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>, so the default value from the algorithm factory is 8.</span></span> <span data-ttu-id="d35a7-112">Pour .NET Core et .NET 5 +, la fabrique d’algorithmes retourne une implémentation non publique, qui, jusqu’à présent, avait une valeur par défaut de 64.</span><span class="sxs-lookup"><span data-stu-id="d35a7-112">For .NET Core and .NET 5+, the algorithm factory returns a non-public implementation, which, until now, had a default value of 64.</span></span>

<span data-ttu-id="d35a7-113">La modification de la <xref:System.Security.Cryptography.TripleDES> <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> valeur de la classe d’implémentation à 8 permet aux applications écrites pour .NET Framework qui ont spécifié le mode de chiffrement <xref:System.Security.Cryptography.CipherMode.CFB> , mais n’ont pas explicitement assigné la <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> propriété, pour continuer à fonctionner sur .net 5.</span><span class="sxs-lookup"><span data-stu-id="d35a7-113">Changing the <xref:System.Security.Cryptography.TripleDES> implementation class' <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> value to 8 allows for applications written for .NET Framework that specified the cipher mode as <xref:System.Security.Cryptography.CipherMode.CFB> but didn't explicitly assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property, to continue to function on .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d35a7-114">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d35a7-114">Version introduced</span></span>

<span data-ttu-id="d35a7-115">5,0 RTM</span><span class="sxs-lookup"><span data-stu-id="d35a7-115">5.0 RTM</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d35a7-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d35a7-116">Recommended action</span></span>

<span data-ttu-id="d35a7-117">Les applications qui chiffrent ou déchiffrent les données dans les versions RC1 ou RC2 de .NET 5,0 le font avec CFB64, quand les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="d35a7-117">Applications that encrypt or decrypt data in the RC1 or RC2 versions of .NET 5.0 do so with CFB64, when the following conditions are met:</span></span>

- <span data-ttu-id="d35a7-118">Avec une <xref:System.Security.Cryptography.TripleDES> instance de <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d35a7-118">With a <xref:System.Security.Cryptography.TripleDES> instance from <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="d35a7-119">À l’aide de la valeur par défaut pour <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> .</span><span class="sxs-lookup"><span data-stu-id="d35a7-119">Using the default value for <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span></span>
- <span data-ttu-id="d35a7-120">Avec la <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> propriété définie sur <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d35a7-120">With the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> property set to <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d35a7-121">Pour conserver ce comportement, assignez la <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> propriété à `64` .</span><span class="sxs-lookup"><span data-stu-id="d35a7-121">To maintain this behavior, assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property to `64`.</span></span>

<span data-ttu-id="d35a7-122">Toutes les `TripleDES` implémentations n’utilisent pas la même valeur par défaut pour <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> .</span><span class="sxs-lookup"><span data-stu-id="d35a7-122">Not all `TripleDES` implementations use the same default for <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span></span> <span data-ttu-id="d35a7-123">Si vous utilisez le <xref:System.Security.Cryptography.CipherMode.CFB> mode de chiffrement sur les <xref:System.Security.Cryptography.TripleDES> instances, nous vous recommandons de toujours assigner explicitement la valeur de la <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> propriété.</span><span class="sxs-lookup"><span data-stu-id="d35a7-123">We recommend that if you use the <xref:System.Security.Cryptography.CipherMode.CFB> cipher mode on <xref:System.Security.Cryptography.TripleDES> instances, you should always explicitly assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property value.</span></span>

```csharp
TripleDES cipher = TripleDES.Create();
cipher.Mode = CipherMode.CFB;
// Explicitly set the FeedbackSize for CFB to control between CFB8 and CFB64.
cipher.FeedbackSize = 8;
```

#### <a name="category"></a><span data-ttu-id="d35a7-124">Category</span><span class="sxs-lookup"><span data-stu-id="d35a7-124">Category</span></span>

- <span data-ttu-id="d35a7-125">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="d35a7-125">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d35a7-126">API affectées</span><span class="sxs-lookup"><span data-stu-id="d35a7-126">Affected APIs</span></span>

- <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.TripleDES.Create`
- `P:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize`

-->
