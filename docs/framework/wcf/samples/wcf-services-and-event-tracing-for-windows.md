---
title: WCF Services et suivi d'événements Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: b8a1f30f20aa2c541a574a070b3644569d633ca2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183213"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>WCF Services et suivi d'événements Windows
Cet exemple montre comment utiliser le tracé analytique dans Windows Communication Foundation (WCF) pour émettre des événements dans Event Tracing for Windows (ETW). Les traces analytiques sont des événements émis à des points clés de la pile WCF qui permettent le dépannage des services WCF dans l’environnement de production.

 La trace analytique dans les services WCF est le traçage qui peut être activé dans un environnement de production avec un impact minimal sur les performances. Ces traces sont émises en tant qu'événements dans une session de suivi ETW.

 Cet exemple comprend un service WCF de base dans lequel les événements sont émis du service au journal de l’événement, qui peut être consulté à l’aide de Event Viewer. Il est également possible de commencer une session ETW dédiée qui écoute les événements du service WCF. L'exemple comprend un script permettant de créer une session de suivi ETW dédiée qui stocke des événements dans un fichier binaire pouvant être lu à l'aide de l'Observateur d'événements.

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. À l’aide de Visual Studio 2012, ouvrez le fichier de solution EtwAnalyticTraceSample.sln.

2. Pour générer la solution, appuyez sur Ctrl+Maj+B.

3. Pour exécuter la solution, appuyez sur Ctrl+F5.

     Dans le navigateur Web, cliquez sur **Calculator.svc**. L'URI du document WSDL du service doit s'afficher dans le navigateur. Copiez cet URI.

     Par défaut, le service commence à écouter les `http://localhost:1378/Calculator.svc`demandes sur le port 1378 .

4. Exécuter le client de test WCF (WcfTestClient.exe).

     Le client de test WCF (WcfTestClient.exe) est situé à `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.  Le par défaut Visual Studio 2012 installer dir est `C:\Program Files\Microsoft Visual Studio 10.0`.

5. Au sein du client de test WCF, ajoutez le service en sélectionnant **Le fichier,** puis **ajoutez le service**.

     Ajoutez l'adresse du point de terminaison dans la zone d'entrée. Par défaut, il s’agit de `http://localhost:1378/Calculator.svc`.

6. Ouvrez l'application Observateur d'événements.

     Avant d’invoquer le service, commencez Event Viewer et assurez-vous que le journal de l’événement est à l’écoute des événements de suivi émis par le service WCF.

7. Du menu **Démarrer,** sélectionnez **des outils administratifs,** puis **Event Viewer**.  Activez les journaux **Analytic** et **Debug.**

8. Dans la vue d’arbre dans Event Viewer, naviguez vers **Event Viewer**, Applications et **Services Logs**, **Microsoft**, **Windows**, puis **Application Server-Applications**. Application à clic droit **Server-Applications**, sélectionnez **View**, puis **Afficher les journaux Analytiques et Debug**.

     Assurez-vous que l’option **Afficher l’analyse et les journaux Debug** est vérifiée.

9. Activez le journal **Analytic.**

     Dans la vue d’arbre dans Event Viewer, naviguez vers **Event Viewer**, Applications et **Services Logs**, **Microsoft**, **Windows**, puis **Application Server-Applications**. Cliquez à droite **Analytic** et **sélectionnez Active Log**.

#### <a name="to-test-the-service"></a>Pour tester le service

1. Revenez au client de test `Divide` WCF et double-clic et conservez les valeurs par défaut, qui spécifient un dénominateur de 0.

     Si le dénominateur est 0, le service génère une erreur.

2. Observez les événements émis par le service.

     Retournez à Event Viewer et naviguez vers **Event Viewer**, Applications and **Services Logs**, **Microsoft**, **Windows**, puis **Application Server-Applications**. Cliquez à droite **Analytic** et **sélectionnez Refresh**.

     Les événements du traçage analytique de WCF s'affichent dans l'Observateur d'événements. Notez qu'en raison de l'erreur générée par le service, un événement de trace d'erreur est visible dans l'Observateur d'événements.

3. Répétez les étapes 1 et 2, mais avec des entrées valides. La valeur du paramètre `N2` peut être n'importe quel nombre différent de 0.

     Actualisez le canal analytique pour constater que les événements WCF n'incluent aucun événement d'erreur.

 L'exemple montre les événements de trace analytique émis par un service WCF.

#### <a name="to-cleanup-optional"></a>Pour effectuer un nettoyage (facultatif)

1. Ouvrez l'observateur d'événements.

2. Naviguez vers **Event Viewer**, Applications et **Services Logs**, **Microsoft**, **Windows**, puis **Application-Server-Applications**. Cliquez à droite **Analytic** et sélectionnez **Disable Log**.

3. Naviguez vers **Event Viewer**, Applications et **Services Logs**, **Microsoft**, **Windows**, puis **Application-Server-Applications**. Cliquez à droite **Analytic** et sélectionnez **Clear Log**.

4. Choisissez l’option **Clear** pour effacer les événements.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
