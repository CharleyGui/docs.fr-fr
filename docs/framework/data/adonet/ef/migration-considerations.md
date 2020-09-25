---
title: Considérations sur la migration (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: d5151f0215cde1c5e35cc87c3cd667e16a23a1df
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175471"
---
# <a name="migration-considerations-entity-framework"></a>Considérations sur la migration (Entity Framework)

L’Entity Framework ADO.NET offre plusieurs avantages pour une application existante. La possibilité d'utiliser un modèle conceptuel pour séparer des structures de données utilisées par l'application du schéma de la source de données constitue l'un de ces avantages les plus importants. Cela vous permet d'apporter facilement des modifications à venir au modèle de stockage ou à la source de données eux-mêmes sans apporter de modifications de compensation à l'application. Pour plus d’informations sur les avantages de l’utilisation de la Entity Framework, consultez [Entity Framework vue d’ensemble](overview.md) et [Entity Data Model](../entity-data-model.md).  
  
 Pour tirer parti des avantages de la Entity Framework, vous pouvez migrer une application existante vers le Entity Framework. Certaines tâches sont communes à toutes les applications migrées. Ces tâches courantes incluent la mise à niveau de l’application pour utiliser le .NET Framework à partir de la version 3,5 du Service Pack 1 (SP1), la définition des modèles et du mappage, et la configuration du Entity Framework. Lorsque vous migrez une application vers le Entity Framework, des considérations supplémentaires s’appliquent. Ces points dépendent du type d'application qui est migrée et des fonctionnalités spécifiques de l'application. Cette rubrique fournit des informations vous permettant de choisir la meilleure approche à utiliser lorsque vous mettez à niveau une application existante.  
  
## <a name="general-migration-considerations"></a>Considérations générales sur la migration  

 Les considérations suivantes s’appliquent lorsque vous migrez une application vers l’Entity Framework :  
  
- Toute application qui utilise le .NET Framework à partir de la version 3,5 SP1 peut être migrée vers le Entity Framework, à condition que le fournisseur de données de la source de données utilisée par l’application prenne en charge l’Entity Framework.  
  
- Il est possible qu’Entity Framework ne prenne pas en charge toutes les fonctionnalités d’un fournisseur de source de données, même si ce fournisseur prend en charge Entity Framework.  
  
- Pour une application volumineuse ou complexe, vous n'êtes pas obligé de migrer la totalité de l'application vers Entity Framework à la fois. Toutefois, toute partie de l’application qui n’utilise pas Entity Framework doit néanmoins être modifiée lorsque la source de données change.  
  
- La connexion du fournisseur de données utilisée par le Entity Framework peut être partagée avec d’autres parties de votre application, car le Entity Framework utilise des fournisseurs de données ADO.NET pour accéder à la source de données. Par exemple, le fournisseur SqlClient est utilisé par Entity Framework pour accéder à une base de données SQL Server. Pour plus d’informations, consultez la page [Fournisseur EntityClient pour Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Tâches de migration communes  

 Le chemin d’accès à la migration d’une application existante vers le Entity Framework dépend à la fois du type d’application et de la stratégie d’accès aux données existante. Toutefois, vous devez toujours effectuer les tâches suivantes lorsque vous migrez une application existante vers le Entity Framework.  
  
> [!NOTE]
> Toutes ces tâches sont effectuées automatiquement lorsque vous utilisez les outils Entity Data Model à partir de Visual Studio 2008. Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
1. Mettez à niveau l'application.  
  
     Un projet créé à l’aide d’une version antérieure de Visual Studio et du .NET Framework doit être mis à niveau pour utiliser Visual Studio 2008 SP1 et le .NET Framework à partir de la version 3,5 SP1.  
  
2. Définissez les modèles et le mappage.  
  
     Les fichiers de modèle et de mappage définissent des entités dans le modèle conceptuel, des structures dans la source de données (telles que des tables, des procédures stockées et des vues), ainsi que le mappage entre les entités et les structures de la source de données. Pour plus d’informations, consultez [Comment : définir manuellement les fichiers de modèle et de mappage](/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).  
  
     Les types définis dans le modèle de stockage doivent correspondre aux noms des objets présents dans la source de données. Si l'application existante expose des données en tant qu'objets, vous devez vous assurer que les entités et les propriétés définies dans le modèle conceptuel correspondent aux noms de ces classes de données et propriétés existantes. Pour plus d’informations, consultez [Comment : personnaliser la modélisation et le mappage de fichiers pour travailler avec des objets personnalisés](/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100)).  
  
    > [!NOTE]
    > Entity Data Model Designer peut être utilisé pour renommer des entités du modèle conceptuel afin qu'elles correspondent à des objets existants. Pour plus d’informations, consultez [Entity Data Model Designer](/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)).  
  
3. Définissez la chaîne de connexion.  
  
     L’Entity Framework utilise une chaîne de connexion spécialement mise en forme lors de l’exécution de requêtes sur un modèle conceptuel. Cette chaîne de connexion encapsule des informations relatives aux fichiers de modèle et de mappage et à la connexion à la source de données. Pour plus d’informations, consultez [Comment : définir la chaîne de connexion](how-to-define-the-connection-string.md).  
  
4. Configurez le projet Visual Studio.  
  
     Les références aux assemblys Entity Framework et aux fichiers de modèle et de mappage doivent être ajoutées au projet Visual Studio. Vous pouvez ajouter ces fichiers de mappage au projet pour garantir qu'ils sont déployés avec l'application dans l'emplacement indiqué dans la chaîne de connexion. Pour plus d’informations, consultez [procédure : configurer manuellement un projet de Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Considérations relatives aux applications comportant des objets existants  

 À partir du .NET Framework 4, le Entity Framework prend en charge les objets CLR « Plain Old » (POCO), également appelés objets ignorant la persistance. Dans la plupart des cas, vos objets existants peuvent fonctionner avec le Entity Framework en apportant des modifications mineures. Pour plus d’informations, consultez [utilisation des entités POCO](/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100)). Vous pouvez également migrer une application vers le Entity Framework et utiliser les classes de données générées par les outils de Entity Framework. Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>Considérations relatives aux applications qui utilisent des fournisseurs ADO.NET  

 Les fournisseurs ADO.NET, tels que SqlClient, vous permettent d’interroger une source de données pour retourner des données tabulaires. Les données peuvent également être chargées dans un jeu de données ADO.NET. La liste suivante décrit les éléments à prendre en compte pour la mise à niveau d’une application qui utilise un fournisseur ADO.NET existant :  
  
- Affichage de données tabulaires à l'aide d'un lecteur de données.  

  Vous pouvez envisager d’exécuter une [!INCLUDE[esql](../../../../../includes/esql-md.md)] requête à l’aide du fournisseur EntityClient et d’énumérer l' <xref:System.Data.EntityClient.EntityDataReader> objet retourné. Procédez ainsi uniquement si votre application affiche des données tabulaires à l’aide d’un lecteur de données et ne requiert pas les fonctionnalités fournies par le Entity Framework pour la matérialisation des données dans des objets, le suivi des modifications et l’apport de mises à jour. Vous pouvez continuer à utiliser le code d'accès aux données existant qui effectuer des mises à jour dans la source de données, mais vous pouvez utiliser la connexion existante accessible à partir de la propriété <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> de l'objet <xref:System.Data.EntityClient.EntityConnection>. Pour plus d’informations, consultez la page [Fournisseur EntityClient pour Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
- Utilisation de datasets.  

  Le Entity Framework fournit un grand nombre des fonctionnalités fournies par le jeu de données, y compris la persistance en mémoire, le suivi des modifications, la liaison de données et la sérialisation d’objets en tant que données XML. Pour plus d’informations, consultez [utilisation des objets](working-with-objects.md).  
  
  Si le Entity Framework ne fournit pas les fonctionnalités du jeu de données nécessaire à votre application, vous pouvez toujours tirer parti des avantages des requêtes LINQ à l’aide de LINQ to DataSet. Pour plus d’informations, [consultez LINQ to DataSet](../linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Considérations relatives aux applications qui lient des données à des contrôles  

 La .NET Framework vous permet d’encapsuler des données dans une source de données, telle qu’un DataSet ou un contrôle de source de données ASP.NET, puis de lier des éléments d’interface utilisateur à ces contrôles de données. La liste suivante décrit les considérations concernant la liaison de contrôles à des données Entity Framework.  
  
- Liaison de données à des contrôles.  

  Lorsque vous interrogez le modèle conceptuel, le Entity Framework retourne les données sous forme d’objets qui sont des instances de types d’entité. Ces objets peuvent être liés directement à des contrôles, et cette liaison prend en charge les mises à jour. Cela signifie que les modifications apportées aux données dans un contrôle, telles qu’une ligne dans un <xref:System.Windows.Forms.DataGridView> , sont automatiquement enregistrées dans la base de données lorsque la <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> méthode est appelée.  
  
  Si votre application énumère les résultats d’une requête pour afficher des données dans un objet <xref:System.Windows.Forms.DataGridView> ou un autre type de contrôle que prend en charge la liaison de données, vous pouvez modifier votre application pour lier le contrôle au résultat d’un objet <xref:System.Data.Objects.ObjectQuery%601>.  
  
  Pour plus d’informations, consultez [liaison d’objets à des contrôles](/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100)).  
  
- ASP.NET contrôles de source de données.  

  Le Entity Framework comprend un contrôle de source de données conçu pour simplifier la liaison de données dans les applications Web ASP.NET. Pour plus d’informations, consultez [vue d’ensemble du contrôle serveur Web EntityDataSource](/previous-versions/aspnet/cc488502(v=vs.100)).  
  
## <a name="other-considerations"></a>Autres considérations  

 Les remarques suivantes peuvent s’appliquer lorsque vous effectuez une migration de types spécifiques d’applications vers Entity Framework.  
  
- Applications qui exposent des services de données.  

  Les services Web et les applications basées sur Windows Communication Foundation (WCF) exposent les données d'une source de données sous-jacente en utilisant un format de messagerie de demande/réponse XML. Le Entity Framework prend en charge la sérialisation d’objets d’entité à l’aide de la sérialisation de contrat de données binary, XML ou WCF. La sérialisation binaire et la sérialisation WCF prennent tous les deux en charge la sérialisation complète de graphiques d'objets. Pour plus d’informations, consultez [génération d’applications multicouches](/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100)).  
  
- Applications qui utilisent des données XML.  

  La sérialisation d’objets vous permet de créer des services de données de Entity Framework. Ces services fournissent des données à des applications qui utilisent des données XML, telles que les applications Internet AJAX. Dans ce cas, envisagez d’utiliser WCF Data Services. Ces services de données sont basés sur le modèle EDM (Entity Data Model) et fournissent un accès dynamique aux données d'entité à l'aide d'actions HTTP REST (Representational State Transfer) standard, telles que GET, PUT et POST. Pour plus d’informations, consultez [WCF Data Services 4.5](../../wcf/index.md).  
  
  Le Entity Framework ne prend pas en charge un type de données XML natif. Cela signifie que, lorsqu'une entité est mappée à une table avec une colonne XML, la propriété d'entité équivalente de la colonne XML est une chaîne. Les objets peuvent être déconnectés et sérialisés sous forme de données XML. Pour plus d’informations, consultez [sérialisation d’objets](/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
  Si votre application nécessite la possibilité d'interroger des données XML, vous pouvez tout de même tirer parti des avantages des requêtes LINQ en utilisant LINQ to XML. Pour plus d’informations, consultez [LINQ to XML (C#)](../../../../standard/linq/linq-xml-overview.md) ou [LINQ to XML (Visual Basic)](../../../../standard/linq/linq-xml-overview.md).  
  
- Applications qui gèrent l'état.  

  Les applications Web ASP.NET doivent souvent conserver l’état d’une page Web ou d’une session utilisateur. Les objets d’une <xref:System.Data.Objects.ObjectContext> instance peuvent être stockés dans l’état d’affichage du client ou dans l’état de session sur le serveur, puis récupérés et attachés ultérieurement à un nouveau contexte d’objet. Pour plus d’informations, consultez [attachement et détachement d’objets](/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100)).  
  
## <a name="see-also"></a>Voir aussi

- [Considérations relatives au déploiement](deployment-considerations.md)
- [Terminologie Entity Framework](terminology.md)
