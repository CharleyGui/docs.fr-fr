---
title: Quand déployer des conteneurs Windows sur des machines virtuelles Azure (cloud IaaS)
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Quand déployer des conteneurs Windows sur les VM Azure (nuage IaaS)
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577902"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Quand déployer des conteneurs Windows sur des machines virtuelles Azure (cloud IaaS)

Si votre organisation utilise des VM Azure, même si vous utilisez également des conteneurs Windows, vous avez toujours affaire à IaaS. Cela signifie que le traitement des opérations d’infrastructure, des correctifs VM OS et de la complexité de l’infrastructure pour les applications hautement évolutives lorsque vous avez besoin de déployer à plusieurs machines virtuelles dans une infrastructure équilibrée de charge. Les principaux scénarios d’utilisation des conteneurs Windows dans un VM Azure sont les :

- **Environnement de développement/test**: Un VM dans le nuage est parfait pour le développement et les tests dans le cloud. Vous pouvez rapidement créer ou arrêter l’environnement en fonction de vos besoins.

- **Besoins d’évolutivité des petites et moyennes**années : Dans les scénarios où vous pourriez avoir besoin de quelques VM pour votre environnement de production, la gestion d’un petit nombre de VM pourrait être abordable jusqu’à ce que vous puissiez passer à des environnements PaaS plus avancés, comme des orchestrateurs.

- **Environnement de production avec outils**de déploiement existants : Vous vous déplacez peut-être d’un environnement sur site dans lequel vous avez investi dans des outils pour effectuer des déploiements complexes vers des VM ou des serveurs en métal nu (comme des marionnettes ou des outils similaires). Pour passer au cloud avec un minimum de modifications des procédures de déploiement de l’environnement de production, vous pouvez continuer à utiliser ces outils pour vous déployer dans les VM Azure. Toutefois, vous voudrez utiliser Windows Containers comme unité de déploiement pour améliorer l’expérience de déploiement.

>[!div class="step-by-step"]
>[Suivant précédent](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[Next](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
