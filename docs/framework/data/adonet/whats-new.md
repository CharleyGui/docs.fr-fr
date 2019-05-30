---
title: Nouveautés dans ADO.NET
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: 77a7aa5721a83bf7bc8d3e3cbf57a77c56267062
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379983"
---
# <a name="whats-new-in-adonet"></a>Nouveautés dans ADO.NET

Les fonctionnalités suivantes sont nouvelles dans ADO.NET dans le .NET Framework 4.5.

## <a name="sqlclient-data-provider"></a>Fournisseur de données SqlClient

Les fonctionnalités suivantes sont nouvelles dans le fournisseur de données .NET Framework pour SQL Server dans .NET Framework 4.5 :

- Les mots clés de chaîne de connexion ConnectRetryCount et ConnectRetryInterval (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) vous permettent de contrôler la fonctionnalité de résilience des connexions inactives.

- Prise en charge à partir de SQL Server à une application de diffusion en continu prend en charge les scénarios où les données sur le serveur sont non structurées.  Consultez [prise en charge de la diffusion en continu SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md) pour plus d’informations.

- La prise en charge a été ajoutée pour la programmation asynchrone.  Consultez [programmation asynchrone](../../../../docs/framework/data/adonet/asynchronous-programming.md) pour plus d’informations.

- Les échecs de connexion sont désormais enregistrés dans le journal des événements étendus. Pour plus d’informations, consultez [Traçage de données dans ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md).

- SqlClient prend désormais en charge haute disponibilité de SQL Server, fonctionnalité de récupération d’urgence, AlwaysOn. Pour plus d’informations, consultez [prise en charge de SqlClient pour la haute disponibilité, récupération d’urgence](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

- Un mot de passe peut être passée comme un <xref:System.Security.SecureString> lors de l’utilisation de l’authentification SQL Server. Pour plus d'informations, voir <xref:System.Data.SqlClient.SqlCredential>.

- Lorsque `TrustServerCertificate` a la valeur false et `Encrypt` a la valeur true, le nom du serveur (ou adresse IP) dans un certificat SSL SQL Server doit correspondre exactement au nom de serveur (ou adresse IP) spécifié dans la chaîne de connexion. Sinon, la connexion échouera. Pour plus d'informations, consultez la description de l'option de connexion `Encrypt` dans <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

  Si cette modification empêche une application existante de se connecter, vous pouvez résoudre le problème de l'application en utilisant l'un des éléments suivants :

  - Délivrez un certificat qui spécifie le nom court dans le champ de nom commun (CN) ou d'autre nom de l'objet (SAN). Cette solution fonctionne pour la mise en miroir de base de données.

  - Ajoutez un alias qui mappe le nom court au nom de domaine complet.

  - Utilisez le nom de domaine qualifié complet dans la chaîne de connexion.

- SqlClient prend en charge la protection étendue. Pour plus d’informations sur la Protection étendue, consultez [connexion à la base de données de moteur à l’aide de la Protection étendue](https://go.microsoft.com/fwlink/?LinkId=219978).

- SqlClient prend en charge les connexions aux bases de données LocalDB. Pour plus d’informations, consultez [prise en charge de SqlClient pour LocalDB](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-localdb.md).

- `Type System Version=SQL Server 2012;` est une nouvelle valeur à passer à la propriété de connexion `Type System Version`. La valeur `Type System Version=Latest;` est désormais obsolète et a été rendue équivalente à `Type System Version=SQL Server 2008;`. Pour plus d'informations, consultez <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

- SqlClient fournit la prise en charge supplémentaire des colonnes éparses, une fonctionnalité ajoutée dans SQL Server 2008. Si votre application accède déjà aux données dans un table qui utilise des colonnes éparses, vous devez constater une augmentation des performances. La colonne IsColumnSet de <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> indique si une colonne est une colonne éparse qui est membre d'un jeu de colonnes. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Indique si une colonne est une colonne éparse (consultez [Collections de schémas SQL Server](../../../../docs/framework/data/adonet/sql-server-schema-collections.md) pour plus d’informations). Pour plus d’informations sur les colonnes éparses, consultez [à l’aide des colonnes éparses](https://go.microsoft.com/fwlink/?LinkId=224244).

- L'assembly Microsoft.SqlServer.Types.dll, contenant les types de données spatiales, a été mis à niveau de la version 10.0 vers la version 11.0. Les applications qui référencent cet assembly peuvent échouer. Pour plus d’informations, consultez [modifications avec rupture des fonctionnalités du moteur de base de données](https://go.microsoft.com/fwlink/?LinkId=224367).

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

Le .NET Framework 4.5 ajoute des API qui permettent aux nouveaux scénarios lorsque vous travaillez avec Entity Framework 5.0. Pour plus d’informations sur les améliorations et fonctionnalités qui ont été ajoutées à Entity Framework 5.0, consultez les rubriques suivantes : [Quelles sont les nouveautés](https://go.microsoft.com/fwlink/?LinkID=251106) et [versions et Entity Framework le contrôle de version](https://go.microsoft.com/fwlink/?LinkId=234899).

## <a name="see-also"></a>Voir aussi

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [Vue d’ensemble d’ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [SQL Server et ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)
- [Quelles sont les nouveautés dans WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
