---
title: Intégration CLR SQL Server
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: d9fe0f03c88584607c6bc38fcbcff3f9424fd40c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183024"
---
# <a name="sql-server-common-language-runtime-integration"></a>Intégration CLR SQL Server

SQL Server 2005 a introduit l'intégration du composant Common Language Runtime (CLR) de .NET Framework pour Microsoft Windows. Cela signifie que vous pouvez écrire des procédures stockées, des déclencheurs, des types définis par l'utilisateur, des fonctions définies par l'utilisateur, des agrégats définis par l'utilisateur et des fonctions de flux évaluées par une table, en utilisant tout langage .NET Framework, notamment Microsoft Visual Basic .NET et Microsoft Visual C#. L'espace de noms <xref:Microsoft.SqlServer.Server> contient un ensemble de nouvelles API permettant au code managé d'interagir avec l'environnement Microsoft SQL Server.  
  
 Cette section décrit les fonctions et les comportements spécifiques à l'intégration de CLR dans SQL Server et aux extensions spécifiques au mode in-process SQL Server pour ADO.NET.  
  
 Cette section a uniquement pour but de fournir les informations indispensables pour commencer à programmer avec l'intégration de CLR dans SQL Server et n'est nullement exhaustive. Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.  
  
 **Documentation SQL Server**  
  
1. [Concepts de programmation pour l'intégration du CLR](/sql/relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts)  
  
## <a name="in-this-section"></a>Dans cette section  

 [Introduction à l'intégration CLR SQL Server](introduction-to-sql-server-clr-integration.md)  
 Fournit une présentation de l'intégration de CLR dans SQL Server. Fournit des liens vers d'autres rubriques.  
  
 [Fonctions CLR définies par l’utilisateur](clr-user-defined-functions.md)  
 Explique comment implémenter et utiliser les différents types de fonctions CLR : fonctions table, scalaires et d'agrégation définies par l'utilisateur.  
  
 [Types CLR définis par l’utilisateur](clr-user-defined-types.md)  
 Explique comment implémenter et utiliser les types CLR définis par l'utilisateur. Fournit des liens vers d'autres rubriques.  
  
 [Procédures stockées du CLR](clr-stored-procedures.md)  
 Explique comment implémenter et utiliser les procédures stockées CLR. Fournit des liens vers d'autres rubriques.  
  
 [Déclencheurs CLR](clr-triggers.md)  
 Explique comment implémenter et utiliser les déclencheurs CLR. Fournit des liens vers d'autres rubriques.  
  
 [Connexion contextuelle](the-context-connection.md)  
 Décrit la connexion de contexte.  
  
 [Comportement SQL Server spécifique au processus d'ADO.NET](sql-server-in-process-specific-behavior-of-adonet.md)  
 Décrit les extensions spécifiques au mode in-process SQL Server pour ADO.NET et la connexion de contexte. Fournit des liens vers d'autres rubriques.  
  
## <a name="see-also"></a>Voir aussi

- [SQL Server et ADO.NET](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
