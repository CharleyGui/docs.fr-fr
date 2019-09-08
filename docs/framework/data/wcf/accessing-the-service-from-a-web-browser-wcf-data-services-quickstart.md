---
title: Accès au service à partir d'un navigateur Web (démarrage rapide des services de données WCF)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: eb7f1c97722b45a93c310fb8bcbdb42beece2553
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780543"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="d8e2b-102">Accès au service à partir d'un navigateur Web (démarrage rapide des services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="d8e2b-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="d8e2b-103">Il s’agit de la deuxième tâche du démarrage rapide WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-103">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="d8e2b-104">Au cours de cette tâche, vous allez démarrer le WCF Data Services à partir de Visual Studio et éventuellement désactiver la lecture de flux dans le navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-104">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="d8e2b-105">Vous récupérez ensuite le document de définition de service, ainsi que les ressources du service de données en soumettant des requêtes HTTP d’accès via un navigateur Web aux ressources exposées.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-105">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="d8e2b-106">Par défaut, Visual Studio affecte automatiquement un numéro de port à l'URI `localhost` sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-106">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="d8e2b-107">Cette tâche utilise le numéro de port `12345` dans les exemples d’URI.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-107">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="d8e2b-108">Pour plus d’informations sur la définition d’un numéro de port spécifique dans votre projet Visual Studio, consultez [création du service de données](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="d8e2b-108">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="d8e2b-109">Pour demander le document de service par défaut à l'aide d'Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="d8e2b-109">To request the default service document by using Internet Explorer</span></span>

1. <span data-ttu-id="d8e2b-110">Dans Internet Explorer, dans le menu **Outils** , sélectionnez **Options Internet**, cliquez sur l’onglet **contenu** , cliquez sur **paramètres**, puis désactivez l' **affichage des flux**.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-110">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="d8e2b-111">Cette opération garantit que la lecture de flux est désactivée.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-111">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="d8e2b-112">Si vous ne désactivez pas cette fonctionnalité, le navigateur Web traitera le document encodé AtomPub retourné comme un flux XML au lieu d'afficher les données XML brutes.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-112">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d8e2b-113">Si votre navigateur ne peut pas afficher le flux sous forme de données XML brutes, vous devriez encore être en mesure de voir le flux sous forme de code source de la page.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-113">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2. <span data-ttu-id="d8e2b-114">Dans Visual Studio, appuyez sur la touche **F5** pour démarrer le débogage de l’application.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-114">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3. <span data-ttu-id="d8e2b-115">Ouvrez un navigateur Web sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-115">Open a Web browser on the local computer.</span></span> <span data-ttu-id="d8e2b-116">Dans la barre d'adresses, entrez l'URI suivant :</span><span class="sxs-lookup"><span data-stu-id="d8e2b-116">In the address bar, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="d8e2b-117">Cette opération retourne le document du service par défaut qui contient une liste des jeux d'entités exposés par ce service de données.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-117">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="d8e2b-118">Pour accéder aux ressources de jeu d'entités depuis un navigateur Web</span><span class="sxs-lookup"><span data-stu-id="d8e2b-118">To access entity set resources from a Web browser</span></span>

1. <span data-ttu-id="d8e2b-119">Dans la barre d'adresse de votre navigateur Web, entrez l'URI suivant :</span><span class="sxs-lookup"><span data-stu-id="d8e2b-119">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="d8e2b-120">Cette opération retourne un jeu de tous les clients dans l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-120">This returns a set of all customers in the Northwind sample database.</span></span>

2. <span data-ttu-id="d8e2b-121">Dans la barre d'adresse de votre navigateur Web, entrez l'URI suivant :</span><span class="sxs-lookup"><span data-stu-id="d8e2b-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="d8e2b-122">Cette opération retourne une instance d'entité pour le client spécifique, `ALFKI`.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-122">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3. <span data-ttu-id="d8e2b-123">Dans la barre d'adresse de votre navigateur Web, entrez l'URI suivant :</span><span class="sxs-lookup"><span data-stu-id="d8e2b-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="d8e2b-124">Cette opération parcourt la relation entre les clients et les ordres pour retourner un jeu de tous les ordres pour le client `ALFKI` spécifique.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-124">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4. <span data-ttu-id="d8e2b-125">Dans la barre d'adresse de votre navigateur Web, entrez l'URI suivant :</span><span class="sxs-lookup"><span data-stu-id="d8e2b-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="d8e2b-126">Cette opération filtre des ordres qui appartiennent au client `ALFKI` spécifique afin que seul un ordre spécifique soit retourné selon la valeur `OrderID` fournie.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-126">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d8e2b-127">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d8e2b-127">Next Steps</span></span>

<span data-ttu-id="d8e2b-128">Vous avez correctement accédé à la WCF Data Services à partir d’un navigateur Web, le navigateur émettant des demandes HTTP obtenir aux ressources spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-128">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="d8e2b-129">Un navigateur Web fournit un moyen simple d'expérimenter la syntaxe d'adressage des demandes et d'afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-129">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="d8e2b-130">Toutefois, un service des données de production n'est pas accessible en général par cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-130">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="d8e2b-131">Généralement, les applications interagissent avec le service de données par le biais de code d'application ou de langages de script.</span><span class="sxs-lookup"><span data-stu-id="d8e2b-131">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="d8e2b-132">Ensuite, vous allez créer une application cliente qui utilise des bibliothèques clientes pour accéder aux ressources du service des données comme s'il s'agissait d'objets CLR (Common Language runtime) :</span><span class="sxs-lookup"><span data-stu-id="d8e2b-132">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d8e2b-133">Création de l’application cliente du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d8e2b-133">Creating the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="d8e2b-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8e2b-134">See also</span></span>

- [<span data-ttu-id="d8e2b-135">Accès aux ressources d’un service de données</span><span class="sxs-lookup"><span data-stu-id="d8e2b-135">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
