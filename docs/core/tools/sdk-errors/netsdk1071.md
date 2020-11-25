---
title: "NETSDK1071 : PackageReference à' {0} 'a spécifié une version de `{1}` ."
description: Comment résoudre le problème d’un PackageReference sur un sous-package inclus avec une version de l’infrastructure.
author: Forgind
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1071
ms.openlocfilehash: 1381fc63941ec04efb31035d13913620a195c236
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713078"
---
# <a name="netsdk1071-explicitly-versioned-packagereference-to-a-metapackage-that-would-be-included-with-the-framework"></a><span data-ttu-id="8bd3a-103">NETSDK1071 : PackageReference avec version explicite vers un repackage qui serait inclus dans le Framework.</span><span class="sxs-lookup"><span data-stu-id="8bd3a-103">NETSDK1071: Explicitly versioned PackageReference to a metapackage that would be included with the framework.</span></span>

<span data-ttu-id="8bd3a-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net 5.0.100 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="8bd3a-104">**This article applies to:** ✔️ .NET 5.0.100 SDK and later versions</span></span>

<span data-ttu-id="8bd3a-105">Lorsque le kit de développement logiciel (SDK) .NET émet un avertissement NETSDK1071, il peut y avoir un conflit de version entre la version d’un PackageReference spécifié dans un et la version de ce dernier, comme référencé implicitement via une propriété TargetFramework :</span><span class="sxs-lookup"><span data-stu-id="8bd3a-105">When the .NET SDK issues warning NETSDK1071, it suggests there may be a version conflict in the future between the version of a metapackage specified in a PackageReference and the version of that metapackage as implicitly referenced via a TargetFramework property:</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="8bd3a-106">Dans la mesure où la « TargetFramework » insère automatiquement une version du produit, les versions sont en conflit si elles diffèrent.</span><span class="sxs-lookup"><span data-stu-id="8bd3a-106">Since the TargetFramework automatically brings in a version of the metapackage, the versions will conflict should they ever differ.</span></span>

<span data-ttu-id="8bd3a-107">Pour résoudre ce problème :</span><span class="sxs-lookup"><span data-stu-id="8bd3a-107">To resolve this:</span></span>

1. <span data-ttu-id="8bd3a-108">Envisagez, quand vous ciblez .NET Core ou .NET Standard, d’éviter les références explicites à `Microsoft.NETCore.App` ou `NETStandard.Library` dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="8bd3a-108">Consider, when targeting .NET Core or .NET Standard, avoiding explicit references to `Microsoft.NETCore.App` or `NETStandard.Library` in your project file.</span></span>
2. <span data-ttu-id="8bd3a-109">Si vous avez besoin d’une version spécifique du runtime lorsque vous ciblez .NET Core, utilisez la `<RuntimeFrameworkVersion>` propriété au lieu de référencer directement le repackage.</span><span class="sxs-lookup"><span data-stu-id="8bd3a-109">If you need a specific version of the runtime when targeting .NET Core, use the `<RuntimeFrameworkVersion>`property instead of referencing the metapackage directly.</span></span> <span data-ttu-id="8bd3a-110">Par exemple, cela peut se produire si vous utilisez des [déploiements autonomes](../../deploying/index.md#publish-self-contained) et que vous avez besoin d’un correctif spécifique du runtime LTS 1.0.0.</span><span class="sxs-lookup"><span data-stu-id="8bd3a-110">As an example, this could happen if you're using [self-contained deployments](../../deploying/index.md#publish-self-contained) and need a specific patch of the 1.0.0 LTS runtime.</span></span>
3. <span data-ttu-id="8bd3a-111">Si vous avez besoin d’une version spécifique de `NetStandard.Library` lorsque vous ciblez .NET standard, vous pouvez utiliser la `<NetStandardImplicitPackageVersion>` propriété et la définir sur la version dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="8bd3a-111">If you need a specific version of `NetStandard.Library` when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set it to the version you need.</span></span>
4. <span data-ttu-id="8bd3a-112">N’ajoutez pas ou ne mettez pas à jour explicitement des références à `Microsoft.NETCore.App` ou `NETSTandard.Library` dans des projets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8bd3a-112">Don't explicitly add or update references to either `Microsoft.NETCore.App` or `NETSTandard.Library` in .NET Framework projects.</span></span> <span data-ttu-id="8bd3a-113">NuGet installe automatiquement toute version de dont `NETStandard.Library` vous avez besoin lors de l’utilisation d’un package NuGet .NET standard.</span><span class="sxs-lookup"><span data-stu-id="8bd3a-113">NuGet automatically installs any version of `NETStandard.Library` you need when using a .NET Standard-based NuGet package.</span></span>
5. <span data-ttu-id="8bd3a-114">Ne spécifiez pas de version pour `Microsoft.AspNetCore.App` ou `Microsoft.AspNetCore.All` lors de l’utilisation de .net Core 2.1 +, car le kit SDK .net Core sélectionne automatiquement la version appropriée.</span><span class="sxs-lookup"><span data-stu-id="8bd3a-114">Do not specify a version for `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` when using .NET Core 2.1+, as the .NET Core SDK automatically selects the appropriate version.</span></span> <span data-ttu-id="8bd3a-115">(Remarque : cela fonctionne uniquement quand vous ciblez .NET Core 2,1 si le projet utilise également `Microsoft.NET.Sdk.Web` .</span><span class="sxs-lookup"><span data-stu-id="8bd3a-115">(Note: This only works when targeting .NET Core 2.1 if the project also uses `Microsoft.NET.Sdk.Web`.</span></span> <span data-ttu-id="8bd3a-116">Ce problème a été résolu dans le kit de développement logiciel (SDK) .NET Core 2,2.)</span><span class="sxs-lookup"><span data-stu-id="8bd3a-116">This problem was resolved in the .NET Core 2.2 SDK.)</span></span>
6. <span data-ttu-id="8bd3a-117">Si vous souhaitez que l’avertissement disparaissent, vous pouvez également le désactiver :</span><span class="sxs-lookup"><span data-stu-id="8bd3a-117">If you want the warning to go away, you can also disable it:</span></span>

   ```xml
   <PackageReference Include="Microsoft.NetCore.App" Version="2.2.8" >
     <AllowExplicitVersion>true</AllowExplicitVersion>
   </PackageReference>
   ```
