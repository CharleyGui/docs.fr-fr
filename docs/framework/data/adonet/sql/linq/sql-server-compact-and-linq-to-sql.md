---
title: SQL Server Compact et LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: b5a1a12018bd85cf313c1841e6b67ab2edf67b4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792534"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact et LINQ to SQL
SQL Server Compact est la base de données par défaut installée avec Visual Studio. Pour plus d’informations, consultez [utilisation de SQL Server Compact (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).  
  
 Cette rubrique décrit les principales différences d’utilisation, de configuration, de jeux de fonctionnalités et d’étendue [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de prise en charge.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Caractéristiques de SQL Server Compact par rapport à LINQ to SQL  
 Par défaut, SQL Server Compact est installé pour toutes les éditions de Visual Studio. il est donc disponible sur l’ordinateur de développement [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]pour une utilisation avec. Mais le déploiement d’une application qui utilise SQL Server Compact [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et diffère de celle d’une application SQL Server. SQL Server Compact ne fait pas partie du .NET Framework et doit par conséquent être fourni avec l'application ou téléchargé séparément depuis le site Microsoft.  
  
 Notez les caractéristiques suivantes :  
  
- SQL Server Compact est fourni comme une DLL qui peut être utilisée directement sur les fichiers de base de données (extension .sdf).  
  
- SQL Server Compact s’exécute dans le même processus que l’application cliente. L’efficacité de la communication avec SQL Server Compact peut donc être beaucoup plus élevée que la communication avec SQL Server. En revanche, SQL Server Compact nécessite l’interopérabilité entre le code managé et le code non managé avec ses coûts de surveillance.  
  
- La taille de la DLL SQL Server Compact est faible. Cette fonctionnalité réduit la taille globale de l'application.  
  
- Le runtime de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et l'outil en ligne de commande SQLMetal prennent en charge SQL Server Compact.  
  
- Le Concepteur Objet Relationnel ne prend pas en charge SQL Server Compact.  
  
## <a name="feature-set"></a>Jeu de fonctionnalités  
 L’ensemble de fonctionnalités de SQL Server Compact est bien plus simple que l’ensemble de fonctionnalités de SQL Server des manières suivantes, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] qui peuvent affecter les applications :  
  
- SQL Server Compact ne prend pas en charge de procédures stockées ou de vues.  
  
- SQL Server Compact prend en charge uniquement un sous-ensemble de types de données et de fonctions SQL.  
  
- SQL Server Compact prend en charge uniquement un sous-ensemble de constructions SQL.  
  
- SQL Server Compact fournit uniquement un optimiseur minimal. Il est possible que certaines requêtes expirent.  
  
- SQL Server Compact ne prend pas en charge la confiance partielle.  
  
## <a name="see-also"></a>Voir aussi

- [Référence](reference.md)
