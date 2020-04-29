---
ms.openlocfilehash: d7a93cb539baee6a70f75d3afe52fd7546ac2399
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507077"
---
### <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a><span data-ttu-id="00524-101">Extensions : modifications de référence de package affectant certains packages NuGet</span><span class="sxs-lookup"><span data-stu-id="00524-101">Extensions: Package reference changes affecting some NuGet packages</span></span>

<span data-ttu-id="00524-102">Avec la migration de certains `Microsoft.Extensions.*` packages NuGet du référentiel [dotnet/extensions](https://github.com/dotnet/extensions) vers [dotnet/Runtime](https://github.com/dotnet/runtime), comme décrit dans [ASPNET/announcements # 411](https://github.com/aspnet/Announcements/issues/411), les modifications d’empaquetage sont appliquées à certains des packages migrés.</span><span class="sxs-lookup"><span data-stu-id="00524-102">With the migration of some `Microsoft.Extensions.*` NuGet packages from the [dotnet/extensions](https://github.com/dotnet/extensions) repository to [dotnet/runtime](https://github.com/dotnet/runtime), as described in [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), packaging changes are being applied to some of the migrated packages.</span></span> <span data-ttu-id="00524-103">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033).</span><span class="sxs-lookup"><span data-stu-id="00524-103">For discussion on this issue, see [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="00524-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="00524-104">Version introduced</span></span>

<span data-ttu-id="00524-105">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="00524-105">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="00524-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="00524-106">Old behavior</span></span>

<span data-ttu-id="00524-107">Certains `Microsoft.Extensions.*` packages incluent des références de package pour les API sur lesquelles votre application s’appuie.</span><span class="sxs-lookup"><span data-stu-id="00524-107">Some `Microsoft.Extensions.*` packages included package references for APIs on which your app relied.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="00524-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="00524-108">New behavior</span></span>

<span data-ttu-id="00524-109">Votre application doit peut-être `Microsoft.Extensions.*` ajouter des dépendances de package.</span><span class="sxs-lookup"><span data-stu-id="00524-109">Your app may have to add `Microsoft.Extensions.*` package dependencies.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="00524-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="00524-110">Reason for change</span></span>

<span data-ttu-id="00524-111">Les stratégies d’empaquetage ont été mises à jour pour mieux s’aligner avec le référentiel *dotnet/Runtime* .</span><span class="sxs-lookup"><span data-stu-id="00524-111">Packaging policies were updated to better align with the *dotnet/runtime* repository.</span></span> <span data-ttu-id="00524-112">Dans la nouvelle stratégie, les références de package inutilisées sont supprimées des fichiers *. nupkg* lors de l’empaquetage.</span><span class="sxs-lookup"><span data-stu-id="00524-112">Under the new policy, unused package references are removed from *.nupkg* files during packaging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="00524-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="00524-113">Recommended action</span></span>

<span data-ttu-id="00524-114">Les consommateurs des packages concernés doivent ajouter une dépendance directe sur la dépendance de package supprimée dans leur projet si les API de la dépendance de package supprimée sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="00524-114">Consumers of the affected packages should add a direct dependency on the removed package dependency in their project if APIs from removed package dependency are used.</span></span> <span data-ttu-id="00524-115">Le tableau suivant répertorie les packages affectés et les modifications correspondantes.</span><span class="sxs-lookup"><span data-stu-id="00524-115">The following table lists the affected packages and the corresponding changes.</span></span>

|<span data-ttu-id="00524-116">Nom du package</span><span class="sxs-lookup"><span data-stu-id="00524-116">Package name</span></span>|<span data-ttu-id="00524-117">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="00524-117">Change description</span></span>|
|------------|------------------|
|[<span data-ttu-id="00524-118">Microsoft. extensions. Configuration. Binder</span><span class="sxs-lookup"><span data-stu-id="00524-118">Microsoft.Extensions.Configuration.Binder</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|<span data-ttu-id="00524-119">Suppression de la référence à`Microsoft.Extensions.Configuration`</span><span class="sxs-lookup"><span data-stu-id="00524-119">Removed reference to `Microsoft.Extensions.Configuration`</span></span>|
|[<span data-ttu-id="00524-120">Microsoft. extensions. Configuration. JSON</span><span class="sxs-lookup"><span data-stu-id="00524-120">Microsoft.Extensions.Configuration.Json</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |<span data-ttu-id="00524-121">Suppression de la référence à`System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="00524-121">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="00524-122">Microsoft. extensions. Hosting. Abstracts</span><span class="sxs-lookup"><span data-stu-id="00524-122">Microsoft.Extensions.Hosting.Abstractions</span></span>](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|<span data-ttu-id="00524-123">Suppression de la référence à`Microsoft.Extensions.Logging.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="00524-123">Removed reference to `Microsoft.Extensions.Logging.Abstractions`</span></span>|
|[<span data-ttu-id="00524-124">Microsoft.Extensions.Logging</span><span class="sxs-lookup"><span data-stu-id="00524-124">Microsoft.Extensions.Logging</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |<span data-ttu-id="00524-125">Suppression de la référence à`Microsoft.Extensions.Configuration.Binder`</span><span class="sxs-lookup"><span data-stu-id="00524-125">Removed reference to `Microsoft.Extensions.Configuration.Binder`</span></span>|
|[<span data-ttu-id="00524-126">Microsoft. extensions. Logging. console</span><span class="sxs-lookup"><span data-stu-id="00524-126">Microsoft.Extensions.Logging.Console</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |<span data-ttu-id="00524-127">Suppression de la référence à`Microsoft.Extensions.Configuration.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="00524-127">Removed reference to `Microsoft.Extensions.Configuration.Abstractions`</span></span>|
|[<span data-ttu-id="00524-128">Microsoft. extensions. Logging. EventLog</span><span class="sxs-lookup"><span data-stu-id="00524-128">Microsoft.Extensions.Logging.EventLog</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |<span data-ttu-id="00524-129">Référence supprimée `System.Diagnostics.EventLog` à pour le moniker du Framework cible .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="00524-129">Removed reference to `System.Diagnostics.EventLog` for the .NET Framework 4.6.1 target framework moniker</span></span>|
|[<span data-ttu-id="00524-130">Microsoft. extensions. Logging. EventSource</span><span class="sxs-lookup"><span data-stu-id="00524-130">Microsoft.Extensions.Logging.EventSource</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |<span data-ttu-id="00524-131">Suppression de la référence à`System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="00524-131">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="00524-132">Microsoft. extensions. options</span><span class="sxs-lookup"><span data-stu-id="00524-132">Microsoft.Extensions.Options</span></span>](https://nuget.org/packages/Microsoft.Extensions.Options)                          |<span data-ttu-id="00524-133">Suppression de la référence à`System.ComponentModel.Annotations`</span><span class="sxs-lookup"><span data-stu-id="00524-133">Removed reference to `System.ComponentModel.Annotations`</span></span>|

<span data-ttu-id="00524-134">Par exemple, la référence de package `Microsoft.Extensions.Configuration` à a été `Microsoft.Extensions.Configuration.Binder`supprimée de.</span><span class="sxs-lookup"><span data-stu-id="00524-134">For example, the package reference to `Microsoft.Extensions.Configuration` was removed from `Microsoft.Extensions.Configuration.Binder`.</span></span> <span data-ttu-id="00524-135">Aucune API de la dépendance n’a été utilisée dans le package.</span><span class="sxs-lookup"><span data-stu-id="00524-135">No API from the dependency was used in the package.</span></span> <span data-ttu-id="00524-136">Les utilisateurs `Microsoft.Extensions.Configuration.Binder` de qui dépendent des API `Microsoft.Extensions.Configuration` de doivent ajouter une référence directe à celui-ci dans leur projet.</span><span class="sxs-lookup"><span data-stu-id="00524-136">Users of `Microsoft.Extensions.Configuration.Binder` who depend on APIs from `Microsoft.Extensions.Configuration` should add a direct reference to it in their project.</span></span>

#### <a name="category"></a><span data-ttu-id="00524-137">Category</span><span class="sxs-lookup"><span data-stu-id="00524-137">Category</span></span>

<span data-ttu-id="00524-138">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="00524-138">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="00524-139">API affectées</span><span class="sxs-lookup"><span data-stu-id="00524-139">Affected APIs</span></span>

<span data-ttu-id="00524-140">None</span><span class="sxs-lookup"><span data-stu-id="00524-140">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
