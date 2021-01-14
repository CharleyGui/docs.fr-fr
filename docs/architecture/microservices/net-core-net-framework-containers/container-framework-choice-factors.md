---
title: 'Table de décision : versions de .NET Framework à utiliser pour Docker'
description: Architecture de microservices .NET pour les applications .NET en conteneur | Table de décision, versions de .NET Framework à utiliser pour Docker
ms.date: 01/13/2021
ms.openlocfilehash: 35f101b3f4030e081068677b3754363bf6cd8210
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188658"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Table de décision : versions de .NET Framework à utiliser pour Docker

Le tableau de décision suivant indique s’il faut utiliser .NET Framework ou .NET 5. N’oubliez pas que pour les conteneurs Linux, vous avez besoin d’hôtes Docker basés sur Linux (machines virtuelles ou serveurs) et que pour les conteneurs Windows, vous avez besoin d’hôtes Docker basés sur Windows Server (machines virtuelles ou serveurs).

> [!IMPORTANT]
> Vos machines de développement exécuteront un hôte Docker, Linux ou Windows. Les microservices connexes que vous souhaitez exécuter et tester ensemble dans une solution devront tous s’exécuter sur la même plateforme de conteneur.

| Architecture / Type d’application | Conteneurs Linux | Conteneurs Windows |
|-------------------------|------------------|--------------------|
| Microservices sur des conteneurs | .NET 5 | .NET 5 |
| Application monolithique | .NET 5 | .NET Framework <br/> .NET 5 |
| Performances et scalabilité de pointe | .NET 5 | .NET 5 |
| Migration d’application existante Windows Server (« brown-field ») vers des conteneurs | -- | .NET Framework |
| Développement basé sur un nouveau conteneur (« green-field ») | .NET 5 | .NET 5 |
| ASP.NET Core | .NET 5 | .NET 5 (recommandé) <br/> .NET Framework |
| ASP.NET 4 (MVC 5, API web 2 et Web Forms) | -- | .NET Framework |
| Services SignalR | .NET Core 2.1 ou version ultérieure | .NET Framework <br/> .NET Core 2.1 ou version ultérieure |
| WCF, WF et autres frameworks existants | WCF dans .NET Core (bibliothèque cliente uniquement) | .NET Framework <br/> WCF dans .NET 5 (bibliothèque cliente uniquement) |
| Consommation des services Azure | .NET 5 <br/> (enfin, la plupart des services Azure fourniront des kits de développement logiciel client pour .NET 5) | .NET Framework <br/> .NET 5 <br/> (enfin, la plupart des services Azure fourniront des kits de développement logiciel client pour .NET 5) |

>[!div class="step-by-step"]
>[Précédent](net-framework-container-scenarios.md) 
> [Suivant](net-container-os-targets.md)
