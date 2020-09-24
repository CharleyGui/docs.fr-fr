---
title: Écriture de Dynamic SQL sécurisé dans SQL Server
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: c598427a17ceb289f75fab481a55016f0efe5624
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147448"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>Écriture de Dynamic SQL sécurisé dans SQL Server

L’injection SQL est le processus par lequel un utilisateur malveillant entre des instructions Transact-SQL au lieu d’une entrée valide. Si l’entrée est transmise directement au serveur sans validation et si l’application exécute par inadvertance le code injecté, l’attaque risque d’endommager ou de détruire des données.  
  
 Les procédures qui permettent de créer des instructions SQL doivent être vérifiées et analysées à la recherche d’éventuelles failles autorisant cette injection, car SQL Server exécute toutes les requêtes syntaxiquement correctes qu’il reçoit. Même les données paramétrables peuvent être manipulées par un pirate compétent et déterminé. Si vous utilisez le SQL dynamique, veillez à paramétrer vos commandes et n’incluez jamais de valeurs de paramètre directement dans la chaîne de requête.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Anatomie d'une attaque par injection de code SQL  

 Le processus d'injection consiste à terminer prématurément une chaîne de texte et à ajouter une nouvelle commande. Étant donné que la commande insérée peut avoir d'autres chaînes ajoutées préalablement à son exécution, l'attaquant termine la chaîne injectée par une marque de commentaire « -- ». Le texte qui vient à la suite est ignoré au moment de l'exécution. Plusieurs commandes peuvent être insérées à l’aide d’un point-virgule (;) séparateur.  
  
 Tant que le code SQL injecté est syntaxiquement correct, il n'est pas possible de détecter par programme cette modification. Par conséquent, vous devez valider toutes les entrées utilisateur et vérifier très attentivement le code qui exécute les commandes SQL construites dans le serveur utilisé. Ne concaténez jamais une entrée utilisateur qui n'est pas validée. La concaténation de chaîne est le point d'entrée principal pour l'injection de scripts.  
  
 Voici quelques conseils utiles :  
  
- Ne créez jamais d’instructions Transact-SQL directement à partir de l’entrée utilisateur ; utilisez des procédures stockées pour valider les entrées utilisateur.  
  
- Validez les entrées utilisateur en testant leur type, leur longueur, leur format et leur plage. Utilisez la fonction Transact-SQL QUOTENAME() pour échapper les noms système ou la fonction REPLACE() pour échapper n’importe quel caractère d’une chaîne.  
  
- Implémentez plusieurs couches de validation dans chaque niveau de votre application.  
  
- Testez la taille et le type de données de l'entrée et appliquez les limites appropriées. Cela peut permettre d'éviter des dépassements de mémoire tampon délibérés.  
  
- Testez le contenu des variables de chaîne et acceptez uniquement les valeurs attendues. Rejetez les entrées contenant des données binaires, des séquences de caractères d'échappement et des caractères de commentaire.  
  
- Lorsque vous utilisez des documents XML, validez toutes les données par rapport à leurs schémas lorsqu'elles sont entrées.  
  
- Dans des environnements à plusieurs niveaux, toutes les données doivent être validées avant leur acceptation dans la zone de confiance.  
  
- N’acceptez pas les chaînes suivantes dans les champs à partir desquels les noms de fichiers peuvent être construits : AUX, CLOCK$, COM1 à COM8, CON, CONFIG$, LPT1 à LPT8, NUL et PRN.  
  
- Utilisez des objets <xref:System.Data.SqlClient.SqlParameter> avec des procédures stockées et des commandes pour fournir la vérification de type et la validation de la longueur.  
  
- Utilisez des expressions <xref:System.Text.RegularExpressions.Regex> dans le code client pour filtrer les caractères non valides.  
  
## <a name="dynamic-sql-strategies"></a>Stratégies SQL dynamique  

 L’exécution d’instructions SQL créées dynamiquement dans votre code procédural interrompt la chaîne de propriétés, ce qui amène SQL Server à vérifier les autorisations de l’appelant par rapport aux objets auxquels le SQL dynamique accède.  
  
 SQL Server propose des méthodes pour accorder aux utilisateurs l’accès aux données à l’aide de procédures stockées et de fonctions définies par l’utilisateur qui exécutent du code SQL dynamique.  
  
- Utilisation de l’emprunt d’identité avec la clause Transact-SQL EXECUTE AS, comme décrit dans [Personnalisation des autorisations avec l’emprunt d’identité dans SQL Server](customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Signature de procédures stockées avec des certificats, comme décrit dans [Signature de procédures stockées dans SQL Server](signing-stored-procedures-in-sql-server.md).  
  
### <a name="execute-as"></a>EXECUTE AS  

 La clause EXECUTE AS remplace les autorisations de l’appelant par celles de l’utilisateur spécifié dans la clause EXECUTE AS. Les procédures stockées ou déclencheurs imbriqués s’exécutent dans le contexte de sécurité de l’utilisateur proxy. Cela peut perturber les applications qui reposent sur la sécurité au niveau des lignes ou nécessitent un audit. Certaines fonctions qui retournent l’identité de l’utilisateur retournent l’utilisateur spécifié dans la clause EXECUTE AS, et non l’appelant d’origine. Le contexte d’exécution est rétabli à l’appelant d’origine uniquement après l’exécution de la procédure ou lors de l’émission d’une instruction REVERT.  
  
### <a name="certificate-signing"></a>Signature du certificat  

 Lorsqu’une procédure stockée qui a été signée avec un certificat s’exécute, les autorisations accordées à l’utilisateur du certificat sont fusionnées avec celles de l’appelant. Le contexte d’exécution reste le même ; l’utilisateur du certificat n’emprunte pas l’identité de l’appelant. La signature de procédures stockées nécessite l’implémentation de plusieurs étapes. Chaque fois que la procédure est modifiée, elle doit être de nouveau signée.  
  
### <a name="cross-database-access"></a>Accès aux bases de données croisées  

 Le chaînage des propriétés des bases de données croisées ne fonctionne pas dans les cas où des instructions SQL créées dynamiquement sont exécutées. Il est possible de contourner cette restriction dans SQL Server en créant une procédure stockée qui accède aux données dans une autre base de données et en signant la procédure avec un certificat qui existe dans les deux bases de données. Cela permet aux utilisateurs d’accéder aux ressources de base de données utilisées par la procédure sans leur accorder un accès ou des autorisations de base de données.  
  
## <a name="external-resources"></a>Ressources externes  

 Pour plus d'informations, consultez les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Procédures stockées](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) et [Injection SQL](/sql/relational-databases/security/sql-injection) dans la Documentation en ligne de SQL Server|Des rubriques décrivant comment créer des procédures stockées et comment fonctionne l’injection SQL.|  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Vue d'ensemble de la sécurité SQL Server](overview-of-sql-server-security.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Gestion des autorisations avec les procédures stockées dans SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Signature de procédures stockées dans SQL Server](signing-stored-procedures-in-sql-server.md)
- [Personnalisation des autorisations avec l'emprunt d'identité dans SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
