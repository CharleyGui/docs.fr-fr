---
title: Sécurité SQL Server
ms.date: 03/30/2017
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.openlocfilehash: c5fd9cc82a3b1e4ffa217d65c542376fe067db06
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791620"
---
# <a name="sql-server-security"></a>Sécurité SQL Server
SQL Server possède de nombreuses fonctionnalités qui prennent en charge la création d'applications de base de données sécurisées.  
  
 Les principaux éléments à prendre en compte au niveau de la sécurité, tels que le vol ou l'altération de données, concernent toutes les versions de SQL Server. L'intégrité des données doit également être prise en considération comme un problème de sécurité. Si les données ne sont pas protégées, elles peuvent devenir inutilisables si une manipulation ad hoc est autorisée et que les données sont modifiées, par inadvertance ou malveillance, avec des valeurs incorrectes ou entièrement supprimées. Par ailleurs, des exigences juridiques doivent souvent être observées, telles que le stockage correct des informations confidentielles. Le stockage de certains types de données personnelles est totalement interdit, selon les lois en vigueur dans une juridiction donnée.  
  
 Chaque version de SQL Server présente des fonctionnalités de sécurité différentes, comme chaque version de Windows, les versions les plus récentes apportant des améliorations par rapport aux plus anciennes. Il est important de comprendre que les fonctionnalités de sécurité à elles seules ne peuvent pas garantir une application de base de données sécurisée. Chaque application de base de données est unique au niveau de sa configuration, de son environnement d’exécution, de son modèle de déploiement, de son emplacement physique et de ses types d’utilisateurs. Certaines applications de portée locale peuvent se contenter d'une sécurité minimale alors que d'autres applications locales ou déployées sur Internet peuvent nécessiter des mesures de sécurité strictes, ainsi qu'une surveillance et une évaluation permanentes.  
  
 Les exigences de sécurité d'une application de base de données SQL Server doivent être examinées au moment de la conception, et non pas à une étape ultérieure. L'évaluation des menaces aux premiers stades du cycle de développement vous donne la possibilité d'atténuer les dommages susceptibles de se produire lorsqu'une vulnérabilité est détectée.  
  
 Même si la conception initiale d'une application est fiable, de nouvelles menaces peuvent émerger à mesure que le système évolue. En créant plusieurs lignes de défense autour de vos bases de données, vous pouvez minimiser les dommages induits par une violation de la sécurité. Votre première ligne de défense consiste à réduire la surface d'attaque en n'accordant jamais plus d'autorisations que nécessaire.  
  
 Les rubriques de cette section décrivent brièvement les fonctionnalités de sécurité de SQL Server qui concernent les développeurs et fournissent des liens vers des rubriques pertinentes dans la documentation en ligne de SQL Server et d'autres ressources qui fournissent des explications plus détaillées.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble de la sécurité SQL Server](overview-of-sql-server-security.md)  
 Décrit l'architecture et les fonctionnalités de sécurité de SQL Server.  
  
 [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)  
 Contient des rubriques présentant différents scénarios de sécurité pour les applications ADO.NET et SQL Server.  
  
 [Sécurité SQL Server Express](sql-server-express-security.md)  
 Décrit les considérations de sécurité pour SQL Server Express.  
  
## <a name="related-sections"></a>Rubriques connexes  
[Security Center pour SQL Server Moteur de base de données et Azure SQL Database](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
Décrit les considérations de sécurité pour SQL Server et Azure SQL Database.

[Considérations sur la sécurité pour une installation SQL Server](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
Décrit les problèmes de sécurité à prendre en compte avant d’installer SQL Server.

## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [SQL Server et ADO.NET](index.md)
