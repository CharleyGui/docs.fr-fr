---
title: 'Table de décision : versions de .NET Framework à utiliser pour Docker'
description: Architecture de microservices .NET pour les applications .NET en conteneur | Table de décision, versions de .NET Framework à utiliser pour Docker
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675816"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Table de décision : versions de .NET Framework à utiliser pour Docker

La table de décision ci-dessous vous indique s’il convient d’utiliser .NET Framework ou .NET Core. N’oubliez pas que pour les conteneurs Linux, vous avez besoin d’hôtes Docker basés sur Linux (machines virtuelles ou serveurs) et que pour les conteneurs Windows, vous avez besoin d’hôtes Docker basés sur Windows Server (machines virtuelles ou serveurs).

> [!IMPORTANT]
> Vos machines de développement exécuteront un hôte Docker, Linux ou Windows. Les microservices connexes que vous souhaitez exécuter et tester ensemble dans une solution devront tous s’exécuter sur la même plateforme de conteneur.

<table>
<thead>
<tr class="header">
<th><strong>Architecture / Type d’application</strong></th>
<th><strong>Conteneurs Linux</strong></th>
<th><strong>Conteneurs Windows</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Microservices sur des conteneurs</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Application monolithique</td>
<td>.NET Core</td>
<td><p>.NET Framework</p>
<p>.NET Core</p></td>
</tr>
<tr class="odd">
<td>Performances et scalabilité de pointe</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Migration d’application existante Windows Server (« brown-field ») vers des conteneurs</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="odd">
<td>Développement basé sur un nouveau conteneur (« green-field »)</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>ASP.NET Core</td>
<td>.NET Core</td>
<td><p>.NET Core (recommandé)</p>
<p>.NET Framework</p></td>
</tr>
<tr class="odd">
<td>ASP.NET 4 (MVC 5, API web 2 et Web Forms)</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="even">
<td>Services SignalR</td>
<td>.NET Core 2.1 ou version ultérieure</td>
<td><p>.NET Framework</p>
<p>.NET Core 2.1 ou version ultérieure</p></td>
</tr>
<tr class="odd">
<td>WCF, WF et autres frameworks existants</td>
<td>WCF dans .NET Core (uniquement la bibliothèque cliente WCF)</td>
<td><p>.NET Framework</p>
<p>WCF dans .NET Core (uniquement la bibliothèque cliente WCF)</p></td>
</tr>
<tr class="even">
<td>Consommation des services Azure</td>
<td><p>.NET Core</p>
<p>(tous les services Azure fourniront les SDK clients pour .NET Core)</p></td>
<td><p>.NET Framework</p>
<p>.NET Core</p>
<p>(tous les services Azure fourniront les SDK clients pour .NET Core)</p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
>[Précédent](net-framework-container-scenarios.md)
>[Suivant](net-container-os-targets.md)
