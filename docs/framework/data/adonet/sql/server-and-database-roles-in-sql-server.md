---
title: Serveur et rôles de base de données dans SQL Server
description: En savoir plus sur les rôles serveur fixes et les rôles de base de données fixes, qui ont un ensemble fixe d’autorisations qui leur sont attribuées. SQL Server utilise la sécurité basée sur les rôles.
ms.date: 03/30/2017
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
ms.openlocfilehash: 3babf6b249da6e67a6a48bcad647e4674650c348
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177330"
---
# <a name="server-and-database-roles-in-sql-server"></a>Serveur et rôles de base de données dans SQL Server

Toutes les versions de SQL Server utilisent la sécurité basée sur les rôles, qui vous permet d'attribuer des autorisations à un rôle ou à un groupe d'utilisateurs au lieu de les attribuer à des utilisateurs individuels. Les rôles serveur fixes et de base de données fixes possèdent un ensemble fixe d'autorisations qui leur sont attribuées.  
  
## <a name="fixed-server-roles"></a>Rôles serveur fixes  

 Les rôles serveur fixes disposent d'un ensemble fixe d'autorisations et d'une portée à l'échelle du serveur. Ils sont destinés à être utilisés pour administrer SQL Server et les autorisations qui leur sont attribuées ne peuvent pas être modifiées. Des connexions peuvent être attribuées aux rôles serveur fixes sans qu'un compte d'utilisateur figure dans une base de données.  
  
> [!IMPORTANT]
> Le rôle serveur fixe `sysadmin` englobe tous les autres rôles et a une portée illimitée. N'ajoutez pas de principaux à ce rôle à moins qu'ils soient dotés d'une confiance très élevée. Les membres du rôle `sysadmin` possèdent des privilèges d'administrateur irrévocables sur toutes les bases de données et ressources de serveur.  
  
 Soyez sélectif lors de l'ajout d'utilisateurs à des rôles serveur fixes. Par exemple, le rôle `bulkadmin` permet aux utilisateurs d'insérer le contenu d'un fichier local quelconque dans une table, ce qui peut mettre en danger l'intégrité des données. Consultez Documentation en ligne de SQL Server pour obtenir la liste complète des rôles serveur fixes et des autorisations.  
  
## <a name="fixed-database-roles"></a>Rôles de base de données fixes  

 Les rôles de base de données fixes possèdent un ensemble prédéfini d'autorisations conçues pour vous permettre de gérer aisément des groupes d'autorisations. Les membres du rôle `db_owner` peuvent effectuer toutes les activités de configuration et de maintenance sur la base de données.  
  
 Pour plus d'informations sur les rôles prédéfinis de SQL Server, consultez les ressources répertoriées ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Rôles de niveau serveur](/sql/relational-databases/security/authentication-access/server-level-roles)|Décrit les rôles serveur fixes et les autorisations qui leur sont associées dans SQL Server.|  
|[Rôles au niveau de la base de données](/sql/relational-databases/security/authentication-access/database-level-roles)|Décrit les rôles de base de données fixes et les autorisations qui leur sont attribuées|  
  
## <a name="database-roles-and-users"></a>Rôles de base de données et utilisateurs  

 Les connexions doivent être mappées sur des comptes d'utilisateur de base de données afin de fonctionner avec des objets de base de données. Les utilisateurs de base de données peuvent alors être ajoutés à des rôles de base de données et héritent de tous les jeux d'autorisations associés à ces rôles. Toutes les autorisations peuvent être accordées.  
  
 Vous devez également prendre en compte le rôle `public`, le compte d'utilisateur `dbo` et le compte `guest` lors de la conception de la sécurité pour votre application.  
  
### <a name="the-public-role"></a>Rôle public  

 Le rôle `public` est inclus dans chaque base de données, y compris les bases de données système. Il ne peut pas être supprimé et vous ne pouvez pas ajouter ni supprimer d’utilisateurs dans ce rôle. Les autorisations accordées au rôle `public` sont héritées par tous les autres utilisateurs et rôles car ils appartiennent par défaut au rôle `public`. Accordez au rôle `public` uniquement les autorisations que vous souhaitez accorder à tous les utilisateurs.  
  
### <a name="the-dbo-user-account"></a>Compte d'utilisateur dbo  

 Le compte `dbo`, ou propriétaire de base de données, est un compte d'utilisateur qui possède des autorisations implicites pour effectuer toutes les activités dans la base de données. Les membres du rôle serveur fixe `sysadmin` sont automatiquement mappés sur `dbo`.  
  
> [!NOTE]
> `dbo` est également le nom d’un schéma, comme indiqué dans [propriété et séparation des schémas utilisateur dans SQL Server](ownership-and-user-schema-separation-in-sql-server.md).  
  
 Le compte d'utilisateur `dbo` est fréquemment confondu avec le rôle de base de données fixe `db_owner`. La portée de `db_owner` est une base de données, tandis que la portée de `sysadmin` est le serveur dans son intégralité. L'appartenance au rôle `db_owner` ne confère pas les privilèges d'utilisateur `dbo`.  
  
### <a name="the-guest-user-account"></a>Compte d'utilisateur guest  

 Une fois qu'un utilisateur a été authentifié et autorisé à se connecter à une instance de SQL Server, un compte d'utilisateur distinct doit exister dans chaque base de données à laquelle l'utilisateur doit accéder. Exiger un compte d'utilisateur dans chaque base de données empêche les utilisateurs de se connecter à une instance de SQL Server et d'accéder à toutes les bases de données sur un serveur. L’existence d’un compte d’utilisateur `guest` dans la base de données permet de contourner cette exigence en permettant à une connexion sans compte d’utilisateur de base de données d’accéder à une base de données.  
  
 Le compte `guest` est un compte intégré dans toutes les versions de SQL Server. Il est désactivé par défaut dans les nouvelles bases de données. S'il est activé, vous pouvez le désactiver en révoquant son autorisation CONNECT, en exécutant l'instruction Transact-SQL REVOKE CONNECT FROM GUEST.  
  
> [!IMPORTANT]
> Évitez d'utiliser le compte `guest` ; toutes les connexions sans autorisations de base de données propres obtiennent les autorisations de base de données accordées à ce compte. Si vous devez utiliser le compte `guest`, accordez-lui des autorisations minimales.  
  
 Pour plus d'informations sur les connexions, les utilisateurs et les rôles SQL Server, consultez les ressources répertoriées ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Prise en main des autorisations du moteur de base de données](/sql/relational-databases/security/authentication-access/getting-started-with-database-engine-permissions)|Contient des liens vers des rubriques qui décrivent les entités de sécurité, les rôles, les informations d'identification, les éléments sécurisables et les autorisations.|  
|[Principaux](/sql/relational-databases/security/authentication-access/principals-database-engine)|Décrit les entités de sécurité et contient des liens vers des rubriques qui décrivent les rôles serveur et de base de données.|  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Authentification dans SQL Server](authentication-in-sql-server.md)
- [Propriété et séparation des schémas utilisateur dans SQL Server](ownership-and-user-schema-separation-in-sql-server.md)
- [Autorisation et permissions dans SQL Server](authorization-and-permissions-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
