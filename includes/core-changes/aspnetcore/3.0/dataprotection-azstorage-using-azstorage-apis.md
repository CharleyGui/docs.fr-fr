---
ms.openlocfilehash: f6e4c3d5c5fd020562e48515554136e0f8b6785c
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440421"
---
### <a name="data-protection-dataprotectionblobs-uses-new-azure-storage-apis"></a><span data-ttu-id="f6f5b-101">Protection des données : DataProtection. blob utilise les nouvelles API de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="f6f5b-101">Data Protection: DataProtection.Blobs uses new Azure Storage APIs</span></span>

<span data-ttu-id="f6f5b-102">`Azure.Extensions.AspNetCore.DataProtection.Blobs` dépend des [bibliothèques de stockage Azure](https://github.com/Azure/azure-storage-net).</span><span class="sxs-lookup"><span data-stu-id="f6f5b-102">`Azure.Extensions.AspNetCore.DataProtection.Blobs` depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="f6f5b-103">Ces bibliothèques ont renommé leurs assemblys, leurs packages et leurs espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="f6f5b-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="f6f5b-104">À partir de ASP.NET Core 3,0, `Azure.Extensions.AspNetCore.DataProtection.Blobs` utilise les nouvelles `Azure.Storage.` API et les packages préfixés.</span><span class="sxs-lookup"><span data-stu-id="f6f5b-104">Starting in ASP.NET Core 3.0, `Azure.Extensions.AspNetCore.DataProtection.Blobs` uses the new `Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="f6f5b-105">Pour toute question sur les API de stockage Azure, utilisez <https://github.com/Azure/azure-storage-net> .</span><span class="sxs-lookup"><span data-stu-id="f6f5b-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="f6f5b-106">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="f6f5b-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f6f5b-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f6f5b-107">Version introduced</span></span>

<span data-ttu-id="f6f5b-108">3.0</span><span class="sxs-lookup"><span data-stu-id="f6f5b-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f6f5b-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="f6f5b-109">Old behavior</span></span>

<span data-ttu-id="f6f5b-110">Le package a référencé le `WindowsAzure.Storage` package NuGet.</span><span class="sxs-lookup"><span data-stu-id="f6f5b-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>
<span data-ttu-id="f6f5b-111">Le package fait référence au `Microsoft.Azure.Storage.Blob` package NuGet.</span><span class="sxs-lookup"><span data-stu-id="f6f5b-111">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f6f5b-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="f6f5b-112">New behavior</span></span>

<span data-ttu-id="f6f5b-113">Le package fait référence au `Azure.Storage.Blob` package NuGet.</span><span class="sxs-lookup"><span data-stu-id="f6f5b-113">The package references the `Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f6f5b-114">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="f6f5b-114">Reason for change</span></span>

<span data-ttu-id="f6f5b-115">Cette modification permet `Azure.Extensions.AspNetCore.DataProtection.Blobs` de migrer vers les packages de stockage Azure recommandés.</span><span class="sxs-lookup"><span data-stu-id="f6f5b-115">This change allows `Azure.Extensions.AspNetCore.DataProtection.Blobs` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f6f5b-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f6f5b-116">Recommended action</span></span>

<span data-ttu-id="f6f5b-117">Si vous avez encore besoin d’utiliser les anciennes API de stockage Azure avec ASP.NET Core 3,0, ajoutez une dépendance directe au package [WindowsAzure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) ou [Microsoft. Azure. Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/).</span><span class="sxs-lookup"><span data-stu-id="f6f5b-117">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the package [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) or [Microsoft.Azure.Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/).</span></span> <span data-ttu-id="f6f5b-118">Ce package peut être installé avec les nouvelles `Azure.Storage` API.</span><span class="sxs-lookup"><span data-stu-id="f6f5b-118">This package can be installed alongside the new `Azure.Storage` APIs.</span></span>

<span data-ttu-id="f6f5b-119">Dans de nombreux cas, la mise à niveau implique uniquement la modification des `using` instructions pour utiliser les nouveaux espaces de noms :</span><span class="sxs-lookup"><span data-stu-id="f6f5b-119">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
- using Microsoft.Azure.Storage;
- using Microsoft.Azure.Storage.Blob;
+ using Azure.Storage;
+ using Azure.Storage.Blobs;
```

#### <a name="category"></a><span data-ttu-id="f6f5b-120">Category</span><span class="sxs-lookup"><span data-stu-id="f6f5b-120">Category</span></span>

<span data-ttu-id="f6f5b-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f6f5b-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f6f5b-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="f6f5b-122">Affected APIs</span></span>

<span data-ttu-id="f6f5b-123">Aucun</span><span class="sxs-lookup"><span data-stu-id="f6f5b-123">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
