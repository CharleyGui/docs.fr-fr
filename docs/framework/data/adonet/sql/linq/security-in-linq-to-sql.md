---
title: Sécurité dans LINQ to SQL
ms.date: 03/30/2017
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
ms.openlocfilehash: 6260f0c565a25764c8fabd2770d4f06a987aa9bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173391"
---
# <a name="security-in-linq-to-sql"></a>Sécurité dans LINQ to SQL

Les risques de sécurité sont toujours présents lorsque vous vous connectez à une base de données. Même si LINQ to SQL inclut de nouvelles méthodes d'utilisation des données dans SQL Server, il ne fournit pas de mécanismes de sécurité supplémentaires.  
  
## <a name="access-control-and-authentication"></a>Contrôle d'accès et authentification  

 LINQ to SQL ne dispose pas de modèle utilisateur ou de mécanismes d'authentification qui lui sont propres. SQL Server Security vous permet de contrôler l'accès à la base de données, aux tables de base de données, aux vues et aux procédures stockées qui sont mappées à votre modèle objet. Accordez l'accès requis minimal aux utilisateurs et exigez des mots de passe forts pour l'authentification des utilisateurs.  
  
## <a name="mapping-and-schema-information"></a>Informations de mappage et de schéma  

 Les informations de schéma de base de données et de mappage de type SQL-CLR de votre modèle objet ou fichier de mappage externe sont consultables par tous ceux qui ont accès à ces fichiers via le système de fichiers. Supposons que les informations de schéma sont disponibles pour tous les utilisateurs qui peuvent accéder au modèle objet ou au fichier de mappage externe. Pour empêcher un accès plus généralisé aux informations de schéma, utilisez des mécanismes de sécurité des fichiers pour sécuriser les fichiers sources et les fichiers de mappage.  
  
## <a name="connection-strings"></a>Chaînes de connexion  

 Dans la mesure du possible, vous devez éviter d'utiliser des mots de passe dans les chaînes de connexion. Non seulement une chaîne de connexion constitue un risque de sécurité en tant que telle, mais elle peut également être ajoutée en texte clair au modèle objet ou au fichier de mappage externe lors de l'utilisation du Concepteur Objet/Relationnel ou de l'outil de ligne de commande SQLMetal. Toute personne pouvant accéder au modèle objet ou au fichier de mappage externe via le système de fichiers peut visualiser le mot de passe de connexion (s'il est inclus dans la chaîne de connexion).  
  
 Pour réduire de tels risques, utilisez la sécurité intégrée pour établir une connexion approuvée avec SQL Server. En utilisant cette approche, vous ne devez pas stocker de mot de passe dans la chaîne de connexion. Pour plus d’informations, consultez [SQL Server Security](../sql-server-security.md).  
  
 En l'absence de sécurité intégrée, un mot de passe en texte clair est nécessaire dans la chaîne de connexion. La méthode la plus appropriée pour sécuriser votre chaîne de connexion, dans l'ordre croissant de risque, est la suivante :  
  
- Utilisez la sécurité intégrée.  
  
- Sécurisez les chaînes de connexion à l'aide de mots de passe et minimisez l'accès à celles-ci.  
  
- Utilisez une classe <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> au lieu d'une chaîne de connexion car elle limite la durée d'exposition. La classe <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> LINQ to SQL peut être instanciée à l'aide d'un objet <xref:System.Data.SqlClient.SqlConnection>.  
  
- Minimisez les durées de vie et les points d'accès pour toutes les chaînes de connexion.  
  
## <a name="see-also"></a>Voir aussi

- [Informations générales](background-information.md)
- [Questions fréquentes (FAQ)](frequently-asked-questions.md)
