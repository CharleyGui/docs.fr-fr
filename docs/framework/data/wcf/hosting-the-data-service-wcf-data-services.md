---
title: Hébergement du service de données (services de données WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: 5dfa1d9f02f660b55ecf6598ef5012174a1ba853
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172591"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>Hébergement du service de données (services de données WCF)

À l’aide de WCF Data Services, vous pouvez créer un service qui expose les données sous forme de flux OData (Open Data Protocol). Ce service de données est défini comme une classe qui hérite de <xref:System.Data.Services.DataService%601>. Cette classe fournit les fonctionnalités requises pour traiter les messages de demande, effectuer des mises à jour sur la source de données et générer des messages de réponse, comme requis par OData. Toutefois, un service de données ne peut pas se lier à un socket de réseau et écouter les requêtes HTTP entrantes. Pour ces fonctionnalités requises, le service de données s'appuie sur un composant d'hébergement.

 L’hôte du service de données effectue les tâches suivantes pour le compte du service de données :

- Écoute les demandes et les transmet au service de données.

- Crée une instance du service de données pour chaque demande.

- Demande au service de données de traiter la requête entrante.

- Envoie la réponse de la part du service de données.

 Pour simplifier l’hébergement d’un service de données, WCF Data Services est conçu pour s’intégrer à Windows Communication Foundation (WCF). Le service de données fournit une implémentation WCF par défaut qui sert d’hôte de service de données dans une application ASP.NET. Vous pouvez donc héberger un service de données de l'une des façons suivantes :

- Dans une application ASP.NET.

- Dans une application managée qui prend en charge des services WCF auto-hébergés.

- Dans un autre hôte de service de données personnalisé.

## <a name="hosting-a-data-service-in-an-aspnet-application"></a>Hébergement de services de données dans une application ASP.NET

Quand vous utilisez la boîte de dialogue **Ajouter un nouvel élément** dans Visual Studio 2015 pour définir un service de données dans une application ASP.net, l’outil génère deux nouveaux fichiers dans le projet. Le premier fichier a une extension `.svc` et indique à l’exécution WCF comment instancier le service de données. Voici un exemple de ce fichier pour l’exemple de service de données Northwind créé lorsque vous terminez le [démarrage rapide](quickstart-wcf-data-services.md):

```aspx-csharp
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 Cette directive dit à l'application de créer l'hôte de service pour la classe de service de données nommée en utilisant la classe <xref:System.Data.Services.DataServiceHostFactory>.

 La page code-behind du fichier `.svc` contient la classe constituant l'implémentation du service de données lui-même, défini comme suit dans le cas de l'exemple de service de données Northwind :

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 Comme un service de données se comporte comme un service WCF, le service de données s’intègre à ASP.NET et suit le modèle de programmation Web WCF. Pour plus d’informations, consultez [services WCF et ASP.net](../../wcf/feature-details/wcf-services-and-aspnet.md) et [modèle de programmation http Web WCF](../../wcf/feature-details/wcf-web-http-programming-model.md).

## <a name="self-hosted-wcf-services"></a>Services WCF auto-hébergés

 Étant donné qu’il intègre une implémentation WCF, WCF Data Services prendre en charge l’auto-hébergement d’un service de données en tant que service WCF. Un service peut être auto-hébergé dans n’importe quelle application .NET Framework, telle qu’une application console. La classe <xref:System.Data.Services.DataServiceHost>, qui hérite de <xref:System.ServiceModel.Web.WebServiceHost>, est utilisée pour instancier le service de données à une adresse spécifique.

 L'auto-hébergement peut être utilisé pour le développement et les tests parce qu'elle permet de simplifier le déploiement et le dépannage du service. Toutefois, ce type d’hébergement ne fournit pas les fonctionnalités d’hébergement et de gestion avancées fournies par ASP.NET ou par Internet Information Services (IIS). Pour plus d’informations, consultez [hébergement dans une application managée](../../wcf/feature-details/hosting-in-a-managed-application.md).

## <a name="defining-a-custom-data-service-host"></a>Définition d'un hôte de service de données personnalisé

 Dans les cas où l'implémentation hôte de WCF est trop restrictive, vous pouvez également définir un hôte personnalisé pour un service de données. Toute classe qui implémente l'interface <xref:System.Data.Services.IDataServiceHost> peut être utilisée comme hôte de réseau pour un service de données. Un hôte personnalisé doit implémenter l'interface <xref:System.Data.Services.IDataServiceHost> et pouvoir gérer les responsabilités de base suivantes de l'hôte de service de données :

- Fournir le service de données avec le chemin d’accès racine du service.

- Traiter les informations d'en-tête de demande et de réponse à l'implémentation appropriée du membre <xref:System.Data.Services.IDataServiceHost>.

- Gérer les exceptions déclenchées par le service de données.

- Valider les paramètres de la chaîne de requête.

## <a name="see-also"></a>Voir aussi

- [Définition des services de données WCF](defining-wcf-data-services.md)
- [Exposition de vos données comme service](exposing-your-data-as-a-service-wcf-data-services.md)
- [Configuration du service de données](configuring-the-data-service-wcf-data-services.md)
