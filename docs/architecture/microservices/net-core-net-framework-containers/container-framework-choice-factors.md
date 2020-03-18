---
title: 'Table de décision : versions de .NET Framework à utiliser pour Docker'
description: Architecture de microservices .NET pour les applications .NET en conteneur | Table de décision, versions de .NET Framework à utiliser pour Docker
ms.date: 09/11/2018
ms.openlocfilehash: 8ffe2b7bc0bee976d3a63b274994dbcc8aef0c61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628317"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Table de décision : versions de .NET Framework à utiliser pour Docker

La table de décision ci-dessous vous indique s’il convient d’utiliser .NET Framework ou .NET Core. N’oubliez pas que pour les conteneurs Linux, vous avez besoin d’hôtes Docker basés sur Linux (machines virtuelles ou serveurs) et que pour les conteneurs Windows, vous avez besoin d’hôtes Docker basés sur Windows Server (machines virtuelles ou serveurs).

> [!IMPORTANT]
> Vos machines de développement exécuteront un hôte Docker, Linux ou Windows. Les microservices connexes que vous souhaitez exécuter et tester ensemble dans une solution devront tous s’exécuter sur la même plateforme de conteneur.

| Architecture / Type d’application | Conteneurs Linux | Conteneurs Windows |
|-------------------------|------------------|--------------------|
| Microservices sur des conteneurs | .NET Core | .NET Core |
| Application monolithique | .NET Core | .NET Framework <br/> .NET Core |
| Performances et scalabilité de pointe | .NET Core | .NET Core |
| Migration d’application existante Windows Server (« brown-field ») vers des conteneurs | -- | .NET Framework |
| Développement basé sur un nouveau conteneur (« green-field ») | .NET Core | .NET Core |
| ASP.NET Core | .NET Core | .NET Core (recommandé) <br/> .NET Framework |
| ASP.NET 4 (MVC 5, API web 2 et Web Forms) | -- | .NET Framework |
| Services SignalR | .NET Core 2.1 ou version ultérieure | .NET Framework <br/> .NET Core 2.1 ou version ultérieure |
| WCF, WF et autres frameworks existants | WCF en .NET Core (bibliothèque cliente seulement) | .NET Framework <br/> WCF en .NET Core (bibliothèque cliente seulement) |
| Consommation des services Azure | .NET Core <br/> (éventuellement, la plupart des services Azure fourniront des SDK clients pour .NET Core) | .NET Framework <br/> .NET Core <br/> (éventuellement, la plupart des services Azure fourniront des SDK clients pour .NET Core) |

>[!div class="step-by-step"]
>[Suivant précédent](net-framework-container-scenarios.md)
>[Next](net-container-os-targets.md)
