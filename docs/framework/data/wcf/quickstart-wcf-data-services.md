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
# <a name="quickstart-wcf-data-services"></a>Démarrage rapide (services de données WCF)

Ce quickstart vous aide à vous familiariser avec les services de données WCF et le protocole de données ouvertes (OData) à travers une série de tâches qui prennent en charge les sujets de [Getting Started](getting-started-with-wcf-data-services.md).

## <a name="what-youll-learn"></a>Ce que vous allez apprendre

La première tâche dans ce quickstart montre comment créer un service de données pour exposer un flux OData à partir de la base de données de l’échantillon Northwind. Dans des sujets ultérieurs, vous accéderez au flux OData en utilisant un navigateur Web, et créerez également une application client de la Fondation de présentation Windows (WPF) qui consomme le flux OData en utilisant les bibliothèques clientes.

## <a name="prerequisites"></a>Prérequis

Pour compléter ce démarrage rapide, installez les composants suivants :

- Visual Studio

- Un exemple de SQL Server. Cela inclut SQL Server Express, qui est inclus dans une installation par défaut de Visual Studio 2015, ou dans le cadre de la charge de travail de **stockage et de traitement** des données dans Visual Studio 2017 ou plus tard.

- Exemple de base de données Northwind. Pour installer la base de données, exécutez le script Transact-SQL à partir de [Northwind et pubs échantillons de bases](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)de données pour Microsoft SQL Server .

## <a name="wcf-data-services-quickstart-tasks"></a>WCF data services quickstart tâches

 [Créer le service de données](creating-the-data-service.md)

 Définir l'application ASP.NET, définir le modèle de données, créer le service de données et autoriser l'accès aux ressources.

 [Accédez au Service à partir d’un navigateur Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 Démarrez le service à partir de Visual Studio et accédez au service en soumettant des demandes HTTP GET via un navigateur Web au flux exposé.

 [Créer l’application client cadre .NET](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 Créez une application WPF pour consommer le flux OData, lier les données aux contrôles Windows, modifier les données dans les contrôles consolidés, puis renvoyer les modifications au service de données.

> [!NOTE]
> Les fichiers de projet d’une version complétée du quickstart peuvent être téléchargés à partir de [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Démarrer rapidement](creating-the-data-service.md)

## <a name="see-also"></a>Voir aussi

- [ADO.NET Entity Framework](../adonet/ef/index.md)
