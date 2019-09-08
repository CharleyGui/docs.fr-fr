---
title: Authentification dans SQL Server
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 49835ebf8ebe4d5bd200ed771477edc8af580b7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794297"
---
# <a name="authentication-in-sql-server"></a>Authentification dans SQL Server
SQL Server prend en charge deux modes d'authentification, le mode d'authentification Windows et le mode mixte.  
  
- L'authentification Windows correspond au mode par défaut et il est souvent qualifié de sécurité intégrée car ce modèle de sécurité SQL Server est étroitement intégré à Windows. Des comptes d'utilisateurs et de groupes Windows spécifiques sont approuvés pour se connecter à SQL Server. Les utilisateurs Windows qui ont déjà été authentifiés n'ont pas besoin de présenter d'informations d'identification supplémentaires.  
  
- Le mode mixte prend en charge l'authentification par Windows et par SQL Server. Les paires nom d'utilisateur–mot de passe sont conservées dans SQL Server.  
  
> [!IMPORTANT]
> Il est recommandé d'utiliser l'authentification Windows chaque fois que possible. L'authentification Windows utilise une série de messages chiffrés pour authentifier les utilisateurs dans SQL Server. Lorsque SQL Server des connexions sont utilisées, les noms de connexion SQL Server et les mots de passe chiffrés sont transmis sur le réseau, ce qui les rend moins sécurisés.  
  
 Avec l'authentification Windows, les utilisateurs ont déjà ouvert une session Windows et n'ont pas besoin d'ouvrir une session SQL Server distincte. L’exemple `SqlConnection.ConnectionString` suivant spécifie l’authentification Windows sans obliger les utilisateurs à fournir un nom d’utilisateur ou un mot de passe.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
> Les connexions sont différentes des utilisateurs de base de données. Vous devez mapper les connexions ou les groupes Windows sur les utilisateurs de base de données ou les rôles dans une opération distincte. Vous accordez ensuite des autorisations aux utilisateurs ou aux rôles pour accéder aux objets de base de données.  
  
## <a name="authentication-scenarios"></a>Scénarios d'authentification  
 L'authentification Windows représente généralement le meilleur choix dans les situations suivantes :  
  
- Il existe un contrôleur de domaine.  
  
- L'application et la base de données se trouvent sur le même ordinateur.  
  
- Vous utilisez une instance de SQL Server Express ou de base de données locale.  
  
 Les connexions SQL Server sont souvent utilisées dans les situations suivantes :  
  
- si vous avez un groupe de travail ;  
  
- les utilisateurs se connectent à partir de domaines différents, non approuvés ;  
  
- Applications Internet, telles que ASP.NET.  
  
> [!NOTE]
> La spécification de l'authentification Windows ne désactive pas les connexions SQL Server. Utilisez l'instruction Transact-SQL ALTER LOGIN DISABLE pour désactiver des connexions SQL Server dotées de privilèges élevés.  
  
## <a name="login-types"></a>Types de connexions  
 SQL Server prend en charge trois types de connexions :  
  
- Compte d'utilisateur Windows local ou compte de domaine approuvé. SQL Server s'appuie sur Windows pour authentifier les comptes d'utilisateurs Windows.  
  
- Groupe Windows. Accorder l'accès à un groupe Windows permet d'accorder l'accès à toutes les connexions utilisateur Windows membres du groupe.  
  
- Connexion SQL Server. SQL Server stocke le nom d'utilisateur et un hachage du mot de passe dans la base de données MASTER, en utilisant des méthodes d'authentification internes pour vérifier les tentatives de connexion.  
  
> [!NOTE]
> SQL Server fournit des connexions créées à partir de certificats ou de clés asymétriques qui sont utilisées uniquement pour la signature de code. Elles ne peuvent pas être utilisées pour se connecter à SQL Server.  
  
## <a name="mixed-mode-authentication"></a>Authentification en mode mixte  
 Si vous devez utiliser l'authentification en mode mixte, vous devez créer des connexions SQL Server qui sont stockées dans SQL Server. Vous devez ensuite fournir le nom d'utilisateur et le mot de passe SQL Server au moment de l'exécution.  
  
> [!IMPORTANT]
> SQL Server est installé avec une connexion SQL Server nommée `sa` (abréviation de « system administrator »). Attribuez un mot de passe fort à la connexion `sa` et n'utilisez pas la connexion `sa` dans votre application. La connexion `sa` correspond au rôle serveur fixe `sysadmin`, qui possède des informations d'identification d'administration irrévocables sur le serveur entier. Si un attaquant bénéficie de l'accès en tant qu'administrateur système, les dommages potentiels sont sans limite. Tous les membres du groupe `BUILTIN\Administrators` Windows (groupe des administrateurs locaux) sont membres du rôle `sysadmin` par défaut, mais peuvent être supprimés de ce rôle.  
  
 SQL Server fournit des mécanismes de stratégie de mot de passe Windows pour les connexions SQL Server [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] lorsqu’il s’exécute sur ou versions ultérieures. Les stratégies de complexité des mots de passe sont conçues pour prévenir les attaques en force brute en augmentant le nombre de mots de passe possibles. SQL Server pouvez appliquer les mêmes stratégies de complexité et d’expiration [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] que celles utilisées dans aux mots de passe utilisés dans SQL Server.  
  
> [!IMPORTANT]
> La concaténation des chaînes de connexion à partir des entrées utilisateur peut vous rendre vulnérable à une attaque par injection de chaîne de connexion. Utilisez le <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pour créer des chaînes de connexion valides du point de vue de la syntaxe au moment de l'exécution. Pour plus d’informations, consultez [Builders de chaînes de connexion](../connection-string-builders.md).  
  
## <a name="external-resources"></a>Ressources externes  
 Pour plus d'informations, voir les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Principaux](/sql/relational-databases/security/authentication-access/principals-database-engine)|Décrit les connexions et autres entités de sécurité dans SQL Server.|  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Connexion à une source de données](../connecting-to-a-data-source.md)
- [Chaînes de connexion](../connection-strings.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
