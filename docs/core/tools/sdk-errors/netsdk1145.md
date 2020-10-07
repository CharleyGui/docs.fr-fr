---
title: 'NETSDK1145 : ciblage ou apphost Pack manquant'
description: Comment résoudre le problème de l’absence du Pack de ciblage pendant la restauration du package NuGet
author: wli3
ms.topic: error-reference
ms.date: 09/14/2020
f1_keywords:
- NETSDK1145
ms.openlocfilehash: c343952582cafb63eae388fd216769e6c67d4741
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805323"
---
# <a name="netsdk1145-targeting-or-apphost-pack-missing"></a><span data-ttu-id="3d7c9-103">NETSDK1145 : ciblage ou apphost Pack manquant</span><span class="sxs-lookup"><span data-stu-id="3d7c9-103">NETSDK1145: Targeting or apphost pack missing</span></span>

<span data-ttu-id="3d7c9-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net 5.0.100 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="3d7c9-104">**This article applies to:** ✔️ .NET 5.0.100 SDK and later versions</span></span>

<span data-ttu-id="3d7c9-105">Lorsque le kit de développement logiciel (SDK) .NET émet une erreur NETSDK1145, le Pack de ciblage ou apphost n’est pas installé et la restauration des packages NuGet n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3d7c9-105">When the .NET SDK issues error NETSDK1145, the targeting or apphost pack is not installed and NuGet package restore is not supported.</span></span> <span data-ttu-id="3d7c9-106">Cela est généralement dû à l’utilisation d’un kit de développement logiciel (SDK) plus récent que celui inclus dans Visual Studio pour les projets C++/CLI.</span><span class="sxs-lookup"><span data-stu-id="3d7c9-106">This is typically caused by having a newer SDK than the one included in Visual Studio for C++/CLI projects.</span></span> <span data-ttu-id="3d7c9-107">Mettez à niveau Visual Studio, supprimez _global.js_ si elle spécifie une certaine version du SDK et désinstallez le kit de développement logiciel (SDK) plus récent.</span><span class="sxs-lookup"><span data-stu-id="3d7c9-107">Upgrade Visual Studio, remove _global.json_ if it specifies a certain SDK version, and uninstall the newer SDK.</span></span> <span data-ttu-id="3d7c9-108">Vous pouvez également remplacer la version de ciblage ou de apphost.</span><span class="sxs-lookup"><span data-stu-id="3d7c9-108">Alternatively, you could override the targeting or apphost version.</span></span> <span data-ttu-id="3d7c9-109">Recherchez la version qui existe sous le répertoire Pack à partir du message d’erreur et qui correspond au Framework cible du projet.</span><span class="sxs-lookup"><span data-stu-id="3d7c9-109">Find the version that exists under the pack directory from the error message and matches the target framework of the project.</span></span> <span data-ttu-id="3d7c9-110">Ajoutez le code suivant au projet :</span><span class="sxs-lookup"><span data-stu-id="3d7c9-110">Add the following to the project:</span></span>

<span data-ttu-id="3d7c9-111">Pour apphost Pack</span><span class="sxs-lookup"><span data-stu-id="3d7c9-111">For apphost pack</span></span>

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```

<span data-ttu-id="3d7c9-112">Pour le Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="3d7c9-112">For targeting pack</span></span>

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```
