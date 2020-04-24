---
title: Classes utilisées dans les E/S de fichiers .NET Framework et le système de fichiers
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: fe70f8fb655579049bb36fc324d04530259d25f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348927"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Classes utilisées dans les E/S de fichier du .NET Framework et le système de fichiers (Visual Basic)

Les tableaux suivants répertorient les classes couramment utilisées pour les E/S de fichier du .NET Framework. Ces classes sont réparties dans les catégories suivantes : classes d’E/S de fichier, classes utilisées pour créer des flux et classes utilisées pour lire et écrire dans les flux.  
  
Pour obtenir une liste plus complète, consultez [Vue d’ensemble de la bibliothèque de classes](../../../../standard/class-library-overview.md).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Classes d’E/S de base pour les fichiers, les lecteurs et les répertoires  

 Le tableau suivant répertorie et décrit les principales classes utilisées pour les E/S de fichier.  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Fournit des méthodes statiques pour la création, le déplacement et l’énumération dans les répertoires et les sous-répertoires.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Fournit des méthodes d’instance pour la création, le déplacement et l’énumération dans les répertoires et les sous-répertoires.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Fournit des méthodes d’instance pour la création, le déplacement et l’énumération dans les lecteurs.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Fournit des méthodes statiques pour la création, la copie, la suppression, le déplacement et l’ouverture de fichiers, et facilite la création d’objets `FileStream`.|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Définit des constantes pour l’accès en lecture, en écriture ou en lecture/écriture à un fichier.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|Fournit des attributs pour les fichiers et répertoires, tels que `Archive`, `Hidden` et `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Fournit des méthodes statiques pour la création, la copie, la suppression, le déplacement et l’ouverture de fichiers, et facilite la création d’objets `FileStream`.|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Contrôle l’ouverture d’un fichier. Ce paramètre est spécifié dans de nombreux constructeurs pour `FileStream` et `IsolatedStorageFileStream`, ainsi que pour les méthodes `Open` de <xref:System.IO.File> et <xref:System.IO.FileInfo>.|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Définit des constantes pour le contrôle du type d’accès que d’autres flux de fichiers peuvent avoir sur le même fichier.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Fournit des méthodes et des propriétés pour le traitement des chaînes de répertoire.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Contrôle l’accès des fichiers et des dossiers en définissant les autorisations <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> et <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>.|  
  
## <a name="classes-used-to-create-streams"></a>Classes utilisées pour créer des flux  

 Le tableau suivant répertorie et décrit les principales classes utilisées pour créer des flux.  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Ajoute une couche de mise en mémoire tampon aux opérations de lecture et d’écriture sur un autre flux.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|Prend en charge l’accès aléatoire aux fichiers par le biais de sa méthode <xref:System.IO.FileStream.Seek%2A>. <xref:System.IO.FileStream> ouvre par défaut les fichiers de façon synchrone, mais prend également en charge les opérations asynchrones.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Crée un flux dont le magasin de stockage est une mémoire et non un fichier.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Fournit le flux de données sous-jacent pour l’accès réseau.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Définit un flux qui lie les flux de données aux transformations par chiffrement.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Classes utilisées pour lire et écrire dans des flux  

 Le tableau suivant répertorie les classes spécifiques utilisées pour lire et écrire dans des fichiers avec des flux.  
  
|**Classe**|**Description**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Lit des chaînes encodées et des types de données primitifs à partir d’un <xref:System.IO.FileStream>.|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Écrit des chaînes encodées et des types de données primitifs dans un <xref:System.IO.FileStream>.|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Lit les caractères d’un <xref:System.IO.FileStream>, en utilisant <xref:System.IO.StreamReader.CurrentEncoding%2A> pour convertir des caractères en octets et des octets en caractères. <xref:System.IO.StreamReader> a un constructeur qui tente de déterminer le <xref:System.IO.StreamReader.CurrentEncoding%2A> correct pour un flux donné, en fonction de la présence d’un préambule propre à <xref:System.IO.StreamReader.CurrentEncoding%2A>, tel qu’une marque d’ordre d’octet.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Écrit des caractères dans un `FileStream`, en utilisant <xref:System.IO.StreamWriter.Encoding%2A> pour convertir des caractères en octets.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Lit des caractères dans un `String`. La sortie peut être un flux de n’importe quel encodage ou un `String`.|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Écrit des caractères dans un `String`. La sortie peut être un flux de n’importe quel encodage ou un `String`.|  
  
## <a name="see-also"></a>Voir aussi

- [Composition de flux](../../../../standard/io/composing-streams.md)
- [E/s de fichier et de flux](../../../../standard/io/index.md)
- [E/s de fichier asynchrones](../../../../standard/io/asynchronous-file-i-o.md)
- [Concepts de base du système de fichiers et des E/S de fichier du .NET Framework (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
