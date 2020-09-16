---
title: Vue d’ensemble d’Entity Framework
description: Le Entity Framework dans ADO.NET prend en charge le développement d’applications orientées données qui fonctionnent à un niveau d’abstraction plus élevé que les applications traditionnelles.
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: e6b7a605f88aecc76cb182473d9dd9f925a4d5a9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557981"
---
# <a name="entity-framework-overview"></a>Présentation de Entity Framework

Le Entity Framework est un ensemble de technologies ADO.NET qui prennent en charge le développement d’applications logicielles orientées données. Les architectes et les développeurs d'applications orientées données sont confrontés à la nécessité d'atteindre deux objectifs très différents. Ils doivent modeler les entités, les relations et la logique des problèmes liés à l'activité de l'entreprise qu'ils résolvent, et ils doivent également travailler avec les moteurs de données utilisés pour stocker et récupérer les données. Les données peuvent être réparties entre plusieurs systèmes de stockage, chacun ayant ses propres protocoles ; même les applications qui fonctionnent avec un seul système de stockage doivent équilibrer les besoins du système de stockage par rapport aux besoins en matière d’écriture d’un code d’application efficace et facile à gérer.

Le Entity Framework permet aux développeurs de travailler avec des données sous la forme d’objets et de propriétés spécifiques à un domaine, tels que des clients et des adresses de clients, sans avoir à se préoccuper des tables et des colonnes de base de données sous-jacentes dans lesquelles sont stockées ces données. Avec Entity Framework, les développeurs peuvent travailler à un niveau supérieur d’abstraction lorsqu’ils traitent les données, et peuvent créer et maintenir des applications orientées données avec moins de code que dans les applications traditionnelles. Étant donné que le Entity Framework est un composant du .NET Framework, Entity Framework applications peuvent s’exécuter sur n’importe quel ordinateur sur lequel le .NET Framework à partir de la version 3,5 SP1 est installé.

## <a name="give-life-to-models"></a>Donnez vie aux modèles
 La division de l'application ou du service en trois parties (modèle de domaine, modèle logique et modèle physique) constitue une approche de conception commune et utilisé de longue date pour la construction d'une application ou d'un service. Le modèle de domaine définit les entités et les relations dans le système qui est en cours de modélisation. Le modèle logique d'une base de données relationnelle normalise les entités et les relations dans des tables avec des contraintes de clé étrangère. Le modèle physique s'occupe des fonctionnalités d'un moteur de données particulier en spécifiant des détails de stockage tels que le partitionnement et l'indexation.

 Le modèle physique est perfectionné par les administrateurs de bases de données pour améliorer les performances, mais les programmeurs qui écrivent du code d'application limitent principalement leur utilisation du modèle logique à l'écriture de requêtes SQL et à l'appel de procédures stockées. Les modèles de domaine sont généralement utilisés comme un outil permettant de capturer et de communiquer les besoins d’une application, fréquemment sous la forme de diagrammes inertes qui sont consultés et passés en revue dans les phases préliminaires d’un projet, puis abandonnés. De nombreuses équipes de développement ne créent pas de modèle conceptuel et commencent en spécifiant des tables, des colonnes et des clés dans une base de données relationnelle.

 Le Entity Framework donne vie aux modèles en permettant aux développeurs d’interroger des entités et des relations dans le modèle de domaine (appelé modèle *conceptuel* dans le Entity Framework) tout en s’appuyant sur le Entity Framework pour convertir ces opérations en commandes spécifiques à la source de données. Cela libère les applications des dépendances codées en dur sur une source de données particulière.

 Lorsque vous utilisez Code First, le modèle conceptuel est mappé au modèle de stockage dans le code. Le Entity Framework peut déduire le modèle conceptuel en fonction des types d’objets et des configurations supplémentaires que vous définissez. Les métadonnées de mappage sont générées au moment de l'exécution selon une combinaison de la manière dont vous avez défini vos types de domaine et données de configuration supplémentaires que vous fournissez dans le code. Entity Framework génère la base de données selon les besoins en fonction des métadonnées. Pour plus d’informations, consultez [création d’un modèle](/ef/ef6/modeling/).

 Lorsque vous utilisez Entity Data Model Tools, le modèle conceptuel, le modèle de stockage et les mappages entre les deux sont exprimés dans les schémas basés sur XML et sont définis dans les fichiers qui ont les extensions de nom correspondantes :

- Le langage CSDL (Conceptual Schema Definition Language) définit le modèle conceptuel. Le langage CSDL est l’implémentation de la Entity Framework du [Entity Data Model](../entity-data-model.md). L’extension de fichier est .csdl.

- Le langage SSDL (Store Schema Definition Language) définit le modèle de stockage, également appelé « modèle logique ». L’extension de fichier est .ssdl.

- Le langage MSL (Mapping Specification Language) définit les mappages entre le modèle de stockage et le modèle conceptuel. L’extension de fichier est .msl.

Le modèle de stockage et les mappages peuvent être modifiés le cas échéant, sans besoin de modifier le modèle conceptuel, les classes de données ou le code d'application. Étant donné que les modèles de stockage sont spécifiques au fournisseur, vous pouvez travailler avec un modèle conceptuel cohérent entre différentes sources de données.

Le Entity Framework utilise ces fichiers de modèle et de mappage pour créer, lire, mettre à jour et supprimer des opérations sur les entités et les relations dans le modèle conceptuel à des opérations équivalentes dans la source de données. Le Entity Framework prend même en charge le mappage d’entités du modèle conceptuel à des procédures stockées dans la source de données. Pour plus d’informations, consultez [spécifications CSDL, SSDL et MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).

## <a name="map-objects-to-data"></a>Mapper des objets à des données
 La programmation orientée objet présente une difficulté pour l'interaction avec les systèmes de stockage des données. Bien que l'organisation des classes reflète souvent l'organisation des tables de bases de données relationnelles, l'adéquation n'est pas parfaite. Plusieurs tables normalisées correspondent fréquemment à une seule classe, et les relations entre les classes sont souvent représentées différemment des relations entre les tables. Par exemple, pour représenter le client d'une commande, une classe `Order` peut utiliser une propriété qui contient une référence à une instance d'une classe `Customer`, tandis qu'une ligne de la table `Order` d'une base de données contient une colonne (ou un ensemble de colonnes) de clé étrangère avec une valeur qui correspond à une valeur de clé primaire dans la table `Customer`. Une classe `Customer` peut avoir une propriété nommée `Orders` qui contient une collection d'instances de la classe `Order` alors que la table `Customer` d'une base de données n'a aucune colonne comparable. L’Entity Framework offre aux développeurs la possibilité de représenter les relations de cette manière, ou de modéliser plus étroitement les relations lorsqu’elles sont représentées dans la base de données.

 Les solutions existantes ont essayé de rétablir la continuité de ce qu'on appelle fréquemment « défaut d'adaptation d'impédance », en mappant uniquement des classes et des propriétés orientées objet à des colonnes et à des tables relationnelles. Au lieu d’aborder cette approche traditionnelle, le Entity Framework mappe les tables relationnelles, les colonnes et les contraintes de clé étrangère dans des modèles logiques à des entités et des relations dans des modèles conceptuels. Cela permet une plus grande souplesse dans la définition des objets et l'optimisation du modèle logique. Les outils de Entity Data Model génèrent des classes de données extensibles basées sur le modèle conceptuel. Ces classes sont des classes partielles qui peuvent être étendues avec des membres supplémentaires que le développeur ajoute. Par défaut, les classes générées pour un modèle conceptuel particulier dérivent de classes de base qui fournissent des services de matérialisation d'entités sous forme d'objets, ainsi que de suivi et d'enregistrement des modifications. Les développeurs peuvent utiliser ces classes pour travailler avec les entités et les relations sous forme d'objets liés par des associations. Les développeurs peuvent également personnaliser les classes générées pour un modèle conceptuel. Pour plus d’informations, consultez [utilisation des objets](working-with-objects.md).

## <a name="access-and-change-entity-data"></a>Accéder aux données d’entité et les modifier

Plus qu'une simple solution de mappage relationnel objet supplémentaire, Entity Framework permet fondamentalement à des applications d'accéder à des données qui sont représentées sous la forme d'entités et de relations dans le modèle conceptuel, et de les modifier. Le Entity Framework utilise des informations dans les fichiers de modèle et de mappage pour traduire des requêtes d’objet sur des types d’entités représentés dans le modèle conceptuel en requêtes spécifiques à la source de données. Les résultats de la requête sont matérialisés en objets gérés par le Entity Framework. L’Entity Framework fournit les méthodes suivantes pour interroger un modèle conceptuel et retourner des objets :

- LINQ to Entities. Fournit la prise en charge de LINQ (Language Integrated Query) pour interroger des types d'entités définis dans un modèle conceptuel. Pour plus d’informations, consultez [LINQ to Entities](./language-reference/linq-to-entities.md).

- [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Dialecte SQL indépendant du stockage qui fonctionne directement avec les entités dans le modèle conceptuel et qui prend en charge les concepts de Entity Data Model. [!INCLUDE[esql](../../../../../includes/esql-md.md)] est utilisé à la fois avec les requêtes d’objet et les requêtes exécutées à l’aide du fournisseur EntityClient. Pour plus d’informations, consultez [Entity SQL vue d’ensemble](./language-reference/entity-sql-overview.md).

Le Entity Framework contient le fournisseur de données EntityClient. Ce fournisseur gère les connexions, traduit les requêtes d’entité en requêtes spécifiques à la source de données et retourne un lecteur de données que le Entity Framework utilise pour matérialiser des données d’entité dans des objets. Lorsque la matérialisation d'objets n'est pas requise, le fournisseur EntityClient peut également être utilisé comme un fournisseur de données ADO.NET standard en permettant aux applications d'exécuter des requêtes [!INCLUDE[esql](../../../../../includes/esql-md.md)] et d'utiliser le lecteur de données en lecture seule retournées. Pour plus d’informations, consultez la page [Fournisseur EntityClient pour Entity Framework](entityclient-provider-for-the-entity-framework.md).

Le diagramme suivant illustre l'architecture Entity Framework pour l'accès aux données :

![Diagramme architectural Entity Framework](./media/wd-efarchdiagram.gif "wd_EFArchDiagram")

Les outils de Entity Data Model peuvent générer une classe dérivée de `System.Data.Objects.ObjectContext` ou `System.Data.Entity.DbContext` qui représente le conteneur d’entités dans le modèle conceptuel. Ce contexte de l'objet fournit les fonctionnalités permettant de suivre les modifications, et de gérer les identités, l'accès concurrentiel et les relations. Cette classe expose également une méthode `SaveChanges` qui écrit les insertions, les mises à jour et des suppressions dans la source de données. Comme les requêtes, ces modifications sont apportées soit par des commandes générées automatiquement par le système, soit par des procédures stockées qui sont spécifiées par le développeur.

## <a name="data-providers"></a>Fournisseurs de données

Le `EntityClient` fournisseur étend le modèle de fournisseur ADO.net en accédant aux données en termes d’entités conceptuelles et de relations. Il exécute des requêtes qui utilisent [!INCLUDE[esql](../../../../../includes/esql-md.md)]. [!INCLUDE[esql](../../../../../includes/esql-md.md)] fournit le langage de requête sous-jacent qui permet à `EntityClient` de communiquer avec la base de données. Pour plus d’informations, consultez la page [Fournisseur EntityClient pour Entity Framework](entityclient-provider-for-the-entity-framework.md).

Le Entity Framework comprend un Fournisseur de données SqlClient mis à jour qui prend en charge les arborescences de commandes canoniques. Pour plus d’informations, consultez [SqlClient pour le Entity Framework](sqlclient-for-the-entity-framework.md).

## <a name="entity-data-model-tools"></a>Outils Entity Data Model

Avec le runtime Entity Framework, Visual Studio comprend les outils de mappage et de modélisation. Pour plus d’informations, consultez [modélisation et mappage](modeling-and-mapping.md).

## <a name="learn-more"></a>En savoir plus

Pour en savoir plus sur le Entity Framework, consultez :

[Prise en main](getting-started.md) -fournit des informations sur la façon d’être opérationnel rapidement à l’aide du [démarrage rapide](/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100)), qui montre comment créer une application Entity Framework simple.

[Terminologie de Entity Framework](terminology.md) : définit un grand nombre des termes introduits par le Entity Data Model et la Entity Framework et utilisés dans la documentation de Entity Framework.

[Ressources de Entity Framework](resources.md) : fournit des liens vers des rubriques conceptuelles et des liens vers des rubriques et des ressources externes sur la création d’applications Entity Framework.

## <a name="see-also"></a>Voir aussi

- [ADO.NET Entity Framework](index.md)
