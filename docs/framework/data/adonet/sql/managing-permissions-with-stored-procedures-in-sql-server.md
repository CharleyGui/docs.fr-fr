---
title: Gestion des autorisations avec les procédures stockées dans SQL Server
description: Découvrez comment restreindre l’accès à vos données et objets de base de données en implémentant l’accès à l’aide de procédures stockées ou de fonctions définies par l’utilisateur.
ms.date: 03/30/2017
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
ms.openlocfilehash: 890c1c6dd7003f3abd684d6c827b6a77a3a019c1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286286"
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a>Gestion des autorisations avec les procédures stockées dans SQL Server
Une méthode pour créer plusieurs lignes de défense autour de votre base de données consiste à implémenter tous les accès aux données à l'aide de procédures stockées ou de fonctions définies par l'utilisateur. Vous révoquez ou refusez toutes les autorisations sur les objets sous-jacents, tels que les tables, et accordez les autorisations EXECUTE sur les procédures stockées De cette manière, vous créez un périmètre de sécurité autour vos objets de données et de base de données.  
  
## <a name="stored-procedure-benefits"></a>Avantages des procédures stockées  
 Les procédures stockées ont les avantages suivants :  
  
- Les règles d'entreprise et la logique des données peuvent être encapsulées de telle sorte que les utilisateurs ont accès aux données et aux objets uniquement selon les méthodes définies par les développeurs et les administrateurs de bases de données.   
  
- Des procédures stockées paramétrées et chargées de valider toutes les entrées d'utilisateur peuvent servir à contrer les attaques par injection SQL. Si vous utilisez du code SQL dynamique, veillez à paramétrer vos commandes et n'incluez jamais de valeurs de paramètre directement dans une chaîne de requête.  
  
- Les modifications des requêtes et des données ad hoc peuvent être interdites. Ainsi, les utilisateurs ne peuvent pas, par inadvertance ou par malveillance, détruire des données ou exécuter des requêtes qui nuisent aux performances sur le serveur ou le réseau.  
  
- Les erreurs peuvent être traitées dans le code de procédure sans passer directement dans les applications clientes. Cela empêche le retour de messages d'erreur, ce qui peut contribuer à une attaque de détection. Enregistrez les erreurs et traitez-les sur le serveur.  
  
- Les procédures stockées peuvent être écrites une seule fois et sont accessibles par de nombreuses applications.  
  
- Les applications clientes n'ont pas besoin de recevoir des informations sur les structures de données sous-jacentes. Le code des procédures stockées peut être modifié sans nécessiter des changements dans les applications clientes à condition que ces changements ne concernent pas les listes de paramètres ou les types de données retournés.  
  
- Les procédures stockées peuvent réduire le trafic réseau en associant plusieurs opérations dans un appel de procédure.  
  
## <a name="stored-procedure-execution"></a>Exécution des procédures stockées  
 Les procédures stockées tirent parti du chaînage des propriétés permettant de fournir l'accès aux données pour ne pas que les utilisateurs aient l'autorisation explicite d'accéder aux objets de base de données. Une chaîne de propriétés existe lorsque les objets qui sont accessibles les uns aux autres de manière séquentielle sont détenus par le même utilisateur. Par exemple, une procédure stockée peut appeler d'autres procédures stockées, ou une procédure stockée peut accéder à plusieurs tables. Si tous les objets dans la chaîne d'exécution ont le même propriétaire, SQL Server se contente de vérifier l'autorisation EXECUTE pour l'appelant, et non les autorisations de l'appelant sur d'autres objets. Par conséquent, il vous suffit d'accorder les autorisations EXECUTE sur les procédures stockées ; vous pouvez révoquer ou refuser toutes les autorisations sur les tables sous-jacentes.   
  
## <a name="best-practices"></a>Bonnes pratiques  
 La simple écriture de procédures stockées ne suffit pas à sécuriser votre application de façon adéquate. Vous devez également envisager les défaillances de sécurité potentielles suivantes.  
  
- Accordez les autorisations EXECUTE sur les procédures stockées pour les rôles de base de données que vous souhaitez faire accéder aux données.  
  
- Révoquez ou refusez toutes les autorisations sur les tables sous-jacentes pour tous les rôles et les utilisateurs de la base de données, y compris le rôle `public`. Tous les utilisateurs héritent des autorisations de public. Par conséquent, le refus des autorisations à `public` signifient que seuls les membres et les propriétaires `sysadmin` ont un accès ; tous les autres utilisateurs ne pourront pas hériter des autorisations issues des appartenances d'autres rôles.  
  
- N'ajoutez pas d'utilisateurs ou de rôles aux rôles `sysadmin` ou `db_owner`. Les administrateurs système et les propriétaires de bases de données peuvent accéder à tous les objets de base de données.  
  
- Désactivez le compte `guest`. Cela empêche les utilisateurs anonymes de se connecter à la base de données. Le compte invité est désactivé par défaut dans les nouvelles bases de données.  
  
- Implémentez la gestion des erreurs et enregistrez les erreurs.  
  
- Créez des procédures stockées paramétrées qui valident toutes les entrées d'utilisateur. Traitez toutes les entrées d'utilisateur comme non approuvées.  
  
- Évitez d'utiliser le code SQL dynamique, sauf si cela est absolument nécessaire. Utilisez la fonction Transact-SQL QUOTENAME() pour délimiter une valeur de chaîne et échapper à toute occurrence du délimiteur dans la chaîne d'entrée.  
  
## <a name="external-resources"></a>Ressources externes  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Procédures stockées](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) et [injection SQL](/sql/relational-databases/security/sql-injection)|Les articles décrivent comment créer des procédures stockées et comment fonctionne l’injection SQL.|  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Vue d'ensemble de la sécurité SQL Server](overview-of-sql-server-security.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Écriture d’une instruction SQL dynamique sécurisée dans SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Signature de procédures stockées dans SQL Server](signing-stored-procedures-in-sql-server.md)
- [Personnalisation des autorisations avec l’emprunt d’identité dans SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)
- [Modification des données avec les procédures stockées](../modifying-data-with-stored-procedures.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
