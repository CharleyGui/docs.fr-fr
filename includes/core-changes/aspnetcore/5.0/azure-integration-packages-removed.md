---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291641"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="f56cc-101">Azure : Les paquets d’intégration Azure préfixés de Microsoft supprimés</span><span class="sxs-lookup"><span data-stu-id="f56cc-101">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="f56cc-102">Les `Microsoft.*` paquets suivants qui assurent l’intégration entre ASP.NET Core et Azure SDKs ne sont pas inclus dans ASP.NET Core 5.0 :</span><span class="sxs-lookup"><span data-stu-id="f56cc-102">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="f56cc-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), qui intègre [Azure Key Vault](/azure/key-vault/) dans le [système Configuration](/aspnet/core/fundamentals/configuration/).</span><span class="sxs-lookup"><span data-stu-id="f56cc-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="f56cc-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), qui intègre Azure Key Vault dans le [système ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="f56cc-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="f56cc-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), qui intègre [Azure Blob Storage](/azure/storage/blobs/) dans le système ASP.NET Core Data Protection.</span><span class="sxs-lookup"><span data-stu-id="f56cc-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="f56cc-106">Pour discussion sur cette question, voir [dotnet/aspnetcore-19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="f56cc-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f56cc-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f56cc-107">Version introduced</span></span>

<span data-ttu-id="f56cc-108">5.0 Aperçu 1</span><span class="sxs-lookup"><span data-stu-id="f56cc-108">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f56cc-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="f56cc-109">Old behavior</span></span>

<span data-ttu-id="f56cc-110">Les `Microsoft.*` forfaits intègrent les services Azure avec les API Configuration et Protection des Données.</span><span class="sxs-lookup"><span data-stu-id="f56cc-110">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f56cc-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="f56cc-111">New behavior</span></span>

<span data-ttu-id="f56cc-112">De `Azure.*` nouveaux forfaits intègrent les services Azure aux API Configuration et Protection des Données.</span><span class="sxs-lookup"><span data-stu-id="f56cc-112">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f56cc-113">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="f56cc-113">Reason for change</span></span>

<span data-ttu-id="f56cc-114">Le changement a `Microsoft.*` été apporté parce que les paquets étaient :</span><span class="sxs-lookup"><span data-stu-id="f56cc-114">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="f56cc-115">Utilisation de versions désuètes de l’Azure SDK.</span><span class="sxs-lookup"><span data-stu-id="f56cc-115">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="f56cc-116">Des mises à jour simples n’étaient pas possibles car les nouvelles versions de l’Azure SDK incluaient des modifications de rupture.</span><span class="sxs-lookup"><span data-stu-id="f56cc-116">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="f56cc-117">Lié à l’horaire de sortie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f56cc-117">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="f56cc-118">Le transfert de la propriété des paquets à l’équipe Azure SDK permet de mettre à jour les paquets au fur et à mesure que le SDK Azure est mis à jour.</span><span class="sxs-lookup"><span data-stu-id="f56cc-118">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f56cc-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f56cc-119">Recommended action</span></span>

<span data-ttu-id="f56cc-120">Dans ASP.NET Projets Core 2.1 ou plus `Microsoft.*` tard, `Azure.*` remplacez l’ancien par les nouveaux paquets.</span><span class="sxs-lookup"><span data-stu-id="f56cc-120">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="f56cc-121">Vieux</span><span class="sxs-lookup"><span data-stu-id="f56cc-121">Old</span></span> | <span data-ttu-id="f56cc-122">Nouveau</span><span class="sxs-lookup"><span data-stu-id="f56cc-122">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="f56cc-123">Azure.AspNetCore.DataProtection.Keys Azure.AspNetCore.DataProtection.Keys Azure.AspNetCore.DataProtection.Keys Azure</span><span class="sxs-lookup"><span data-stu-id="f56cc-123">Azure.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="f56cc-124">Azure.AspNetCore.DataProtection.Blobs Azure.AspNetCore.DataProtection.Blobs Azure.AspNetCore.DataProtection.Blobs Azure</span><span class="sxs-lookup"><span data-stu-id="f56cc-124">Azure.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="f56cc-125">Azure.Extensions.Configuration.Secrets Azure.Extensions.Configuration.Secrets Azure.Extensions.Configuration.Secrets Azure</span><span class="sxs-lookup"><span data-stu-id="f56cc-125">Azure.Extensions.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

<span data-ttu-id="f56cc-126">Les nouveaux paquets utilisent une nouvelle version de l’Azure SDK qui comprend des changements de rupture.</span><span class="sxs-lookup"><span data-stu-id="f56cc-126">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="f56cc-127">Les habitudes générales d’utilisation sont inchangées.</span><span class="sxs-lookup"><span data-stu-id="f56cc-127">The general usage patterns are unchanged.</span></span> <span data-ttu-id="f56cc-128">Certaines surcharges et options peuvent différer pour s’adapter aux changements des API azure SDK sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="f56cc-128">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="f56cc-129">Les anciens paquets seront:</span><span class="sxs-lookup"><span data-stu-id="f56cc-129">The old packages will:</span></span>

* <span data-ttu-id="f56cc-130">Soyez soutenu par l’équipe ASP.NET Core pour la durée de vie de .NET Core 2.1 et 3.1.</span><span class="sxs-lookup"><span data-stu-id="f56cc-130">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="f56cc-131">Ne pas être inclus dans .NET 5.</span><span class="sxs-lookup"><span data-stu-id="f56cc-131">Not be included in .NET 5.</span></span>

<span data-ttu-id="f56cc-132">Lors de la mise à niveau de `Azure.*` votre projet à .NET 5, passez aux paquets pour maintenir le soutien.</span><span class="sxs-lookup"><span data-stu-id="f56cc-132">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

#### <a name="category"></a><span data-ttu-id="f56cc-133">Category</span><span class="sxs-lookup"><span data-stu-id="f56cc-133">Category</span></span>

<span data-ttu-id="f56cc-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f56cc-134">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f56cc-135">API affectées</span><span class="sxs-lookup"><span data-stu-id="f56cc-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
