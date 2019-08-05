---
title: Quel système d’exploitation cibler avec les conteneurs .NET
description: Architecture de microservices .NET pour les applications .NET en conteneur | Quel système d’exploitation cibler avec les conteneurs .NET
ms.date: 01/07/2019
ms.openlocfilehash: 6f160aeba5257722490788271e6f89359342cc0d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675756"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="78c89-103">Quel système d’exploitation cibler avec les conteneurs .NET</span><span class="sxs-lookup"><span data-stu-id="78c89-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="78c89-104">Compte tenu de la diversité des systèmes d’exploitation pris en charge par Docker et des différences entre .NET Framework et .NET Core, vous avez tout intérêt à cibler le système d’exploitation et la version en fonction du framework que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="78c89-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="78c89-105">Pour Windows, vous pouvez utiliser Windows Server Core ou Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="78c89-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="78c89-106">Ces versions de Windows offrent des caractéristiques différentes (IIS dans Windows Server Core et un serveur web auto-hébergé comme Kestrel dans Nano Server) qui peuvent être nécessaires à .NET Framework ou .NET Core, respectivement.</span><span class="sxs-lookup"><span data-stu-id="78c89-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span>

<span data-ttu-id="78c89-107">Pour Linux, plusieurs distributions sont disponibles et prises en charge dans les images .NET Docker officielles (comme Debian).</span><span class="sxs-lookup"><span data-stu-id="78c89-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="78c89-108">La figure 3-1 indique la version du système d’exploitation à utiliser en fonction de la version du .NET Framework utilisée.</span><span class="sxs-lookup"><span data-stu-id="78c89-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![Lorsque vous déployez des applications .NET Framework héritées, vous devez cibler Windows Server Core, compatible avec les applications héritées et IIS, dont l’image est plus grande.](./media/image1.png)

<span data-ttu-id="78c89-113">**Figure 3-1** :</span><span class="sxs-lookup"><span data-stu-id="78c89-113">**Figure 3-1.**</span></span> <span data-ttu-id="78c89-114">systèmes d’exploitation à cibler en fonction des versions de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="78c89-114">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="78c89-115">Vous pouvez aussi créer votre propre image Docker si souhaitez utiliser une autre distribution Linux ou une image contenant des versions non fournies par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="78c89-115">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="78c89-116">Par exemple, vous pouvez créer une image avec ASP.NET Core s’exécutant sur le .NET Framework classique et Windows Server Core, ce qui n’est pas un scénario très courant pour Docker.</span><span class="sxs-lookup"><span data-stu-id="78c89-116">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="78c89-117">Au moment d’ajouter le nom de l’image à votre fichier Dockerfile, vous pouvez sélectionner le système d’exploitation et la version en fonction de la balise que vous utilisez, comme dans les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="78c89-117">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="78c89-118">Image</span><span class="sxs-lookup"><span data-stu-id="78c89-118">Image</span></span></th>
<th><span data-ttu-id="78c89-119">Commentaires</span><span class="sxs-lookup"><span data-stu-id="78c89-119">Comments</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td><span data-ttu-id="78c89-120">mcr.microsoft.com/dotnet/core/runtime:2.2</span><span class="sxs-lookup"><span data-stu-id="78c89-120">mcr.microsoft.com/dotnet/core/runtime:2.2</span></span></td>
<td><span data-ttu-id="78c89-121">Multi-architecture .NET Core 2.2 : prend en charge Linux et Windows Nano Server en fonction de l’hôte Docker.</span><span class="sxs-lookup"><span data-stu-id="78c89-121">.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="78c89-122">mcr.microsoft.com/dotnet/core/aspnet:2.2</span><span class="sxs-lookup"><span data-stu-id="78c89-122">mcr.microsoft.com/dotnet/core/aspnet:2.2</span></span></td>
<td><p><span data-ttu-id="78c89-123">Multi-architecture ASP.NET Core 2.2 : prend en charge Linux et Windows Nano Server en fonction de l’hôte Docker.</span><span class="sxs-lookup"><span data-stu-id="78c89-123">ASP.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></p>
<p><span data-ttu-id="78c89-124">L’image aspnetcore a quelques optimisations pour ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="78c89-124">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="78c89-125">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span><span class="sxs-lookup"><span data-stu-id="78c89-125">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span></span></td>
<td><span data-ttu-id="78c89-126">Runtime .NET Core 2.2 uniquement sur la distribution Linux Alpine</span><span class="sxs-lookup"><span data-stu-id="78c89-126">.NET Core 2.2 runtime-only on Linux Alpine distro</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="78c89-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span><span class="sxs-lookup"><span data-stu-id="78c89-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span></span></td>
<td><span data-ttu-id="78c89-128">Runtime .NET Core 2.2 uniquement sur Windows Nano Server (Windows Server version 1803)</span><span class="sxs-lookup"><span data-stu-id="78c89-128">.NET Core 2.2 runtime-only on Windows Nano Server (Windows Server version 1803)</span></span></td>
</tr>
</tbody>
</table>

> [!div class="step-by-step"]
> <span data-ttu-id="78c89-129">[Précédent](container-framework-choice-factors.md)
> [Suivant](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="78c89-129">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
