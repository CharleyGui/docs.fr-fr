---
ms.openlocfilehash: 1ddc2cea19872b44ff9659bcebd76117587ea89a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159485"
---
### <a name="targetframework-change-from-netcoreapp-to-net"></a><span data-ttu-id="c5970-101">Modification de TargetFramework de netcoreapp en net</span><span class="sxs-lookup"><span data-stu-id="c5970-101">TargetFramework change from netcoreapp to net</span></span>

<span data-ttu-id="c5970-102">La valeur de la propriété MSBuild est `TargetFramework` passée de `netcoreapp3.1` à `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="c5970-102">The value for the MSBuild `TargetFramework` property changed from `netcoreapp3.1` to `net5.0`.</span></span> <span data-ttu-id="c5970-103">Cela peut interrompre le code qui s’appuie sur l’analyse de la valeur de `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="c5970-103">This can break code that relies on parsing the value of `TargetFramework`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c5970-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c5970-104">Version introduced</span></span>

<span data-ttu-id="c5970-105">5.0</span><span class="sxs-lookup"><span data-stu-id="c5970-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="c5970-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="c5970-106">Change description</span></span>

<span data-ttu-id="c5970-107">Dans .NET Core 1,0-3,1, la valeur de la `TargetFramework` propriété MSBuild commence par `netcoreapp` , par exemple, `netcoreapp3.1` pour les applications qui ciblent .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="c5970-107">In .NET Core 1.0 - 3.1, the value for the MSBuild `TargetFramework` property starts with `netcoreapp`, for example, `netcoreapp3.1` for apps that target .NET Core 3.1.</span></span> <span data-ttu-id="c5970-108">À compter de .NET 5,0, cette valeur est simplifiée pour commencer `net` , par exemple, pour `net5.0` .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="c5970-108">Starting in .NET 5.0, this value is simplified to just start with `net`, for example, `net5.0` for .NET 5.0.</span></span>

<span data-ttu-id="c5970-109">Pour plus d’informations, consultez [l’avenir des .NET standard et des noms de](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) [Framework cibles dans .net 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).</span><span class="sxs-lookup"><span data-stu-id="c5970-109">For more information, see [The future of .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) and [Target framework names in .NET 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c5970-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="c5970-110">Reason for change</span></span>

- <span data-ttu-id="c5970-111">Simplifie la `TargetFramework` valeur.</span><span class="sxs-lookup"><span data-stu-id="c5970-111">Simplifies the `TargetFramework` value.</span></span>
- <span data-ttu-id="c5970-112">Permet aux projets d’inclure un `TargetPlatform` dans la `TargetFramework` propriété.</span><span class="sxs-lookup"><span data-stu-id="c5970-112">Enables projects to include a `TargetPlatform` in the `TargetFramework` property.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c5970-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c5970-113">Recommended action</span></span>

<span data-ttu-id="c5970-114">Si vous avez une logique qui analyse la valeur de `TargetFramework` , vous devez la mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="c5970-114">If you have logic that parses the value of `TargetFramework`, you'll need to update it.</span></span> <span data-ttu-id="c5970-115">Par exemple, la condition MSBuild suivante s’appuie sur la valeur de `TargetFramework` .</span><span class="sxs-lookup"><span data-stu-id="c5970-115">For example, the following MSBuild condition relies on the value of `TargetFramework`.</span></span>

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

<span data-ttu-id="c5970-116">Pour cette exigence, vous pouvez mettre à jour le code pour comparer l’identificateur de Framework cible à la place.</span><span class="sxs-lookup"><span data-stu-id="c5970-116">For this requirement, you can update the code to compare the target framework identifier instead.</span></span>

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

#### <a name="category"></a><span data-ttu-id="c5970-117">Category</span><span class="sxs-lookup"><span data-stu-id="c5970-117">Category</span></span>

<span data-ttu-id="c5970-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="c5970-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c5970-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="c5970-119">Affected APIs</span></span>

<span data-ttu-id="c5970-120">N/A</span><span class="sxs-lookup"><span data-stu-id="c5970-120">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
