---
title: Le fichier est trop volumineux pour être lu dans un tableau d'octets
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: b81fc9332d5f1347404fcdd73bce72b6b09778b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363122"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>Le fichier est trop volumineux pour être lu dans un tableau d'octets
La taille du fichier que vous tentez de lire dans un tableau d’octets dépasse 4 Go. La `My.Computer.FileSystem.ReadAllBytes` méthode ne peut pas lire un fichier qui dépasse cette taille.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Utilisez un <xref:System.IO.StreamReader> pour lire le fichier. Pour plus d’informations, consultez [principes de base de l’e/s de fichier .NET Framework et du système de fichiers (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [Accès au fichier avec Visual Basic](../../developing-apps/programming/drives-directories-files/file-access.md)
- [Procédure : lire du texte à partir de fichiers avec un StreamReader](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
