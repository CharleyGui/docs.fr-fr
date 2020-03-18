---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902019"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="d4f4d-101">Protection des données : DataProtection.AzureStorage utilise de nouvelles API de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="d4f4d-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="d4f4d-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>dépend des [bibliothèques de stockage Azure](https://github.com/Azure/azure-storage-net).</span><span class="sxs-lookup"><span data-stu-id="d4f4d-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="d4f4d-103">Ces bibliothèques ont rebaptisé leurs assemblages, forfaits et espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="d4f4d-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="d4f4d-104">À partir de ASP.NET Core `Microsoft.AspNetCore.DataProtection.AzureStorage` 3.0, `Microsoft.Azure.Storage.`utilise les nouvelles API et les paquets préfixés.</span><span class="sxs-lookup"><span data-stu-id="d4f4d-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="d4f4d-105">Pour des questions sur les API de stockage Azure, utilisez <https://github.com/Azure/azure-storage-net>.</span><span class="sxs-lookup"><span data-stu-id="d4f4d-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="d4f4d-106">Pour discussion sur cette question, voir [dotnet/aspnetcore 8472](https://github.com/dotnet/aspnetcore/issues/8472).</span><span class="sxs-lookup"><span data-stu-id="d4f4d-106">For discussion on this issue, see [dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d4f4d-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d4f4d-107">Version introduced</span></span>

<span data-ttu-id="d4f4d-108">3.0</span><span class="sxs-lookup"><span data-stu-id="d4f4d-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d4f4d-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="d4f4d-109">Old behavior</span></span>

<span data-ttu-id="d4f4d-110">Le paquet faisait `WindowsAzure.Storage` référence au paquet NuGet.</span><span class="sxs-lookup"><span data-stu-id="d4f4d-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d4f4d-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="d4f4d-111">New behavior</span></span>

<span data-ttu-id="d4f4d-112">Le paquet `Microsoft.Azure.Storage.Blob` fait référence au package NuGet.</span><span class="sxs-lookup"><span data-stu-id="d4f4d-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d4f4d-113">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="d4f4d-113">Reason for change</span></span>

<span data-ttu-id="d4f4d-114">Ce changement `Microsoft.AspNetCore.DataProtection.AzureStorage` permet de migrer vers les paquets de stockage Azure recommandés.</span><span class="sxs-lookup"><span data-stu-id="d4f4d-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d4f4d-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d4f4d-115">Recommended action</span></span>

<span data-ttu-id="d4f4d-116">Si vous avez encore besoin d’utiliser les anciennes API de stockage Azure avec ASP.NET Core 3.0, ajoutez une dépendance directe au package [WindowsAzure.Storage.](https://www.nuget.org/packages/WindowsAzure.Storage/)</span><span class="sxs-lookup"><span data-stu-id="d4f4d-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="d4f4d-117">Ce paquet peut être installé `Microsoft.Azure.Storage` aux côtés des nouvelles API.</span><span class="sxs-lookup"><span data-stu-id="d4f4d-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="d4f4d-118">Dans de nombreux cas, la `using` mise à niveau ne consiste qu’à modifier les instructions pour utiliser les nouveaux espaces de noms :</span><span class="sxs-lookup"><span data-stu-id="d4f4d-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="d4f4d-119">Category</span><span class="sxs-lookup"><span data-stu-id="d4f4d-119">Category</span></span>

<span data-ttu-id="d4f4d-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d4f4d-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d4f4d-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="d4f4d-121">Affected APIs</span></span>

<span data-ttu-id="d4f4d-122">None</span><span class="sxs-lookup"><span data-stu-id="d4f4d-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
