---
title: Intégration CLR SQL Server
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 77b40c6a1576b87d9bb4a7eb4b1ee3df8828b892
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780859"
---
# <a name="sql-server-common-language-runtime-integration"></a>Intégration CLR SQL Server
SQL Server 2005 a introduit l'intégration du composant Common Language Runtime (CLR) de .NET Framework pour Microsoft Windows. Cela signifie que vous pouvez écrire des procédures stockées, des déclencheurs, des types définis par l'utilisateur, des fonctions définies par l'utilisateur, des agrégats définis par l'utilisateur et des fonctions de flux évaluées par une table, en utilisant tout langage .NET Framework, notamment Microsoft Visual Basic .NET et Microsoft Visual C#. L'espace de noms <xref:Microsoft.SqlServer.Server> contient un ensemble de nouvelles API permettant au code managé d'interagir avec l'environnement Microsoft SQL Server.  
  
 Cette section décrit les fonctions et les comportements spécifiques à l'intégration de CLR dans SQL Server et aux extensions spécifiques au mode in-process SQL Server pour ADO.NET.  
  
 Cette section a uniquement pour but de fournir les informations indispensables pour commencer à programmer avec l'intégration de CLR dans SQL Server et n'est nullement exhaustive. Pour obtenir des informations plus détaillées, voir la documentation en ligne de SQL Server pour la version de SQL Server que vous utilisez.  
  
 **Documentation en ligne de SQL Server**  
  
1. [Concepts de programmation de l’intégration du Common Language Runtime (CLR)](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a>Dans cette section  
 [Introduction à l’intégration CLR SQL Server](introduction-to-sql-server-clr-integration.md)  
 Fournit une présentation de l'intégration de CLR dans SQL Server. Fournit des liens vers d'autres rubriques.  
  
 [Fonctions CLR définies par l’utilisateur](clr-user-defined-functions.md)  
 Décrit comment implémenter et utiliser les différents types de fonctions CLR : fonctions table, fonctions scalaires et fonctions d'agrégation définies par l'utilisateur.  
  
 [Types CLR définis par l’utilisateur](clr-user-defined-types.md)  
 Décrit comment implémenter et utiliser des types CLR définis par l'utilisateur. Fournit des liens vers d'autres rubriques.  
  
 [Procédures stockées CLR](clr-stored-procedures.md)  
 Décrit comment implémenter et utiliser des procédures stockées CLR. Fournit des liens vers d'autres rubriques.  
  
 [Déclencheurs CLR](clr-triggers.md)  
 Décrit comment implémenter et utiliser des déclencheurs CLR. Fournit des liens vers d'autres rubriques.  
  
 [Connexion de contexte](the-context-connection.md)  
 Décrit la connexion de contexte.  
  
 [Comportement SQL Server spécifique au processus d’ADO.NET](sql-server-in-process-specific-behavior-of-adonet.md)  
 Décrit les extensions spécifiques au mode in-process SQL Server pour ADO.NET et la connexion de contexte. Fournit des liens vers d'autres rubriques.  
  
## <a name="see-also"></a>Voir aussi

- [SQL Server et ADO.NET](index.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
