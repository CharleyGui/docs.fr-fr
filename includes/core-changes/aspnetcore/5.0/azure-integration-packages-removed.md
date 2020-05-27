---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291641"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="b8fb7-101">Azure : packages d’intégration Azure préfixés par Microsoft supprimés</span><span class="sxs-lookup"><span data-stu-id="b8fb7-101">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="b8fb7-102">Les `Microsoft.*` packages suivants qui assurent l’intégration entre les ASP.net Core et les kits de développement logiciel (SDK) Azure ne sont pas inclus dans ASP.NET Core 5,0 :</span><span class="sxs-lookup"><span data-stu-id="b8fb7-102">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="b8fb7-103">[Microsoft. extensions. Configuration. AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), qui intègre [Azure Key Vault](/azure/key-vault/) dans le [système de configuration](/aspnet/core/fundamentals/configuration/).</span><span class="sxs-lookup"><span data-stu-id="b8fb7-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="b8fb7-104">[Microsoft. AspNetCore. dataprotection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), qui intègre Azure Key Vault dans le [système de Protection des données ASP.net Core](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="b8fb7-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="b8fb7-105">[Microsoft. AspNetCore. dataprotection. AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), qui intègre le [stockage d’objets BLOB Azure](/azure/storage/blobs/) dans le système de protection des données ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="b8fb7-106">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="b8fb7-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b8fb7-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b8fb7-107">Version introduced</span></span>

<span data-ttu-id="b8fb7-108">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="b8fb7-108">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b8fb7-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="b8fb7-109">Old behavior</span></span>

<span data-ttu-id="b8fb7-110">Les `Microsoft.*` packages intègrent les services Azure avec les API de configuration et de protection des données.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-110">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b8fb7-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="b8fb7-111">New behavior</span></span>

<span data-ttu-id="b8fb7-112">`Azure.*`Les nouveaux packages intègrent les services Azure avec les API de configuration et de protection des données.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-112">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b8fb7-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="b8fb7-113">Reason for change</span></span>

<span data-ttu-id="b8fb7-114">La modification a été apportée parce que les `Microsoft.*` packages étaient :</span><span class="sxs-lookup"><span data-stu-id="b8fb7-114">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="b8fb7-115">À l’aide de versions obsolètes du kit de développement logiciel (SDK) Azure.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-115">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="b8fb7-116">Les mises à jour simples n’étaient pas possibles car les nouvelles versions du kit de développement logiciel (SDK) Azure comprenaient des modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-116">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="b8fb7-117">Lié au calendrier des versions de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-117">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="b8fb7-118">Le transfert de la propriété des packages à l’équipe du kit de développement logiciel (SDK) Azure active les mises à jour du package lors de la mise à jour du kit SDK Azure.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-118">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b8fb7-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b8fb7-119">Recommended action</span></span>

<span data-ttu-id="b8fb7-120">Dans ASP.NET Core projets 2,1 ou versions ultérieures, remplacez l’ancien `Microsoft.*` par les nouveaux `Azure.*` packages.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-120">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="b8fb7-121">Ancien</span><span class="sxs-lookup"><span data-stu-id="b8fb7-121">Old</span></span> | <span data-ttu-id="b8fb7-122">Nouveau</span><span class="sxs-lookup"><span data-stu-id="b8fb7-122">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="b8fb7-123">Azure. AspNetCore. DataProtection. Keys</span><span class="sxs-lookup"><span data-stu-id="b8fb7-123">Azure.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="b8fb7-124">Azure. AspNetCore. DataProtection. blob</span><span class="sxs-lookup"><span data-stu-id="b8fb7-124">Azure.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="b8fb7-125">Azure. extensions. Configuration. secrets</span><span class="sxs-lookup"><span data-stu-id="b8fb7-125">Azure.Extensions.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

<span data-ttu-id="b8fb7-126">Les nouveaux packages utilisent une nouvelle version du kit de développement logiciel (SDK) Azure qui comprend des modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-126">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="b8fb7-127">Les modèles d’utilisation générale sont inchangés.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-127">The general usage patterns are unchanged.</span></span> <span data-ttu-id="b8fb7-128">Certaines surcharges et options peuvent varier pour s’adapter aux modifications apportées aux API du kit de développement logiciel (SDK) Azure sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-128">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="b8fb7-129">Les anciens packages vont :</span><span class="sxs-lookup"><span data-stu-id="b8fb7-129">The old packages will:</span></span>

* <span data-ttu-id="b8fb7-130">Être pris en charge par l’équipe ASP.NET Core pendant la durée de vie de .NET Core 2,1 et 3,1.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-130">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="b8fb7-131">Ne sont pas inclus dans .NET 5.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-131">Not be included in .NET 5.</span></span>

<span data-ttu-id="b8fb7-132">Lors de la mise à niveau de votre projet vers .NET 5, effectuez la transition vers les `Azure.*` packages pour maintenir la prise en charge.</span><span class="sxs-lookup"><span data-stu-id="b8fb7-132">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

#### <a name="category"></a><span data-ttu-id="b8fb7-133">Category</span><span class="sxs-lookup"><span data-stu-id="b8fb7-133">Category</span></span>

<span data-ttu-id="b8fb7-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b8fb7-134">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b8fb7-135">API affectées</span><span class="sxs-lookup"><span data-stu-id="b8fb7-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
