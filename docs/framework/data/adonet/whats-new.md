---
title: Nouveautés dans ADO.NET
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: 0a02ca3885524c5fcf8def603acdce33a972d283
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791260"
---
# <a name="whats-new-in-adonet"></a>Nouveautés dans ADO.NET

Les fonctionnalités suivantes sont nouvelles dans ADO.NET dans le .NET Framework 4,5.

## <a name="sqlclient-data-provider"></a>Fournisseur de données SqlClient

Les fonctionnalités suivantes sont nouvelles dans le Fournisseur de données .NET Framework pour SQL Server dans .NET Framework 4,5 :

- Les mots clés de chaîne de connexion ConnectRetryCount et ConnectRetryInterval (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) vous permettent de contrôler la fonctionnalité de résilience des connexions inactives.

- La prise en charge de la diffusion en continu de SQL Server à une application prend en charge les scénarios où les données sur le serveur ne sont pas structurées.  Pour plus d’informations, consultez [prise en charge de la diffusion en continu SqlClient](sqlclient-streaming-support.md) .

- La prise en charge a été ajoutée pour la programmation asynchrone.  Pour plus d’informations, consultez [programmation asynchrone](asynchronous-programming.md) .

- Les échecs de connexion sont désormais enregistrés dans le journal des événements étendus. Pour plus d’informations, consultez [Traçage de données dans ADO.NET](data-tracing.md).

- SqlClient prend désormais en charge la haute disponibilité, la fonctionnalité de récupération d’urgence de SQL Server, AlwaysOn. Pour plus d’informations, consultez [prise en charge de SqlClient pour la haute disponibilité et la récupération d’urgence](./sql/sqlclient-support-for-high-availability-disaster-recovery.md).

- Un mot de passe peut être passé <xref:System.Security.SecureString> en tant que lors de l’utilisation de l’authentification SQL Server. Pour plus d'informations, voir <xref:System.Data.SqlClient.SqlCredential>.

- Lorsque `TrustServerCertificate` a la valeur `Encrypt` false et que a la valeur true, le nom du serveur (ou l’adresse IP) dans un certificat SSL SQL Server doit correspondre exactement au nom du serveur (ou à l’adresse IP) spécifié dans la chaîne de connexion. Sinon, la connexion échouera. Pour plus d'informations, consultez la description de l'option de connexion `Encrypt` dans <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

  Si cette modification empêche une application existante de se connecter, vous pouvez résoudre le problème de l'application en utilisant l'un des éléments suivants :

  - Délivrez un certificat qui spécifie le nom court dans le champ de nom commun (CN) ou d'autre nom de l'objet (SAN). Cette solution fonctionne pour la mise en miroir de base de données.

  - Ajoutez un alias qui mappe le nom court au nom de domaine complet.

  - Utilisez le nom de domaine qualifié complet dans la chaîne de connexion.

- SqlClient prend en charge la protection étendue. Pour plus d’informations sur la protection étendue, consultez [connexion au moteur de base de données à l’aide de la protection étendue](https://go.microsoft.com/fwlink/?LinkId=219978).

- SqlClient prend en charge les connexions aux bases de données LocalDB. Pour plus d’informations, consultez [prise en charge de SqlClient pour](./sql/sqlclient-support-for-localdb.md)la base de données locale.

- `Type System Version=SQL Server 2012;` est une nouvelle valeur à passer à la propriété de connexion `Type System Version`. La valeur `Type System Version=Latest;` est désormais obsolète et a été rendue équivalente à `Type System Version=SQL Server 2008;`. Pour plus d'informations, consultez <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

- SqlClient fournit la prise en charge supplémentaire des colonnes éparses, une fonctionnalité ajoutée dans SQL Server 2008. Si votre application accède déjà aux données dans un table qui utilise des colonnes éparses, vous devez constater une augmentation des performances. La colonne IsColumnSet de <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> indique si une colonne est une colonne éparse qui est membre d'un jeu de colonnes. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>indique si une colonne est une colonne éparse (pour plus d’informations, consultez [SQL Server collections de schémas](sql-server-schema-collections.md) ). Pour plus d’informations sur les colonnes éparses, consultez [utilisation de colonnes éparses](https://go.microsoft.com/fwlink/?LinkId=224244).

- L'assembly Microsoft.SqlServer.Types.dll, contenant les types de données spatiales, a été mis à niveau de la version 10.0 vers la version 11.0. Les applications qui référencent cet assembly peuvent échouer. Pour plus d’informations, consultez [modifications critiques apportées aux fonctionnalités de moteur de base de données](https://go.microsoft.com/fwlink/?LinkId=224367).

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

Le .NET Framework 4,5 ajoute des API qui permettent de nouveaux scénarios lors de l’utilisation du Entity Framework 5,0. Pour plus d’informations sur les améliorations et les fonctionnalités qui ont été ajoutées au Entity Framework 5,0, consultez les rubriques suivantes : [Nouveautés](https://go.microsoft.com/fwlink/?LinkID=251106) et versions de [Entity Framework et contrôle de version](https://go.microsoft.com/fwlink/?LinkId=234899).

## <a name="see-also"></a>Voir aussi

- [ADO.NET](index.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
- [SQL Server et ADO.NET](./sql/index.md)
- [Nouveautés de WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
