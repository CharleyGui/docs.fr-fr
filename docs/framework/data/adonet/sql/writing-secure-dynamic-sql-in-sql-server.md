---
title: Écriture de Dynamic SQL sécurisé dans SQL Server
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: c02455ba8798df1de1d52f6b4db3426d41b95daf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791423"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>Écriture de Dynamic SQL sécurisé dans SQL Server
L'injection SQL est le processus qui permet à un utilisateur malveillant d'entrer des instructions Transact-SQL au lieu d'une entrée valide. Si l’entrée est transmise directement au serveur sans validation et si l’application exécute accidentellement le code injecté, l’attaque risque d’endommager ou de détruire des données.  
  
 Il est nécessaire de vérifier les vulnérabilités en matière d’injection de toute procédure qui construit des instructions SQL car SQL Server exécutera toutes les requêtes syntaxiquement valides qu’il reçoit. Même les données paramétrées peuvent être manipulées par un pirate expérimenté et déterminé. Si vous utilisez du code SQL dynamique, veillez à paramétrer vos commandes et n'incluez jamais de valeurs de paramètre directement dans la chaîne de requête.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Anatomie d'une attaque par injection de code SQL  
 Le processus d'injection consiste à terminer prématurément une chaîne de texte et à ajouter une nouvelle commande. Dans la mesure où des chaînes supplémentaires peuvent être ajoutées à la commande insérée avant son exécution, le pirate termine la chaîne injectée avec une marque de commentaire "--". Le texte qui suit est ignoré au moment de l'exécution. Plusieurs commandes peuvent être insérées en utilisant le séparateur point-virgule (;).  
  
 Tant que le code SQL injecté en syntaxiquement correct, la falsification ne peut pas être détectée par programme. Vous devez par conséquent valider toutes les entrées d’utilisateur et revoir avec soin le code qui exécute des commandes SQL construites sur le serveur que vous utilisez. Ne concaténez jamais des entrées d'utilisateur qui ne sont pas validées. La concaténation de chaînes est le principal point d'entrée pour l'injection de script.  
  
 Voici quelques conseils utiles :  
  
- Ne générez jamais des instructions Transact-SQL directement à partir d'entrées d'utilisateur. Utilisez des procédures stockées pour valider les entrées d'utilisateur.  
  
- Validez les entrées d'utilisateur en testant le type, la longueur, le format et la plage. Utilisez la fonction Transact-SQL QUOTENAME() pour échapper les noms système ou la fonction REPLACE() pour échapper tout caractère d'une chaîne.  
  
- Implémentez plusieurs couches de validation dans chaque niveau de votre application.  
  
- Testez la taille et le type de données des entrées et appliquez des limites appropriées. Cela permet d'éviter les dépassements délibérés de mémoire tampon.  
  
- Testez le contenu des variables de chaîne et acceptez uniquement les valeurs attendues. Rejetez les entrées qui contiennent des données binaires, des séquences d'échappement et des caractères de commentaire.  
  
- Lorsque vous travaillez avec des documents XML, validez toutes les données par rapport à leur schéma tel qu'il est entré.  
  
- Dans les environnements multicouches, toutes les données doivent être validées avant admission dans la zone de confiance.  
  
- N’acceptez pas les chaînes suivantes dans les champs à partir desquels les noms de fichiers peuvent être construits : Aux, CLOCK $, COM1 à COM8, CON, CONFIG $, LPT1 à LPT8, NUL et PRN.  
  
- Utilisez des objets <xref:System.Data.SqlClient.SqlParameter>  avec des procédures stockées et des commandes pour fournir le contrôle de type et la validation de longueur.  
  
- Utilisez des expressions <xref:System.Text.RegularExpressions.Regex> pour filtrer les caractères non valides.  
  
## <a name="dynamic-sql-strategies"></a>Stratégies SQL dynamique  
 L'exécution d'instructions SQL créées de manière dynamique dans votre code de procédure rompt la chaîne de propriétés, ce qui conduit SQL Server à vérifier les autorisations de l'appelant par rapport aux objets auxquels le code SQL dynamique accède.  
  
 SQL Server dispose de méthodes pour accorder aux utilisateurs l'accès aux données à l'aide de procédures stockées et de fonctions définies par l'utilisateur qui exécutent du code SQL dynamique.  
  
- Utilisation de l’emprunt d’identité avec la clause Transact-SQL EXECUTE AS, comme décrit dans [Personnalisation des autorisations avec l’emprunt d’identité dans SQL Server](customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Signature de procédures stockées avec des certificats, comme décrit dans [Signature de procédures stockées dans SQL Server](signing-stored-procedures-in-sql-server.md).  
  
### <a name="execute-as"></a>EXECUTE AS  
 La clause EXECUTE AS remplace les autorisations de l'appelant par celles de l'utilisateur spécifié dans la clause EXECUTE AS. Les procédures stockées ou déclencheurs imbriqués s'exécutent dans le contexte de sécurité de l'utilisateur proxy. Les applications qui reposent sur la sécurité de niveau ligne ou qui nécessitent un audit risquent alors de s'arrêter. Certaines fonctions qui retournent l'identité de l'utilisateur retournent l'utilisateur spécifié dans la clause EXECUTE AS, et non l'appelant d'origine. Le contexte d'exécution de l'appelant d'origine est rétabli uniquement après exécution de la procédure ou lorsqu'une instruction REVERT est émise.  
  
### <a name="certificate-signing"></a>Signature du certificat  
 Lors de l'exécution d'une procédure stockée qui a été signée avec un certificat, les autorisations accordées à l'utilisateur de ce certificat sont fusionnées avec celles de l'appelant. Le contexte d'exécution reste le même ; l'utilisateur du certificat n'emprunte pas l'identité de l'appelant. Plusieurs étapes sont nécessaires pour implémenter la signature des procédures stockées. La procédure doit être de nouveau signée après chaque modification.  
  
### <a name="cross-database-access"></a>Accès aux bases de données croisées  
 Le chaînage des propriétés des bases de données croisées ne fonctionne pas en cas d'exécution d'instructions SQL créées de manière dynamique. Il est possible de contourner cette restriction dans SQL Server en créant une procédure stockée qui accède aux données dans une autre base de données et en signant la procédure avec un certificat qui existe dans les deux bases de données. De cette manière, les utilisateurs ont accès aux ressources de base de données utilisées par la procédure sans que l'accès ou les autorisations de base de données leur soient octroyés.  
  
## <a name="external-resources"></a>Ressources externes  
 Pour plus d'informations, voir les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Procédures stockées](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) et [Injection SQL](/sql/relational-databases/security/sql-injection) dans la documentation en ligne de SQL Server|Ces rubriques expliquent comment créer des procédures stockées et comment fonctionne l'injection SQL.|  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Vue d’ensemble de la sécurité SQL Server](overview-of-sql-server-security.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Gestion des autorisations avec les procédures stockées dans SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Signature de procédures stockées dans SQL Server](signing-stored-procedures-in-sql-server.md)
- [Personnalisation des autorisations avec l’emprunt d’identité dans SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
