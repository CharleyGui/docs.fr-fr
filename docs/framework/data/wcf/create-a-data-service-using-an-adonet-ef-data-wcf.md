---
title: 'Procédure : Créer un service de données à l’aide d’une source de données ADO.NET Entity Framework (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: ae4176fd986f870523e44a11eee48850e2dddd7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791078"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>Procédure : Créer un service de données à l’aide d’une source de données ADO.NET Entity Framework (WCF Data Services)

WCF Data Services expose les données d’entité en tant que service de données. Ces données d’entité sont fournies par le[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] ADO.net lorsque la source de données est une base de données relationnelle. Cette rubrique vous montre comment créer un [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]modèle de données basé sur dans une application Web Visual Studio basée sur une base de données existante et utiliser ce modèle de données pour créer un nouveau service de données.

Fournit également un outil en ligne de commande qui peut générer [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] un modèle en dehors d’un projet Visual Studio. [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] Pour plus d’informations, consultez [Guide pratique pour Utilisez EdmGen. exe pour générer les fichiers](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)de modèle et de mappage.

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>Pour ajouter à une application Web existante un modèle Entity Framework qui repose sur une base de données existante

1. Dans le menu **projet** , cliquez sur **Ajouter** > **un nouvel élément**.

2. Dans le volet **modèles** , cliquez sur la catégorie **données** , puis sélectionnez **ADO.NET Entity Data Model**.

3. Entrez le nom du modèle, puis cliquez sur **Ajouter**.

     La première page de l'Assistant Entity Data Model s'affiche.

4. Dans la boîte de dialogue **choisir le contenu du Model** , sélectionnez **générer à partir de la base de données**. Cliquez ensuite sur **Suivant**.

5. Cliquez sur le bouton **nouvelle connexion** .

6. Dans la boîte de dialogue **Propriétés de connexion** , tapez le nom de votre serveur, sélectionnez la méthode d’authentification, tapez le nom de la base de données, puis cliquez sur **OK**.

     La boîte de dialogue **choisir votre connexion de données** est mise à jour avec vos paramètres de connexion à la base de données.

7. Vérifiez que la case à cocher **enregistrer les paramètres de connexion de l’entité dans App. config en tant que :** est activée. Cliquez ensuite sur **Suivant**.

8. Dans la boîte de dialogue **choisir vos objets de base de données** , sélectionnez tous les objets de base de données que vous envisagez d’exposer dans le service de données.

    > [!NOTE]
    > Les objets inclus dans le modèle de données ne sont pas exposés automatiquement par le service de données. Ils doivent être exposés explicitement par le service lui-même. Pour plus d’informations, consultez [configuration du service de données](configuring-the-data-service-wcf-data-services.md).

9. Cliquez sur **Terminer** pour terminer l’Assistant.

     Cela crée un modèle de données par défaut basé sur la base de données spécifique. [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] permet de personnaliser le modèle de données. Pour plus d’informations, consultez [Entity Data Model des tâches d’outils](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a>Pour créer le service de données à l'aide du nouveau modèle de données

1. Dans Visual Studio, ouvrez le fichier .edmx qui représente le modèle de données.

2. Dans l' **Explorateur de modèles**, cliquez avec le bouton droit sur le modèle, cliquez sur **Propriétés**, puis notez le nom du conteneur d’entités.

3. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet ASP.net, puis cliquez sur **Ajouter** > **un nouvel élément**.

4. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez le modèle **service de données WCF** dans la catégorie **Web** .

   ![Modèle d’élément de service de données WCF dans Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Le modèle de **service de données WCF** est disponible dans visual studio 2015, mais pas dans visual studio 2017.

5. Fournissez un nom pour le service, puis cliquez sur **OK**.

     Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service. La fenêtre de l'éditeur de code s'ouvre par défaut.

6. Dans le code pour le service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui hérite de la classe <xref:System.Data.Objects.ObjectContext> et qui correspond au conteneur d'entités du modèle de données, noté à l'étape 2.

7. Dans le code pour le service de données, permettez aux clients autorisés d'accéder aux jeux d'entités exposés par le service de données. Pour plus d’informations, consultez [création du service de données](creating-the-data-service.md).

8. Pour tester le service de données Northwind. svc à l’aide d’un navigateur Web, suivez les instructions de la rubrique [accès au service à partir d’un navigateur Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Voir aussi

- [Définition de WCF Data Services](defining-wcf-data-services.md)
- [Fournisseurs de services de données](data-services-providers-wcf-data-services.md)
- [Guide pratique pour Créer un service de données à l’aide du fournisseur de réflexion](create-a-data-service-using-rp-wcf-data-services.md)
- [Guide pratique pour Créer un service de données à l’aide d’une source de données LINQ to SQL](create-a-data-service-using-linq-to-sql-wcf.md)
