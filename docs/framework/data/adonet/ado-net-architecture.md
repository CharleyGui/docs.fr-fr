---
title: Architecture ADO.NET
ms.date: 03/30/2017
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
ms.openlocfilehash: 282f18cc7d379dffc410a0c62dc3b3e66e0a44f6
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267970"
---
# <a name="adonet-architecture"></a>Architecture ADO.NET
Le traitement des données repose traditionnellement sur un modèle à deux couches utilisant une connexion. Le traitement des données utilisant de plus en plus des architectures multicouches, les programmeurs s'orientent vers une approche déconnectée de façon à proposer une meilleure évolutivité pour leurs applications.  
  
## <a name="adonet-components"></a>Composants d'ADO.NET  
 Les deux principaux composants d’ADO.NET pour accéder et manipuler les données sont les fournisseurs de données .NET Framework et le <xref:System.Data.DataSet>.  
  
### <a name="net-framework-data-providers"></a>Fournisseur de données .NET Framework  
 Les fournisseurs de données .NET Framework sont des composants explicitement conçus pour la manipulation des données et pour un accès aux données rapide, avant uniquement et en lecture seule. L'objet `Connection` assure la connectivité avec une source de données. L'objet `Command` permet d'accéder aux commandes de base de données en vue de retourner des données, de modifier des données, d'exécuter des procédures stockées et d'envoyer ou récupérer des informations sur les paramètres. Le `DataReader` fournit un flux très performant de données en provenance de la source de données. Enfin, le `DataAdapter` établit une passerelle entre l'objet `DataSet` et la source de données. Le `DataAdapter` utilise des objets `Command` pour exécuter des commandes SQL au niveau de la source de données afin d'une part de charger le `DataSet` avec des données, et d'autre part afin de répercuter dans la source de données les modifications apportées aux données contenues dans le `DataSet`. Pour plus d’informations, consultez [fournisseurs de données .NET Framework](../../../../docs/framework/data/adonet/data-providers.md) et [extraction et modification des données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>DataSet  
 Le `DataSet` ADO.NET est explicitement conçu pour un accès aux données indépendant de toute source de données. Il peut donc être utilisé avec plusieurs sources de données différentes, utilisé avec des données XML ou utilisé pour gérer des données locales de l'application. Le `DataSet` contient une collection d’un ou plusieurs objets <xref:System.Data.DataTable> constitués de lignes et de colonnes de données, ainsi que des informations concernant les contraintes de clé primaire, de clé étrangère et des informations relationnelles sur les données contenues dans les objets `DataTable`. Pour plus d’informations, consultez [DataSets, DataTables et DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Le diagramme suivant illustre la relation entre un fournisseur de données .NET Framework et un `DataSet`.  
  
 ![Graphique ADO.Net](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Architecture ADO.NET  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>Choix d'un DataReader ou d'un DataSet  
 Lorsque vous décidez si votre application doit utiliser un `DataReader` (consultez [extraction de données à l’aide d’un DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)) ou un `DataSet` (consultez [DataSets, DataTables et DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)), tenez compte du type de fonctionnalités nécessaires à votre application. Utilisez un `DataSet` pour effectuer les opérations suivantes :  
  
- Mettre des données en cache localement dans votre application afin de pouvoir les manipuler. Si vous devez uniquement lire les résultats d'une requête, le `DataReader` est le meilleur choix.  
  
- Fournir un accès distant entre couches ou à partir d'un service Web XML.  
  
- Interagir dynamiquement avec les données par le biais par exemple de la liaison à un contrôle Windows Forms ou de la combinaison et la mise en relation de données de diverses sources.  
  
- Réaliser un traitement complet des données sans qu'une connexion ouverte à la source de données soit nécessaire, ce qui libère la connexion pour d'autres clients.  
  
 Si vous n'avez pas besoin de la fonctionnalité fournie par le `DataSet`, vous pouvez améliorer les performances de votre application en utilisant le `DataReader` pour retourner les données avec un accès en lecture seule et avant uniquement. Bien que le `DataAdapter` utilise le `DataReader` pour remplir le contenu d’un `DataSet` (consultez [remplissage d’un DataSet à partir d’un DataAdapter](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)), à l’aide de la `DataReader`, vous pouvez améliorer les performances, car vous économiserez la mémoire qui doit être consommé par le `DataSet`et d’éviter le traitement est requis pour créer et remplir le contenu de la `DataSet`.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 LINQ to DataSet offre des fonctionnalités de requête ainsi qu’une vérification des types au moment de la compilation sur les données mises en cache dans un objet DataSet. Il vous permet d'écrire des requêtes dans l'un des langages de développement du .NET Framework, tels que C# ou Visual Basic. Pour plus d’informations, [consultez LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 La fonctionnalité LINQ to SQL prend en charge les requêtes sur un modèle objet mappé sur les structures de données d'une base de données relationnelle sans utiliser de modèle conceptuel intermédiaire. Chaque table est représentée par une classe distincte, associant étroitement le modèle objet au schéma de la base de données relationnelle. La fonctionnalité LINQ to SQL convertit des requêtes LINQ dans le modèle objet en données Transact-SQL et les envoie à la base de données en vue de leur exécution. Lorsque la base de données retourne les résultats, LINQ to SQL reconvertit les résultats en objets. Pour plus d’informations, consultez [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 ADO.NET Entity Framework est conçu pour permettre aux développeurs de créer des applications d'accès aux données en programmant à partir d'un modèle d'application conceptuel plutôt que directement sur un schéma de stockage relationnel. L'objectif est de limiter les opérations de codage et de maintenance requises par les applications orientées données. Pour plus d’informations, consultez [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
## <a name="wcf-data-services"></a>Services de données WCF  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] est utilisé pour déployer des services de données sur le Web ou sur un intranet. Les données sont structurées sous la forme d'entités et de relations conformément aux spécifications du modèle EDM. Les données déployées sur ce modèle sont adressables par le protocole HTTP standard. Pour plus d’informations, consultez [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="xml-and-adonet"></a>XML et ADO.NET  
 ADO.NET exploite la puissance de XML pour fournir un accès déconnecté aux données. ADO.NET a été conçu de pair avec les classes XML dans le .NET Framework ; les deux sont des composants d’une architecture unique.  
  
 ADO.NET et les classes XML du .NET Framework convergent dans le `DataSet` objet. Le `DataSet` peut être rempli de données provenant d'une source XML, qu'il s'agisse d'un fichier ou d'un flux XML. Le `DataSet` peut être écrit en XML conforme au W3C (World Wide Web Consortium), y compris son schéma, en tant que schéma en langage XSD (XML Schema Definition), quelle que soit la source des données contenues dans le `DataSet`. Le format de sérialisation natif du `DataSet` étant XML, il constitue un excellent support pour le déplacement de données entre couches, faisant ainsi du `DataSet` le meilleur choix pour communiquer à distance les données et le contexte du schéma vers et à partir d’un service web XML. Pour plus d’informations, consultez [Documents et données XML](../../../../docs/standard/data/xml/index.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble d’ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
