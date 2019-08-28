---
title: Suivi SQL
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 24cc484bf11d7cedab949d61c63f805a28a9f849
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038053"
---
# <a name="sql-tracking"></a>Suivi SQL
Cet exemple montre comment écrire un participant de suivi SQL personnalisé, qui écrit des enregistrements de suivi dans une base de données SQL. Windows Workflow Foundation (WF) fournit le suivi de workflow pour obtenir une visibilité sur l’exécution d’une instance de Workflow. Le runtime de suivi émet des enregistrements de suivi de workflow lors de l'exécution du workflow. Pour plus d’informations sur le suivi de workflow, consultez [suivi et traçage de workflow](../workflow-tracking-and-tracing.md).

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. Vérifiez que vous disposez de SQL Server 2008, SQL Server 2008 Express ou version plus récente. Les scripts fournis avec l'exemple supposent l'utilisation d'une instance SQL Express sur votre ordinateur local. Si vous avez une instance différente, modifiez les scripts liés à la base de données avant d'exécuter l'exemple.

2. Créez la base de données de suivi SQL Server en exécutant Trackingsetup.cmd dans le répertoire de scripts (\WF\Basic\Tracking\SqlTracking\CS\Scripts). Cela crée une base de données appelée TrackingSample.

    > [!NOTE]
    > Le script crée la base de données sur l'instance par défaut de SQL Express. Si vous souhaitez l'installer sur une instance de base de données différente, modifiez le script Trackingsetup.cmd.  
  
3. Ouvrez SqlTrackingSample. sln dans Visual Studio 2010.  
  
4. Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
5. Appuyez sur F5 pour exécuter l'application.  
  
     La fenêtre du navigateur s'ouvre et affiche la liste des répertoires pour l'application.  
  
6. Dans le navigateur, cliquez sur StockPriceService.xamlx.  
  
7. Le navigateur affiche la page StockPriceService, laquelle contient l'adresse WSDL du service local. Copiez cette adresse.  
  
     Un exemple de l’adresse WSDL du service local `http://localhost:65193/StockPriceService.xamlx?wsdl`est.  
  
8. À l’aide de l’Explorateur de fichiers, exécutez le client test WCF (WcfTestClient. exe). Il se trouve dans le répertoire Microsoft Visual Studio 10.0\Common7\IDE.  
  
9. Dans le client test WCF, cliquez sur le menu **fichier** et sélectionnez **Ajouter un service**. Collez l'adresse du service local dans la zone de texte. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
10. Dans le client test WCF, double-cliquez sur **GetStockPrice**. Cela ouvre l' `GetStockPrice` opération qui accepte un paramètre, tapez la valeur `Contoso` et cliquez sur **appeler**.  
  
11. Les enregistrements de suivi émis sont écrits dans une base de données SQL. Pour afficher les enregistrements de suivi, ouvrez la base de données TrackingSample dans SQL Management Studio et naviguez jusqu'aux tables. Pour plus d’informations sur la SQL Server Management Studio, consultez [Présentation des SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645). SQL Server 2008 Management Studio Express peut être téléchargé [ici](https://go.microsoft.com/fwlink/?LinkId=180520). L'exécution d'une requête Sélection dans les tables affiche les données dans les enregistrements de suivi stockés dans les tables respectives.  
  
#### <a name="to-uninstall-the-sample"></a>Pour désinstaller l'exemple  
  
1. Exécutez le script Trackingcleanup.cmd dans le répertoire de l'exemple (\WF\Basic\Tracking\SqlTracking).  
  
    > [!NOTE]
    > Trackingcleanup.cmd essaie de supprimer la base de données de votre ordinateur local SQL Express. Si vous utilisez une autre instance SQL Server, modifiez Trackingcleanup.cmd.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de surveillance AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
