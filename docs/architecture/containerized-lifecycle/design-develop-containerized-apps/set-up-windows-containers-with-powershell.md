---
title: Utilisation de commandes Windows PowerShell dans un fichier DockerFile pour configurer des conteneurs Windows (basés sur le standard Docker)
description: Apprendre à se servir de PowerShell en utilisant Docker dans des conteneurs Windows
ms.date: 08/06/2020
ms.openlocfilehash: 4e7b9e7fedf11b97b3f468aef541bf72a4e88ebc
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915384"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>Utilisation de commandes Windows PowerShell dans un fichier DockerFile pour configurer des conteneurs Windows (basés sur le standard Docker)

Les [conteneurs Windows](/virtualization/windowscontainers/about/index) vous permettent de convertir vos applications Windows existantes en images Docker et de les déployer avec les mêmes outils que le reste de l’écosystème Docker.

Pour utiliser des conteneurs Windows, vous devez simplement écrire des commandes Windows PowerShell dans le fichier Dockerfile, comme dans l’exemple suivant :

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

Dans ce cas, nous nous servons de Windows PowerShell pour installer une image de base Windows Server Core, mais aussi d’IIS.

De la même façon, vous pouvez aussi utiliser des commandes Windows PowerShell pour configurer des composants supplémentaires comme les classiques ASP.NET 4.x et .NET 4.6 ou tout autre logiciel Windows, comme indiqué ici :

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[Précédent](visual-studio-tools-for-docker.md) 
> [Suivant](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
