---
title: WCF Services et suivi d'événements Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 5bf965ad6a9997ec0603325f246679cf42662a52
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094811"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>WCF Services et suivi d'événements Windows
Cet exemple montre comment utiliser le traçage analytique dans Windows Communication Foundation (WCF) pour émettre des événements dans Suivi d’v nements pour Windows (ETW). Les traces analytiques sont des événements émis à des points clés dans la pile WCF qui permettent de résoudre les problèmes des services WCF dans l’environnement de production.

 Le suivi analytique dans les services WCF est le suivi qui peut être activé dans un environnement de production avec un impact minimal sur les performances. Ces traces sont émises en tant qu'événements dans une session de suivi ETW.

 Cet exemple comprend un service WCF de base dans lequel les événements sont émis à partir du service dans le journal des événements, qui peut être affiché à l’aide de observateur d’événements. Il est également possible de démarrer une session ETW dédiée qui écoute les événements du service WCF. L'exemple comprend un script permettant de créer une session de suivi ETW dédiée qui stocke des événements dans un fichier binaire pouvant être lu à l'aide de l'Observateur d'événements.

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. À l’aide de Visual Studio 2012, ouvrez le fichier solution EtwAnalyticTraceSample. sln.

2. Pour générer la solution, appuyez sur Ctrl+Maj+B.

3. Pour exécuter la solution, appuyez sur Ctrl+F5.

     Dans le navigateur Web, cliquez sur **Calculator. svc**. L'URI du document WSDL du service doit s'afficher dans le navigateur. Copiez cet URI.

     Par défaut, le service commence à écouter les demandes sur le port 1378 `http://localhost:1378/Calculator.svc`.

4. Exécutez le client test WCF (WcfTestClient. exe).

     Le client test WCF (WcfTestClient. exe) se trouve dans `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.  Le répertoire d’installation par défaut de Visual Studio 2012 est `C:\Program Files\Microsoft Visual Studio 10.0`.

5. Dans le client test WCF, ajoutez le service en sélectionnant **fichier**, puis **Ajouter un service**.

     Ajoutez l'adresse du point de terminaison dans la zone d'entrée. Par défaut, il s’agit de `http://localhost:1378/Calculator.svc`.

6. Ouvrez l'application Observateur d'événements.

     Avant d’appeler le service, démarrez observateur d’événements et assurez-vous que le journal des événements écoute les événements de suivi émis à partir du service WCF.

7. Dans le menu **Démarrer** , sélectionnez **Outils d’administration**, puis **Observateur d’événements**.  Activez les journaux d' **analyse** et de **débogage** .

8. Dans l’arborescence de observateur d’événements, accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, puis serveur d’applications **-applications**. Cliquez avec le bouton droit sur **serveur d’applications-applications**, sélectionnez **affichage**, puis **Affichez les journaux d’analyse et de débogage**.

     Assurez-vous que l’option **afficher les journaux d’analyse et de débogage** est activée.

9. Activez le journal d' **analyse** .

     Dans l’arborescence de observateur d’événements, accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, puis serveur d’applications **-applications**. Cliquez avec le bouton droit sur **analyse** et sélectionnez **activer le journal**.

#### <a name="to-test-the-service"></a>Pour tester le service

1. Revenez au client test WCF, double-cliquez sur `Divide` et conservez les valeurs par défaut, qui spécifient un dénominateur de 0.

     Si le dénominateur est 0, le service génère une erreur.

2. Observez les événements émis par le service.

     Revenez à observateur d’événements et accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, puis serveur d’applications **-applications**. Cliquez avec le bouton droit sur **analyse** , puis sélectionnez **Actualiser**.

     Les événements du traçage analytique de WCF s'affichent dans l'Observateur d'événements. Notez qu'en raison de l'erreur générée par le service, un événement de trace d'erreur est visible dans l'Observateur d'événements.

3. Répétez les étapes 1 et 2, mais avec des entrées valides. La valeur du paramètre `N2` peut être n'importe quel nombre différent de 0.

     Actualisez le canal analytique pour constater que les événements WCF n'incluent aucun événement d'erreur.

 L'exemple montre les événements de trace analytique émis par un service WCF.

#### <a name="to-cleanup-optional"></a>Pour effectuer un nettoyage (facultatif)

1. Ouvrez Observateur d'événements.

2. Accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, puis **application-serveur-applications**. Cliquez avec le bouton droit sur **analyse** et sélectionnez **désactiver le journal**.

3. Accédez à **Observateur d’événements**, **journaux des applications et des services**, **Microsoft**, **Windows**, puis **application-serveur-applications**. Cliquez avec le bouton droit sur **analyse** et sélectionnez **effacer le journal**.

4. Choisissez l’option **Effacer** pour effacer les événements.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de surveillance AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
