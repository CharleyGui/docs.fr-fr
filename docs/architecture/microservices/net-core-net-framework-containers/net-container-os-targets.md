---
title: Quel système d’exploitation cibler avec les conteneurs .NET
description: Architecture de microservices .NET pour les applications .NET en conteneur | Quel système d’exploitation cibler avec les conteneurs .NET
ms.date: 01/07/2019
ms.openlocfilehash: 8bcfa0212f84c575a63f76e05edec1e511cadc36
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772002"
---
# <a name="what-os-to-target-with-net-containers"></a>Quel système d’exploitation cibler avec les conteneurs .NET

Compte tenu de la diversité des systèmes d’exploitation pris en charge par Docker et des différences entre .NET Framework et .NET Core, vous avez tout intérêt à cibler le système d’exploitation et la version en fonction du framework que vous utilisez.

Pour Windows, vous pouvez utiliser Windows Server Core ou Windows Nano Server. Ces versions de Windows offrent des caractéristiques différentes (IIS dans Windows Server Core et un serveur web auto-hébergé comme Kestrel dans Nano Server) qui peuvent être nécessaires à .NET Framework ou .NET Core, respectivement.

Pour Linux, plusieurs distributions sont disponibles et prises en charge dans les images .NET Docker officielles (comme Debian).

La figure 3-1 indique la version du système d’exploitation à utiliser en fonction de la version du .NET Framework utilisée.

![Lorsque vous déployez des applications .NET Framework héritées, vous devez cibler Windows Server Core, compatible avec les applications héritées et IIS, dont l’image est plus grande. Lorsque vous déployez des applications .NET Core, vous pouvez cibler Windows Nano Server, optimisé pour le cloud, qui utilise Kestrel, est plus petit et démarre plus rapidement. Vous pouvez également cibler Linux, prenant en charge Debian, Alpine et d’autres. Utilise également Kestrel, est plus petit et démarre plus rapidement.](./media/image1.png)

**Figure 3-1** : systèmes d’exploitation à cibler en fonction des versions de .NET Framework

Vous pouvez aussi créer votre propre image Docker si souhaitez utiliser une autre distribution Linux ou une image contenant des versions non fournies par Microsoft. Par exemple, vous pouvez créer une image avec ASP.NET Core s’exécutant sur le .NET Framework classique et Windows Server Core, ce qui n’est pas un scénario très courant pour Docker.

> [!IMPORTANT]
> Lorsque vous utilisez des images Windows Server Core, vous pouvez constater que certaines dll sont manquantes, par rapport aux images Windows complètes. Vous pouvez peut-être résoudre ce problème en créant une image Server Core personnalisée, en ajoutant les fichiers manquants au moment de la génération de l’image, comme indiqué dans ce [Commentaire GitHub](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).

Au moment d’ajouter le nom de l’image à votre fichier Dockerfile, vous pouvez sélectionner le système d’exploitation et la version en fonction de la balise que vous utilisez, comme dans les exemples suivants :

| Image | Comments |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:2.2 | Architecture multi-architecture .NET Core 2,2 : prend en charge Linux et Windows nano Server en fonction de l’hôte de la station d’accueil. |
| mcr.microsoft.com/dotnet/core/aspnet:2.2 | Architecture multi-architecture ASP.NET Core 2,2 : prend en charge Linux et Windows nano Server en fonction de l’hôte de l’ordinateur de la station d’accueil. <br/> L’image aspnetcore a quelques optimisations pour ASP.NET Core. |
| mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine | Runtime .NET Core 2.2 uniquement sur la distribution Linux Alpine |
| mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803 | Runtime .NET Core 2.2 uniquement sur Windows Nano Server (Windows Server version 1803) |

## <a name="additional-resources"></a>Ressources supplémentaires

- **BitmapDecoder échoue en raison de l’absence de WindowsCodecsExt. dll (problème GitHub)**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [Précédent](container-framework-choice-factors.md)
> [Suivant](official-net-docker-images.md)
