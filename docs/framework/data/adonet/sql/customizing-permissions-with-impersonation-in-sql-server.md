---
title: Personnalisation des autorisations avec l'emprunt d'identité dans SQL Server
ms.date: 03/30/2017
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
ms.openlocfilehash: 84c5585912ba259fdcefaae186138c4466b16206
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180853"
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a>Personnalisation des autorisations avec l'emprunt d'identité dans SQL Server

De nombreuses applications utilisent des procédures stockées pour accéder aux données, en se basant sur le chaînage des propriétés de manière à limiter l'accès aux tables de base. Vous pouvez accorder des autorisations EXECUTE sur les procédures stockées, en révoquant ou refusant des autorisations sur les tables de base. SQL Server ne vérifie pas les autorisations de l'appelant si la procédure stockée et les tables ont le même propriétaire. Toutefois, le chaînage des propriétés ne fonctionne pas si les objets ont des propriétaires différents ou dans le cas d'instructions SQL dynamiques.  
  
 Vous pouvez utiliser la clause EXECUTE AS dans une procédure stockée lorsque l'appelant ne possède pas d'autorisations sur les objets de base de données référencés. Avec la clause EXECUTE AS, le contexte d'exécution est basculé vers l'utilisateur proxy. Tout le code, de même que les appels de procédures stockées ou de déclencheurs, s'exécute dans le contexte de sécurité de l'utilisateur proxy. Le contexte d’exécution est rétabli à l’appelant d’origine uniquement après l’exécution de la procédure ou lors de l’émission d’une instruction REVERT.  
  
## <a name="context-switching-with-the-execute-as-statement"></a>Changement de contexte avec l'instruction EXECUTE AS  

 L'instruction  Transact-SQL EXECUTE AS vous permet de basculer le contexte d'exécution d'une instruction en empruntant l'identité d'un autre utilisateur de connexion ou de base de données. Cette technique est utile pour tester des requêtes et des procédures en tant qu'un autre utilisateur.  
  
```sql  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 Vous devez posséder des autorisations IMPERSONATE sur la connexion ou l'utilisateur dont vous empruntez l'identité. Cette autorisation est implicite pour `sysadmin` dans toutes les bases de données et pour les membres du rôle `db_owner` dans les bases de données qu'ils possèdent.  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a>Octroi d'autorisations avec la clause EXECUTE AS  

 Vous pouvez utiliser la clause EXECUTE AS dans l'en-tête de définition d'une procédure stockée, d'un déclencheur ou d'une fonction définie par l'utilisateur (sauf pour les fonctions table inline). La procédure est alors exécutée dans le contexte du nom d'utilisateur ou du mot clé spécifié dans la clause EXECUTE AS. Vous pouvez créer dans la base de données un utilisateur proxy qui n'est pas mappé à une connexion, en lui accordant uniquement les autorisations nécessaires sur les objets auxquels la procédure accède. Seul l'utilisateur proxy spécifié dans la clause EXECUTE AS doit posséder des autorisations sur tous les objets auxquels le module accède.  
  
> [!NOTE]
> Pour certaines actions, comme TRUNCATE TABLE, aucune autorisation ne peut être accordée. En incorporant l'instruction dans une procédure et en spécifiant un utilisateur proxy possédant des autorisations ALTER TABLE, vous pouvez étendre les autorisations de troncation de la table aux appelants possédant uniquement des autorisations EXECUTE sur la procédure.  
  
 Le contexte spécifié dans la clause EXECUTE AS est valide pour la durée de la procédure, y compris les procédures et déclencheurs imbriqués. Le contexte de l'appelant est rétabli une fois l'exécution terminée ou lorsque l'instruction REVERT est émise.  
  
 Pour utiliser la clause EXECUTE AS dans une procédure, les trois étapes suivantes sont nécessaires :  
  
1. Dans la base de données, créez un utilisateur proxy qui n'est pas mappé à une connexion. Cette étape n'est pas obligatoire, mais elle s'avère utile lors de la gestion des autorisations.  
  
```sql
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1. Accordez les autorisations nécessaires à l'utilisateur proxy.  
  
2. Ajoutez la clause EXECUTE AS à la procédure stockée ou à la fonction définie par l'utilisateur.  
  
```sql
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
> Les applications qui nécessitent un audit peuvent s'arrêter car le contexte de sécurité d'origine de l'appelant n'est pas conservé. Les fonctions intégrées qui retournent l'identité de l'utilisateur actif, comme SESSION_USER, USER ou USER_NAME, retournent l'utilisateur associé à la clause EXECUTE AS, et non l'appelant d'origine.  
  
### <a name="using-execute-as-with-revert"></a>Utilisation de la clause EXECUTE AS avec l'instruction REVERT  

 Vous pouvez utiliser l'instruction Transact-SQL REVERT pour rétablir le contexte d'exécution d'origine.  
  
 La clause facultative, WITH NO Revert COOKIE = @variableName , vous permet de rebasculer le contexte d’exécution vers l’appelant si la @variableName variable contient la valeur correcte. Vous pouvez ainsi rétablir le contexte d'exécution de l'appelant dans les environnements utilisant le regroupement de connexions. Étant donné que la valeur de @variableName est connue uniquement de l’appelant de l’instruction EXECUTE AS, l’appelant peut garantir que le contexte d’exécution ne peut pas être modifié par l’utilisateur final qui appelle l’application. Une fois fermée, la connexion retourne dans le regroupement de connexions. Pour plus d’informations sur le regroupement de connexions dans ADO.NET, consultez [SQL Server le regroupement de connexions (ADO.net)](../sql-server-connection-pooling.md).  
  
### <a name="specifying-the-execution-context"></a>Spécification du contexte d'exécution  

 Parallèlement à la spécification d'un utilisateur, vous pouvez utiliser la clause EXECUTE AS avec chacun des mots clés suivants.  
  
- CALLER. L'exécution en tant que CALLER est la valeur par défaut. Si aucune autre option n'est spécifiée, la procédure s'exécute dans le contexte de sécurité de l'appelant.  
  
- OWNER. L'exécution en tant que OWNER exécute la procédure dans le contexte de sécurité du propriétaire de la procédure. Si la procédure est créée dans un schéma détenu par `dbo` ou le propriétaire de la base de données, la procédure s'exécutera avec des autorisations illimitées.  
  
- SELF. L'exécution en tant que SELF exécute la procédure dans le contexte de sécurité du créateur de la procédure stockée. Cela revient à exécuter la procédure en tant qu'un utilisateur spécifié, ce dernier étant la personne qui crée ou modifie la procédure.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Vue d'ensemble de la sécurité SQL Server](overview-of-sql-server-security.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Gestion des autorisations avec les procédures stockées dans SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Écriture d’une instruction SQL dynamique sécurisée dans SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Signature de procédures stockées dans SQL Server](signing-stored-procedures-in-sql-server.md)
- [Modification des données avec les procédures stockées](../modifying-data-with-stored-procedures.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
