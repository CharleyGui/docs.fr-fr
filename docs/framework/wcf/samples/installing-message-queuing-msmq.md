---
title: Installation de Message Queuing (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 118143f2d434e9f4399c3e9141743fc0254b61ab
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039623"
---
# <a name="installing-message-queuing-msmq"></a>Installation de Message Queuing (MSMQ)
Les procédures suivantes indiquent comment installer Message Queuing 4.0 et Message Queuing 3.0.  
  
> [!NOTE]
> Message Queuing 4.0 n'est pas disponible dans [!INCLUDE[wxp](../../../../includes/wxp-md.md)] et [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
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
    > Si vous exécutez [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], sélectionnez Serveur d'applications pour accéder à Message Queuing.  
  
4. Vérifiez que l'option Prise en charge HTTP MSMQ est activée dans la page de détails.  
  
5. Cliquez sur **OK** pour quitter la page de détails, puis cliquez sur **suivant**. Terminez l'installation.  
  
6. Si vous êtes invité à redémarrer l’ordinateur, cliquez sur **OK** pour terminer l’installation.  
  
## <a name="see-also"></a>Voir aussi

- [Instructions d’installation](../../../../docs/framework/wcf/samples/set-up-instructions.md)
