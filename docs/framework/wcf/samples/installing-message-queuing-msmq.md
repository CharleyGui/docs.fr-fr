---
title: Installation de Message Queuing (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 1bf79ed5dbcb9f2ace903260cc440e77df3aef09
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592292"
---
# <a name="installing-message-queuing-msmq"></a>Installation de Message Queuing (MSMQ)
Les procédures suivantes indiquent comment installer Message Queuing 4.0 et Message Queuing 3.0.  
  
> [!NOTE]
> Message Queuing 4,0 n’est pas disponible dans Windows XP et Windows Server 2003.  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>Pour installer Message Queuing 4.0 sur Windows Server 2008 ou Windows Server 2008 R2  
  
1. Dans Gestionnaire de serveur, cliquez sur **fonctionnalités**.  
  
2. Dans le volet de droite, sous **Résumé des fonctionnalités**, cliquez sur **Ajouter des fonctionnalités**.  
  
3. Dans la fenêtre qui s’affiche, développez **Message Queuing**.  
  
4. Développez **Services Message Queuing**.  
  
5. Cliquez sur **intégration des services d’annuaire** (pour les ordinateurs joints à un domaine), puis cliquez sur **prise en charge http**.  
  
6. Cliquez sur **suivant**, puis sur **installer**.  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>Pour installer Message Queuing 4.0 sur Windows 7 ou Windows Vista  
  
1. Ouvrez le **Panneau de configuration**.  
  
2. Cliquez sur **programmes** puis, sous **programmes et fonctionnalités**, cliquez sur **activer et désactiver des fonctionnalités Windows**.  
  
3. Développez Microsoft Message Queue Server (MSMQ), développez le noyau du serveur MSMQ (Microsoft Message Queue), puis cochez les cases des fonctionnalités Message Queuing à installer :  
  
    - Intégration des services de domaine Active Directory MSMQ (pour les ordinateurs liés à un domaine).  
  
    - Prise en charge HTTP MSMQ.  
  
4. Cliquez sur **OK**.  
  
5. Si vous êtes invité à redémarrer l’ordinateur, cliquez sur **OK** pour terminer l’installation.  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>Pour installer Message Queuing 3.0 sur Windows XP et Windows Server 2003  
  
1. Ouvrez le **Panneau de configuration**.  
  
2. Cliquez sur **Ajout/suppression de programmes** , puis sur Ajouter des **composants Windows**.  
  
3. Sélectionnez Message Queuing, puis cliquez sur **Détails**.  
  
    > [!NOTE]
    > Si vous exécutez Windows Server 2003, sélectionnez serveur d’applications pour accéder à Message Queuing.  
  
4. Vérifiez que l'option Prise en charge HTTP MSMQ est activée dans la page de détails.  
  
5. Cliquez sur **OK** pour quitter la page de détails, puis cliquez sur **suivant**. Terminez l'installation.  
  
6. Si vous êtes invité à redémarrer l’ordinateur, cliquez sur **OK** pour terminer l’installation.  
  
## <a name="see-also"></a>Voir aussi

- [Instructions d'installation](set-up-instructions.md)
