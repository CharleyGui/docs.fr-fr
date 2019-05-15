---
title: 'Procédure : émettre un son en boucle dans un formulaire Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
ms.openlocfilehash: e14d9de2326234b86c1f24b227e86f822fbfdb71
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592357"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a>Procédure : émettre un son en boucle dans un formulaire Windows
L'exemple de code suivant joue un son de manière répétitive. Quand le code du gestionnaire d'événements `stopPlayingButton_Click` est exécuté, le son s'arrête. Si aucun son n'est joué, rien ne se produit.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys System et System.Windows.Forms ;  
  
- que vous remplaciez le nom de fichier `"c:\Windows\Media\chimes.wav"` par un nom de fichier valide.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les opérations de fichiers doivent être placées dans des blocs de gestion des exceptions appropriés.  
  
 Les conditions ci-dessous peuvent générer une exception.  
  
- Le chemin d'accès est mal formé. Par exemple, il contient des caractères qui ne sont pas valides ou est constitué uniquement d'espaces blancs (classe <xref:System.ArgumentException>).  
  
- Le chemin d'accès est en lecture seule (classe <xref:System.IO.IOException>).  
  
- Le nom du chemin d'accès est `Nothing` (classe <xref:System.ArgumentNullException>).  
  
- Le nom du chemin d'accès est trop long (classe <xref:System.IO.PathTooLongException>).  
  
- Le chemin d'accès n'est pas valide (classe <xref:System.IO.DirectoryNotFoundException>).  
  
- Le chemin d’accès n’est constitué que d’un signe deux-points « : » (classe <xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu. Par exemple, le fichier Form1.vb peut ne pas être un fichier source Visual Basic. Vérifiez toutes les entrées avant d'utiliser les données dans votre application.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [Guide pratique pour Un signal sonore à partir d’un formulaire Windows](how-to-play-a-sound-from-a-windows-form.md)
- [Vue d’ensemble de la classe SoundPlayer](soundplayer-class-overview.md)
