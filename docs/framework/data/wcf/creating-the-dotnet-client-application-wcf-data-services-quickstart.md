---
title: Création de l'application cliente .NET Framework (démarrage rapide des services de données WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 9995a509bf997298d991a1f66cfdf3cae6cd0395
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790967"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>Création de l'application cliente .NET Framework (démarrage rapide des services de données WCF)

Il s’agit de la dernière tâche du démarrage rapide WCF Data Services. Dans cette tâche, vous allez ajouter une application console à la solution, ajouter une référence au [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] flux dans cette nouvelle application cliente et accéder au flux OData à partir de l’application cliente à l’aide des classes de service de données client et des bibliothèques clientes générées. .

> [!NOTE]
> Il n'est pas obligatoire pour une application cliente .NET Framework d'accéder à un flux de données. Le service de données est accessible par tout composant d’application qui consomme un flux OData. Pour plus d’informations, consultez [utilisation d’un service de données dans une application cliente](using-a-data-service-in-a-client-application-wcf-data-services.md).

## <a name="to-create-the-client-application-by-using-visual-studio"></a>Pour créer l'application cliente à l'aide de Visual Studio

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution, cliquez sur **Ajouter**, puis sur **nouveau projet**.

2. Dans le volet gauche, sélectionnez **installé** > [**visuel C#**  ou **Visual Basic**] > **Bureau Windows**, puis sélectionnez le modèle **application WPF** .

3. Entrez `NorthwindClient` pour le nom du projet, puis cliquez sur **OK**.

4. Ouvrez le fichier MainWindow.xaml et remplacez le code XAML par le code suivant :

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a>Pour ajouter une référence de service de données au projet

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet NorthwindClient, cliquez sur **Ajouter** > une**référence de service**, puis sur **découvrir**.

     Cette opération affiche le service de données Northwind que vous avez créé dans la première tâche.

2. Dans la zone de texte **espace** de `Northwind`noms, tapez, puis cliquez sur **OK**.

     Cette opération ajoute un nouveau fichier de code au projet qui contient les classes de données utilisées pour accéder et interagir avec les ressources du service de données sous la forme d'objets. Les classes de données sont créées dans l'espace de noms `NorthwindClient.Northwind`.

## <a name="to-access-data-service-data-in-the-wpf-application"></a>Pour accéder aux données du service des données dans l'application WPF

1. Dans **Explorateur de solutions** sous **NorthwindClient**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Ajouter une référence**.

2. Dans la boîte de dialogue **Ajouter une référence** , cliquez sur l’onglet **.net** , sélectionnez l’assembly System. Data. services. client. dll, puis cliquez sur **OK**.

3. Dans **Explorateur de solutions** sous **NorthwindClient**, ouvrez la page de codes du fichier MainWindow. xaml et ajoutez l’instruction suivante `using` (`Imports` dans Visual Basic).

    [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#using)]
    [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#using)]

4. Insérez le code suivant qui interroge le service de données et lie le résultat à une <xref:System.Data.Services.Client.DataServiceCollection%601> dans la classe `MainWindow`:

    > [!NOTE]
    > Vous devez remplacer le nom d'hôte `localhost:12345` par le serveur et le port qui hébergent votre instance du service de données Northwind.

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#querycode)]

5. Insérez le code suivant qui enregistre les modifications dans la classe `MainWindow` :

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a>Pour générer et exécuter l'application NothwindClient

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet NorthwindClient et sélectionnez **définir comme projet de démarrage**.

2. Appuyez sur **F5** pour démarrer l’application.

     Cette opération génère et démarre l'application cliente. Les données sont demandées auprès du service et s'affichent dans la console.

3. Modifiez une valeur dans la colonne **Quantity** de la grille de données, puis cliquez sur **Enregistrer**.

     Les modifications sont enregistrées sur le service de données.

    > [!NOTE]
    > Cette version de l'application NorthwindClient ne prend pas en charge l'ajout et la suppression d'entités.

## <a name="next-steps"></a>Étapes suivantes

Vous avez créé avec succès l’application cliente qui accède à l’exemple de flux OData Northwind. Vous avez également terminé le WCF Data Services démarrage rapide !

Pour plus d’informations sur l’accès à un flux OData à partir d’une application .NET Framework, consultez [WCF Data Services bibliothèque cliente](wcf-data-services-client-library.md).

## <a name="see-also"></a>Voir aussi

- [Prise en main](getting-started-with-wcf-data-services.md)
- [Ressources](wcf-data-services-resources.md)
