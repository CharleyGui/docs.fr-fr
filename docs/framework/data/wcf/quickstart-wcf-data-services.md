---
title: Démarrage rapide (services de données WCF)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: df6806cd77e7ff109d79f7ba61866763de4c7fc1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790368"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="8fa6e-102">Démarrage rapide (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="8fa6e-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="8fa6e-103">Ce guide de démarrage rapide vous permet de vous familiariser avec WCF Data Services et le par le [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] biais d’une série de tâches qui prennent en charge les rubriques de [prise en main](getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8fa6e-103">This quickstart helps you become familiar with WCF Data Services and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="8fa6e-104">Ce que vous allez apprendre</span><span class="sxs-lookup"><span data-stu-id="8fa6e-104">What you'll learn</span></span>

<span data-ttu-id="8fa6e-105">La première tâche de ce guide de démarrage rapide montre comment créer un service de données pour exposer un flux OData à partir de l’exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="8fa6e-106">Dans les rubriques ultérieures, vous accéderez au flux OData à l’aide d’un navigateur Web et vous créerez également une application cliente Windows Presentation Foundation (WPF) qui consomme le flux OData à l’aide des bibliothèques clientes.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8fa6e-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="8fa6e-107">Prerequisites</span></span>

<span data-ttu-id="8fa6e-108">Pour effectuer ce démarrage rapide, vous devez installer les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="8fa6e-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="8fa6e-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8fa6e-109">Visual Studio</span></span>

- <span data-ttu-id="8fa6e-110">Instance de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-110">An instance of SQL Server.</span></span> <span data-ttu-id="8fa6e-111">Cela inclut SQL Server Express, qui est inclus dans une installation par défaut de Visual Studio 2015 ou dans le cadre de la charge de travail **stockage et traitement des données** dans visual studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017.</span></span>

- <span data-ttu-id="8fa6e-112">Exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-112">The Northwind sample database.</span></span> <span data-ttu-id="8fa6e-113">Pour télécharger cet exemple de base de données, consultez la page de téléchargement, [Exemples de bases de données pour SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="8fa6e-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="8fa6e-114">Tâches de démarrage rapide de WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="8fa6e-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="8fa6e-115">Créer le service de données</span><span class="sxs-lookup"><span data-stu-id="8fa6e-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="8fa6e-116">Définir l'application ASP.NET, définir le modèle de données, créer le service de données et autoriser l'accès aux ressources.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="8fa6e-117">Accéder au service à partir d’un navigateur Web</span><span class="sxs-lookup"><span data-stu-id="8fa6e-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="8fa6e-118">Démarrez le service à partir de Visual Studio et accédez au service en soumettant des demandes HTTP d’extraction via un navigateur Web au flux exposé.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="8fa6e-119">Créer l’application cliente .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8fa6e-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="8fa6e-120">Créer une application WPF pour consommer le flux OData, lier des données aux contrôles Windows, modifier les données dans les contrôles liés, puis renvoyer les modifications au service de données.</span><span class="sxs-lookup"><span data-stu-id="8fa6e-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="8fa6e-121">Les fichiers projet d’une version terminée du démarrage rapide peuvent être téléchargés à partir de la page [WCF Data Services Quickstart (OData Service and WPF Client)](https://go.microsoft.com/fwlink/?LinkId=179994) .</span><span class="sxs-lookup"><span data-stu-id="8fa6e-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8fa6e-122">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8fa6e-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8fa6e-123">Démarrer le démarrage rapide</span><span class="sxs-lookup"><span data-stu-id="8fa6e-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="8fa6e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fa6e-124">See also</span></span>

- [<span data-ttu-id="8fa6e-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8fa6e-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
