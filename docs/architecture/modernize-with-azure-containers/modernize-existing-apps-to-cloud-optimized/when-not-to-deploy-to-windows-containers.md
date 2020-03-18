---
title: Quand ne pas déployer sur des conteneurs Windows
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Lorsque vous ne devez pas vous déployer dans les conteneurs Windows
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577952"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Quand ne pas déployer sur des conteneurs Windows

Certaines technologies Windows ne sont pas prises en charge par Windows Containers. Dans ces cas, vous devez toujours migrer vers des magnétoscopes standards, généralement avec uniquement Windows et IIS.

Cas non pris en charge dans windows Containers, en mai 2018 :

- Microsoft Message Queuing (MSMQ) n’est actuellement disponible que dans les conteneurs Windows en fonction de windows Server v1803 version, mais pas dans toute autre version antérieure.

  - [Forum de demande UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Forum de discussion](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Microsoft Distributed Transaction Coordinator (MSDTC) n’est actuellement pas pris en charge dans windows Containers.

  - [Numéro GitHub](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Microsoft Office ne prend actuellement pas en charge les conteneurs.

  - [Forum de demande UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- Les applications d’interface utilisateur (applications client avec une interface utilisateur visuelle) ne sont pas des scénarios pris en charge.

- Les rôles d’infrastructure Windows (DNS, DHCP, DC, NTP, PRINT, serveur de fichiers, IAM, etc.) ne sont pas des scénarios pris en charge.

Pour d’autres scénarios et demandes non pris en charge par la <https://windowsserver.uservoice.com/forums/304624-containers>communauté, consultez le forum UserVoice pour les conteneurs Windows : .

### <a name="additional-resources"></a>Ressources supplémentaires

- **Machines et conteneurs virtuels en Azure**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Suivant précédent](deploy-existing-net-apps-as-windows-containers.md)
> [Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
