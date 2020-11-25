---
title: 'Modification avec rupture : Azure : packages d’intégration Azure préfixés par Microsoft supprimés'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé Azure : packages d’intégration Azure préfixés par Microsoft supprimés'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b9f685b8c9fdcd73044f78840f2732809a0de710
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761226"
---
# <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="298f0-103">Azure : packages d’intégration Azure préfixés par Microsoft supprimés</span><span class="sxs-lookup"><span data-stu-id="298f0-103">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="298f0-104">Les `Microsoft.*` packages suivants qui assurent l’intégration entre les ASP.net Core et les kits de développement logiciel (SDK) Azure ne sont pas inclus dans ASP.NET Core 5,0 :</span><span class="sxs-lookup"><span data-stu-id="298f0-104">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="298f0-105">[Microsoft.Extensions.Configfiguration. AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), qui intègre [Azure Key Vault](/azure/key-vault/) dans le [système de configuration](/aspnet/core/fundamentals/configuration/).</span><span class="sxs-lookup"><span data-stu-id="298f0-105">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="298f0-106">[Microsoft. AspNetCore. dataprotection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), qui intègre Azure Key Vault dans le [système de Protection des données ASP.net Core](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="298f0-106">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="298f0-107">[Microsoft. AspNetCore. dataprotection. AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), qui intègre le [stockage d’objets BLOB Azure](/azure/storage/blobs/) dans le système de protection des données ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="298f0-107">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="298f0-108">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="298f0-108">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="298f0-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="298f0-109">Version introduced</span></span>

<span data-ttu-id="298f0-110">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="298f0-110">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="298f0-111">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="298f0-111">Old behavior</span></span>

<span data-ttu-id="298f0-112">Les `Microsoft.*` packages intègrent les services Azure avec les API de configuration et de protection des données.</span><span class="sxs-lookup"><span data-stu-id="298f0-112">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="298f0-113">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="298f0-113">New behavior</span></span>

<span data-ttu-id="298f0-114">`Azure.*`Les nouveaux packages intègrent les services Azure avec les API de configuration et de protection des données.</span><span class="sxs-lookup"><span data-stu-id="298f0-114">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="298f0-115">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="298f0-115">Reason for change</span></span>

<span data-ttu-id="298f0-116">La modification a été apportée parce que les `Microsoft.*` packages étaient :</span><span class="sxs-lookup"><span data-stu-id="298f0-116">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="298f0-117">À l’aide de versions obsolètes du kit de développement logiciel (SDK) Azure.</span><span class="sxs-lookup"><span data-stu-id="298f0-117">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="298f0-118">Les mises à jour simples n’étaient pas possibles car les nouvelles versions du kit de développement logiciel (SDK) Azure comprenaient des modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="298f0-118">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="298f0-119">Lié au calendrier des versions de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="298f0-119">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="298f0-120">Le transfert de la propriété des packages à l’équipe du kit de développement logiciel (SDK) Azure active les mises à jour du package lors de la mise à jour du kit SDK Azure.</span><span class="sxs-lookup"><span data-stu-id="298f0-120">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="298f0-121">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="298f0-121">Recommended action</span></span>

<span data-ttu-id="298f0-122">Dans ASP.NET Core projets 2,1 ou versions ultérieures, remplacez l’ancien `Microsoft.*` par les nouveaux `Azure.*` packages.</span><span class="sxs-lookup"><span data-stu-id="298f0-122">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="298f0-123">Ancien</span><span class="sxs-lookup"><span data-stu-id="298f0-123">Old</span></span> | <span data-ttu-id="298f0-124">Nouveau</span><span class="sxs-lookup"><span data-stu-id="298f0-124">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="298f0-125">Azure. extensions. AspNetCore. DataProtection. Keys</span><span class="sxs-lookup"><span data-stu-id="298f0-125">Azure.Extensions.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="298f0-126">Azure. extensions. AspNetCore. DataProtection. blob</span><span class="sxs-lookup"><span data-stu-id="298f0-126">Azure.Extensions.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="298f0-127">Azure.Extensions.AspNetCore.Configfiguration. Secrète</span><span class="sxs-lookup"><span data-stu-id="298f0-127">Azure.Extensions.AspNetCore.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

<span data-ttu-id="298f0-128">Les nouveaux packages utilisent une nouvelle version du kit de développement logiciel (SDK) Azure qui comprend des modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="298f0-128">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="298f0-129">Les modèles d’utilisation générale sont inchangés.</span><span class="sxs-lookup"><span data-stu-id="298f0-129">The general usage patterns are unchanged.</span></span> <span data-ttu-id="298f0-130">Certaines surcharges et options peuvent varier pour s’adapter aux modifications apportées aux API du kit de développement logiciel (SDK) Azure sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="298f0-130">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="298f0-131">Les anciens packages vont :</span><span class="sxs-lookup"><span data-stu-id="298f0-131">The old packages will:</span></span>

* <span data-ttu-id="298f0-132">Être pris en charge par l’équipe ASP.NET Core pendant la durée de vie de .NET Core 2,1 et 3,1.</span><span class="sxs-lookup"><span data-stu-id="298f0-132">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="298f0-133">Ne sont pas inclus dans .NET 5.</span><span class="sxs-lookup"><span data-stu-id="298f0-133">Not be included in .NET 5.</span></span>

<span data-ttu-id="298f0-134">Lors de la mise à niveau de votre projet vers .NET 5, effectuez la transition vers les `Azure.*` packages pour maintenir la prise en charge.</span><span class="sxs-lookup"><span data-stu-id="298f0-134">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="298f0-135">API affectées</span><span class="sxs-lookup"><span data-stu-id="298f0-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
