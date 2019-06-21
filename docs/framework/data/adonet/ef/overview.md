---
title: Vue d’ensemble d’Entity Framework
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: e6c96326991c6f883ad670393bb5c2691f8ad29e
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307344"
---
# <a name="entity-framework-overview"></a>Présentation d’Entity Framework

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] est un ensemble de technologies dans ADO.NET qui prennent en charge le développement d'applications logicielles orientées données. Les architectes et les développeurs d'applications orientées données sont confrontés à la nécessité d'atteindre deux objectifs très différents. Ils doivent modeler les entités, les relations et la logique des problèmes liés à l'activité de l'entreprise qu'ils résolvent, et ils doivent également travailler avec les moteurs de données utilisés pour stocker et récupérer les données. Les données peuvent être réparties entre plusieurs systèmes de stockage, chacun ayant ses propres protocoles ; même les applications qui fonctionnent avec un seul système de stockage doivent équilibrer les besoins du système de stockage par rapport aux besoins en matière d’écriture d’un code d’application efficace et facile à gérer.

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] permet aux développeurs de travailler avec des données sous la forme de propriétés et d'objets spécifiques aux domaines, tels que des clients et des adresses de clients, sans qu'il soit nécessaire de se préoccuper des tables et des colonnes de base de données sous-jacentes dans lesquelles sont stockées ces données. Avec [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], les développeurs peuvent travailler à un niveau supérieur d'abstraction lorsqu'ils traitent les données, et peuvent créer et maintenir des applications orientées données avec moins de code que dans les applications traditionnelles. Étant donné que le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] est un composant du .NET Framework, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] applications peuvent s’exécuter sur n’importe quel ordinateur sur lequel est installé le .NET Framework depuis la version 3.5 SP1.

## <a name="give-life-to-models"></a>Donner vie aux modèles
 La division de l'application ou du service en trois parties (modèle de domaine, modèle logique et modèle physique) constitue une approche de conception commune et utilisé de longue date pour la construction d'une application ou d'un service. Le modèle de domaine définit les entités et les relations dans le système qui est en cours de modélisation. Le modèle logique d'une base de données relationnelle normalise les entités et les relations dans des tables avec des contraintes de clé étrangère. Le modèle physique s'occupe des fonctionnalités d'un moteur de données particulier en spécifiant des détails de stockage tels que le partitionnement et l'indexation.

 Le modèle physique est perfectionné par les administrateurs de bases de données pour améliorer les performances, mais les programmeurs qui écrivent du code d'application limitent principalement leur utilisation du modèle logique à l'écriture de requêtes SQL et à l'appel de procédures stockées. Les modèles de domaine sont généralement utilisés comme un outil permettant de capturer et de communiquer les besoins d’une application, fréquemment sous la forme de diagrammes inertes qui sont consultés et passés en revue dans les phases préliminaires d’un projet, puis abandonnés. De nombreuses équipes de développement ne créent pas de modèle conceptuel et commencent en spécifiant des tables, des colonnes et des clés dans une base de données relationnelle.

 Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] donne vie aux modèles en permettant aux développeurs d’interroger des entités et des relations dans le modèle de domaine (appelé un *conceptuel* modèle dans le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]) tout en s’appuyant sur le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pour traduire ces opérations de commandes spécifique à la source de données. Cela libère les applications des dépendances codées en dur sur une source de données particulière.

 Lorsque vous utilisez Code First, le modèle conceptuel est mappé au modèle de stockage dans le code. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] peut déduire le modèle conceptuel basé sur les types d'objets et les configurations supplémentaires que vous définissez. Les métadonnées de mappage sont générées au moment de l'exécution selon une combinaison de la manière dont vous avez défini vos types de domaine et données de configuration supplémentaires que vous fournissez dans le code. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] génère la base de données nécessaire en fonction des métadonnées. Pour plus d’informations, consultez [création et mappage d’un modèle conceptuel](https://go.microsoft.com/fwlink/?LinkID=235382).

 Lorsque vous utilisez Entity Data Model Tools, le modèle conceptuel, le modèle de stockage et les mappages entre les deux sont exprimés dans les schémas basés sur XML et sont définis dans les fichiers qui ont les extensions de nom correspondantes :

- Le langage CSDL (Conceptual Schema Definition Language) définit le modèle conceptuel. CSDL est la [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]d’implémentation de la [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md). L’extension de fichier est .csdl.

- Le langage SSDL (Store Schema Definition Language) définit le modèle de stockage, également appelé « modèle logique ». L’extension de fichier est .ssdl.

- Le langage MSL (Mapping Specification Language) définit les mappages entre le modèle de stockage et le modèle conceptuel. L’extension de fichier est .msl.

Le modèle de stockage et les mappages peuvent être modifiés le cas échéant, sans besoin de modifier le modèle conceptuel, les classes de données ou le code d'application. Étant donné que les modèles de stockage sont spécifiques au fournisseur, vous pouvez travailler avec un modèle conceptuel cohérent entre différentes sources de données.

Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise ces modéliser et mapper des fichiers pour créer, lire, mettre à jour et supprimer des opérations sur les entités et les relations dans le modèle conceptuel en opérations équivalentes dans la source de données. Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] même prend en charge le mappage d’entités dans le modèle conceptuel aux procédures stockées dans la source de données. Pour plus d’informations, consultez [CSDL, SSDL et MSL spécifications](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md).

## <a name="map-objects-to-data"></a>Map (objets) aux données
 La programmation orientée objet présente une difficulté pour l'interaction avec les systèmes de stockage des données. Bien que l'organisation des classes reflète souvent l'organisation des tables de bases de données relationnelles, l'adéquation n'est pas parfaite. Plusieurs tables normalisées correspondent fréquemment à une seule classe, et les relations entre les classes sont souvent représentées différemment des relations entre les tables. Par exemple, pour représenter le client d'une commande, une classe `Order` peut utiliser une propriété qui contient une référence à une instance d'une classe `Customer`, tandis qu'une ligne de la table `Order` d'une base de données contient une colonne (ou un ensemble de colonnes) de clé étrangère avec une valeur qui correspond à une valeur de clé primaire dans la table `Customer`. Une classe `Customer` peut avoir une propriété nommée `Orders` qui contient une collection d'instances de la classe `Order` alors que la table `Customer` d'une base de données n'a aucune colonne comparable. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] donne aux développeurs la flexibilité de représenter les relations de cette façon, ou de modeler de façon plus précise les relations lorsqu'elles sont représentées dans la base de données.

 Les solutions existantes ont essayé de rétablir la continuité de ce qu'on appelle fréquemment « défaut d'adaptation d'impédance », en mappant uniquement des classes et des propriétés orientées objet à des colonnes et à des tables relationnelles. Au lieu d’adopter cette approche traditionnelle, la [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] mappe des tables relationnelles, des colonnes et des contraintes de clé étrangère dans des modèles logiques à des entités et relations dans les modèles conceptuels. Cela permet une plus grande souplesse dans la définition des objets et l'optimisation du modèle logique. Les outils Entity Data Model génèrent des classes de données extensibles basées sur le modèle conceptuel. Ces classes sont des classes partielles qui peuvent être étendues avec des membres supplémentaires que le développeur ajoute. Par défaut, les classes générées pour un modèle conceptuel particulier dérivent de classes de base qui fournissent des services de matérialisation d'entités sous forme d'objets, ainsi que de suivi et d'enregistrement des modifications. Les développeurs peuvent utiliser ces classes pour travailler avec les entités et les relations sous forme d'objets liés par des associations. Les développeurs peuvent également personnaliser les classes générées pour un modèle conceptuel. Pour plus d’informations, consultez [utilisation d’objets](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).

## <a name="access-and-change-entity-data"></a>Données d’entité accès et les modifications

Plus qu'une simple solution de mappage relationnel objet supplémentaire, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] permet fondamentalement à des applications d'accéder à des données qui sont représentées sous la forme d'entités et de relations dans le modèle conceptuel, et de les modifier. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise les informations contenues dans le modèle et les fichiers de mappage pour traduire des requêtes d'objet sur des types d'entités qui sont représentés en requêtes spécifiques à la source de données dans le modèle conceptuel. Résultats des requêtes sont matérialisés en objets que le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] gère. Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] fournit les méthodes suivantes pour interroger un modèle conceptuel et retourner des objets :

- [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]. Fournit la prise en charge Language-Integrated Query (LINQ) pour interroger des types d’entité qui sont définis dans un modèle conceptuel. Pour plus d’informations, consultez [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).

- [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Un dialecte indépendant du stockage de SQL qui fonctionne directement avec les entités dans le modèle conceptuel et qui prend en charge les concepts de l’Entity Data Model. [!INCLUDE[esql](../../../../../includes/esql-md.md)] est utilisé avec les requêtes d’objet et les requêtes sont exécutées à l’aide du fournisseur EntityClient. Pour plus d’informations, consultez [Entity SQL Overview](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclut le fournisseur de données EntityClient. Ce fournisseur gère les connexions, traduit des requêtes d'entité dans les requêtes spécifiques à la source de données et retourne un lecteur de données que [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise pour matérialiser les données d'entité dans des objets. Lorsque la matérialisation d'objets n'est pas requise, le fournisseur EntityClient peut également être utilisé comme un fournisseur de données ADO.NET standard en permettant aux applications d'exécuter des requêtes [!INCLUDE[esql](../../../../../includes/esql-md.md)] et d'utiliser le lecteur de données en lecture seule retournées. Pour plus d’informations, consultez [fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

Le diagramme suivant illustre l'architecture [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pour l'accès aux données :

![Diagramme Architectural de Entity Framework](../../../../../docs/framework/data/adonet/ef/media/wd-efarchdiagram.gif "wd_EFArchDiagram")

L’Entity Data Model Tools peut générer une classe dérivée de `System.Data.Objects.ObjectContext` ou `System.Data.Entity.DbContext` qui représente le conteneur d’entités dans le modèle conceptuel. Ce contexte de l'objet fournit les fonctionnalités permettant de suivre les modifications, et de gérer les identités, l'accès concurrentiel et les relations. Cette classe expose également une méthode `SaveChanges` qui écrit les insertions, les mises à jour et des suppressions dans la source de données. Comme les requêtes, ces modifications sont apportées soit par des commandes générées automatiquement par le système, soit par des procédures stockées qui sont spécifiées par le développeur.

## <a name="data-providers"></a>Fournisseurs de données

Le `EntityClient` fournisseur étend le modèle de fournisseur ADO.NET en accédant aux données en termes d’entités conceptuelles et de relations. Il exécute des requêtes qui utilisent [!INCLUDE[esql](../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../includes/esql-md.md)] fournit le langage de requête sous-jacent qui permet à `EntityClient` de communiquer avec la base de données. Pour plus d’informations, consultez [fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclut un fournisseur de données SqlClient mis à jour qui prend en charge les arborescences de commandes canoniques. Pour plus d’informations, consultez [SqlClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md).

## <a name="entity-data-model-tools"></a>Outils Entity data model

Avec le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] runtime, Visual Studio inclut le mappage et les outils de modélisation. Pour plus d’informations, consultez [de modélisation et mappage](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md).

## <a name="learn-more"></a>En savoir plus

Pour en savoir plus sur la [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], consultez :

[Mise en route](../../../../../docs/framework/data/adonet/ef/getting-started.md) - fournit des informations sur comment être opérationnel et en cours d’exécution rapidement à l’aide de la [Quickstart](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100)), qui montre comment créer un simple [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.

[Terminologie Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md) -définit un grand nombre des termes introduits par Entity Data Model et [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et qui sont utilisés dans [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.

[Ressources Entity Framework](../../../../../docs/framework/data/adonet/ef/resources.md) - fournit des liens vers des rubriques conceptuelles et des liens vers les rubriques externes et des ressources pour la création de [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] applications.

## <a name="see-also"></a>Voir aussi

- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
