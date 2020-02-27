---
title: 'Table de décision : versions de .NET Framework à utiliser pour Docker'
description: Architecture de microservices .NET pour les applications .NET en conteneur | Table de décision, versions de .NET Framework à utiliser pour Docker
ms.date: 09/11/2018
ms.openlocfilehash: 8ffe2b7bc0bee976d3a63b274994dbcc8aef0c61
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628317"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Table de décision : versions de .NET Framework à utiliser pour Docker

La table de décision ci-dessous vous indique s’il convient d’utiliser .NET Framework ou .NET Core. N’oubliez pas que pour les conteneurs Linux, vous avez besoin d’hôtes Docker basés sur Linux (machines virtuelles ou serveurs) et que pour les conteneurs Windows, vous avez besoin d’hôtes Docker basés sur Windows Server (machines virtuelles ou serveurs).

> [!IMPORTANT]
> Vos machines de développement exécuteront un hôte Docker, Linux ou Windows. Les microservices connexes que vous souhaitez exécuter et tester ensemble dans une solution devront tous s’exécuter sur la même plateforme de conteneur.

| Architecture/type d’application | Conteneurs Linux | Conteneurs Windows |
|-------------------------|------------------|--------------------|
| Microservices sur des conteneurs | .NET Core | .NET Core |
| Application monolithique | .NET Core | .NET Framework <br/> .NET Core |
| Performances et scalabilité de pointe | .NET Core | .NET Core |
| Migration d’application existante Windows Server (« brown-field ») vers des conteneurs | -- | .NET Framework |
| Développement basé sur un nouveau conteneur (« green-field ») | .NET Core | .NET Core |
| ASP.NET Core | .NET Core | .NET Core (recommandé) <br/> .NET Framework |
| ASP.NET 4 (MVC 5, API web 2 et Web Forms) | -- | .NET Framework |
| Services SignalR | .NET Core 2.1 ou version ultérieure | .NET Framework <br/> .NET Core 2.1 ou version ultérieure |
| WCF, WF et autres frameworks existants | WCF dans .NET Core (bibliothèque cliente uniquement) | .NET Framework <br/> WCF dans .NET Core (bibliothèque cliente uniquement) |
| Consommation des services Azure | .NET Core <br/> (enfin, la plupart des services Azure fourniront des kits de développement logiciel client pour .NET Core) | .NET Framework <br/> .NET Core <br/> (enfin, la plupart des services Azure fourniront des kits de développement logiciel client pour .NET Core) |

>[!div class="step-by-step"]
>[Précédent](net-framework-container-scenarios.md)
>[Suivant](net-container-os-targets.md)
