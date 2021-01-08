---
title: Quand ne pas déployer sur des conteneurs Windows
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Quand ne pas déployer sur des conteneurs Windows
ms.date: 12/21/2020
ms.openlocfilehash: 4eea24ab8deb3719c778b45b3ddc1309277a3f50
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025171"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Quand ne pas déployer sur des conteneurs Windows

Certaines technologies Windows ne sont pas prises en charge par les conteneurs Windows. Dans ce cas, vous devez toujours migrer vers les machines virtuelles de normalisation, généralement avec uniquement Windows et IIS.

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

Pour d’autres scénarios et demandes non pris en charge à partir de la Communauté, consultez le Forum UserVoice pour les conteneurs Windows : <https://windowsserver.uservoice.com/forums/304624-containers> .

### <a name="additional-resources"></a>Ressources supplémentaires

- **Machines virtuelles et conteneurs dans Azure**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Précédent](deploy-existing-net-apps-as-windows-containers.md) 
>  [Suivant](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
