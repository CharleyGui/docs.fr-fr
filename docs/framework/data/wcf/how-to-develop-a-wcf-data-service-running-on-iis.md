---
title: 'Procédure : développer un WCF Data Service qui fonctionne sur IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 8a1a0c2c55267940463e2c9ab82bb52345269260
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121611"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Comment : Développer un service de données WCF fonctionnant sur l’IIS

Cet article montre comment utiliser WCF Data Services pour créer un service de données basé sur la base de données de l’échantillon Northwind hébergée par une application Web ASP.NET fonctionnant sur Internet Information Services (IIS). Pour un exemple de la façon de créer le même service de données Northwind comme une application Web ASP.NET qui s’exécute sur le serveur de développement ASP.NET, voir le [WCF Data Services quickstart](quickstart-wcf-data-services.md).

> [!NOTE]
> Pour créer le service de données Northwind, installez d’abord la base de données de l’échantillon Northwind sur l’ordinateur local. Pour installer la base de données, exécutez le script Transact-SQL à partir de [Northwind et pubs échantillons de bases](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)de données pour Microsoft SQL Server .

Cet article montre comment créer un service de données en utilisant le fournisseur de cadre d’entité. Il existe d'autres fournisseurs de services de données. Pour plus d’informations, voir [Fournisseurs de services de données](data-services-providers-wcf-data-services.md).

Après avoir créé le service, vous devez explicitement fournir un accès aux ressources du service de données. Pour plus d’informations, voir [Comment : Activer l’accès au service de données](how-to-enable-access-to-the-data-service-wcf-data-services.md).

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>Créez l’application web ASP.NET qui s’exécute sur IIS

1. Dans Visual Studio, dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

2. Dans la boîte de dialogue **du nouveau projet,** sélectionnez la catégorie **>** **(Visual C)** ou **Visual Basic**( > catégorie **Web.**

3. Sélectionnez le modèle **Application web ASP.NET** .

4. Entrez `NorthwindService` comme nom du projet.

5. Cliquez sur **OK**.

6. Au menu du **projet,** sélectionnez **NorthwindService Properties**.

7. Sélectionnez l’onglet **Web,** puis **sélectionnez Utilisez le serveur Web local IIS**.

8. Cliquez **sur Créer l’annuaire virtuel,** puis cliquez **sur OK**.

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

    1. Ouvrez IIS Manager et naviguez vers l’application PhotoService sous **site Web par défaut**.

    2. Dans l'affichage **Fonctionnalités**, double-cliquez sur **Authentification**.

    3. Dans la page **Authentification**, sélectionnez **Authentification anonyme**.

    4. Dans le volet **Actions,** cliquez sur **Edit** pour définir le principal de sécurité sous lequel les utilisateurs anonymes se connecteront au site.

    5. Dans la boîte de dialogue **Edit Anonymous Authentication Credentials,** sélectionnez **l’identité du pool d’applications**.

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

1. Dans **Solution Explorer**, cliquez à droite sur le nom du projet ASP.NET, puis cliquez sur **Ajouter** > **un nouvel article**.

2. Dans la boîte de dialogue **Add New Item,** sélectionnez **ADO.NET modèle de données d’entité**.

3. Pour le nom du modèle `Northwind.edmx`de données, tapez .

4. Dans l’Assistant modèle de données d’entité, **sélectionnez Générer à partir de la base de données,** puis cliquez sur **Next**.

5. Connectez le modèle de données à la base de données en faisant l’une des étapes suivantes, puis cliquez sur **Next**:

    - Si vous n’avez pas de connexion de base de données déjà configurée, cliquez sur **New Connection** et créez une nouvelle connexion. Pour plus d'informations, consultez [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)). Cette instance SQL Server doit avoir l'exemple de base de données Northwind joint.

         \- ou -

    - Si vous avez une connexion de base de données déjà configurée pour vous connecter à la base de données Northwind, sélectionnez cette connexion dans la liste des connexions.

6. Dans la page finale de l'Assistant, activez les cases à cocher pour toutes les tables de la base de données puis désactivez les cases pour les vues et les procédures stockées.

7. Cliquez sur **Terminer** pour fermer l'Assistant.

## <a name="create-the-data-service"></a>Créer le service de données

1. Dans **Solution Explorer**, cliquez à droite sur le nom de votre projet ASP.NET, puis cliquez sur **Ajouter** > **un nouvel article**.

2. Dans la boîte de dialogue **Add New Item,** sélectionnez **WCF Data Service**.

   ![Modèle d’élément WCF Data Service dans Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > Le modèle **WCF Data Service** est disponible en Visual Studio 2015, mais pas dans Visual Studio 2017 ou plus tard.

3. Pour le nom du `Northwind`service, entrez .

     Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service. La fenêtre de l'éditeur de code s'ouvre par défaut. Dans **Solution Explorer**, le service a le nom, Northwind, et l’extension .svc.cs ou .svc.vb.

4. Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindEntities`. La définition de classe doit ressembler aux éléments suivants:

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>Voir aussi

- [Exposition de vos données comme service](exposing-your-data-as-a-service-wcf-data-services.md)
