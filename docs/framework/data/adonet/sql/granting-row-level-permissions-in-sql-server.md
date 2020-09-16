---
title: Attribution d'autorisations de niveau ligne dans SQL Server
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 0b34eaee4b66a2be82049816f0a98b9f53012303
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554851"
---
# <a name="granting-row-level-permissions-in-sql-server"></a>Attribution d'autorisations de niveau ligne dans SQL Server

Dans certains scénarios, il est nécessaire de contrôler l’accès aux données plus précisément qu’en se contentant d’accorder, de révoquer ou de refuser des autorisations. Par exemple, l’application de base de données d’un hôpital peut nécessiter que chaque médecin ne puisse accéder qu’aux informations de ses propres patients. Des scénarios similaires existent dans de nombreux environnements, notamment dans les applications financières, juridiques, publiques et militaires. Pour gérer ces scénarios, SQL Server 2016 propose une fonctionnalité [Sécurité au niveau des lignes](/sql/relational-databases/security/row-level-security) qui simplifie et centralise la logique d’accès au niveau des lignes dans une stratégie de sécurité. Pour les versions antérieures de SQL Server, une fonctionnalité similaire peut être obtenue à l’aide de vues permettant de mettre en œuvre un filtrage au niveau des lignes.

## <a name="implementing-row-level-filtering"></a>Implémentation du filtrage au niveau des lignes

Le filtrage au niveau des lignes est utilisé pour les applications qui stockent des informations dans une seule table, comme dans l’exemple de l’hôpital ci-dessus. Pour implémenter le filtrage au niveau des lignes, chaque ligne est associée à une colonne qui définit un paramètre de différenciation, comme un nom d’utilisateur, une étiquette ou tout autre identificateur. Vous créez une stratégie de sécurité ou une vue sur la table, qui filtre les lignes auxquelles l’utilisateur a accès. Vous créez ensuite des procédures stockées paramétrées qui contrôlent les types de requêtes que l’utilisateur peut exécuter.

L’exemple suivant décrit comment configurer le filtrage au niveau des lignes à partir d’un nom d’utilisateur ou d’un nom de connexion.

- Créez la table en ajoutant une colonne pour stocker le nom.

- Activez le filtrage au niveau des lignes :

  - Si vous utilisez SQL Server 2016 ou version ultérieure, ou [Azure SQL Database](/azure/sql-database/), créez une stratégie de sécurité qui ajoute un prédicat sur la table pour limiter les lignes retournées à celles qui correspondent à l’utilisateur de base de données actuel (à l’aide de la fonction intégrée CURRENT_USER()) ou au nom de connexion actuel (à l’aide de la fonction intégrée SUSER_SNAME()) :

      ```sql
      CREATE SCHEMA Security
      GO

      CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)
          RETURNS TABLE
          WITH SCHEMABINDING
      AS
          RETURN SELECT 1 AS accessResult
          WHERE @UserName = SUSER_SNAME()
      GO

      CREATE SECURITY POLICY Security.userAccessPolicy
          ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,
          ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable
      GO
      ```

  - Si vous utilisez une version de SQL Server antérieure à 2016, vous pouvez obtenir des fonctionnalités similaires à l’aide d’une vue :

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- Créez des procédures stockées pour sélectionner, insérer, mettre à jour et supprimer des données. Si le filtrage est imposé par une stratégie de sécurité, les procédures stockées doivent effectuer ces opérations directement sur la table de base. Dans le cas contraire, si le filtrage est imposé par une vue, les procédures stockées doivent plutôt fonctionner sur la vue. La stratégie de sécurité ou la vue filtre automatiquement les lignes retournées ou modifiées par les requêtes utilisateur, et la procédure stockée fournit une limite de sécurité plus élevée pour empêcher les utilisateurs bénéficiant d’un accès direct aux requêtes d’exécuter des requêtes capables de déduire l’existence des données filtrées.

- Pour les procédures stockées qui insèrent des données, capturez le nom d’utilisateur à l’aide de la même fonction que celle spécifiée dans la stratégie de sécurité ou la vue et insérez cette valeur dans la colonne UserName.

- Refusez au rôle `public` toutes les autorisations sur les tables (et les vues, le cas échéant). Les utilisateurs ne peuvent pas hériter des autorisations d’autres rôles de base de données, car le prédicat de filtre repose sur des noms d’utilisateurs ou de connexion, et non sur des rôles.

- Accordez aux rôles de base de données l'autorisation EXECUTE sur les procédures stockées. Les utilisateurs ne peuvent accéder aux données que par le biais des procédures stockées fournies.

## <a name="see-also"></a>Voir aussi

- [Sécurité au niveau des lignes](/sql/relational-databases/security/row-level-security)
- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Vue d'ensemble de la sécurité SQL Server](overview-of-sql-server-security.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Gestion des autorisations avec les procédures stockées dans SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Écriture d’une instruction SQL dynamique sécurisée dans SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
