---
title: Sécurisation des applications
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: c1bdf4329665e4d29a47c26fb7dba8eb41c1cc3a
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980026"
---
# <a name="securing-adonet-applications"></a>Sécurisation des applications ADO.NET
L'écriture d'une application ADO.NET sécurisée ne se limite pas à éviter les pièges de codage courants, tels que la non validation des entrées d'utilisateur. Une application qui accède à des données présente de nombreux points de défaillance possibles qu’un agresseur peut exploiter pour extraire, manipuler ou détruire des données sensibles. Il est donc important de comprendre tous les aspects de la sécurité, depuis le processus de modélisation de menace durant la phase de conception de votre application, jusqu'à son déploiement éventuel et sa maintenance en cours.  
  
 Le .NET Framework fournit de nombreux services, classes et outils utiles permettant de sécuriser et d'administrer des applications de base de données. Le Common Language Runtime (CLR) fournit un environnement de type sécurisé pour l'exécution du code, avec une sécurité d'accès du code pour restreindre les autorisations de code managé. L'adoption des procédés de codage sécurisés pour l'accès aux données permet de réduire les dommages infligés par un intrus potentiel.  
  
 L'écriture d'un code sécurisé ne protège pas contre les défaillances de sécurité volontaires lors de l'utilisation de ressources non managées telles que des bases de données. La plupart des bases de données de serveur, telles que SQL Server, possèdent leurs propres systèmes de sécurité qui renforcent la sécurité si ceux-ci sont correctement implémentés. Cependant, même une source de données équipée d'un système de sécurité robuste peut faire l'objet d'une attaque si elle n'est pas configurée de manière appropriée.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble de la sécurité](security-overview.md)  
 Fournit des recommandations pour la conception d'applications ADO.NET sécurisées.  
  
 [Sécuriser l’accès aux données](secure-data-access.md)  
 Décrit comment utiliser des données à partir d'une source de données sécurisée.  
  
 [Applications clientes sécurisées](secure-client-applications.md)  
 Décrit des considérations sur la sécurité pour les applications clientes.  
  
 [Sécurité d’accès du code et ADO.NET](code-access-security.md)  
 Décrit comment utiliser la sécurité d'accès du code (CAS) pour protéger le code ADO.NET. Explique également comment travailler avec une confiance partielle.  
  
 [Confidentialité et sécurité des données](privacy-and-data-security.md)  
 Décrit les options de chiffrement pour les applications ADO.NET.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Sécurité SQL Server](./sql/sql-server-security.md)  
 Décrit les fonctionnalités de sécurité SQL Server du point de vue d’un développeur.  
  
 [Considérations relatives à la sécurité](./ef/security-considerations.md)  
 Décrit la sécurité des applications reposant sur Entity Framework.  
  
 [Security](../../../standard/security/index.md)  
 Contient des liens vers des rubriques qui décrivent tous les aspects de la sécurité dans .NET.  
  
 [Outils de sécurité](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))  
 Outils .NET Framework pour la sécurisation et l'administration de la stratégie de sécurité.  
  
 [Ressources de création des applications sécurisées](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))  
 Fournit des liens vers des rubriques pour la création d'applications sécurisées.  
  
 [Bibliographie relative à la sécurité](/visualstudio/ide/securing-applications)  
 Fournit des liens vers des ressources externes disponibles en ligne et sous forme de documentation.  
  
## <a name="see-also"></a>Voir aussi

- [ADO.NET](index.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
