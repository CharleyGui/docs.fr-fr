---
title: Créer un service de données WCF dans Visual Studio
description: Découvrez comment créer un exemple de service de données qui utilise WCF Data Services pour exposer un flux OData basé sur un exemple de base de données.
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: f6e95ce58e055f0c745b781c664309e4ef91ffc6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554011"
---
# <a name="create-the-data-service"></a>Créer le service de données

Dans cette rubrique, vous allez créer un exemple de service de données qui utilise WCF Data Services pour exposer un flux Open Data Protocol (OData) basé sur l’exemple de base de données Northwind. La tâche implique les étapes fondamentales suivantes :

1. Créez une application Web ASP.NET.

2. Définissez le modèle de données à l'aide des outils Entity Data Model.

3. Ajoutez le service de données à l'application Web.

4. Activez l'accès au service de données.

## <a name="create-the-aspnet-web-app"></a>Créer l’application Web ASP.NET

1. Dans Visual Studio, dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

1. Dans la boîte de dialogue **nouveau projet** , sous Visual Basic ou Visual C#, sélectionnez la catégorie **Web** , puis sélectionnez **application Web ASP.net**.

1. Entrez `NorthwindService` comme nom du projet, puis sélectionnez **OK**.

1. Dans la boîte de dialogue **nouvelle application Web ASP.net** , sélectionnez **vide** , puis cliquez sur **OK**.

1. (Facultatif) Spécifiez un numéro de port spécifique pour votre application Web. Remarque : le numéro `12345` de port est utilisé dans cette série de rubriques de démarrage rapide.

    1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet ASP.net que vous venez de créer, puis choisissez **Propriétés**.

    2. Sélectionnez l’onglet **Web** et définissez la valeur de la zone de texte **port spécifique** sur `12345` .

## <a name="define-the-data-model"></a>Définir le modèle de données

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet ASP.net, puis cliquez sur **Ajouter**  >  **un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez la catégorie **données** , puis sélectionnez **ADO.NET Entity Data Model**.

3. Pour le nom du modèle de données, entrez `Northwind.edmx` .

4. Dans l' **assistant Entity Data Model**, sélectionnez le **Concepteur EF à partir de la base de données**, puis cliquez sur **suivant**.

5. Connectez le modèle de données à la base de données en procédant de l’une des manières suivantes, puis cliquez sur **suivant**:

    - Si aucune connexion de base de données n’est déjà configurée, cliquez sur **nouvelle connexion** et créez une nouvelle connexion. Pour plus d'informations, consultez [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). Cette instance SQL Server doit avoir l'exemple de base de données Northwind joint.

         \- ou -

    - Si vous avez une connexion de base de données déjà configurée pour vous connecter à la base de données Northwind, sélectionnez cette connexion dans la liste des connexions.

6. Dans la page finale de l'Assistant, activez les cases à cocher pour toutes les tables de la base de données puis désactivez les cases pour les vues et les procédures stockées.

7. Cliquez sur **Terminer** pour fermer l'Assistant.

## <a name="create-the-wcf-data-service"></a>Créer le service de données WCF

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet ASP.net, puis choisissez **Ajouter**  >  **un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez le modèle élément de **service de données WCF** dans la catégorie **Web** .

   ![Modèle d’élément de service de données WCF dans Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Le modèle de **service de données WCF** est disponible dans visual studio 2015, mais pas dans visual studio 2017 ou version ultérieure.

3. Pour le nom du service, tapez `Northwind` .

     Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service. La fenêtre de l'éditeur de code s'ouvre par défaut. Dans **Explorateur de solutions**, le service porte le nom Northwind avec l’extension *. svc.cs* ou *. svc. vb*.

4. Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindEntities`. La définition de classe doit ressembler aux éléments suivants:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a>Activer l’accès aux ressources du service de données

1. Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     Cela permet aux clients autorisés d'accéder aux ressources en lecture et en écriture pour les jeux d'entités spécifiés.

    > [!NOTE]
    > Tout client qui peut accéder à l'application ASP.NET peut également accéder aux ressources exposées par le service de données. Dans un service de données de production, pour empêcher l'accès non autorisé aux ressources, vous devez également sécuriser l'application elle-même. Pour plus d'informations, consultez [Securing WCF Data Services](securing-wcf-data-services.md).

## <a name="next-steps"></a>Étapes suivantes

Vous avez correctement créé un nouveau service de données qui expose un flux OData basé sur l’exemple de base de données Northwind, et vous avez activé l’accès au flux pour les clients qui ont des autorisations sur l’application Web ASP.NET. Ensuite, vous allez démarrer le service de données à partir de Visual Studio et accéder au flux OData en soumettant des demandes HTTP d’extraction via un navigateur Web :

> [!div class="nextstepaction"]
> [Accéder au service à partir d’un navigateur Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Voir aussi

- [Outils de Entity Data Model ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
