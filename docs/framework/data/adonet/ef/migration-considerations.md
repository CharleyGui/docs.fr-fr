---
title: Considérations sur la migration (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: 0fafa786805a14d9adc3523a5eb876e7e5b0e9c5
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489871"
---
# <a name="migration-considerations-entity-framework"></a>Considérations sur la migration (Entity Framework)
ADO.NET Entity Framework offre plusieurs avantages à une application existante. La possibilité d'utiliser un modèle conceptuel pour séparer des structures de données utilisées par l'application du schéma de la source de données constitue l'un de ces avantages les plus importants. Cela vous permet d'apporter facilement des modifications à venir au modèle de stockage ou à la source de données eux-mêmes sans apporter de modifications de compensation à l'application. Pour plus d’informations sur les avantages de l’utilisation de la [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], consultez [présentation d’Entity Framework](../../../../../docs/framework/data/adonet/ef/overview.md) et [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Pour tirer parti des avantages de la [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], vous pouvez migrer une application existante vers le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Certaines tâches sont communes à toutes les applications migrées. Ces tâches communes incluent la mise à niveau de l’application pour utiliser le .NET Framework depuis la version 3.5 Service Pack 1 (SP1), définition des modèles de mappage et configuration d’Entity Framework. Lorsque vous effectuez la migration d'une application vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], des points supplémentaires sont à prendre en considération. Ces points dépendent du type d'application qui est migrée et des fonctionnalités spécifiques de l'application. Cette rubrique fournit des informations vous permettant de choisir la meilleure approche à utiliser lorsque vous mettez à niveau une application existante.  
  
## <a name="general-migration-considerations"></a>Considérations générales sur la migration  
 Les considérations suivantes s'appliquent lorsque vous effectuez la migration d'une application vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] :  
  
- Toute application qui utilise le .NET Framework depuis la version 3.5 SP1 peut être migrée vers Entity Framework, tant que le fournisseur de données pour la source de données qui est utilisé par l’application prend en charge Entity Framework.  
  
- Il est possible qu’Entity Framework ne prenne pas en charge toutes les fonctionnalités d’un fournisseur de source de données, même si ce fournisseur prend en charge Entity Framework.  
  
- Pour une application volumineuse ou complexe, vous n'êtes pas obligé de migrer la totalité de l'application vers Entity Framework à la fois. Toutefois, toute partie de l’application qui n’utilise pas Entity Framework doit néanmoins être modifiée lorsque la source de données change.  
  
- La connexion du fournisseur de données utilisée par Entity Framework peut être partagée avec d’autres parties de votre application, car le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise des fournisseurs de données ADO.NET pour accéder à la source de données. Par exemple, le fournisseur SqlClient est utilisé par Entity Framework pour accéder à une base de données SQL Server. Pour plus d’informations, consultez [fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Tâches de migration communes  
 Le chemin d’accès pour effectuer la migration d’une application existante vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dépend à la fois du type d’application et de la stratégie d’accès aux données existante. Toutefois, vous devez toujours effectuer les tâches suivantes lorsque vous migrez une application existante vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
> [!NOTE]
>  Toutes ces tâches sont effectuées automatiquement lorsque vous utilisez les outils Entity Data Model à partir de Visual Studio 2008. Pour plus d'informations, voir [Procédure : Utilisez l’Assistant Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
1. Mettez à niveau l'application.  
  
     Un projet créé à l’aide d’une version antérieure de Visual Studio et .NET Framework doit être mis à niveau pour utiliser Visual Studio 2008 SP1 et .NET Framework depuis la version 3.5 SP1.  
  
2. Définissez les modèles et le mappage.  
  
     Les fichiers de modèle et de mappage définissent des entités dans le modèle conceptuel, des structures dans la source de données (telles que des tables, des procédures stockées et des vues), ainsi que le mappage entre les entités et les structures de la source de données. Pour plus d'informations, voir [Procédure : Définir le modèle manuellement et de fichiers de mappage](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).  
  
     Les types définis dans le modèle de stockage doivent correspondre aux noms des objets présents dans la source de données. Si l'application existante expose des données en tant qu'objets, vous devez vous assurer que les entités et les propriétés définies dans le modèle conceptuel correspondent aux noms de ces classes de données et propriétés existantes. Pour plus d'informations, voir [Procédure : Personnaliser la modélisation et mappage de fichiers pour travailler avec des objets personnalisés](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100)).  
  
    > [!NOTE]
    >  Entity Data Model Designer peut être utilisé pour renommer des entités du modèle conceptuel afin qu'elles correspondent à des objets existants. Pour plus d’informations, consultez [Entity Data Model Designer](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)).  
  
3. Définissez la chaîne de connexion.  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise une chaîne de connexion spécialement mise en forme lors de l'exécution de requêtes sur un modèle conceptuel. Cette chaîne de connexion encapsule des informations relatives aux fichiers de modèle et de mappage et à la connexion à la source de données. Pour plus d'informations, voir [Procédure : Définir la chaîne de connexion](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md).  
  
4. Configurer le projet Visual Studio.  
  
     Références à [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] assemblys et le modèle et le mappage de fichiers doivent être ajoutés au projet Visual Studio. Vous pouvez ajouter ces fichiers de mappage au projet pour garantir qu'ils sont déployés avec l'application dans l'emplacement indiqué dans la chaîne de connexion. Pour plus d'informations, voir [Procédure : Configurer manuellement un projet Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Considérations relatives aux applications comportant des objets existants  
 En commençant par le .NET Framework 4, le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] « plain old » prend en charge les objets CLR (POCO), également appelées objets ignorant la persistance. Dans la plupart des cas, vos objets existants peuvent fonctionner avec [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] en effectuant des changements mineurs. Pour plus d’informations, consultez [utilisation des entités POCO](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100)). Vous pouvez également migrer une application à le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et utiliser les classes de données qui sont générés par les outils Entity Framework. Pour plus d'informations, voir [Procédure : Utilisez l’Assistant Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>Considérations relatives aux applications qui utilisent des fournisseurs ADO.NET  
 Les fournisseurs ADO.NET, tels que SqlClient, vous permettent de vous permettent d’interroger une source de données pour retourner des données tabulaires. Données peuvent également être chargées dans un DataSet ADO.NET. La liste suivante décrit les considérations relatives à la mise à niveau une application qui utilise un fournisseur ADO.NET existant :  
  
- Affichage de données tabulaires à l'aide d'un lecteur de données.  

  Vous pouvez envisager d’exécuter un [!INCLUDE[esql](../../../../../includes/esql-md.md)] interroger à l’aide du fournisseur EntityClient et énumérer des retourné <xref:System.Data.EntityClient.EntityDataReader> objet. Procédez de cette manière si votre application affiche des données tabulaires à l'aide d'un lecteur de données et ne requiert pas les fonctionnalités fournies par [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pour la matérialisation des données dans des objets, le suivi des modifications et l'exécution des mises à jour. Vous pouvez continuer à utiliser le code d'accès aux données existant qui effectuer des mises à jour dans la source de données, mais vous pouvez utiliser la connexion existante accessible à partir de la propriété <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> de l'objet <xref:System.Data.EntityClient.EntityConnection>. Pour plus d’informations, consultez [fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
- Utilisation de datasets.  

  Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] fournit la plupart des fonctionnalités fournies par le DataSet, y compris la persistance en mémoire, suivi des modifications, la liaison de données et sérialisation des objets en tant que données XML. Pour plus d’informations, consultez [utilisation d’objets](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
  Si le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ne fournissent pas les fonctionnalités du DataSet requises par votre application, vous pouvez toujours tirer parti des avantages des requêtes LINQ en utilisant [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]. Pour plus d’informations, [consultez LINQ to DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Considérations relatives aux applications qui lient des données à des contrôles  
 Le .NET Framework vous permet d’encapsuler des données dans une source de données, comme un jeu de données ou un contrôle de source de données ASP.NET, puis lier les éléments d’interface utilisateur à ces contrôles de données. La liste suivante décrit les considérations concernant la liaison de contrôles à des données Entity Framework.  
  
- Liaison de données à des contrôles.  

  Lorsque vous interrogez le modèle conceptuel, le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] retourne les données sous la forme d’objets qui sont des instances de types d’entités. Ces objets peuvent être liés directement à des contrôles, et cette liaison prend en charge les mises à jour. Cela signifie que les modifications apportées aux données dans un contrôle, par exemple une ligne dans un <xref:System.Windows.Forms.DataGridView>, sont automatiquement enregistrées dans la base de données lors de la <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> méthode est appelée.  
  
  Si votre application énumère les résultats d’une requête pour afficher des données dans un objet <xref:System.Windows.Forms.DataGridView> ou un autre type de contrôle que prend en charge la liaison de données, vous pouvez modifier votre application pour lier le contrôle au résultat d’un objet <xref:System.Data.Objects.ObjectQuery%601>.  
  
  Pour plus d’informations, consultez [liaison d’objets aux contrôles](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100)).  
  
- Contrôles de source de données ASP.NET.  

  Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclut un contrôle de source de données conçu pour simplifier la liaison de données dans les applications Web ASP.NET. Pour plus d’informations, consultez [vue d’ensemble du contrôle serveur Web EntityDataSource](https://docs.microsoft.com/previous-versions/aspnet/cc488502(v=vs.100)).  
  
## <a name="other-considerations"></a>Autres considérations  
 Les remarques suivantes peuvent s’appliquer lorsque vous effectuez une migration de types spécifiques d’applications vers Entity Framework.  
  
- Applications qui exposent des services de données.  

  Les services Web et les applications basées sur Windows Communication Foundation (WCF) exposent les données d'une source de données sous-jacente en utilisant un format de messagerie de demande/réponse XML. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] prend en charge la sérialisation d'objets entité en utilisant la sérialisation de contrat de données binaire, XML ou WCF. La sérialisation binaire et la sérialisation WCF prennent tous les deux en charge la sérialisation complète de graphiques d'objets. Pour plus d’informations, consultez [création d’Applications multiniveau](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100)).  
  
- Applications qui utilisent des données XML.  

  La sérialisation des objets vous permet de créer des services des données [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Ces services fournissent des données à des applications qui utilisent des données XML, telles que les applications Internet AJAX. Dans ces cas, envisagez d'utiliser [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]. Ces services de données sont basées sur l’Entity Data Model et fournissent un accès dynamique aux données d’entité à l’aide des actions Representational State Transfer (REST) HTTP standard, telles que GET, PUT et post-traitement. Pour plus d’informations, consultez [WCF Data Services 4.5](../../../../../docs/framework/data/wcf/index.md).  
  
  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ne prend pas en charge le type de données XML natif. Cela signifie que, lorsqu'une entité est mappée à une table avec une colonne XML, la propriété d'entité équivalente de la colonne XML est une chaîne. Les objets peuvent être déconnectés et sérialisés sous forme de données XML. Pour plus d’informations, consultez [sérialisation d’objets](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
  Si votre application nécessite la possibilité d'interroger des données XML, vous pouvez tout de même tirer parti des avantages des requêtes LINQ en utilisant LINQ to XML. Pour plus d’informations, consultez [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ou [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
- Applications qui gèrent l'état.  

  Les applications Web ASP.NET doivent fréquemment gérer l’état d’une page Web ou d’une session utilisateur. Objets dans un <xref:System.Data.Objects.ObjectContext> instance permettre être stockée dans l’état d’affichage client ou dans l’état de session sur le serveur et versions ultérieures récupérée et rattachée à un contexte d’objet. Pour plus d’informations, consultez [attachement et détachement des objets](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100)).  
  
## <a name="see-also"></a>Voir aussi

- [Points à prendre en considération pour le déploiement](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [Terminologie Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md)
