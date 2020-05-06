---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902019"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="5e633-101">Protection des données : DataProtection. AzureStorage utilise les nouvelles API de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="5e633-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="5e633-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>dépend des [bibliothèques de stockage Azure](https://github.com/Azure/azure-storage-net).</span><span class="sxs-lookup"><span data-stu-id="5e633-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="5e633-103">Ces bibliothèques ont renommé leurs assemblys, leurs packages et leurs espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="5e633-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="5e633-104">À partir de ASP.NET Core 3,0 `Microsoft.AspNetCore.DataProtection.AzureStorage` , utilise les `Microsoft.Azure.Storage.`nouvelles API et les packages préfixés.</span><span class="sxs-lookup"><span data-stu-id="5e633-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="5e633-105">Pour toute question sur les API de stockage Azure <https://github.com/Azure/azure-storage-net>, utilisez.</span><span class="sxs-lookup"><span data-stu-id="5e633-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="5e633-106">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 8472](https://github.com/dotnet/aspnetcore/issues/8472).</span><span class="sxs-lookup"><span data-stu-id="5e633-106">For discussion on this issue, see [dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5e633-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="5e633-107">Version introduced</span></span>

<span data-ttu-id="5e633-108">3.0</span><span class="sxs-lookup"><span data-stu-id="5e633-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5e633-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="5e633-109">Old behavior</span></span>

<span data-ttu-id="5e633-110">Le package a référencé le `WindowsAzure.Storage` package NuGet.</span><span class="sxs-lookup"><span data-stu-id="5e633-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5e633-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="5e633-111">New behavior</span></span>

<span data-ttu-id="5e633-112">Le package fait référence `Microsoft.Azure.Storage.Blob` au package NuGet.</span><span class="sxs-lookup"><span data-stu-id="5e633-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5e633-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="5e633-113">Reason for change</span></span>

<span data-ttu-id="5e633-114">Cette modification permet `Microsoft.AspNetCore.DataProtection.AzureStorage` de migrer vers les packages de stockage Azure recommandés.</span><span class="sxs-lookup"><span data-stu-id="5e633-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5e633-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="5e633-115">Recommended action</span></span>

<span data-ttu-id="5e633-116">Si vous avez encore besoin d’utiliser les anciennes API de stockage Azure avec ASP.NET Core 3,0, ajoutez une dépendance directe au package [WindowsAzure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) .</span><span class="sxs-lookup"><span data-stu-id="5e633-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="5e633-117">Ce package peut être installé avec les nouvelles `Microsoft.Azure.Storage` API.</span><span class="sxs-lookup"><span data-stu-id="5e633-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="5e633-118">Dans de nombreux cas, la mise à niveau implique `using` uniquement la modification des instructions pour utiliser les nouveaux espaces de noms :</span><span class="sxs-lookup"><span data-stu-id="5e633-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="5e633-119">Category</span><span class="sxs-lookup"><span data-stu-id="5e633-119">Category</span></span>

<span data-ttu-id="5e633-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5e633-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5e633-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="5e633-121">Affected APIs</span></span>

<span data-ttu-id="5e633-122">Aucun</span><span class="sxs-lookup"><span data-stu-id="5e633-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
