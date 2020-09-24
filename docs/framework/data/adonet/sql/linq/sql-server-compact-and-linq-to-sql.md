---
title: SQL Server Compact et LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 7963db9e05eca7a7a148228c6d2fbca0221ca870
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155677"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact et LINQ to SQL

SQL Server Compact est la base de données par défaut installée avec Visual Studio. Pour plus d’informations, consultez [utilisation de SQL Server Compact (Visual Studio)](/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).  
  
 Cette rubrique décrit les principales différences d’utilisation, de configuration, de jeux de fonctionnalités et d’étendue de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] prise en charge.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Caractéristiques de SQL Server Compact par rapport à LINQ to SQL  

 Par défaut, SQL Server Compact est installé pour toutes les éditions de Visual Studio. il est donc disponible sur l’ordinateur de développement pour une utilisation avec [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Mais le déploiement d’une application qui utilise SQL Server Compact et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] diffère de celle d’une application SQL Server. SQL Server Compact ne fait pas partie du .NET Framework et doit par conséquent être fourni avec l'application ou téléchargé séparément depuis le site Microsoft.  
  
 Notez les caractéristiques suivantes :  
  
- SQL Server Compact est fourni comme une DLL qui peut être utilisée directement sur les fichiers de base de données (extension .sdf).  
  
- SQL Server Compact s'exécute au cours du même processus que l'application cliente. L’efficacité de la communication avec SQL Server Compact peut donc être beaucoup plus élevée que la communication avec SQL Server. En revanche, SQL Server Compact requiert l'interopérabilité entre le code managé et le code non managé avec ses coûts connexes.  
  
- La taille de la DLL SQL Server Compact est faible. Cette fonctionnalité réduit la taille globale de l'application.  
  
- Le runtime de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et l'outil en ligne de commande SQLMetal prennent en charge SQL Server Compact.  
  
- Le Concepteur Objet Relationnel ne prend pas en charge SQL Server Compact.  
  
## <a name="feature-set"></a>Jeu de fonctionnalités  

 L’ensemble de fonctionnalités de SQL Server Compact est bien plus simple que l’ensemble de fonctionnalités de SQL Server des manières suivantes, qui peuvent affecter les [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :  
  
- SQL Server Compact ne prend pas en charge de procédures stockées ou de vues.  
  
- SQL Server Compact prend en charge uniquement un sous-ensemble de types de données et de fonctions SQL.  
  
- SQL Server Compact prend en charge uniquement un sous-ensemble de constructions SQL.  
  
- SQL Server Compact fournit uniquement un optimiseur minimal. Il est possible que certaines requêtes expirent.  
  
- SQL Server Compact ne prend pas en charge la confiance partielle.  
  
## <a name="see-also"></a>Voir aussi

- [Référence](reference.md)
