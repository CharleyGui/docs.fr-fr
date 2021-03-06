---
title: Scénarios de sécurité des applications dans SQL Server
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: 2d0e65f61939312bf29111e87c49366cd9e389be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197649"
---
# <a name="application-security-scenarios-in-sql-server"></a>Scénarios de sécurité des applications dans SQL Server

Il n’existe pas de méthode correcte pour créer une application cliente SQL Server sécurisée. Chaque application est unique dans ses exigences, son environnement de déploiement et sa population d’utilisateurs. Une application qui est raisonnablement sécurisée lors du déploiement initial peut devenir moins sécurisée au fil du temps. Il est impossible de prédire avec précision quelles menaces peuvent émerger à l’avenir.  
  
 SQL Server, en tant que produit, a évolué sur de nombreuses versions pour incorporer les fonctionnalités de sécurité les plus récentes, permettant aux développeurs de créer des applications de base de données sécurisées. Toutefois, la sécurité n’est pas innée et finale ; elle nécessite une surveillance et une mise à jour continues.  
  
## <a name="common-threats"></a>Menaces courantes  

 Les développeurs doivent comprendre les menaces de sécurité, les outils fournis pour les éliminer et comment éviter les failles de sécurité. La sécurité peut être considérée comme une chaîne, où la rupture d’un lien compromet la force de l’ensemble. La liste suivante présente certaines menaces de sécurité courantes qui sont abordées plus en détail dans les rubriques de cette section.  
  
### <a name="sql-injection"></a>l’injection de code SQL ;  

 L’injection SQL est le processus par lequel un utilisateur malveillant entre des instructions Transact-SQL au lieu d’une entrée valide. Si l’entrée est transmise directement au serveur sans validation et si l’application exécute par inadvertance le code injecté, l’attaque risque d’endommager ou de détruire des données. Vous pouvez déjouer les attaques par injection SQL Server en utilisant des procédures stockées et des commandes paramétrées, en évitant les instructions SQL dynamiques et en limitant les autorisations de l’ensemble des utilisateurs.  
  
### <a name="elevation-of-privilege"></a>Élévation de privilège  

 Les attaques par élévation de privilèges se produisent lorsqu’un utilisateur est en mesure de prendre les privilèges d’un compte approuvé, comme un propriétaire ou un administrateur. Travaillez toujours sous les comptes d’utilisateur dotés des privilèges minimum et attribuez uniquement les autorisations nécessaires. Évitez d’utiliser des comptes d’administration ou de propriétaire pour exécuter du code. Cela limite l’étendue des dommages qui peuvent se produire si une attaque réussit. Lorsque vous effectuez des tâches qui nécessitent des autorisations supplémentaires, utilisez la signature de procédure ou l’emprunt d’identité uniquement pour la durée de la tâche. Vous pouvez signer les procédures stockées à l’aide de certificats ou utiliser l’emprunt d’identité pour affecter des autorisations de manière temporaire.  
  
### <a name="probing-and-intelligent-observation"></a>Détection des attaques et surveillance intelligente  

 Une attaque par sondage peut utiliser des messages d’erreur générés par une application pour rechercher des failles de sécurité. Implémentez la gestion des erreurs dans tout le code procédural pour empêcher les informations d’erreur SQL Server d’être renvoyées à l’utilisateur final.  
  
### <a name="authentication"></a>Authentification  

 Une attaque par injection de chaîne de connexion peut se produire lors de l’utilisation de connexions SQL Server si une chaîne de connexion basée sur l’entrée de l’utilisateur est générée au moment de l’exécution. Si la chaîne de connexion n’est pas vérifiée par rapport à des paires de mots clés valides, une personne malveillante peut insérer des caractères supplémentaires, et accéder potentiellement à des données sensibles ou à d’autres ressources sur le serveur. Utilisez l’authentification Windows dans la mesure du possible. Si vous devez utiliser des connexions SQL Server, utilisez le <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pour créer et valider les chaînes de connexion au moment de l’exécution.  
  
### <a name="passwords"></a>Mots de passe  

 De nombreuses attaques réussissent parce qu’un intrus a pu obtenir ou deviner un mot de passe pour un utilisateur privilégié. Les mots de passe constituant votre première ligne de défense contre les intrus, le choix de mots de passe forts est essentiel à la sécurité de votre système. Créez et appliquez des stratégies de mot de passe pour l'authentification en mode mixte.  
  
 Affectez toujours un mot de passe fort au compte `sa`, même si vous utilisez l’authentification Windows.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Gestion des autorisations avec les procédures stockées dans SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)  
 Décrit comment utiliser des procédures stockées pour gérer les autorisations et contrôler l'accès aux données. L'utilisation des procédures stockées est un moyen efficace pour pallier de nombreuses menaces concernant la sécurité.  
  
 [Écriture d’une instruction SQL dynamique sécurisée dans SQL Server](writing-secure-dynamic-sql-in-sql-server.md)  
 Décrit les techniques d’écriture de SQL dynamique sécurisé à l’aide de procédures stockées.  
  
 [Signature de procédures stockées dans SQL Server](signing-stored-procedures-in-sql-server.md)  
 Décrit comment signer une procédure stockée avec un certificat pour permettre aux utilisateurs de disposer des données auxquelles ils n'ont pas un accès direct. Cela permet aux procédures stockées d'effectuer des opérations que l'appelant n'est pas autorisé à effectuer directement.  
  
 [Personnalisation des autorisations avec l'emprunt d'identité dans SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)  
 Décrit la manière d'utiliser la clause EXECUTE AS pour emprunter l'identité d'un autre utilisateur. L'emprunt d'identité transfère le contexte de l'exécution de l'appelant vers l'utilisateur spécifié.  
  
 [Attribution d'autorisations de niveau ligne dans SQL Server](granting-row-level-permissions-in-sql-server.md)  
 Décrit comment implémenter des autorisations au niveau de la ligne pour limiter l'accès aux données.  
  
 [Création de rôles d'applications dans SQL Server](creating-application-roles-in-sql-server.md)  
 Décrit les fonctions et les fonctionnalités de rôles d'application.  
  
 [Activation de l'accès entre bases de données dans SQL Server](enabling-cross-database-access-in-sql-server.md)  
 Décrit comment activer l'accès aux bases de données croisées sans risque pour la sécurité.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité SQL Server](sql-server-security.md)
- [Vue d'ensemble de la sécurité SQL Server](overview-of-sql-server-security.md)
- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
