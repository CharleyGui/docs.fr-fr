---
title: LINQ et répertoires de fichiers
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: 390d3c7a1c738aea0df8e3dcad0edb70563f8fb6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347801"
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ and File Directories (Visual Basic)
De nombreuses opérations du système de fichiers sont des requêtes et l’approche de LINQ leur convient donc bien.  
  
 Notez que les requêtes de cette section sont non destructives. Elles ne sont pas utilisées pour modifier le contenu des fichiers ou des dossiers d’origine. La règle suivie est que les requêtes ne doivent pas provoquer des effets secondaires. En règle générale, tout code (y compris les requêtes qui utilisent des opérateurs de création / mise à jour / suppression) qui modifie les données sources doit rester distinct du code qui interroge simplement les données.  
  
 Cette section contient les rubriques suivantes :  
  
 [How to: Query for Files with a Specified Attribute or Name (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Montre comment rechercher des fichiers en examinant une ou plusieurs propriétés de son objet <xref:System.IO.FileInfo>.  
  
 [How to: Group Files by Extension (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Montre comment retourner des groupes d’objets <xref:System.IO.FileInfo> en fonction de leur extension de nom de fichier.  
  
 [How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Montre comment retourner le nombre total d’octets dans tous les fichiers d’une arborescence de répertoires spécifiée.  
  
 [How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Montre comment retourner tous les fichiers qui sont présents dans deux dossiers spécifiés, ainsi que tous les fichiers qui sont présents dans un dossier mais pas dans l’autre.  
  
 [How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Montre comment retourner le fichier le plus grand ou le plus petit, ou un nombre spécifié de fichiers, dans une arborescence de répertoires.  
  
 [How to: Query for Duplicate Files in a Directory Tree (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Montre comment regrouper tous les noms de fichier qui se trouvent dans plusieurs emplacements d’une arborescence de répertoires spécifiée. Montre aussi comment effectuer des comparaisons plus complexes avec un comparateur personnalisé.  
  
 [How to query the contents of files in a folder (LINQ) (Visual Basic)](how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Montre comment itérer au sein des dossiers d’une arborescence, ouvrir chaque fichier et interroger le contenu du fichier.  
  
## <a name="comments"></a>Comments  
 La création d’une source de données représentant avec précision le contenu du système de fichiers et la gestion correcte des exceptions induisent une certaine complexité. Les exemples de cette section créent une collection d’instantanés d’objets <xref:System.IO.FileInfo> qui représente tous les fichiers d’un dossier racine spécifié et de tous ses sous-dossiers. L’état réel de chaque <xref:System.IO.FileInfo> peut changer dans le temps entre le début et la fin de l’exécution d’une requête. Par exemple, vous pouvez créer une liste d’objets <xref:System.IO.FileInfo> à utiliser comme source de données. Si vous essayez d’accéder à la propriété `Length` dans une requête, l’objet <xref:System.IO.FileInfo> tente d’accéder au système de fichiers pour mettre à jour la valeur de `Length`. Si le fichier n’existe plus, vous obtenez une exception <xref:System.IO.FileNotFoundException> dans votre requête, même si vous n’interrogez pas directement le système de fichiers. Certaines requêtes de cette section utilisent une méthode distincte qui consomme ces exceptions particulières dans certains cas. Une autre option consiste à conserver votre source de données à jour dynamiquement en utilisant <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Voir aussi

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
