---
title: Quel système d’exploitation cibler avec les conteneurs .NET
description: Architecture de microservices .NET pour les applications .NET en conteneur | Quel système d’exploitation cibler avec les conteneurs .NET
ms.date: 01/13/2021
ms.openlocfilehash: 1b914d9afca9ade37f13e639f73001b91f338d26
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187979"
---
# <a name="what-os-to-target-with-net-containers"></a>Quel système d’exploitation cibler avec les conteneurs .NET

Étant donné la diversité des systèmes d’exploitation pris en charge par l’arrimeur et les différences entre .NET Framework et .NET 5, vous devez cibler un système d’exploitation spécifique et des versions spécifiques en fonction de l’infrastructure que vous utilisez.

Pour Windows, vous pouvez utiliser Windows Server Core ou Windows Nano Server. Ces versions de Windows fournissent des caractéristiques différentes (IIS dans Windows Server Core par rapport à un serveur Web auto-hébergé comme Kestrel dans nano Server) qui peut être nécessaire par .NET Framework ou .NET 5, respectivement.

Pour Linux, plusieurs distributions sont disponibles et prises en charge dans les images .NET Docker officielles (comme Debian).

Dans la figure 3-1, vous pouvez voir la version du système d’exploitation possible en fonction du .NET Framework utilisé.

![Diagramme montrant le système d’exploitation à utiliser avec les conteneurs .NET.](./media/net-container-os-targets/targeting-operating-systems.png)

**Figure 3-1.** systèmes d’exploitation à cibler en fonction des versions de .NET Framework

Lors du déploiement d’applications .NET Framework héritées, vous devez cibler Windows Server Core, compatible avec les applications héritées et IIS, mais avec une image plus grande. Lors du déploiement d’applications .NET 5, vous pouvez cibler Windows nano Server, qui est optimisé pour le Cloud, utilise Kestrel et est plus petit et démarre plus rapidement. Vous pouvez également cibler Linux, en prenant en charge Debian, Alpine et d’autres. Utilise également Kestrel, est plus petit et démarre plus rapidement.

Vous pouvez aussi créer votre propre image Docker si souhaitez utiliser une autre distribution Linux ou une image contenant des versions non fournies par Microsoft. Par exemple, vous pouvez créer une image avec ASP.NET Core s’exécutant sur le .NET Framework classique et Windows Server Core, ce qui n’est pas un scénario très courant pour Docker.

> [!IMPORTANT]
> Lorsque vous utilisez des images Windows Server Core, vous pouvez constater que certaines dll sont manquantes, par rapport aux images Windows complètes. Vous pouvez peut-être résoudre ce problème en créant une image Server Core personnalisée, en ajoutant les fichiers manquants au moment de la génération de l’image, comme indiqué dans ce [Commentaire GitHub](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).

Au moment d’ajouter le nom de l’image à votre fichier Dockerfile, vous pouvez sélectionner le système d’exploitation et la version en fonction de la balise que vous utilisez, comme dans les exemples suivants :

| Image | Commentaires |
|-------|----------|
| mcr.microsoft.com/dotnet/runtime:5.0 | Architecture multi-architecture de .NET 5 : prend en charge Linux et Windows nano Server en fonction de l’hôte de l’ordinateur de la station d’accueil. |
| mcr.microsoft.com/dotnet/aspnet:5.0 | Architecture multi-architecture ASP.NET Core 5,0 : prend en charge Linux et Windows nano Server en fonction de l’hôte de l’ordinateur de la station d’accueil. <br/> L’image aspnetcore a quelques optimisations pour ASP.NET Core. |
| mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim | Runtime .NET 5 uniquement sur Linux Debian distribution |
| mcr.microsoft.com/dotnet/aspnet:5.0-nanoserver-1809 | Runtime .NET 5 uniquement sur Windows nano Server (Windows Server version 1809) |

## <a name="additional-resources"></a>Ressources supplémentaires

- **BitmapDecoder échoue en raison d’un WindowsCodecsExt.dll manquant (problème GitHub)**  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> [Précédent](container-framework-choice-factors.md) 
>  [Suivant](official-net-docker-images.md)
