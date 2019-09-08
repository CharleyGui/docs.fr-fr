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
# <a name="quickstart-wcf-data-services"></a>Démarrage rapide (services de données WCF)

Ce guide de démarrage rapide vous permet de vous familiariser avec WCF Data Services et le par le [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] biais d’une série de tâches qui prennent en charge les rubriques de [prise en main](getting-started-with-wcf-data-services.md).

## <a name="what-youll-learn"></a>Ce que vous allez apprendre

La première tâche de ce guide de démarrage rapide montre comment créer un service de données pour exposer un flux OData à partir de l’exemple de base de données Northwind. Dans les rubriques ultérieures, vous accéderez au flux OData à l’aide d’un navigateur Web et vous créerez également une application cliente Windows Presentation Foundation (WPF) qui consomme le flux OData à l’aide des bibliothèques clientes.

## <a name="prerequisites"></a>Prérequis

Pour effectuer ce démarrage rapide, vous devez installer les composants suivants :

- Visual Studio

- Instance de SQL Server. Cela inclut SQL Server Express, qui est inclus dans une installation par défaut de Visual Studio 2015 ou dans le cadre de la charge de travail **stockage et traitement des données** dans visual studio 2017.

- Exemple de base de données Northwind. Pour télécharger cet exemple de base de données, consultez la page de téléchargement, [Exemples de bases de données pour SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).

## <a name="wcf-data-services-quickstart-tasks"></a>Tâches de démarrage rapide de WCF Data Services

 [Créer le service de données](creating-the-data-service.md)

 Définir l'application ASP.NET, définir le modèle de données, créer le service de données et autoriser l'accès aux ressources.

 [Accéder au service à partir d’un navigateur Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 Démarrez le service à partir de Visual Studio et accédez au service en soumettant des demandes HTTP d’extraction via un navigateur Web au flux exposé.

 [Créer l’application cliente .NET Framework](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 Créer une application WPF pour consommer le flux OData, lier des données aux contrôles Windows, modifier les données dans les contrôles liés, puis renvoyer les modifications au service de données.

> [!NOTE]
> Les fichiers projet d’une version terminée du démarrage rapide peuvent être téléchargés à partir de la page [WCF Data Services Quickstart (OData Service and WPF Client)](https://go.microsoft.com/fwlink/?LinkId=179994) .

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Démarrer le démarrage rapide](creating-the-data-service.md)

## <a name="see-also"></a>Voir aussi

- [ADO.NET Entity Framework](../adonet/ef/index.md)
