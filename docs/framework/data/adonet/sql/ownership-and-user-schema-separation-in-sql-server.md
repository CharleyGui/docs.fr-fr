---
title: Propriété et séparation des schémas utilisateur dans SQL Server
description: Découvrez comment la séparation utilisateur-schéma permet de gérer SQL Server autorisations d’objet de base de données. Les schémas regroupent les objets dans des espaces de noms distincts.
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: 97e742979785fedd922dc887295b63e2d93bd147
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286260"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a>Propriété et séparation des schémas utilisateur dans SQL Server
Il existe un concept essentiel relative à la sécurité de SQL Server, selon lequel les propriétaires d'objets disposent d'autorisations irrévocables pour les administrer. Vous ne pouvez pas supprimer les privilèges d’un propriétaire d’objets et vous ne pouvez pas supprimer des utilisateurs d’une base de données dans laquelle se trouvent des objets qui leur appartiennent.  
  
## <a name="user-schema-separation"></a>Séparation utilisateur-schéma  
 La séparation utilisateur-schéma permet plus de souplesse dans la gestion des autorisations d'objet de base de données. Un *schéma* est un conteneur nommé pour les objets de base de données, qui vous permet de regrouper des objets dans des espaces de noms distincts. Par exemple, l'exemple de base de données AdventureWorks contient des schémas pour Production, Sales et HumanResources.  
  
 La syntaxe de dénomination en quatre parties destinée à faire référence à des objets spécifie le nom de schéma.  
  
```text
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a>Propriétaires et autorisations de schéma  
 Les schémas peuvent appartenir à n'importe quelle principal de sécurité de base de données, tandis qu'une principal de sécurité unique peut posséder plusieurs schémas. Vous pouvez appliquer des règles de sécurité à un schéma, dont hériteront tous les objets du schéma. Une fois que vous avez défini des autorisations d'accès pour un schéma, elles sont automatiquement appliquées lors de l'ajout de nouveaux objets au schéma. Un schéma par défaut peut être affecté aux utilisateurs, et plusieurs utilisateurs de base de données peuvent partager le même schéma.  
  
 Par défaut, lorsque des développeurs créent des objets dans un schéma, ces objets appartiennent à la principal de sécurité qui possède le schéma, et non aux développeurs. La propriété d'objet peut être transférée avec l'instruction Transact-SQL ALTER AUTHORIZATION. Un schéma peut également contenir des objets qui appartiennent à différents utilisateurs et disposent d'autorisations plus précises que celles affectées au schéma, même si cela n'est pas recommandé car la gestion des autorisations devient alors plus complexe. Les objets peuvent être déplacés entre plusieurs schémas et la propriété de schéma peut être transférée entre plusieurs entités. Les utilisateurs de base de données peuvent être supprimés sans affecter les schémas.  
  
### <a name="built-in-schemas"></a>Schémas intégrés  
 SQL Server est livré avec six schémas prédéfinis qui possèdent les mêmes noms que les utilisateurs et les rôles de base de données intégrés. Ils sont principalement destinés à la compatibilité descendante. Vous pouvez supprimer les schémas qui possèdent les mêmes noms que ceux des rôles de base de données fixes si vous n’en avez pas besoin. Par contre, vous ne pouvez pas déposer les schémas suivants :  
  
- `dbo`  
  
- `guest`  
  
- `sys`  
  
- `INFORMATION_SCHEMA`  
  
 Si vous les supprimez de la base de données model, ils n'apparaîtront pas dans les nouvelles bases de données.  
  
> [!NOTE]
> Les schémas `sys` et `INFORMATION_SCHEMA` sont réservés pour les objets système. Vous ne pouvez pas créer d’objets dans ces schémas et vous ne pouvez pas les déposer.  
  
#### <a name="the-dbo-schema"></a>Schéma dbo  
 Le schéma `dbo` constitue le schéma par défaut d'une base de données qui vient d'être créée. Le schéma `dbo` appartient au compte d'utilisateur `dbo`. Par défaut, les utilisateurs créés avec la commande Transact-SQL CREATE USER ont `dbo` en tant que schéma par défaut.  
  
 Les utilisateurs à qui est affecté le schéma `dbo` n'héritent pas des autorisations du compte d'utilisateur `dbo`. Les utilisateurs n'héritent d'aucune autorisation provenant d'un schéma. En effet, ce sont les objets de base de données contenus dans le schéma qui héritent des autorisations du schéma.  
  
> [!NOTE]
> Lorsque des objets de base de données sont référencés à l'aide d'un nom en une partie dans SQL Server consulte d'abord le schéma par défaut de l'utilisateur. Si l'objet y est introuvable, SQL Server recherche ensuite dans le schéma `dbo`. Si l'objet ne se trouve pas non plus dans le schéma `dbo`, une erreur est retournée.  
  
## <a name="external-resources"></a>Ressources externes  
 Pour plus d'informations sur la propriété d'objet et les schémas, voir les ressources suivantes.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Séparation du schéma et de l’utilisateur](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))|Décrit les modifications introduites par la séparation utilisateur-schéma. Inclut un nouveau comportement, son impact sur la propriété, des affichages catalogue et des autorisations.|  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Authentification dans SQL Server](authentication-in-sql-server.md)
- [Serveur et rôles de base de données dans SQL Server](server-and-database-roles-in-sql-server.md)
- [Autorisation et permissions dans SQL Server](authorization-and-permissions-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
