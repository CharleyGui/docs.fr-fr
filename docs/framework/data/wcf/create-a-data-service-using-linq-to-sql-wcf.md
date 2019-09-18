---
title: 'Procédure : Créer un service de données à l’aide d’une source de données LINQ to SQL (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 6489e451f3790e38ea821104fd2aca5a8c091ba6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053002"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Procédure : Créer un service de données à l’aide d’une source de données LINQ to SQL (WCF Data Services)

WCF Data Services expose les données d’entité en tant que service de données. Le fournisseur de réflexion vous permet de définir un modèle de données basé sur toute classe qui expose des membres qui retournent une <xref:System.Linq.IQueryable%601> implémentation. Pour pouvoir effectuer des mises à jour des données dans la source de données, ces classes doivent également implémenter l'interface <xref:System.Data.Services.IUpdatable>. Pour plus d’informations, consultez [Data Services des fournisseurs](data-services-providers-wcf-data-services.md). Cette rubrique vous montre comment créer des classes LINQ to SQL qui accèdent à l'exemple de base de données Northwind à l'aide du fournisseur de réflexion, et comment créer le service de données basé sur ces classes de données.

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>Pour ajouter des classes LINQ to SQL à un projet.

1. Dans un Visual Basic C# ou une application, dans le menu **projet** , cliquez sur **Ajouter** > **un nouvel élément**.

2. Cliquez sur le modèle **classes de LINQ to SQL** .

3. Remplacez le nom par **Northwind. dbml**.

4. Cliquez sur **Ajouter**.

     Le fichier Northwind.dbml est ajouté au projet et le Concepteur Objet/Relationnel (Concepteur O/R) s'ouvre.

5. Dans **serveur**/**Explorateur de base de données**, sous Northwind, développez **tables** , puis `Customers` faites glisser la table sur le concepteur objet relationnel (Concepteur O/R).

     Une classe d'entité `Customer` est créée et apparaît dans l'aire de conception.

6. Répétez l'étape 6 pour les tables `Orders`, `Order_Details` et `Products`.

7. Cliquez avec le bouton droit sur le nouveau fichier. dbml qui représente les classes LINQ to SQL, puis cliquez sur **afficher le code**.

     Cela crée une nouvelle page code-behind nommée Northwind.cs qui contient une définition de classe partielle pour la classe qui hérite de la classe <xref:System.Data.Linq.DataContext>, dans ce cas `NorthwindDataContext`.

8. Remplacez le contenu du fichier de code Northwind.cs par le code suivant. Ce code implémente le fournisseur de réflexion en étendant les classes de données et <xref:System.Data.Linq.DataContext> générés par LINQ to SQL :

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Pour créer un service de données en utilisant un modèle de données LINQ to SQL

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet ASP.net, puis cliquez sur **Ajouter** > **un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez le modèle de **service de données WCF** à partir de la catégorie **Web** .

   ![Modèle d’élément de service de données WCF dans Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Le modèle de **service de données WCF** est disponible dans visual studio 2015, mais pas dans visual studio 2017.

3. Fournissez un nom pour le service, puis cliquez sur **OK**.

     Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service. La fenêtre de l'éditeur de code s'ouvre par défaut.

4. Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindDataContext`.

5. Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     Cela permet aux clients autorisés d'accéder aux ressources pour les trois jeux d'entités spécifiés.

6. Pour tester le service de données Northwind. svc à l’aide d’un navigateur Web, suivez les instructions de la rubrique [accès au service à partir d’un navigateur Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Créer un service de données à l’aide d’une source de données ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [Guide pratique pour Créer un service de données à l’aide du fournisseur de réflexion](create-a-data-service-using-rp-wcf-data-services.md)
- [Fournisseurs de services de données](data-services-providers-wcf-data-services.md)
