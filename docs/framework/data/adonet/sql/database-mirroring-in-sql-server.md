---
title: Mise en miroir de bases de données dans SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: 7e2c1c8ea1cbc1bb22452b9ef9d1f250c96118ea
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173534"
---
# <a name="database-mirroring-in-sql-server"></a>Mise en miroir de bases de données dans SQL Server

La mise en miroir des bases de données dans SQL Server vous permet de conserver une copie, ou miroir, d’une base de données SQL Server sur un serveur de secours. La mise en miroir garantit que deux copies distinctes des données existent à tout moment, garantissant ainsi une haute disponibilité et une redondance complète des données. Le fournisseur de données .NET pour SQL Server offre une prise en charge implicite de la mise en miroir de base de données, de façon à ce que le développeur ne doive pas exécuter d'action ni écrire de code une fois qu'il a été configuré pour une base de données SQL Server. En outre, l'objet <xref:System.Data.SqlClient.SqlConnection> prend en charge un mode de connexion explicite qui permet de donner le nom d'un serveur partenaire de basculement dans le <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 La séquence d’événements simplifiée suivante se produit pour un objet <xref:System.Data.SqlClient.SqlConnection> qui cible une base de données configurée pour la mise en miroir :  
  
1. L’application cliente se connecte avec succès à la base de données principale et le serveur renvoie le nom du serveur partenaire, qui est ensuite mis en cache sur le client.  
  
2. Si le serveur contenant la base de données principale échoue ou si la connectivité est interrompue, l’état de la connexion et de la transaction est perdu. L’application cliente tente à nouveau d’établir une connexion à la base de données principale et échoue.  
  
3. L’application cliente tente alors de manière transparente d’établir une connexion à la base de données miroir sur le serveur partenaire. En cas de tentative, la connexion est redirigée vers la base de données miroir, qui devient alors la nouvelle base de données principale.  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a>Spécification du partenaire de basculement dans la chaîne de connexion  

 Si vous fournissez le nom d’un serveur partenaire de basculement dans la chaîne de connexion, le client tentera en toute transparence une connexion avec le partenaire de basculement si la base de données principale n’est pas disponible lors de la première connexion de l’application cliente.  
  
```csharp
";Failover Partner=PartnerServerName"  
```  
  
 Si vous omettez le nom du serveur partenaire de basculement et que la base de données principale n’est pas disponible lors de la première connexion de l’application cliente, une <xref:System.Data.SqlClient.SqlException> est déclenchée.  
  
 Lorsqu’une <xref:System.Data.SqlClient.SqlConnection> est ouverte avec succès, le nom du partenaire de basculement est retourné par le serveur et remplace toute valeur fournie dans la chaîne de connexion.  
  
> [!NOTE]
> Vous devez spécifier explicitement le nom de catalogue ou de base de données initial dans la chaîne de connexion pour les scénarios de mise en miroir de bases de données. Si le client reçoit des informations de basculement sur une connexion qui n’a pas de base de données ou de catalogue initial spécifié explicitement, les informations de basculement ne sont pas mises en cache et l’application ne tente pas de basculer en cas d’échec du serveur principal. Si une chaîne de connexion a une valeur pour le partenaire de basculement, mais pas de valeur pour la base de données ou le catalogue initial, une `InvalidArgumentException` est déclenchée.  
  
## <a name="retrieving-the-current-server-name"></a>Extraction du nom de serveur actuel  

 En cas de basculement, vous pouvez récupérer le nom du serveur auquel la connexion actuelle est réellement connectée à l’aide de la propriété <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> d’un objet <xref:System.Data.SqlClient.SqlConnection>. Le fragment de code suivant récupère le nom du serveur actif, en supposant que la variable de connexion fait référence à une <xref:System.Data.SqlClient.SqlConnection> ouverte.  
  
 Quand un événement de basculement se produit et que la connexion est basculée vers le serveur miroir, la propriété **DataSource** est mise à jour afin de refléter le nom du miroir.  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a>Comportement de mise en miroir de SqlClient  

 Le client tente toujours de se connecter au serveur principal actuel. En cas d’échec, il essaie le partenaire de basculement. Si la base de données miroir a déjà été basculée vers le rôle principal sur le serveur partenaire, la connexion réussit et le nouveau mappage de miroir principal est envoyé au client et mis en cache pendant la durée de vie du <xref:System.AppDomain> appelant. Il n’est pas stocké dans un stockage persistant et n’est pas disponible pour des connexions ultérieures dans un **AppDomain** ou processus différent. Toutefois, il est disponible pour des connexions ultérieures à l’intérieur du même **AppDomain**. Notez qu’un autre **AppDomain** ou processus s’exécutant sur le même ou un autre ordinateur a toujours son pool de connexions et que ces connexions ne sont pas réinitialisées. Dans ce cas, en cas d’arrêt de la base de données principale, chaque processus ou **AppDomain** échoue une fois et le pool est automatiquement effacé.  
  
> [!NOTE]
> Le support de la mise en miroir sur le serveur est configuré pour chaque base de données. Si les opérations de manipulation de données sont exécutées sur d’autres bases de données non incluses dans le jeu de données principal/miroir, soit en utilisant des noms en plusieurs parties, soit en modifiant la base de données en cours, les modifications apportées à ces autres bases de données ne se propagent pas en cas de défaillance. Aucune erreur n’est générée lorsque les données sont modifiées dans une base de données qui n’est pas mise en miroir. Le développeur doit évaluer l’impact possible de ces opérations.  
  
## <a name="database-mirroring-resources"></a>Ressources relatives à la mise en miroir de bases de données  

 Pour des informations et de la documentation conceptuelle sur la configuration, le déploiement et l’administration de la mise en miroir, consultez les ressources suivantes dans la documentation de SQL Server.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Mise en miroir de bases de données](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|Décrit comment installer et configurer la mise en miroir dans SQL Server.|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
