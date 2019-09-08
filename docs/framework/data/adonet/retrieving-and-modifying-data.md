---
title: Extraction et modification de données dans ADO.NET
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 78012a6a5ecdfac0e4cd7c4939ae3ab0036ab716
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782853"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Extraction et modification de données dans ADO.NET
Une fonction principale de toute application de base de données consiste à se connecter à une source de données et extraire les données qu'elle contient. Les fournisseurs de données de .NET Framework de ADO.NET jouent le rôle de pont entre une application et une source de données, ce qui vous permet d’exécuter des commandes ainsi que de récupérer des données à l’aide d’un **DataReader** ou d’un **DataAdapter**. Une fonction clé de toute application de base de données est la capacité à mettre à jour les données stockées dans la base de données. Dans ADO.net, la mise à jour des données implique l' <xref:System.Data.DataSet>utilisation des objets **DataAdapter** et, et des objets **Command** , et peut également impliquer l’utilisation de transactions.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Connexion à une source de données](connecting-to-a-data-source.md)  
 Décrit comment établir une connexion à une source de données et comment travailler avec des événements de connexion.  
  
 [Chaînes de connexion](connection-strings.md)  
 Contient des rubriques qui décrivent divers aspects de l'utilisation de chaînes de connexion, y compris des mots clés de chaîne de connexion, des informations de sécurité, ainsi que de leur stockage et leur extraction.  
  
 [Regroupement de connexions](connection-pooling.md)  
 Décrit le regroupement de connexions pour les fournisseurs de données .NET Framework.  
  
 [Commandes et paramètres](commands-and-parameters.md)  
 Contient des rubriques qui décrivent comment créer des commandes et des générateurs de commande, configurer des paramètres et exécuter des commandes pour extraire et modifier des données.  
  
 [DataAdapters et DataReaders](dataadapters-and-datareaders.md)  
 Contient des rubriques qui décrivent les objets DataReader et DataAdapter, les paramètres, la gestion des événements DataAdapter et l'exécution d'opérations par lots.  
  
 [Transactions et accès concurrentiel](transactions-and-concurrency.md)  
 Contient des rubriques qui décrivent comment effectuer des transactions locales, des transactions distribuées et travailler avec l’accès concurrentiel optimiste.  
  
 [Récupération de valeurs d’identité ou de numérotation automatique](retrieving-identity-or-autonumber-values.md)  
 Fournit un exemple de mappage des valeurs générées pour une colonne d' **identité** dans une table SQL Server ou pour un champ **AutoNumber** d’une table Microsoft Access, à une colonne d’une ligne insérée dans une table. Traite de la fusion de valeurs d'identité dans un `DataTable`.  
  
 [Récupération de données binaires](retrieving-binary-data.md)  
 Décrit comment récupérer des données binaires ou des structures de `CommandBehavior`données volumineuses à l’aide de.`SequentialAccess` pour modifier le comportement par défaut d' `DataReader`un.  
  
 [Modification des données avec les procédures stockées](modifying-data-with-stored-procedures.md)  
 Décrit comment utiliser des paramètres d'entrée et sortie de procédure stockée afin d'insérer une ligne dans une base de données et retourner une nouvelle valeur d'identité.  
  
 [Récupération des informations de schéma de base de données](retrieving-database-schema-information.md)  
 Décrit la manière d'obtenir des bases de données ou des catalogues disponibles, des tables et des vues dans une base de données, des contraintes existantes pour des tables et d'autres informations de schéma à partir d'une source de données.  
  
 [DbProviderFactories](dbproviderfactories.md)  
 Décrit le modèle fabrique de fournisseurs et illustre l'utilisation des classes de base dans l'espace de noms `System.Data.Common`.  
  
 [Suivi des données dans ADO.NET](data-tracing.md)  
 Décrit la manière dont ADO.NET offre une fonctionnalité intégrée de traçage de données.  
  
 [Compteurs de performance](performance-counters.md)  
 Décrit les compteurs de performance disponibles pour `SqlClient` et `OracleClient`.  
  
 [Programmation asynchrone](asynchronous-programming.md)  
 Décrit la prise en charge de ADO.NET pour la programmation asynchrone.  
  
 [Prise en charge du streaming pour SqlClient](sqlclient-streaming-support.md)  
 Explique comment écrire des applications qui diffusent en continu des données à partir de SQL Server sans qu’elles soient entièrement chargées en mémoire.  
  
## <a name="see-also"></a>Voir aussi

- [Mappages de types de données dans ADO.NET](data-type-mappings-in-ado-net.md)
- [DataSets, DataTables et DataViews](./dataset-datatable-dataview/index.md)
- [Sécurisation des applications ADO.NET](securing-ado-net-applications.md)
- [SQL Server et ADO.NET](./sql/index.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
