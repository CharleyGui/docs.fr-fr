---
title: Couper les applications autonomes
description: Apprenez à couper les applications autonomes pour réduire leur taille. .NET Core regroupe l’heure d’exécution avec une application qui est publiée autonome et inclut généralement plus de l’exécution alors est nécessaire.
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665634"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="fa3da-104">Couper les déploiements autonomes et les exécutables</span><span class="sxs-lookup"><span data-stu-id="fa3da-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="fa3da-105">Lors de la publication d’une application autonome, le temps d’exécution .NET Core est regroupé avec l’application.</span><span class="sxs-lookup"><span data-stu-id="fa3da-105">When publishing an application self-contained, the .NET Core runtime is bundled together with the application.</span></span> <span data-ttu-id="fa3da-106">Ce regroupement ajoute une quantité importante de contenu à votre application emballée.</span><span class="sxs-lookup"><span data-stu-id="fa3da-106">This bundling adds a significant amount of content to your packaged application.</span></span>

<span data-ttu-id="fa3da-107">Lorsqu’il s’agit de déployer votre application, la taille est souvent un facteur important.</span><span class="sxs-lookup"><span data-stu-id="fa3da-107">When it comes to deploying your application, size is often an important factor.</span></span> <span data-ttu-id="fa3da-108">Garder la taille de l’application de paquet aussi petite que possible est généralement un objectif pour les développeurs d’applications.</span><span class="sxs-lookup"><span data-stu-id="fa3da-108">Keeping the size of the package application as small as possible is typically a goal for application developers.</span></span>

<span data-ttu-id="fa3da-109">Selon la complexité de l’application, seul un sous-ensemble de l’exécution est nécessaire pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="fa3da-109">Depending on the complexity of the application, only a subset of the runtime is required to run the application.</span></span> <span data-ttu-id="fa3da-110">Ces parties inutilisées du temps d’exécution ne sont pas nécessaires et peuvent être extraites de l’application emballée.</span><span class="sxs-lookup"><span data-stu-id="fa3da-110">These unused parts of the runtime are unnecessary and can be trimmed from the packaged application.</span></span>

> [!NOTE]
> <span data-ttu-id="fa3da-111">Le rognage est une fonctionnalité expérimentale dans .NET Core 3.1 et _n’est_ disponible que pour les applications qui sont publiées autonomes.</span><span class="sxs-lookup"><span data-stu-id="fa3da-111">Trimming is an experimental feature in .NET Core 3.1 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="trim-your-application"></a><span data-ttu-id="fa3da-112">Coupez votre demande</span><span class="sxs-lookup"><span data-stu-id="fa3da-112">Trim your application</span></span>

<span data-ttu-id="fa3da-113">L’exemple suivant montre comment couper votre application à l’aide de la commande [de publication dotnet](../tools/dotnet-publish.md) :</span><span class="sxs-lookup"><span data-stu-id="fa3da-113">The following example shows how to trim your application using the [dotnet publish](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

<span data-ttu-id="fa3da-114">La fonction de coupe fonctionne en examinant les binaires d’application pour découvrir et construire un graphique des assemblages de temps d’exécution requis.</span><span class="sxs-lookup"><span data-stu-id="fa3da-114">The trimming feature works by examining the application binaries to discover and build a graph of the required runtime assemblies.</span></span> <span data-ttu-id="fa3da-115">Les assemblages de temps d’exécution restants qui ne sont pas référencés sont coupés.</span><span class="sxs-lookup"><span data-stu-id="fa3da-115">The remaining runtime assemblies that aren't referenced are trimmed.</span></span>

## <a name="trimming-issues-when-using-reflection"></a><span data-ttu-id="fa3da-116">Réduire les problèmes lors de l’utilisation de la réflexion</span><span class="sxs-lookup"><span data-stu-id="fa3da-116">Trimming issues when using reflection</span></span>

<span data-ttu-id="fa3da-117">Il existe des scénarios dans lesquels la fonctionnalité de coupe ne détectera pas les références.</span><span class="sxs-lookup"><span data-stu-id="fa3da-117">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="fa3da-118">Par exemple, une application qui utilise la réflexion pourrait se heurter à cette question parce que la dépendance à l’égard de l’assemblage ne sera connue qu’à l’heure de fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="fa3da-118">For example, an application that uses reflection could run into this issue because the dependency on the assembly will only be known at run time.</span></span>

<span data-ttu-id="fa3da-119">Le rognage n’est qu’un problème si l’utilisation de la réflexion dépend d’un assemblage de temps d’exécution qui n’est pas référencé directement.</span><span class="sxs-lookup"><span data-stu-id="fa3da-119">Trimming is only a problem if the reflection usage depends on a runtime assembly that isn't referenced directly.</span></span> <span data-ttu-id="fa3da-120">Gardez à l’esprit que votre code d’application peut ne pas utiliser la réflexion directement, mais un assemblage tiers que vous faites référence peut l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="fa3da-120">Keep in mind that your application code may not be using reflection directly, but a third-party assembly you're referencing may be using it.</span></span>

<span data-ttu-id="fa3da-121">Lorsque le code fait référence à une API par la réflexion et que vous ne souhaitez pas que le lien pour couper l’assemblage qui contient cette API, vous pouvez modifier votre fichier de projet pour exclure l’assemblage du processus de coupe.</span><span class="sxs-lookup"><span data-stu-id="fa3da-121">When the code is referencing an API through reflection and you don't want the linker to trim the assembly that contains that API, you can modify your project file to exclude the assembly from the trimming process.</span></span> <span data-ttu-id="fa3da-122">L’exemple suivant montre comment `System.Security` empêcher qu’un assemblage appelé ne soit coupé :</span><span class="sxs-lookup"><span data-stu-id="fa3da-122">The following example shows how to prevent an assembly called `System.Security` from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a><span data-ttu-id="fa3da-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa3da-123">See also</span></span>

- [<span data-ttu-id="fa3da-124">.NET Déploiement d’applications de base</span><span class="sxs-lookup"><span data-stu-id="fa3da-124">.NET Core application deployment</span></span>](index.md)
