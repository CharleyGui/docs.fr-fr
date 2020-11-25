---
title: 'Modification avec rupture : extensions : modifications de référence de package affectant certains packages NuGet'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core extensions 5,0 intitulées : modifications de référence de package affectant certains packages NuGet'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 4a525d9f7aad4409fd507fcf80c00968ff4b63d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760963"
---
# <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a><span data-ttu-id="adaec-103">Extensions : modifications de référence de package affectant certains packages NuGet</span><span class="sxs-lookup"><span data-stu-id="adaec-103">Extensions: Package reference changes affecting some NuGet packages</span></span>

<span data-ttu-id="adaec-104">Avec la migration de certains `Microsoft.Extensions.*` packages NuGet du référentiel [dotnet/extensions](https://github.com/dotnet/extensions) vers [dotnet/Runtime](https://github.com/dotnet/runtime), comme décrit dans [ASPNET/announcements # 411](https://github.com/aspnet/Announcements/issues/411), les modifications d’empaquetage sont appliquées à certains des packages migrés.</span><span class="sxs-lookup"><span data-stu-id="adaec-104">With the migration of some `Microsoft.Extensions.*` NuGet packages from the [dotnet/extensions](https://github.com/dotnet/extensions) repository to [dotnet/runtime](https://github.com/dotnet/runtime), as described in [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), packaging changes are being applied to some of the migrated packages.</span></span> <span data-ttu-id="adaec-105">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033).</span><span class="sxs-lookup"><span data-stu-id="adaec-105">For discussion on this issue, see [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="adaec-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="adaec-106">Version introduced</span></span>

<span data-ttu-id="adaec-107">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="adaec-107">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="adaec-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="adaec-108">Old behavior</span></span>

<span data-ttu-id="adaec-109">Certains `Microsoft.Extensions.*` packages incluent des références de package pour les API sur lesquelles votre application s’appuie.</span><span class="sxs-lookup"><span data-stu-id="adaec-109">Some `Microsoft.Extensions.*` packages included package references for APIs on which your app relied.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="adaec-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="adaec-110">New behavior</span></span>

<span data-ttu-id="adaec-111">Votre application doit peut-être ajouter des `Microsoft.Extensions.*` dépendances de package.</span><span class="sxs-lookup"><span data-stu-id="adaec-111">Your app may have to add `Microsoft.Extensions.*` package dependencies.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="adaec-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="adaec-112">Reason for change</span></span>

<span data-ttu-id="adaec-113">Les stratégies d’empaquetage ont été mises à jour pour mieux s’aligner avec le référentiel *dotnet/Runtime* .</span><span class="sxs-lookup"><span data-stu-id="adaec-113">Packaging policies were updated to better align with the *dotnet/runtime* repository.</span></span> <span data-ttu-id="adaec-114">Dans la nouvelle stratégie, les références de package inutilisées sont supprimées des fichiers *. nupkg* lors de l’empaquetage.</span><span class="sxs-lookup"><span data-stu-id="adaec-114">Under the new policy, unused package references are removed from *.nupkg* files during packaging.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="adaec-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="adaec-115">Recommended action</span></span>

<span data-ttu-id="adaec-116">Les consommateurs des packages concernés doivent ajouter une dépendance directe sur la dépendance de package supprimée dans leur projet si les API de la dépendance de package supprimée sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="adaec-116">Consumers of the affected packages should add a direct dependency on the removed package dependency in their project if APIs from removed package dependency are used.</span></span> <span data-ttu-id="adaec-117">Le tableau suivant répertorie les packages affectés et les modifications correspondantes.</span><span class="sxs-lookup"><span data-stu-id="adaec-117">The following table lists the affected packages and the corresponding changes.</span></span>

|<span data-ttu-id="adaec-118">Nom du package</span><span class="sxs-lookup"><span data-stu-id="adaec-118">Package name</span></span>|<span data-ttu-id="adaec-119">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="adaec-119">Change description</span></span>|
|------------|------------------|
|[<span data-ttu-id="adaec-120">Microsoft.Extensions.Configfiguration. Classeur</span><span class="sxs-lookup"><span data-stu-id="adaec-120">Microsoft.Extensions.Configuration.Binder</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|<span data-ttu-id="adaec-121">Suppression de la référence à `Microsoft.Extensions.Configuration`</span><span class="sxs-lookup"><span data-stu-id="adaec-121">Removed reference to `Microsoft.Extensions.Configuration`</span></span>|
|[<span data-ttu-id="adaec-122">Microsoft.Extensions.Configuration.Js</span><span class="sxs-lookup"><span data-stu-id="adaec-122">Microsoft.Extensions.Configuration.Json</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |<span data-ttu-id="adaec-123">Suppression de la référence à `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="adaec-123">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="adaec-124">Microsoft. extensions. Hosting. Abstracts</span><span class="sxs-lookup"><span data-stu-id="adaec-124">Microsoft.Extensions.Hosting.Abstractions</span></span>](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|<span data-ttu-id="adaec-125">Suppression de la référence à `Microsoft.Extensions.Logging.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="adaec-125">Removed reference to `Microsoft.Extensions.Logging.Abstractions`</span></span>|
|[<span data-ttu-id="adaec-126">Microsoft.Extensions.Logging</span><span class="sxs-lookup"><span data-stu-id="adaec-126">Microsoft.Extensions.Logging</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |<span data-ttu-id="adaec-127">Suppression de la référence à `Microsoft.Extensions.Configuration.Binder`</span><span class="sxs-lookup"><span data-stu-id="adaec-127">Removed reference to `Microsoft.Extensions.Configuration.Binder`</span></span>|
|[<span data-ttu-id="adaec-128">Microsoft. extensions. Logging. console</span><span class="sxs-lookup"><span data-stu-id="adaec-128">Microsoft.Extensions.Logging.Console</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |<span data-ttu-id="adaec-129">Suppression de la référence à `Microsoft.Extensions.Configuration.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="adaec-129">Removed reference to `Microsoft.Extensions.Configuration.Abstractions`</span></span>|
|[<span data-ttu-id="adaec-130">Microsoft. extensions. Logging. EventLog</span><span class="sxs-lookup"><span data-stu-id="adaec-130">Microsoft.Extensions.Logging.EventLog</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |<span data-ttu-id="adaec-131">Référence supprimée à `System.Diagnostics.EventLog` pour le moniker du Framework cible .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="adaec-131">Removed reference to `System.Diagnostics.EventLog` for the .NET Framework 4.6.1 target framework moniker</span></span>|
|[<span data-ttu-id="adaec-132">Microsoft. extensions. Logging. EventSource</span><span class="sxs-lookup"><span data-stu-id="adaec-132">Microsoft.Extensions.Logging.EventSource</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |<span data-ttu-id="adaec-133">Suppression de la référence à `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="adaec-133">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="adaec-134">Microsoft. extensions. options</span><span class="sxs-lookup"><span data-stu-id="adaec-134">Microsoft.Extensions.Options</span></span>](https://nuget.org/packages/Microsoft.Extensions.Options)                          |<span data-ttu-id="adaec-135">Suppression de la référence à `System.ComponentModel.Annotations`</span><span class="sxs-lookup"><span data-stu-id="adaec-135">Removed reference to `System.ComponentModel.Annotations`</span></span>|

<span data-ttu-id="adaec-136">Par exemple, la référence de package à `Microsoft.Extensions.Configuration` a été supprimée de `Microsoft.Extensions.Configuration.Binder` .</span><span class="sxs-lookup"><span data-stu-id="adaec-136">For example, the package reference to `Microsoft.Extensions.Configuration` was removed from `Microsoft.Extensions.Configuration.Binder`.</span></span> <span data-ttu-id="adaec-137">Aucune API de la dépendance n’a été utilisée dans le package.</span><span class="sxs-lookup"><span data-stu-id="adaec-137">No API from the dependency was used in the package.</span></span> <span data-ttu-id="adaec-138">Les utilisateurs de `Microsoft.Extensions.Configuration.Binder` qui dépendent des API de `Microsoft.Extensions.Configuration` doivent ajouter une référence directe à celui-ci dans leur projet.</span><span class="sxs-lookup"><span data-stu-id="adaec-138">Users of `Microsoft.Extensions.Configuration.Binder` who depend on APIs from `Microsoft.Extensions.Configuration` should add a direct reference to it in their project.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="adaec-139">API affectées</span><span class="sxs-lookup"><span data-stu-id="adaec-139">Affected APIs</span></span>

<span data-ttu-id="adaec-140">None</span><span class="sxs-lookup"><span data-stu-id="adaec-140">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
