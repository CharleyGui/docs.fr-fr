---
title: Comment utiliser l’appel de code non managé pour lire un fichier WAV-Guide de programmation C#
description: Cet exemple de code C# montre comment utiliser les services d’appel de code non managé pour lire un fichier audio WAV sur le système d’exploitation Windows.
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: b30cb08e2dcde0eb85e8d88a690ae24bf7ae7f22
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302982"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a>Comment utiliser l’appel de code non managé pour lire un fichier WAV (Guide de programmation C#)

L’exemple de code C# suivant montre comment utiliser les services d’appel de code non managé pour lire un fichier audio WAV sur le système d’exploitation Windows.

## <a name="example"></a>Exemple

Cet exemple de code utilise <xref:System.Runtime.InteropServices.DllImportAttribute> pour importer le point d’entrée de la méthode `PlaySound` de `winmm.dll` sous la forme `Form1 PlaySound()`. L’exemple utilise un formulaire Windows Form simple avec un bouton. En cliquant sur le bouton, vous ouvrez une boîte de dialogue <xref:System.Windows.Forms.OpenFileDialog> Windows standard qui permet d’ouvrir un fichier à lire. Lorsqu’un fichier Wave est sélectionné, il est lu à l’aide `PlaySound()` de la méthode de la bibliothèque de *winmm.dll* . Pour plus d’informations sur cette méthode, consultez [Utilisation de la fonction PlaySound avec des fichiers audio Waveform](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). Recherchez et sélectionnez un fichier avec une extension .wav, puis cliquez sur **Ouvrir** pour lire le fichier audio à l’aide de l’appel de code non managé. Une zone de texte affiche le chemin complet du fichier sélectionné.

La boîte de dialogue **Ouvrir les fichiers** est filtrée pour afficher uniquement les fichiers avec une extension .wav au moyen des paramètres de filtre :

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a>Compilation du code

1. Créez un nouveau projet d’application de Windows Forms C# dans Visual Studio et nommez-le **winsound**.

2. Copiez le code ci-dessus et collez-le sur le contenu du fichier *Form1.cs* .

3. Copiez le code suivant et collez-le dans le fichier *Form1.Designer.cs* , dans la `InitializeComponent()` méthode, après tout code existant.

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. Compilez, puis exécutez le code.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Vue d'ensemble de l'interopérabilité](interoperability-overview.md)
- [Présentation détaillée de l’appel de code non managé](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Marshaling de données à l’aide de l’appel de code managé](../../../framework/interop/marshaling-data-with-platform-invoke.md)
