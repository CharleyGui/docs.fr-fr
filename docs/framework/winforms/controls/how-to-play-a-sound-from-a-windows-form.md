---
title: Guide pratique pour émettre un son à partir d'un Windows Form
description: Découvrez comment lire un son à partir d’un Windows Form à un chemin d’accès donné au moment de l’exécution. En savoir plus sur la compilation du code et de l’infrastructure de sécurité .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
ms.openlocfilehash: beb17d994e224f41b2b590ecb1401988cdad314d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613746"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a>Guide pratique pour émettre un son à partir d'un Windows Form
Cet exemple émet un son à un chemin donné au moment de l’exécution.

## <a name="example"></a>Exemple

```vb
Sub PlaySimpleSound()
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")
End Sub
```

```csharp
private void playSimpleSound()
{
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");
    simpleSound.Play();
}
```

## <a name="compiling-the-code"></a>Compilation du code
 Cet exemple nécessite :

- que vous remplaciez le nom de fichier `"c:\Windows\Media\chimes.wav"` par un nom de fichier valide.

- C# Référence à l' <xref:System.Media?displayProperty=nameWithType> espace de noms.

## <a name="robust-programming"></a>Programmation fiable
 Les opérations de fichiers doivent être placées dans des blocs de gestion des exceptions structurés appropriés.

 Les conditions ci-dessous peuvent générer une exception.

- Le chemin d’accès est mal formé. Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (classe <xref:System.ArgumentException>).

- Le chemin d’accès est en lecture seule (classe <xref:System.IO.IOException>).

- Le nom du chemin d’accès est `null` (classe <xref:System.ArgumentNullException>).

- Le nom de chemin d'accès est trop long (classe <xref:System.IO.PathTooLongException>).

- Le chemin d’accès n’est pas valide (classe <xref:System.IO.DirectoryNotFoundException>).

- Le chemin d’accès est uniquement un signe deux-points, «  : » ( <xref:System.NotSupportedException> classe).

## <a name="net-framework-security"></a>Sécurité du .NET Framework
 Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu. Par exemple, le fichier `Form1.vb` peut ne pas être un fichier source Visual Basic. Vérifiez toutes les entrées avant d'utiliser les données dans votre application.

## <a name="see-also"></a>Voir aussi

- <xref:System.Media.SoundPlayer>
- [Guide pratique pour charger un son de façon asynchrone dans un Windows Form](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
