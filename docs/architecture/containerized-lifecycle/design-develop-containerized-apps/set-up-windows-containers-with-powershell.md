---
title: Utilisation de commandes Windows PowerShell dans un fichier DockerFile pour configurer des conteneurs Windows (basés sur le standard Docker)
description: Apprendre à se servir de PowerShell en utilisant Docker dans des conteneurs Windows
ms.date: 08/06/2020
ms.openlocfilehash: 6096e4cbad4fb37b485d595c650dc10dc5ed5a22
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434809"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="915e3-103">Utilisation de commandes Windows PowerShell dans un fichier DockerFile pour configurer des conteneurs Windows (basés sur le standard Docker)</span><span class="sxs-lookup"><span data-stu-id="915e3-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="915e3-104">Les [conteneurs Windows](/virtualization/windowscontainers/about/index) vous permettent de convertir vos applications Windows existantes en images Docker et de les déployer avec les mêmes outils que le reste de l’écosystème Docker.</span><span class="sxs-lookup"><span data-stu-id="915e3-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="915e3-105">Pour utiliser des conteneurs Windows, vous devez simplement écrire des commandes Windows PowerShell dans le fichier Dockerfile, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="915e3-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```dockerfile
FROM mcr.microsoft.com/windows/servercore:ltsc2019
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="915e3-106">Dans ce cas, nous nous servons de Windows PowerShell pour installer une image de base Windows Server Core, mais aussi d’IIS.</span><span class="sxs-lookup"><span data-stu-id="915e3-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="915e3-107">De la même façon, vous pouvez aussi utiliser des commandes Windows PowerShell pour configurer des composants supplémentaires comme les classiques ASP.NET 4.x et .NET 4.6 ou tout autre logiciel Windows, comme indiqué ici :</span><span class="sxs-lookup"><span data-stu-id="915e3-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="915e3-108">[Précédent](visual-studio-tools-for-docker.md) 
> [Suivant](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="915e3-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
