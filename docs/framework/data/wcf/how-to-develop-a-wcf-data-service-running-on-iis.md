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
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="6a2be-102">Comment : développer un service de données WCF s’exécutant sur IIS</span><span class="sxs-lookup"><span data-stu-id="6a2be-102">How to: Develop a WCF data service running on IIS</span></span>

<span data-ttu-id="6a2be-103">Cet article explique comment utiliser WCF Data Services pour créer un service de données basé sur l’exemple de base de données Northwind hébergé par une application Web ASP.NET s’exécutant sur Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="6a2be-103">This article shows how to use WCF Data Services to create a data service that's based on the Northwind sample database that's hosted by an ASP.NET Web app running on Internet Information Services (IIS).</span></span> <span data-ttu-id="6a2be-104">Pour obtenir un exemple de la façon de créer le même service de données Northwind comme une application Web ASP.NET qui s’exécute sur le Serveur de développement ASP.NET, consultez le Guide de [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="6a2be-104">For an example of how to create the same Northwind data service as an ASP.NET Web app that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6a2be-105">Pour créer le service de données Northwind, commencez par installer l’exemple de base de données Northwind sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6a2be-105">To create the Northwind data service, first install the Northwind sample database on the local computer.</span></span> <span data-ttu-id="6a2be-106">Pour installer la base de données, exécutez le script Transact-SQL à partir des [exemples de bases de données Northwind et pubs pour Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span><span class="sxs-lookup"><span data-stu-id="6a2be-106">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

<span data-ttu-id="6a2be-107">Cet article explique comment créer un service de données à l’aide du fournisseur Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="6a2be-107">This article shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="6a2be-108">Il existe d'autres fournisseurs de services de données.</span><span class="sxs-lookup"><span data-stu-id="6a2be-108">Other data services providers are available.</span></span> <span data-ttu-id="6a2be-109">Pour plus d’informations, consultez [Data Services des fournisseurs](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="6a2be-109">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="6a2be-110">Après avoir créé le service, vous devez explicitement fournir un accès aux ressources du service de données.</span><span class="sxs-lookup"><span data-stu-id="6a2be-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="6a2be-111">Pour plus d’informations, consultez [Comment : activer l’accès au service de données](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="6a2be-111">For more information, see [How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="6a2be-112">Créer l’application Web ASP.NET qui s’exécute sur IIS</span><span class="sxs-lookup"><span data-stu-id="6a2be-112">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="6a2be-113">Dans Visual Studio, dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-113">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="6a2be-114">Dans la boîte de dialogue **nouveau projet** , sélectionnez le > **installé** (**Visual C#** ou **Visual Basic**) > catégorie **Web** .</span><span class="sxs-lookup"><span data-stu-id="6a2be-114">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="6a2be-115">Sélectionnez le modèle **Application web ASP.NET** .</span><span class="sxs-lookup"><span data-stu-id="6a2be-115">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="6a2be-116">Entrez `NorthwindService` comme nom du projet.</span><span class="sxs-lookup"><span data-stu-id="6a2be-116">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="6a2be-117">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-117">Click **OK**.</span></span>

6. <span data-ttu-id="6a2be-118">Dans le menu **projet** , sélectionnez **Propriétés de NorthwindService**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-118">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="6a2be-119">Sélectionnez l’onglet **Web** , puis sélectionnez **utiliser le serveur Web IIS local**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-119">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="6a2be-120">Cliquez sur **créer un répertoire virtuel** , puis sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-120">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="6a2be-121">À partir de l'invite de commandes avec des privilèges d'administrateur, exécutez une des commandes suivantes (en fonction du système d'exploitation) :</span><span class="sxs-lookup"><span data-stu-id="6a2be-121">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="6a2be-122">Systèmes 32 bits :</span><span class="sxs-lookup"><span data-stu-id="6a2be-122">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="6a2be-123">Systèmes 64 bits :</span><span class="sxs-lookup"><span data-stu-id="6a2be-123">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="6a2be-124">Cela permet de vérifier que Windows Communication Foundation (WCF) est inscrit sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6a2be-124">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="6a2be-125">À partir de l'invite de commandes avec des privilèges d'administrateur, exécutez une des commandes suivantes (en fonction du système d'exploitation) :</span><span class="sxs-lookup"><span data-stu-id="6a2be-125">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="6a2be-126">Systèmes 32 bits :</span><span class="sxs-lookup"><span data-stu-id="6a2be-126">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="6a2be-127">Systèmes 64 bits :</span><span class="sxs-lookup"><span data-stu-id="6a2be-127">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="6a2be-128">Cela permet de s'assurer qu'IIS s'exécute correctement après que WCF a été installé sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6a2be-128">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="6a2be-129">Vous devrez peut-être redémarrer IIS.</span><span class="sxs-lookup"><span data-stu-id="6a2be-129">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="6a2be-130">Lorsque l'application ASP.NET s'exécute sur IIS7, vous devez aussi effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a2be-130">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="6a2be-131">Ouvrez le gestionnaire des services Internet et accédez à l’application PhotoService sous **site Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-131">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="6a2be-132">Dans l'affichage **Fonctionnalités**, double-cliquez sur **Authentification**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-132">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="6a2be-133">Dans la page **Authentification**, sélectionnez **Authentification anonyme**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-133">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="6a2be-134">Dans le volet **actions** , cliquez sur **modifier** pour définir le principal de sécurité sous lequel les utilisateurs anonymes se connecteront au site.</span><span class="sxs-lookup"><span data-stu-id="6a2be-134">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="6a2be-135">Dans la boîte de dialogue **modifier les informations d’identification d’authentification anonyme** , sélectionnez **identité du pool d’applications**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-135">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="6a2be-136">Lorsque vous utilisez le compte de service réseau, vous accordez aux utilisateurs anonymes l'accès à tout le réseau interne associé à ce compte.</span><span class="sxs-lookup"><span data-stu-id="6a2be-136">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="6a2be-137">En utilisant SQL Server Management Studio, l'utilitaire sqlcmd.exe ou l'Éditeur Transact-SQL dans Visual Studio, exécutez la commande Transact-SQL suivante sur l'instance SQL Server à laquelle la base de données Northwind est attachée :</span><span class="sxs-lookup"><span data-stu-id="6a2be-137">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="6a2be-138">Cela crée une connexion dans l'instance SQL Server pour le compte Windows utilisé pour exécuter IIS.</span><span class="sxs-lookup"><span data-stu-id="6a2be-138">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="6a2be-139">Cela permet à IIS de se connecter à l'instance de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6a2be-139">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="6a2be-140">Avec la base de données Northwind attachée, exécutez les commandes Transact-SQL suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a2be-140">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

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

    <span data-ttu-id="6a2be-141">Cela accorde des droits à la nouvelle connexion et permet à IIS de lire et d'écrire les données dans la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="6a2be-141">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="6a2be-142">Définir le modèle de données</span><span class="sxs-lookup"><span data-stu-id="6a2be-142">Define the data model</span></span>

1. <span data-ttu-id="6a2be-143">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet ASP.net, puis cliquez sur **Ajouter**  >  **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-143">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="6a2be-144">Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-144">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="6a2be-145">Pour le nom du modèle de données, tapez `Northwind.edmx` .</span><span class="sxs-lookup"><span data-stu-id="6a2be-145">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="6a2be-146">Dans l’Assistant Entity Data Model, sélectionnez **générer à partir de la base de données**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-146">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="6a2be-147">Connectez le modèle de données à la base de données en procédant de l’une des manières suivantes, puis cliquez sur **suivant**:</span><span class="sxs-lookup"><span data-stu-id="6a2be-147">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="6a2be-148">Si aucune connexion de base de données n’est déjà configurée, cliquez sur **nouvelle connexion** et créez une nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="6a2be-148">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="6a2be-149">Pour plus d'informations, consultez [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="6a2be-149">For more information, see [How to: Create Connections to SQL Server Databases](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="6a2be-150">Cette instance SQL Server doit avoir l'exemple de base de données Northwind joint.</span><span class="sxs-lookup"><span data-stu-id="6a2be-150">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="6a2be-151">\- ou -</span><span class="sxs-lookup"><span data-stu-id="6a2be-151">\- or -</span></span>

    - <span data-ttu-id="6a2be-152">Si vous avez une connexion de base de données déjà configurée pour vous connecter à la base de données Northwind, sélectionnez cette connexion dans la liste des connexions.</span><span class="sxs-lookup"><span data-stu-id="6a2be-152">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="6a2be-153">Dans la page finale de l'Assistant, activez les cases à cocher pour toutes les tables de la base de données puis désactivez les cases pour les vues et les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="6a2be-153">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="6a2be-154">Cliquez sur **Terminer** pour fermer l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="6a2be-154">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="6a2be-155">Créer le service de données</span><span class="sxs-lookup"><span data-stu-id="6a2be-155">Create the data service</span></span>

1. <span data-ttu-id="6a2be-156">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet ASP.net, puis cliquez sur **Ajouter**  >  **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-156">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="6a2be-157">Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **service de données WCF**.</span><span class="sxs-lookup"><span data-stu-id="6a2be-157">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Modèle d’élément de service de données WCF dans Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="6a2be-159">Le modèle de **service de données WCF** est disponible dans visual studio 2015, mais pas dans visual studio 2017 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="6a2be-159">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="6a2be-160">Pour le nom du service, entrez `Northwind` .</span><span class="sxs-lookup"><span data-stu-id="6a2be-160">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="6a2be-161">Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="6a2be-161">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="6a2be-162">La fenêtre de l'éditeur de code s'ouvre par défaut.</span><span class="sxs-lookup"><span data-stu-id="6a2be-162">By default, the code-editor window opens.</span></span> <span data-ttu-id="6a2be-163">Dans **Explorateur de solutions**, le service porte le nom, Northwind et l’extension. svc.cs ou. svc. vb.</span><span class="sxs-lookup"><span data-stu-id="6a2be-163">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="6a2be-164">Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="6a2be-164">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="6a2be-165">La définition de classe doit ressembler aux éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="6a2be-165">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="6a2be-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a2be-166">See also</span></span>

- [<span data-ttu-id="6a2be-167">Exposition de vos données comme service</span><span class="sxs-lookup"><span data-stu-id="6a2be-167">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
