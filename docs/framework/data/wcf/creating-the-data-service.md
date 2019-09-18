---
title: Créer un service de données WCF dans Visual Studio
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: 582f5f2d6d82613736ed795eebe5129284cdac6e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052981"
---
# <a name="create-the-data-service"></a><span data-ttu-id="896d6-102">Créer le service de données</span><span class="sxs-lookup"><span data-stu-id="896d6-102">Create the data service</span></span>

<span data-ttu-id="896d6-103">Dans cette rubrique, vous allez créer un exemple de service de données qui utilise WCF Data Services [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] pour exposer un flux basé sur l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="896d6-103">In this topic, you create a sample data service that uses WCF Data Services to expose an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="896d6-104">La tâche implique les étapes fondamentales suivantes :</span><span class="sxs-lookup"><span data-stu-id="896d6-104">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="896d6-105">Créez une application Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="896d6-105">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="896d6-106">Définissez le modèle de données à l'aide des outils Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="896d6-106">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="896d6-107">Ajoutez le service de données à l'application Web.</span><span class="sxs-lookup"><span data-stu-id="896d6-107">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="896d6-108">Activez l'accès au service de données.</span><span class="sxs-lookup"><span data-stu-id="896d6-108">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="896d6-109">Créer l’application Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="896d6-109">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="896d6-110">Dans Visual Studio, dans le menu **fichier** , sélectionnez **nouveau** > **projet**.</span><span class="sxs-lookup"><span data-stu-id="896d6-110">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="896d6-111">Dans la boîte de dialogue **nouveau projet** , sous Visual Basic ou visuel C# , sélectionnez la catégorie **Web** , puis sélectionnez **application Web ASP.net**.</span><span class="sxs-lookup"><span data-stu-id="896d6-111">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="896d6-112">Entrez `NorthwindService` comme nom du projet, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="896d6-112">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="896d6-113">Dans la boîte de dialogue **nouvelle application Web ASP.net** , sélectionnez **vide** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="896d6-113">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="896d6-114">(Facultatif) Spécifiez un numéro de port spécifique pour votre application Web.</span><span class="sxs-lookup"><span data-stu-id="896d6-114">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="896d6-115">Remarque : le numéro `12345` de port est utilisé dans cette série de rubriques de démarrage rapide.</span><span class="sxs-lookup"><span data-stu-id="896d6-115">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="896d6-116">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet ASP.net que vous venez de créer, puis choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="896d6-116">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="896d6-117">Sélectionnez l’onglet **Web** et définissez la valeur de la zone de texte **port spécifique** sur `12345`.</span><span class="sxs-lookup"><span data-stu-id="896d6-117">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="896d6-118">Définir le modèle de données</span><span class="sxs-lookup"><span data-stu-id="896d6-118">Define the data model</span></span>

1. <span data-ttu-id="896d6-119">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet ASP.net, puis cliquez sur **Ajouter** > **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="896d6-119">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="896d6-120">Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez la catégorie **données** , puis sélectionnez **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="896d6-120">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="896d6-121">Pour le nom du modèle de données, entrez `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="896d6-121">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="896d6-122">Dans l' **assistant Entity Data Model**, sélectionnez le **Concepteur EF à partir de la base de données**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="896d6-122">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="896d6-123">Connectez le modèle de données à la base de données en procédant de l’une des manières suivantes, puis cliquez sur **suivant**:</span><span class="sxs-lookup"><span data-stu-id="896d6-123">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="896d6-124">Si aucune connexion de base de données n’est déjà configurée, cliquez sur **nouvelle connexion** et créez une nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="896d6-124">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="896d6-125">Pour plus d'informations, voir [Procédure : Créer des connexions aux bases de](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90))données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="896d6-125">For more information, see [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="896d6-126">Cette instance SQL Server doit avoir l'exemple de base de données Northwind joint.</span><span class="sxs-lookup"><span data-stu-id="896d6-126">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="896d6-127">\- ou -</span><span class="sxs-lookup"><span data-stu-id="896d6-127">\- or -</span></span>

    - <span data-ttu-id="896d6-128">Si vous avez une connexion de base de données déjà configurée pour vous connecter à la base de données Northwind, sélectionnez cette connexion dans la liste des connexions.</span><span class="sxs-lookup"><span data-stu-id="896d6-128">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="896d6-129">Dans la page finale de l'Assistant, activez les cases à cocher pour toutes les tables de la base de données puis désactivez les cases pour les vues et les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="896d6-129">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="896d6-130">Cliquez sur **Terminer** pour fermer l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="896d6-130">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="896d6-131">Créer le service de données WCF</span><span class="sxs-lookup"><span data-stu-id="896d6-131">Create the WCF data service</span></span>

1. <span data-ttu-id="896d6-132">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet ASP.net, puis choisissez **Ajouter** > **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="896d6-132">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="896d6-133">Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez le modèle élément de **service de données WCF** dans la catégorie **Web** .</span><span class="sxs-lookup"><span data-stu-id="896d6-133">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Modèle d’élément de service de données WCF dans Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="896d6-135">Le modèle de **service de données WCF** est disponible dans visual studio 2015, mais pas dans visual studio 2017.</span><span class="sxs-lookup"><span data-stu-id="896d6-135">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="896d6-136">Pour le nom du service, tapez `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="896d6-136">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="896d6-137">Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="896d6-137">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="896d6-138">La fenêtre de l'éditeur de code s'ouvre par défaut.</span><span class="sxs-lookup"><span data-stu-id="896d6-138">By default, the code-editor window opens.</span></span> <span data-ttu-id="896d6-139">Dans **Explorateur de solutions**, le service porte le nom Northwind avec l’extension *. svc.cs* ou *. svc. vb*.</span><span class="sxs-lookup"><span data-stu-id="896d6-139">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="896d6-140">Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="896d6-140">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="896d6-141">La définition de classe doit ressembler aux éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="896d6-141">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="896d6-142">Activer l’accès aux ressources du service de données</span><span class="sxs-lookup"><span data-stu-id="896d6-142">Enable access to data service resources</span></span>

1. <span data-ttu-id="896d6-143">Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="896d6-143">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="896d6-144">Cela permet aux clients autorisés d'accéder aux ressources en lecture et en écriture pour les jeux d'entités spécifiés.</span><span class="sxs-lookup"><span data-stu-id="896d6-144">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="896d6-145">Tout client qui peut accéder à l'application ASP.NET peut également accéder aux ressources exposées par le service de données.</span><span class="sxs-lookup"><span data-stu-id="896d6-145">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="896d6-146">Dans un service de données de production, pour empêcher l'accès non autorisé aux ressources, vous devez également sécuriser l'application elle-même.</span><span class="sxs-lookup"><span data-stu-id="896d6-146">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="896d6-147">Pour plus d'informations, consultez [Securing WCF Data Services](securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="896d6-147">For more information, see [Securing WCF Data Services](securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="896d6-148">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="896d6-148">Next steps</span></span>

<span data-ttu-id="896d6-149">Vous avez correctement créé un nouveau service de données qui expose un flux OData basé sur l’exemple de base de données Northwind, et vous avez activé l’accès au flux pour les clients qui ont des autorisations sur l’application Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="896d6-149">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="896d6-150">Ensuite, vous allez démarrer le service de données à partir de Visual Studio et accéder au flux OData en soumettant des demandes HTTP d’extraction via un navigateur Web :</span><span class="sxs-lookup"><span data-stu-id="896d6-150">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="896d6-151">Accéder au service à partir d’un navigateur Web</span><span class="sxs-lookup"><span data-stu-id="896d6-151">Access the service from a web browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="896d6-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="896d6-152">See also</span></span>

- <span data-ttu-id="896d6-153">[Outils de Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="896d6-153">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
