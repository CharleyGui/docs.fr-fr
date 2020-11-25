---
title: 'Modification avec rupture : la modification de TargetFramework de netcoreapp à net'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 où la valeur de la propriété de la propriété de la propriété MSBuild est passée de netcoreapp 3.1 à net 5.0.
ms.date: 10/17/2020
ms.openlocfilehash: c3b39a36548d58d6ed75fd8b1c84b0cccfc738f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760939"
---
# <a name="targetframework-change-from-netcoreapp-to-net"></a><span data-ttu-id="03dc0-103">Modification de TargetFramework de netcoreapp en net</span><span class="sxs-lookup"><span data-stu-id="03dc0-103">TargetFramework change from netcoreapp to net</span></span>

<span data-ttu-id="03dc0-104">La valeur de la propriété MSBuild est `TargetFramework` passée de `netcoreapp3.1` à `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="03dc0-104">The value for the MSBuild `TargetFramework` property changed from `netcoreapp3.1` to `net5.0`.</span></span> <span data-ttu-id="03dc0-105">Cela peut interrompre le code qui s’appuie sur l’analyse de la valeur de `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="03dc0-105">This can break code that relies on parsing the value of `TargetFramework`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="03dc0-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="03dc0-106">Version introduced</span></span>

<span data-ttu-id="03dc0-107">5.0</span><span class="sxs-lookup"><span data-stu-id="03dc0-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="03dc0-108">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="03dc0-108">Change description</span></span>

<span data-ttu-id="03dc0-109">Dans .NET Core 1,0-3,1, la valeur de la `TargetFramework` propriété MSBuild commence par `netcoreapp` , par exemple, `netcoreapp3.1` pour les applications qui ciblent .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="03dc0-109">In .NET Core 1.0 - 3.1, the value for the MSBuild `TargetFramework` property starts with `netcoreapp`, for example, `netcoreapp3.1` for apps that target .NET Core 3.1.</span></span> <span data-ttu-id="03dc0-110">À compter de .NET 5,0, cette valeur est simplifiée pour commencer `net` , par exemple, pour `net5.0` .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="03dc0-110">Starting in .NET 5.0, this value is simplified to just start with `net`, for example, `net5.0` for .NET 5.0.</span></span>

<span data-ttu-id="03dc0-111">Pour plus d’informations, consultez [l’avenir des .NET standard et des noms de](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) [Framework cibles dans .net 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).</span><span class="sxs-lookup"><span data-stu-id="03dc0-111">For more information, see [The future of .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) and [Target framework names in .NET 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="03dc0-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="03dc0-112">Reason for change</span></span>

- <span data-ttu-id="03dc0-113">Simplifie la `TargetFramework` valeur.</span><span class="sxs-lookup"><span data-stu-id="03dc0-113">Simplifies the `TargetFramework` value.</span></span>
- <span data-ttu-id="03dc0-114">Permet aux projets d’inclure un `TargetPlatform` dans la `TargetFramework` propriété.</span><span class="sxs-lookup"><span data-stu-id="03dc0-114">Enables projects to include a `TargetPlatform` in the `TargetFramework` property.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="03dc0-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="03dc0-115">Recommended action</span></span>

<span data-ttu-id="03dc0-116">Si vous avez une logique qui analyse la valeur de `TargetFramework` , vous devez la mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="03dc0-116">If you have logic that parses the value of `TargetFramework`, you'll need to update it.</span></span> <span data-ttu-id="03dc0-117">Par exemple, la condition MSBuild suivante s’appuie sur la valeur de `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="03dc0-117">For example, the following MSBuild condition relies on the value of `TargetFramework`.</span></span>

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

<span data-ttu-id="03dc0-118">Pour cette exigence, vous pouvez mettre à jour le code pour comparer l’identificateur de Framework cible à la place.</span><span class="sxs-lookup"><span data-stu-id="03dc0-118">For this requirement, you can update the code to compare the target framework identifier instead.</span></span>

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

## <a name="affected-apis"></a><span data-ttu-id="03dc0-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="03dc0-119">Affected APIs</span></span>

<span data-ttu-id="03dc0-120">N/A</span><span class="sxs-lookup"><span data-stu-id="03dc0-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
