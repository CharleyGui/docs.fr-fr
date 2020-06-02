---
title: Autorisation et permissions dans SQL Server
description: Apprenez à accorder explicitement des autorisations pour rendre les objets de base de données que vous créez accessibles aux utilisateurs dans SQL Server avec ADO.NET.
ms.date: 03/30/2017
ms.assetid: d340405c-91f4-4837-a3cc-a238ee89888a
ms.openlocfilehash: eb01e29b36da5e1793b9176301a968a42115d19c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286531"
---
# <a name="authorization-and-permissions-in-sql-server"></a>Autorisation et permissions dans SQL Server
Lorsque vous créez des objets de base de données, vous devez accorder explicitement des autorisations de manière à les rendre accessibles aux utilisateurs. Chaque objet sécurisable possède des autorisations qui peuvent être accordées à une principal de sécurité à l'aide d'instructions d'autorisation.  
  
## <a name="the-principle-of-least-privilege"></a>Principe des privilèges minimum  
 Le développement d'une application selon l'approche du compte d'utilisateur disposant de privilèges minimum (LUA, Least-privileged User Account) est un élément important de la stratégie de défense en profondeur visant à contrer les menaces de sécurité. L'approche LUA garantit que les utilisateurs suivent le principe des privilèges minimum et ouvrent toujours leur session avec des comptes d'utilisateurs limités. Les tâches administratives sont classées par rôle serveur fixe. L'utilisation du rôle serveur fixe `sysadmin` est extrêmement limitée.  
  
 Suivez toujours le principe des privilèges minimum lorsque vous accordez des autorisations aux utilisateurs de base de données. Accordez les autorisations minimales nécessaires à un utilisateur ou à un rôle pour accomplir une tâche donnée.  
  
> [!IMPORTANT]
> Le développement et le test d'une application selon l'approche LUA compliquent quelque peu le processus. Il est plus simple de créer des objets et d'écrire du code tout en étant connecté en tant qu'administrateur système ou propriétaire de base de données qu'en utilisant un compte LUA. Cependant, le fait de développer des applications en utilisant un compte disposant de privilèges élevés peut masquer l'impact de fonctionnalités réduites lorsque des utilisateurs disposant de privilèges minimum essaient d'exécuter une application qui requiert des autorisations élevées pour fonctionner correctement. Par ailleurs, le fait d'accorder des autorisations excessives aux utilisateurs afin qu'ils puissent réacquérir une fonctionnalité perdue peut rendre votre application vulnérable aux attaques. La conception, le développement et le test de votre application alors que vous êtes connecté avec un compte LUA appliquent une approche disciplinée qui évite toute mauvaise surprise et empêche de céder à la facilité en accordant des privilèges élevés. Vous pouvez utiliser une connexion SQL Server pour le test même si votre application doit être déployée à l'aide de l'authentification Windows.  
  
## <a name="role-based-permissions"></a>Autorisations basées sur les rôles  
 L'octroi d'autorisations aux rôles plutôt qu'aux utilisateurs simplifie l'administration de la sécurité. Les jeux d'autorisations qui sont assignés aux rôles sont hérités par tous les membres du rôle. Il est plus facile d'ajouter des utilisateurs à un rôle ou d'en supprimer que de recréer des jeux d'autorisations distincts individuellement pour chaque utilisateur. Les rôles peuvent être imbriqués ; toutefois, des niveaux d'imbrication trop nombreux peuvent dégrader les performances. Vous pouvez également ajouter des utilisateurs aux rôles de base de données fixes pour simplifier l'assignation d'autorisations.  
  
 Vous pouvez accorder des autorisations au niveau du schéma. Les utilisateurs héritent automatiquement des autorisations sur tous les nouveaux objets créés dans le schéma. Il n'est alors pas nécessaire d'accorder des autorisations dès que de nouveaux objets sont créés.  
  
## <a name="permissions-through-procedural-code"></a>Autorisations par le biais du code de procédure  
 L'encapsulation de l'accès aux données par le biais de modules, comme des procédures stockées et des fonctions définies par l'utilisateur, offre une couche supplémentaire de protection autour de votre application. Vous pouvez empêcher un utilisateur d'interagir directement avec les objets de base de données en accordant des autorisations uniquement aux procédures stockées et aux fonctions tout en refusant les autorisations sur les objets sous-jacents comme les tables. Pour cela, SQL Server effectue un chaînage de propriétés.  
  
## <a name="permission-statements"></a>Instructions d'autorisation  
 Les trois instructions d'autorisation Transact-SQL sont décrites dans le tableau suivant.  
  
|Instruction d'autorisation|Description|  
|--------------------------|-----------------|  
|GRANT|Accorde une autorisation.|  
|REVOKE|Révoque une autorisation. Il s'agit de l'état par défaut d'un nouvel objet. Une autorisation révoquée pour un utilisateur ou un rôle peut être héritée d'autres groupes ou rôles auxquels la principal de sécurité est assignée.|  
|DENY|DENY révoque une autorisation afin qu'elle ne puisse plus être héritée. DENY a priorité sur toutes les autorisations, mais ne s'applique pas aux propriétaires d'objets ni aux membres de `sysadmin`. Si vous refusez des autorisations sur un objet au rôle `public`, elles sont refusées à tous les utilisateurs et rôles, à l'exception des propriétaires d'objets et des membres `sysadmin`.|  
  
- L'instruction GRANT peut assigner des autorisations à un groupe ou un rôle qui peuvent être héritées par les utilisateurs de base de données. Toutefois, l'instruction DENY a priorité sur toutes les autres instructions d'autorisation. Par conséquent, un utilisateur à qui une autorisation a été refusée ne peut pas en hériter d'un autre rôle.  
  
> [!NOTE]
> Les membres du rôle serveur fixe `sysadmin` et des propriétaires d'objets ne peuvent pas se voir refuser des autorisations.  
  
## <a name="ownership-chains"></a>Chaînes de propriétés  
 SQL Server garantit que seules les entités de sécurité qui en ont reçu l'autorisation peuvent accéder aux objets. Lorsque plusieurs objets de base de données accèdent les uns aux autres, la séquence est qualifiée de chaîne. Lorsque SQL Server traverse les liens de la chaîne, il évalue les autorisations différemment que s'il accédait séparément à chaque élément. Lors de l'accès à un objet par le biais d'une chaîne, SQL Server commence par comparer le propriétaire de l'objet au propriétaire de l'objet appelant (le lien précédent de la chaîne). Si les deux objets ont le même propriétaire, les autorisations de l'objet référencé ne sont pas vérifiées. Si les propriétaires sont différents, la chaîne de propriétés est rompue et SQL Server doit vérifier le contexte de sécurité de l'appelant.  
  
## <a name="procedural-code-and-ownership-chaining"></a>Code de procédure et chaînage de propriétés  
 Supposons qu'un utilisateur bénéficie des autorisations d'exécution sur une procédure stockée qui sélectionne des données dans une table. Si la procédure stockée et la table ont le même propriétaire, il n'est pas nécessaire que l'utilisateur bénéficie d'autorisations quelles qu'elles soient ; il peut même s'en voir refuser. Cependant, si la procédure stockée et la table ont des propriétaires différents, SQL Server doit vérifier les autorisations de l'utilisateur sur la table avant d'autoriser l'accès aux données.  
  
> [!NOTE]
> Le chaînage des propriétés ne s'applique pas aux instructions SQL dynamiques. Pour appeler une procédure qui exécute une instruction SQL, l'appelant doit bénéficier d'autorisations sur les tables sous-jacentes, ce qui rend votre application vulnérable aux attaques par injection de code SQL. SQL Server fournit de nouveaux mécanismes, comme l'emprunt d'identité et la signature de modules à l'aide de certificats, qui ne requièrent pas l'octroi d'autorisations sur les tables sous-jacentes. Ils peuvent également être utilisés avec les procédures stockées CLR.  
  
## <a name="external-resources"></a>Ressources externes  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[autorisations](/sql/relational-databases/security/permissions-database-engine)|Contient des rubriques qui décrivent la hiérarchie des autorisations, les affichages catalogue et les autorisations des rôles serveur et de base de données fixes.|
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Authentification dans SQL Server](authentication-in-sql-server.md)
- [Serveur et rôles de base de données dans SQL Server](server-and-database-roles-in-sql-server.md)
- [Propriété et séparation des schémas utilisateur dans SQL Server](ownership-and-user-schema-separation-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
