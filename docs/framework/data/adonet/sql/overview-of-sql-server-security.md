---
title: Vue d'ensemble de la sécurité SQL Server
description: En savoir plus sur l’architecture de sécurité SQL Server pour comprendre quelles fonctionnalités et fonctionnalités sont des menaces connues et pour anticiper les menaces futures.
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: ba396774e760a550246d0f0507984d3f7212204b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172656"
---
# <a name="overview-of-sql-server-security"></a>Vue d'ensemble de la sécurité SQL Server

Une stratégie de défense en profondeur avec chevauchement des couches de sécurité est le meilleur moyen de contrer les menaces de sécurité. SQL Server propose une architecture de sécurité conçue pour permettre aux administrateurs et aux développeurs de bases de données de créer des applications de base de données sécurisées et de contrer les menaces. Chaque version de SQL Server offre des améliorations par rapport aux versions précédentes avec l’introduction de nouvelles fonctions et fonctionnalités. Pour autant, il ne peut exister de plan de sécurité prêt à l'emploi. Chaque application a des spécifications de sécurité uniques. Les développeurs doivent comprendre quelle combinaison de fonctions et fonctionnalités est la plus adéquate pour contrer les menaces identifiées et pour anticiper les menaces qui risquent de voir le jour dans l’avenir.  
  
 Une instance SQL Server contient une collection hiérarchique d'entités, qui commence par le serveur. Chaque serveur contient plusieurs bases de données et chaque base de données contient une collection d'objets sécurisables. Chaque SQL Server élément sécurisable a des *autorisations* associées qui peuvent être accordées à un *principal*, qui est un individu, un groupe ou un processus autorisé à accéder à SQL Server. L’infrastructure de sécurité SQL Server gère l’accès aux entités sécurisables par le biais de *l’authentification* et de l' *autorisation*.  
  
- L'authentification est le processus de connexion à SQL Server dans lequel une principal de sécurité demande l'accès en soumettant des informations d'identification qui sont évaluées par le serveur. L'authentification établit l'identité de l'utilisateur ou du processus en cours d'authentification.  
  
- L’autorisation est le processus de détermination des ressources sécurisables auxquelles un principal peut accéder, ainsi que des opérations autorisées pour ces ressources.  
  
 Les rubriques de cette section présentent les concepts fondamentaux de la sécurité SQL Server et fournissent des liens vers la version appropriée de la documentation complète en ligne de SQL Server.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Authentification dans SQL Server](authentication-in-sql-server.md)  
 Décrit les connexions et l’authentification dans SQL Server et fournit des liens vers des ressources supplémentaires.  
  
 [Serveur et rôles de base de données dans SQL Server](server-and-database-roles-in-sql-server.md)  
 Décrit le rôle serveur fixe et le rôle de base de données fixe, les rôles de base de données personnalisés et les comptes intégrés, et fournit des liens vers des ressources supplémentaires.  
  
 [Propriété et séparation des schémas utilisateur dans SQL Server](ownership-and-user-schema-separation-in-sql-server.md)  
 Décrit la propriété d'objet et la séparation utilisateur-schéma, et fournit des liens vers des ressources supplémentaires.  
  
 [Autorisation et permissions dans SQL Server](authorization-and-permissions-in-sql-server.md)  
 Décrit l'octroi d'autorisations selon le principe des privilèges minimum et fournit des liens vers des ressources supplémentaires.  
  
 [Chiffrement des données dans SQL Server](data-encryption-in-sql-server.md)  
 Décrit les options de chiffrement de données dans SQL Server et fournit des liens vers des ressources supplémentaires.  
  
 [Sécurité de l'intégration du CLR dans SQL Server](clr-integration-security-in-sql-server.md)  
 Fournit des liens vers les ressources de sécurité d'intégration de CLR.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Sécurité SQL Server](sql-server-security.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
