---
title: Tâches d’E/S courantes
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- I/O, common tasks
ms.assetid: bf00c380-706a-4e38-b829-454a480629fc
ms.openlocfilehash: 01e9d6b50bd7eeafea792a772ca86a81e40dafd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708176"
---
# <a name="common-io-tasks"></a>Tâches d’E/S courantes
L'espace de noms <xref:System.IO> fournit plusieurs classes qui permettent d'exécuter différentes actions, telles que la lecture et l'écriture, sur des fichiers, des répertoires et des flux de données. Pour plus d’informations, voir [Fichier et Stream I/O](../../../docs/standard/io/index.md).  
  
## <a name="common-file-tasks"></a>Tâches de fichier courantes  
  
|Action à réaliser...|Consultez l'exemple décrit dans cette rubrique...|  
|-------------------|--------------------------------------|  
|Créer un fichier texte|Méthode <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType><br /><br /> Méthode <xref:System.IO.FileInfo.CreateText%2A?displayProperty=nameWithType><br /><br /> Méthode <xref:System.IO.File.Create%2A?displayProperty=nameWithType><br /><br /> Méthode <xref:System.IO.FileInfo.Create%2A?displayProperty=nameWithType>|  
|Écrire dans un fichier texte|[Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)<br /><br /> [Comment : Écrire un fichier texte (C/CLI)](/cpp/dotnet/how-to-write-a-text-file-cpp-cli)|  
|Lire à partir d'un fichier texte|[Comment : lire du texte dans un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)|  
|Ajouter du texte dans un fichier|[Comment : ouvrir un fichier journal et y ajouter des éléments](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)<br /><br /> Méthode <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType><br /><br /> Méthode <xref:System.IO.FileInfo.AppendText%2A?displayProperty=nameWithType>|  
|Renommer ou déplacer un fichier|Méthode <xref:System.IO.File.Move%2A?displayProperty=nameWithType><br /><br /> Méthode <xref:System.IO.FileInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Supprimer un fichier|Méthode <xref:System.IO.File.Delete%2A?displayProperty=nameWithType><br /><br /> Méthode <xref:System.IO.FileInfo.Delete%2A?displayProperty=nameWithType>|  
|Copier un fichier|Méthode <xref:System.IO.File.Copy%2A?displayProperty=nameWithType><br /><br /> Méthode <xref:System.IO.FileInfo.CopyTo%2A?displayProperty=nameWithType>|  
|Obtenir la taille d'un fichier|Propriété <xref:System.IO.FileInfo.Length%2A?displayProperty=nameWithType>|  
|Obtenir les attributs d'un fichier|Méthode <xref:System.IO.File.GetAttributes%2A?displayProperty=nameWithType>|  
|Définir les attributs d'un fichier|Méthode <xref:System.IO.File.SetAttributes%2A?displayProperty=nameWithType>|  
|Déterminer si un fichier existe|Méthode <xref:System.IO.File.Exists%2A?displayProperty=nameWithType>|  
|Lire à partir d'un fichier binaire|[Comment : lire et écrire dans un fichier de données créé récemment](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Écrire dans un fichier binaire|[Comment : lire et écrire dans un fichier de données créé récemment](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Récupérer une extension de nom de fichier|Méthode <xref:System.IO.Path.GetExtension%2A?displayProperty=nameWithType>|  
|Récupérer le chemin d’accès qualifié complet d’un fichier|Méthode <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType>|  
|Récupérer le nom de fichier et son extension à partir d’un chemin d’accès|Méthode <xref:System.IO.Path.GetFileName%2A?displayProperty=nameWithType>|  
|Modifier l’extension d’un fichier|Méthode <xref:System.IO.Path.ChangeExtension%2A?displayProperty=nameWithType>|  
  
## <a name="common-directory-tasks"></a>Tâches de répertoire courantes  
  
|Action à réaliser...|Consultez l'exemple décrit dans cette rubrique...|  
|-------------------|--------------------------------------|  
|Accéder à un fichier dans un dossier spécial comme Mes documents|[Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)|  
|Créer un répertoire|Méthode <xref:System.IO.Directory.CreateDirectory%2A?displayProperty=nameWithType><br /><br /> Propriété <xref:System.IO.FileInfo.Directory%2A?displayProperty=nameWithType>|  
|Créer un sous-répertoire|Méthode <xref:System.IO.DirectoryInfo.CreateSubdirectory%2A?displayProperty=nameWithType>|  
|Renommer ou déplacer un répertoire|Méthode <xref:System.IO.Directory.Move%2A?displayProperty=nameWithType><br /><br /> Méthode <xref:System.IO.DirectoryInfo.MoveTo%2A?displayProperty=nameWithType>|  
|Copier un répertoire|[Comment : copier des répertoires](../../../docs/standard/io/how-to-copy-directories.md)|  
|Supprimer un répertoire|Méthode <xref:System.IO.Directory.Delete%2A?displayProperty=nameWithType><br /><br /> Méthode <xref:System.IO.DirectoryInfo.Delete%2A?displayProperty=nameWithType>|  
|Afficher les fichiers et les sous-répertoires d'un répertoire|[Comment : énumérer des répertoires et des fichiers](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)|  
|Rechercher la taille d'un répertoire|Classe <xref:System.IO.Directory?displayProperty=nameWithType>|  
|Déterminer si un répertoire existe|Méthode <xref:System.IO.Directory.Exists%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Voir aussi

- [Fichier et stream I/O](../../../docs/standard/io/index.md)
- [Composing Streams](../../../docs/standard/io/composing-streams.md)
- [E/S sur fichier asynchrones](../../../docs/standard/io/asynchronous-file-i-o.md)
