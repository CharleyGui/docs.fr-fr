---
title: Quand ne pas déployer sur des conteneurs Windows
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Quand ne pas déployer sur des conteneurs Windows
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "69577952"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Quand ne pas déployer sur des conteneurs Windows

Certaines technologies Windows ne sont pas prises en charge par les conteneurs Windows. Dans ce cas, vous devez toujours migrer vers des machines virtuelles standard, généralement avec Windows et IIS uniquement.

Les cas non pris en charge dans les conteneurs Windows, à compter du 2018 mai :

- Microsoft Message Queuing (MSMQ) est actuellement disponible uniquement dans les conteneurs Windows basés sur Windows Server v1803 version, mais pas dans les versions antérieures.

  - [Forum de demande UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Forum de discussion](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Actuellement, Microsoft Distributed Transaction Coordinator (MSDTC) n’est pas pris en charge dans les conteneurs Windows.

  - [Problème GitHub](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Microsoft Office ne prend actuellement pas en charge les conteneurs.

  - [Forum de demande UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- Les applications d’interface utilisateur (applications clientes avec une interface utilisateur visuelle) ne sont pas des scénarios pris en charge.

- Les rôles d’infrastructure Windows (DNS, DHCP, DC, NTP, impression, serveur de fichiers, IAM, etc.) ne sont pas des scénarios pris en charge.

Pour obtenir des scénarios et des demandes supplémentaires non pris en charge par la Communauté, consultez le Forum UserVoice pour les conteneurs Windows : <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Machines virtuelles et conteneurs dans Azure**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Précédent](deploy-existing-net-apps-as-windows-containers.md)
> [Suivant](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
