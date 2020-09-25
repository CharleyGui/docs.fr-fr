---
title: LINQ et répertoires de fichiers (C#)
description: Ces ressources LINQ C# pour les opérations de système de fichiers ne sont pas utilisées pour modifier le contenu des fichiers ou des dossiers.
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: d8ef8ac8a8ff25f0bbac417c07e39f516eee27f2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170478"
---
# <a name="linq-and-file-directories-c"></a>LINQ et répertoires de fichiers (C#)

De nombreuses opérations du système de fichiers sont essentiellement des requêtes et sont donc bien adaptées à l’approche LINQ.  
  
 Les requêtes de cette section ne sont pas destructrices. Elles ne sont pas utilisées pour modifier le contenu des fichiers ou des dossiers d’origine. La règle suivie est que les requêtes ne doivent pas provoquer des effets secondaires. En règle générale, tout code (y compris les requêtes qui utilisent des opérateurs de création / mise à jour / suppression) qui modifie les données sources doit rester distinct du code qui interroge simplement les données.  
  
 Cette section contient les rubriques suivantes :  
  
 [Comment rechercher des fichiers avec un attribut ou un nom spécifié (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)\
 Montre comment rechercher des fichiers en examinant une ou plusieurs propriétés de son objet <xref:System.IO.FileInfo>.  
  
 [Guide pratique pour regrouper des fichiers par extension (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)\
 Montre comment retourner des groupes d’objets <xref:System.IO.FileInfo> en fonction de leur extension de nom de fichier.  
  
 [Comment interroger le nombre total d’octets dans un ensemble de dossiers (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)\
 Montre comment retourner le nombre total d’octets dans tous les fichiers d’une arborescence de répertoires spécifiée.  
  
 Guide pratique [pour comparer le contenu de deux dossiers (LINQ) (C#)](./how-to-compare-the-contents-of-two-folders-linq.md)  
 Montre comment retourner tous les fichiers qui sont présents dans deux dossiers spécifiés, ainsi que tous les fichiers qui sont présents dans un dossier mais pas dans l’autre.  
  
 [Comment interroger les fichiers les plus volumineux dans une arborescence de répertoires (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)\
 Montre comment retourner le fichier le plus grand ou le plus petit, ou un nombre spécifié de fichiers, dans une arborescence de répertoires.  
  
 [Comment interroger des fichiers dupliqués dans une arborescence de répertoires (LINQ) (C#)](./how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)\
 Montre comment regrouper tous les noms de fichier qui se trouvent dans plusieurs emplacements d’une arborescence de répertoires spécifiée. Montre aussi comment effectuer des comparaisons plus complexes avec un comparateur personnalisé.  
  
 [Comment interroger le contenu de fichiers dans un dossier (LINQ) (C#)](./how-to-query-the-contents-of-files-in-a-folder-lin.md)\
 Montre comment itérer au sein des dossiers d’une arborescence, ouvrir chaque fichier et interroger le contenu du fichier.  
  
## <a name="comments"></a>Commentaires  

 La création d’une source de données représentant avec précision le contenu du système de fichiers et la gestion correcte des exceptions induisent une certaine complexité. Les exemples de cette section créent une collection d’instantanés d’objets <xref:System.IO.FileInfo> qui représente tous les fichiers d’un dossier racine spécifié et de tous ses sous-dossiers. L’état réel de chaque <xref:System.IO.FileInfo> peut changer dans le temps entre le début et la fin de l’exécution d’une requête. Par exemple, vous pouvez créer une liste d’objets <xref:System.IO.FileInfo> à utiliser comme source de données. Si vous essayez d’accéder à la propriété `Length` dans une requête, l’objet <xref:System.IO.FileInfo> tente d’accéder au système de fichiers pour mettre à jour la valeur de `Length`. Si le fichier n’existe plus, vous obtenez une exception <xref:System.IO.FileNotFoundException> dans votre requête, même si vous n’interrogez pas directement le système de fichiers. Certaines requêtes de cette section utilisent une méthode distincte qui consomme ces exceptions particulières dans certains cas. Une autre option consiste à conserver votre source de données à jour dynamiquement en utilisant <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Voir aussi

- [LINQ to Objects (C#)](./linq-to-objects.md)
