---
title: 'Procédure : Développer un WCF Data Service qui fonctionne sur IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 75dc18f3ee91ec077ed48c68ec62cb47910d9ddd
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543483"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Comment : développer un service de données WCF s’exécutant sur IIS

Cet article explique comment utiliser WCF Data Services pour créer un service de données basé sur l’exemple de base de données Northwind hébergé par une application Web ASP.NET s’exécutant sur Internet Information Services (IIS). Pour obtenir un exemple de la façon de créer le même service de données Northwind comme une application Web ASP.NET qui s’exécute sur le Serveur de développement ASP.NET, consultez le Guide de [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).

> [!NOTE]
> Pour créer le service de données Northwind, commencez par installer l’exemple de base de données Northwind sur l’ordinateur local. Pour installer la base de données, exécutez le script Transact-SQL à partir des [exemples de bases de données Northwind et pubs pour Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).

Cet article explique comment créer un service de données à l’aide du fournisseur Entity Framework. Il existe d'autres fournisseurs de services de données. Pour plus d’informations, consultez [Data Services des fournisseurs](data-services-providers-wcf-data-services.md).

Après avoir créé le service, vous devez explicitement fournir un accès aux ressources du service de données. Pour plus d’informations, consultez [Comment : activer l’accès au service de données](how-to-enable-access-to-the-data-service-wcf-data-services.md).

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>Créer l’application Web ASP.NET qui s’exécute sur IIS

1. Dans Visual Studio, dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

2. Dans la boîte de dialogue **nouveau projet** , sélectionnez le > **installé** (**Visual C#** ou **Visual Basic**) > catégorie **Web** .

3. Sélectionnez le modèle **Application web ASP.NET** .

4. Entrez `NorthwindService` comme nom du projet.

5. Cliquez sur **OK**.

6. Dans le menu **projet** , sélectionnez **Propriétés de NorthwindService**.

7. Sélectionnez l’onglet **Web** , puis sélectionnez **utiliser le serveur Web IIS local**.

8. Cliquez sur **créer un répertoire virtuel** , puis sur **OK**.

9. À partir de l'invite de commandes avec des privilèges d'administrateur, exécutez une des commandes suivantes (en fonction du système d'exploitation) :

    - Systèmes 32 bits :

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - Systèmes 64 bits :

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     Cela permet de vérifier que Windows Communication Foundation (WCF) est inscrit sur l'ordinateur.

10. À partir de l'invite de commandes avec des privilèges d'administrateur, exécutez une des commandes suivantes (en fonction du système d'exploitation) :

    - Systèmes 32 bits :

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - Systèmes 64 bits :

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     Cela permet de s'assurer qu'IIS s'exécute correctement après que WCF a été installé sur l'ordinateur. Vous devrez peut-être redémarrer IIS.

11. Lorsque l'application ASP.NET s'exécute sur IIS7, vous devez aussi effectuer les étapes suivantes :

    1. Ouvrez le gestionnaire des services Internet et accédez à l’application PhotoService sous **site Web par défaut**.

    2. Dans l'affichage **Fonctionnalités**, double-cliquez sur **Authentification**.

    3. Dans la page **Authentification**, sélectionnez **Authentification anonyme**.

    4. Dans le volet **actions** , cliquez sur **modifier** pour définir le principal de sécurité sous lequel les utilisateurs anonymes se connecteront au site.

    5. Dans la boîte de dialogue **modifier les informations d’identification d’authentification anonyme** , sélectionnez **identité du pool d’applications**.

    > [!IMPORTANT]
    > Lorsque vous utilisez le compte de service réseau, vous accordez aux utilisateurs anonymes l'accès à tout le réseau interne associé à ce compte.

12. En utilisant SQL Server Management Studio, l'utilitaire sqlcmd.exe ou l'Éditeur Transact-SQL dans Visual Studio, exécutez la commande Transact-SQL suivante sur l'instance SQL Server à laquelle la base de données Northwind est attachée :

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    Cela crée une connexion dans l'instance SQL Server pour le compte Windows utilisé pour exécuter IIS. Cela permet à IIS de se connecter à l'instance de SQL Server.

13. Avec la base de données Northwind attachée, exécutez les commandes Transact-SQL suivantes :

    ```sql
    USE Northwind
    GO
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];
    GO
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]
    WITH DEFAULT_DATABASE=[Northwind];
    GO
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    ```

    Cela accorde des droits à la nouvelle connexion et permet à IIS de lire et d'écrire les données dans la base de données Northwind.

## <a name="define-the-data-model"></a>Définir le modèle de données

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet ASP.net, puis cliquez sur **Ajouter**  >  **un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **ADO.NET Entity Data Model**.

3. Pour le nom du modèle de données, tapez `Northwind.edmx` .

4. Dans l’Assistant Entity Data Model, sélectionnez **générer à partir de la base de données**, puis cliquez sur **suivant**.

5. Connectez le modèle de données à la base de données en procédant de l’une des manières suivantes, puis cliquez sur **suivant**:

    - Si aucune connexion de base de données n’est déjà configurée, cliquez sur **nouvelle connexion** et créez une nouvelle connexion. Pour plus d'informations, consultez [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). Cette instance SQL Server doit avoir l'exemple de base de données Northwind joint.

         \- ou -

    - Si vous avez une connexion de base de données déjà configurée pour vous connecter à la base de données Northwind, sélectionnez cette connexion dans la liste des connexions.

6. Dans la page finale de l'Assistant, activez les cases à cocher pour toutes les tables de la base de données puis désactivez les cases pour les vues et les procédures stockées.

7. Cliquez sur **Terminer** pour fermer l'Assistant.

## <a name="create-the-data-service"></a>Créer le service de données

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet ASP.net, puis cliquez sur **Ajouter**  >  **un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **service de données WCF**.

   ![Modèle d’élément de service de données WCF dans Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Le modèle de **service de données WCF** est disponible dans visual studio 2015, mais pas dans visual studio 2017 ou version ultérieure.

3. Pour le nom du service, entrez `Northwind` .

     Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service. La fenêtre de l'éditeur de code s'ouvre par défaut. Dans **Explorateur de solutions**, le service porte le nom, Northwind et l’extension. svc.cs ou. svc. vb.

4. Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindEntities`. La définition de classe doit ressembler aux éléments suivants:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>Voir aussi

- [Exposition de vos données comme service](exposing-your-data-as-a-service-wcf-data-services.md)
