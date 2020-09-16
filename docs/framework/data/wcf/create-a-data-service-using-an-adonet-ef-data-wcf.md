---
title: 'Comment : créer un service de données à l’aide d’une source de données Entity Framework ADO.NET (services de données WCF)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 1e559488a3260fafe6c211ff47226a258fc1289a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557695"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="7aa9b-102">Comment : créer un service de données à l’aide d’une source de données Entity Framework ADO.NET (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="7aa9b-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>

<span data-ttu-id="7aa9b-103">WCF Data Services expose les données d’entité en tant que service de données.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="7aa9b-104">Ces données d’entité sont fournies par l’infrastructure ADO. NETEntity Framework lorsque la source de données est une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-104">This entity data is provided by the ADO.NETEntity Framework when the data source is a relational database.</span></span> <span data-ttu-id="7aa9b-105">Cette rubrique vous indique comment créer un modèle de données basé sur Entity Framework dans une application Web Visual Studio qui repose sur une base de données existante et utilise ce modèle de données pour créer un service de données.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-105">This topic shows you how to create an Entity Framework-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>

<span data-ttu-id="7aa9b-106">Entity Framework fournit également un outil en ligne de commande qui peut générer un modèle Entity Framework en dehors d'un projet Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-106">The Entity Framework also provides a command line tool that can generate an Entity Framework model outside of a Visual Studio project.</span></span> <span data-ttu-id="7aa9b-107">Pour plus d’informations, consultez [Comment : utiliser EdmGen.exe pour générer les fichiers de modèle et de mappage](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="7aa9b-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="7aa9b-108">Pour ajouter à une application Web existante un modèle Entity Framework qui repose sur une base de données existante</span><span class="sxs-lookup"><span data-stu-id="7aa9b-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>

1. <span data-ttu-id="7aa9b-109">Dans le menu **projet** , cliquez sur **Ajouter**  >  **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-109">On the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="7aa9b-110">Dans le volet **modèles** , cliquez sur la catégorie **données** , puis sélectionnez **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="7aa9b-111">Entrez le nom du modèle, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-111">Enter the model name and then click **Add**.</span></span>

     <span data-ttu-id="7aa9b-112">La première page de l'Assistant Entity Data Model s'affiche.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-112">The first page of the Entity Data Model Wizard is displayed.</span></span>

4. <span data-ttu-id="7aa9b-113">Dans la boîte de dialogue **choisir le contenu du Model** , sélectionnez **générer à partir de la base de données**.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="7aa9b-114">Cliquez ensuite sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-114">Then click **Next**.</span></span>

5. <span data-ttu-id="7aa9b-115">Cliquez sur le bouton **nouvelle connexion** .</span><span class="sxs-lookup"><span data-stu-id="7aa9b-115">Click the **New Connection** button.</span></span>

6. <span data-ttu-id="7aa9b-116">Dans la boîte de dialogue **Propriétés de connexion** , tapez le nom de votre serveur, sélectionnez la méthode d’authentification, tapez le nom de la base de données, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>

     <span data-ttu-id="7aa9b-117">La boîte de dialogue **choisir votre connexion de données** est mise à jour avec vos paramètres de connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-117">The **Choose Your Data Connection** dialog box is updated with your database connection settings.</span></span>

7. <span data-ttu-id="7aa9b-118">Vérifiez que la case à cocher **enregistrer les paramètres de connexion de l’entité dans App.Config en tant que :** est activée.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="7aa9b-119">Cliquez ensuite sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-119">Then click **Next**.</span></span>

8. <span data-ttu-id="7aa9b-120">Dans la boîte de dialogue **choisir vos objets de base de données** , sélectionnez tous les objets de base de données que vous envisagez d’exposer dans le service de données.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7aa9b-121">Les objets inclus dans le modèle de données ne sont pas exposés automatiquement par le service de données.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="7aa9b-122">Ils doivent être exposés explicitement par le service lui-même.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="7aa9b-123">Pour plus d’informations, consultez [configuration du service de données](configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7aa9b-123">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>

9. <span data-ttu-id="7aa9b-124">Cliquez sur **Terminer** pour terminer l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-124">Click **Finish** to complete the wizard.</span></span>

     <span data-ttu-id="7aa9b-125">Cela crée un modèle de données par défaut basé sur la base de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="7aa9b-126">Entity Framework permet de personnaliser le modèle de données. </span><span class="sxs-lookup"><span data-stu-id="7aa9b-126">The Entity Framework enables to customize the data model.</span></span> <span data-ttu-id="7aa9b-127">Pour plus d’informations, consultez [Entity Data Model des tâches d’outils](/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7aa9b-127">For more information, see [Entity Data Model Tools Tasks](/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span></span>

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="7aa9b-128">Pour créer le service de données à l'aide du nouveau modèle de données</span><span class="sxs-lookup"><span data-stu-id="7aa9b-128">To create the data service by using the new data model</span></span>

1. <span data-ttu-id="7aa9b-129">Dans Visual Studio, ouvrez le fichier .edmx qui représente le modèle de données.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-129">In Visual Studio, open the .edmx file that represents the data model.</span></span>

2. <span data-ttu-id="7aa9b-130">Dans l' **Explorateur de modèles**, cliquez avec le bouton droit sur le modèle, cliquez sur **Propriétés**, puis notez le nom du conteneur d’entités.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>

3. <span data-ttu-id="7aa9b-131">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet ASP.net, puis cliquez sur **Ajouter**  >  **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-131">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

4. <span data-ttu-id="7aa9b-132">Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez le modèle **service de données WCF** dans la catégorie **Web** .</span><span class="sxs-lookup"><span data-stu-id="7aa9b-132">In the **Add New Item** dialog box, select the **WCF Data Service** template in the **Web** category.</span></span>

   ![Modèle d’élément de service de données WCF dans Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="7aa9b-134">Le modèle de **service de données WCF** est disponible dans visual studio 2015, mais pas dans visual studio 2017 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-134">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

5. <span data-ttu-id="7aa9b-135">Fournissez un nom pour le service, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-135">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="7aa9b-136">Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-136">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="7aa9b-137">La fenêtre de l'éditeur de code s'ouvre par défaut.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-137">By default, the code-editor window opens.</span></span>

6. <span data-ttu-id="7aa9b-138">Dans le code pour le service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui hérite de la classe <xref:System.Data.Objects.ObjectContext> et qui correspond au conteneur d'entités du modèle de données, noté à l'étape 2.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-138">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>

7. <span data-ttu-id="7aa9b-139">Dans le code pour le service de données, permettez aux clients autorisés d'accéder aux jeux d'entités exposés par le service de données.</span><span class="sxs-lookup"><span data-stu-id="7aa9b-139">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="7aa9b-140">Pour plus d’informations, consultez [création du service de données](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="7aa9b-140">For more information, see [Creating the Data Service](creating-the-data-service.md).</span></span>

8. <span data-ttu-id="7aa9b-141">Pour tester le service de données Northwind. svc à l’aide d’un navigateur Web, suivez les instructions de la rubrique [accès au service à partir d’un navigateur Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="7aa9b-141">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7aa9b-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7aa9b-142">See also</span></span>

- [<span data-ttu-id="7aa9b-143">Définition des services de données WCF</span><span class="sxs-lookup"><span data-stu-id="7aa9b-143">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="7aa9b-144">Fournisseurs de services de données</span><span class="sxs-lookup"><span data-stu-id="7aa9b-144">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="7aa9b-145">Procédure : Créer un service de données à l’aide du fournisseur de réflexion</span><span class="sxs-lookup"><span data-stu-id="7aa9b-145">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="7aa9b-146">Procédure : Créer un service de données à l’aide d’une source de données LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7aa9b-146">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
