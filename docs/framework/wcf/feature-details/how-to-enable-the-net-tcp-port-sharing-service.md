---
title: 'Comment : activer le service de partage de ports Net.TCP'
description: Découvrez comment configurer le service de partage de port Net TCP à l’aide de MMC pour activer net. TCP, qui est désactivé par défaut.
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 0292559e3befde7f0b00b36aa10a2d9615daf049
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246998"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Comment : activer le service de partage de ports Net.TCP
Windows Communication Foundation (WCF) utilise un service Windows appelé service de partage de ports net. TCP pour faciliter le partage de ports TCP entre plusieurs processus. Ce service est installé dans le cadre de WCF, mais le service n’est pas activé par défaut pour des raisons de sécurité et doit donc être activé manuellement avant la première utilisation. Cette rubrique décrit comment configurer le service de partage de ports Net.TCP à l'aide du composant logiciel enfichable Microsoft Management Console (MMC).  
  
 Après avoir activé le service de partage de port Net. TCP et l’avoir démarré manuellement, consultez [procédure : configurer un service WCF pour utiliser le partage de ports](how-to-configure-a-wcf-service-to-use-port-sharing.md) pour plus d’informations sur la façon de configurer votre service pour utiliser ce service.  
  
 Pour obtenir un exemple qui utilise le partage de ports net. TCP://, consultez l' [exemple partage de port Net. TCP](../samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>Pour activer le service de partage de ports Net.TCP à l'aide de MMC  
  
1. Dans le menu Démarrer, ouvrez la console de gestion des services en ouvrant une fenêtre d’invite de commandes et `services.msc` en tapant ou en ouvrant exécuter et `services.msc` en tapant dans la zone Ouvrir.  
  
2. Dans la colonne **nom** de la liste des services, cliquez avec le bouton droit sur le **service de partage de port Net. TCP**, puis sélectionnez **Propriétés** dans le menu.  
  
3. Pour activer le démarrage manuel du service, dans la fenêtre **Propriétés** , sélectionnez l’onglet **général** , et dans la zone **type de démarrage** , sélectionnez manuel, puis cliquez sur **appliquer**.  
  
4. Pour démarrer le service, dans la zone État du service, cliquez sur le bouton **Démarrer** . L'état du service doit maintenant afficher "Démarré".  
  
5. Pour revenir à la liste des services, cliquez sur **OK**, puis quittez la console MMC.  
  
## <a name="example"></a>Exemple  
  
## <a name="see-also"></a>Voir aussi

- [Partage de ports Net.TCP](net-tcp-port-sharing.md)
- [Configuration du service de partage de ports Net.TCP](configuring-the-net-tcp-port-sharing-service.md)
