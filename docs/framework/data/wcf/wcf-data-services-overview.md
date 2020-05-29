---
title: Vue d'ensemble des services de données WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services
- WCF Data Services, about
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
ms.openlocfilehash: e4c5bc03038a3df9df2b7629da762caee175b6e8
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202146"
---
# <a name="wcf-data-services-overview"></a>Vue d'ensemble des services de données WCF
WCF Data Services permet la création et la consommation de services de données pour le Web ou un intranet à l’aide de la Open Data Protocol (OData). OData vous permet d’exposer vos données sous forme de ressources adressables par des URI. Cela vous permet d'accéder et de modifier des données en utilisant la sémantique REST (Representational State Transfer), en particulier les verbes HTTP standard GET, PUT, POST et DELETE. Cette rubrique fournit une vue d’ensemble des modèles et des pratiques définis par OData, ainsi que des fonctionnalités fournies par WCF Data Services pour tirer parti d’OData dans les applications basées sur .NET Framework.  
  
## <a name="address-data-as-resources"></a>Adresser des données comme ressources  
 OData expose les données sous forme de ressources adressables par des URI. Les chemins d'accès aux ressources sont construits selon les conventions de relation d'entité de l'Entity Data Model. Dans ce modèle, les entités représentent des unités opérationnelles de données dans un domaine d'application, par exemple les clients, les commandes, les éléments et les produits. Pour plus d’informations, consultez [Entity Data Model](../adonet/entity-data-model.md).  
  
 Dans OData, vous adressez des ressources d’entité en tant que jeu d’entités qui contient des instances de types d’entité. Par exemple, l’URI `https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` retourne toutes les commandes du service de `Northwind` données qui sont liées au client dont la valeur est `CustomerID``ALFKI.`  
  
 Les expressions de requête vous permettent d'effectuer des opérations de requête traditionnelles sur des ressources, telles que filtrer, trier et paginer. Par exemple, l'URI `https://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` filtre les ressources de façon à retourner uniquement les commandes dont le coût de fret est supérieur à 50 $. Pour plus d’informations, consultez [accès aux ressources du service de données](accessing-data-service-resources-wcf-data-services.md).  
  
## <a name="interoperable-data-access"></a>Accès aux données interopérables  
 OData s’appuie sur les protocoles Internet standard pour permettre l’interopérabilité des services de données avec les applications qui n’utilisent pas le .NET Framework. Comme vous pouvez faire appel à des URI standard pour adresser des données, votre application peut accéder à des données et les modifier en utilisant la sémantique REST, en particulier les verbes HTTP standard GET, PUT, POST et DELETE. De cette manière, vous pouvez accéder à ces services depuis tout client qui peut analyser et accéder aux données transmises sur des protocoles HTTP standard.  
  
OData définit un ensemble d’extensions pour le protocole de publication Atom (AtomPub). Il prend en charge les requêtes et les réponses HTTP sous plusieurs formats de données pour prendre en charge des plateformes et des applications clientes diverses. Un flux OData peut représenter des données dans Atom, JavaScript Object Notation (JSON) et au format XML brut. Bien qu'Atom soit le format par défaut, le format du flux est spécifié dans l'en-tête de la requête HTTP. Pour plus d’informations, consultez [OData : format Atom](https://www.odata.org/documentation/odata-version-2-0/atom-format/) et [ODATA : format JSON](https://www.odata.org/documentation/odata-version-2-0/json-format/).  
  
 Lors de la publication de données sous forme de flux OData, WCF Data Services s’appuie sur d’autres fonctionnalités Internet existantes pour des opérations telles que la mise en cache et l’authentification. Pour ce faire, WCF Data Services s’intègre aux applications et services d’hébergement existants, tels que ASP.NET, Windows Communication Foundation (WCF) et Internet Information Services (IIS).  
  
## <a name="storage-independence"></a>Indépendance du stockage  
 Bien que les ressources soient adressées selon un modèle de relation d’entité, WCF Data Services exposer des flux OData, quelle que soit la source de données sous-jacente. Une fois que WCF Data Services accepte une requête HTTP pour une ressource identifiée par un URI, la demande est désérialisée et une représentation de cette demande est transmise à un fournisseur WCF Data Services. Ce fournisseur traduit la demande dans un format spécifique à la source de données et exécute la demande sur la source de données sous-jacente. WCF Data Services atteint l’indépendance du stockage en séparant le modèle conceptuel qui traite les ressources prescrites par OData du schéma spécifique de la source de données sous-jacente.  
  
 WCF Data Services s’intègre au Entity Framework ADO.NET pour vous permettre de créer des services de données qui exposent des données relationnelles. Vous pouvez utiliser les outils Entity Data Model pour créer un modèle de données qui contient des ressources adressables en tant qu'entités et définir en même temps le mappage entre ce modèle et les tables dans la base de données sous-jacente. Pour plus d’informations, consultez [Entity Framework fournisseur](entity-framework-provider-wcf-data-services.md).  
  
 WCF Data Services vous permet également de créer des services de données qui exposent toutes les structures de données qui retournent une implémentation de l' <xref:System.Linq.IQueryable%601> interface. De cette manière, vous pouvez créer des services de données qui exposent des données à partir de types .NET Framework. Les opérations de création, de mise à jour et de suppression sont prises en charge lorsque vous implémentez également l'interface <xref:System.Data.Services.IUpdatable>. Pour plus d’informations, consultez la page [fournisseur de réflexion](reflection-provider-wcf-data-services.md).  
  
 Pour une illustration de la façon dont WCF Data Services s’intègre à ces fournisseurs de données, consultez le diagramme architectural plus loin dans cette rubrique.  
  
## <a name="custom-business-logic"></a>Logique métier personnalisée  
 WCF Data Services facilite l’ajout d’une logique métier personnalisée à un service de données via des opérations de service et des intercepteurs. Les opérations de service sont des méthodes définies sur le serveur qui sont adressables par des URI sous la même forme que des ressources de données. Les opérations de service peuvent également utiliser la syntaxe d'expression de requête pour filtrer, classer et paginer des données retournées par une opération. Par exemple, l'URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` représente un appel à une opération de service nommée `GetOrdersByCity` sur le service de données Northwind qui retourne des commandes de clients de Londres et des résultats paginés triés par `OrderDate`. Pour plus d’informations, consultez [opérations de service](service-operations-wcf-data-services.md).  
  
 Les intercepteurs permettent à la logique d'application personnalisée d'être intégrée dans le traitement des messages de réponse ou de demande par un service de données. Les intercepteurs sont appelés lorsqu'une action de requête, d'insertion, de mise à jour ou de suppression a lieu dans le jeu d'entités spécifié. Un intercepteur peut alors modifier les données, appliquer la stratégie d'autorisation ou même mettre fin à l'opération. Les méthodes d'intercepteur doivent être enregistrées explicitement pour un jeu d'entités donné exposé par un service de données. Pour plus d’informations, consultez [intercepteurs](interceptors-wcf-data-services.md).  
  
## <a name="client-libraries"></a>Bibliothèques clientes  
 OData définit un ensemble de modèles uniformes pour l’interaction avec les services de données. Ainsi, il est possible de créer des composants réutilisables selon ces services, comme des bibliothèques côté client qui simplifient la consommation de ces services de données.  
  
 WCF Data Services comprend des bibliothèques clientes pour les applications clientes basées sur .NET Framework et Silverlight. Ces bibliothèques clientes vous permettent d'interagir avec les services de données en utilisant des objets .NET Framework. Elles prennent également en charge des requêtes basées sur des objets et des requêtes LINQ, le chargement des objets connexes, le suivi des modifications et la résolution d'identité. Pour plus d’informations, consultez [WCF Data Services bibliothèque cliente](wcf-data-services-client-library.md).  
  
 Outre les bibliothèques clientes OData incluses dans le .NET Framework et avec Silverlight, il existe d’autres bibliothèques clientes qui vous permettent de consommer un flux OData dans des applications clientes, telles que des applications PHP, AJAX et Java. Pour plus d’informations sur le kit de développement logiciel (SDK) OData, consultez [exemple de code ODATA SDK](https://www.odata.org/ecosystem/#sdk).
  
## <a name="architecture-overview"></a>Présentation de l'architecture  
 Le diagramme suivant illustre l’architecture WCF Data Services pour l’exposition de flux OData et l’utilisation de ces flux dans les bibliothèques clientes compatibles OData :  
  
 ![Capture d’écran montrant un diagramme d’architecture WCF Data Services.](./media/wcf-data-services-overview/windows-communication-foundation-data-services-architecture.gif)  
  
## <a name="see-also"></a>Voir aussi

- [WCF Data Services 4.5](index.md)
- [Prise en main](getting-started-with-wcf-data-services.md)
- [Définition des services de données WCF](defining-wcf-data-services.md)
- [Accès aux ressources d'un service de données (services de données WCF)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd728283(v=vs.100))
- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
- [Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
