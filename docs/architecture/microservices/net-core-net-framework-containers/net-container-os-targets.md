---
title: Quel système d’exploitation cibler avec les conteneurs .NET
description: Architecture de microservices .NET pour les applications .NET en conteneur | Quel système d’exploitation cibler avec les conteneurs .NET
ms.date: 01/30/2020
ms.openlocfilehash: a09e3981ece478a9795c0f27acc98d604864cdd5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501859"
---
# <a name="what-os-to-target-with-net-containers"></a>Quel système d’exploitation cibler avec les conteneurs .NET

Compte tenu de la diversité des systèmes d’exploitation pris en charge par Docker et des différences entre .NET Framework et .NET Core, vous avez tout intérêt à cibler le système d’exploitation et la version en fonction du framework que vous utilisez.

Pour Windows, vous pouvez utiliser Windows Server Core ou Windows Nano Server. Ces versions de Windows offrent des caractéristiques différentes (IIS dans Windows Server Core et un serveur web auto-hébergé comme Kestrel dans Nano Server) qui peuvent être nécessaires à .NET Framework ou .NET Core, respectivement.

Pour Linux, plusieurs distributions sont disponibles et prises en charge dans les images .NET Docker officielles (comme Debian).

La figure 3-1 indique la version du système d’exploitation à utiliser en fonction de la version du .NET Framework utilisée.

![Diagramme montrant ce qu’OS utiliser avec quels conteneurs .NET.](./media/net-container-os-targets/targeting-operating-systems.png)

**Figure 3-1.** systèmes d’exploitation à cibler en fonction des versions de .NET Framework

Lors du déploiement d’applications cadres .NET héritées, vous devez cibler Windows Server Core, compatible avec les applications existantes et IIS, mais il a une image plus grande. Lorsque vous déployez des applications .NET Core, vous pouvez cibler Windows Nano Server, optimisé pour le cloud, qui utilise Kestrel, est plus petit et démarre plus rapidement. Vous pouvez également cibler Linux, prenant en charge Debian, Alpine et d’autres. Utilise également Kestrel, est plus petit, et commence plus vite.

Vous pouvez aussi créer votre propre image Docker si souhaitez utiliser une autre distribution Linux ou une image contenant des versions non fournies par Microsoft. Par exemple, vous pouvez créer une image avec ASP.NET Core s’exécutant sur le .NET Framework classique et Windows Server Core, ce qui n’est pas un scénario très courant pour Docker.

> [!IMPORTANT]
> Lorsque vous utilisez des images Windows Server Core, vous pouvez constater que certains reflex sont manquants, par rapport aux images Windows complètes. Vous pourriez être en mesure de résoudre ce problème en créant une image personnalisée Server Core, en ajoutant les fichiers manquants au moment de la construction d’images, comme mentionné dans ce [commentaire GitHub](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).

Au moment d’ajouter le nom de l’image à votre fichier Dockerfile, vous pouvez sélectionner le système d’exploitation et la version en fonction de la balise que vous utilisez, comme dans les exemples suivants :

| Image | Commentaires |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:3.1 | .NET Core 3.1 multi-architecture: Prend en charge Linux et Windows Nano Server en fonction de l’hôte Docker. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1 | ASP.NET multi-architecture Core 3.1 : prend en charge Linux et Windows Nano Server en fonction de l’hôte Docker. <br/> L’image aspnetcore a quelques optimisations pour ASP.NET Core. |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim | .NET Core 3.1 runtime-seulement sur Linux Debian distro |
| mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1809 | .NET Core 3.1 runtime-only sur Windows Nano Server (version Windows Server 1809) |

## <a name="additional-resources"></a>Ressources supplémentaires

- **BitmapDecoder échoue en raison de la disparition de WindowsCodecsExt.dll (problème GitHub)**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [Suivant précédent](container-framework-choice-factors.md)
> [Next](official-net-docker-images.md)
