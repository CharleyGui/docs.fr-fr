---
title: Démarrage rapide (services de données WCF)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f945d33a4fc789b3c73c1c80040fc8527301758b
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121225"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="6c815-102">Démarrage rapide (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="6c815-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="6c815-103">Ce quickstart vous aide à vous familiariser avec les services de données WCF et le protocole de données ouvertes (OData) à travers une série de tâches qui prennent en charge les sujets de [Getting Started](getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="6c815-103">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="6c815-104">Ce que vous allez apprendre</span><span class="sxs-lookup"><span data-stu-id="6c815-104">What you'll learn</span></span>

<span data-ttu-id="6c815-105">La première tâche dans ce quickstart montre comment créer un service de données pour exposer un flux OData à partir de la base de données de l’échantillon Northwind.</span><span class="sxs-lookup"><span data-stu-id="6c815-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="6c815-106">Dans des sujets ultérieurs, vous accéderez au flux OData en utilisant un navigateur Web, et créerez également une application client de la Fondation de présentation Windows (WPF) qui consomme le flux OData en utilisant les bibliothèques clientes.</span><span class="sxs-lookup"><span data-stu-id="6c815-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6c815-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="6c815-107">Prerequisites</span></span>

<span data-ttu-id="6c815-108">Pour compléter ce démarrage rapide, installez les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="6c815-108">To complete this quickstart, install the following components:</span></span>

- <span data-ttu-id="6c815-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6c815-109">Visual Studio</span></span>

- <span data-ttu-id="6c815-110">Un exemple de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6c815-110">An instance of SQL Server.</span></span> <span data-ttu-id="6c815-111">Cela inclut SQL Server Express, qui est inclus dans une installation par défaut de Visual Studio 2015, ou dans le cadre de la charge de travail de **stockage et de traitement** des données dans Visual Studio 2017 ou plus tard.</span><span class="sxs-lookup"><span data-stu-id="6c815-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017 or later.</span></span>

- <span data-ttu-id="6c815-112">Exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="6c815-112">The Northwind sample database.</span></span> <span data-ttu-id="6c815-113">Pour installer la base de données, exécutez le script Transact-SQL à partir de [Northwind et pubs échantillons de bases](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)de données pour Microsoft SQL Server .</span><span class="sxs-lookup"><span data-stu-id="6c815-113">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="6c815-114">WCF data services quickstart tâches</span><span class="sxs-lookup"><span data-stu-id="6c815-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="6c815-115">Créer le service de données</span><span class="sxs-lookup"><span data-stu-id="6c815-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="6c815-116">Définir l'application ASP.NET, définir le modèle de données, créer le service de données et autoriser l'accès aux ressources.</span><span class="sxs-lookup"><span data-stu-id="6c815-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="6c815-117">Accédez au Service à partir d’un navigateur Web</span><span class="sxs-lookup"><span data-stu-id="6c815-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="6c815-118">Démarrez le service à partir de Visual Studio et accédez au service en soumettant des demandes HTTP GET via un navigateur Web au flux exposé.</span><span class="sxs-lookup"><span data-stu-id="6c815-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="6c815-119">Créer l’application client cadre .NET</span><span class="sxs-lookup"><span data-stu-id="6c815-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="6c815-120">Créez une application WPF pour consommer le flux OData, lier les données aux contrôles Windows, modifier les données dans les contrôles consolidés, puis renvoyer les modifications au service de données.</span><span class="sxs-lookup"><span data-stu-id="6c815-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="6c815-121">Les fichiers de projet d’une version complétée du quickstart peuvent être téléchargés à partir de [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span><span class="sxs-lookup"><span data-stu-id="6c815-121">Project files from a completed version of the quickstart can be downloaded from [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6c815-122">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6c815-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6c815-123">Démarrer rapidement</span><span class="sxs-lookup"><span data-stu-id="6c815-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="6c815-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c815-124">See also</span></span>

- [<span data-ttu-id="6c815-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6c815-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
