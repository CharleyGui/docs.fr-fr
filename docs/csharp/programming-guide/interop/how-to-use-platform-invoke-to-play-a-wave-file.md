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
ms.openlocfilehash: 6f507fa348bf1ea1b3fc5c3a868a6fbab7f8ec56
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558353"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a><span data-ttu-id="6d004-103">Comment utiliser l’appel de code non managé pour lire un fichier WAV (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6d004-103">How to use platform invoke to play a WAV file (C# Programming Guide)</span></span>

<span data-ttu-id="6d004-104">L’exemple de code C# suivant montre comment utiliser les services d’appel de code non managé pour lire un fichier audio WAV sur le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="6d004-104">The following C# code example illustrates how to use platform invoke services to play a WAV sound file on the Windows operating system.</span></span>

## <a name="example"></a><span data-ttu-id="6d004-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="6d004-105">Example</span></span>

<span data-ttu-id="6d004-106">Cet exemple de code utilise <xref:System.Runtime.InteropServices.DllImportAttribute> pour importer le point d’entrée de la méthode `PlaySound` de `winmm.dll` sous la forme `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="6d004-106">This example code uses <xref:System.Runtime.InteropServices.DllImportAttribute> to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="6d004-107">L’exemple utilise un formulaire Windows Form simple avec un bouton.</span><span class="sxs-lookup"><span data-stu-id="6d004-107">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="6d004-108">En cliquant sur le bouton, vous ouvrez une boîte de dialogue <xref:System.Windows.Forms.OpenFileDialog> Windows standard qui permet d’ouvrir un fichier à lire.</span><span class="sxs-lookup"><span data-stu-id="6d004-108">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="6d004-109">Lorsqu’un fichier Wave est sélectionné, il est lu à l’aide `PlaySound()` de la méthode de la bibliothèque de *winmm.dll* .</span><span class="sxs-lookup"><span data-stu-id="6d004-109">When a wave file is selected, it is played by using the `PlaySound()` method of the *winmm.dll* library.</span></span> <span data-ttu-id="6d004-110">Pour plus d’informations sur cette méthode, consultez [Utilisation de la fonction PlaySound avec des fichiers audio Waveform](/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="6d004-110">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="6d004-111">Recherchez et sélectionnez un fichier avec une extension .wav, puis cliquez sur **Ouvrir** pour lire le fichier audio à l’aide de l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="6d004-111">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="6d004-112">Une zone de texte affiche le chemin complet du fichier sélectionné.</span><span class="sxs-lookup"><span data-stu-id="6d004-112">A text box shows the full path of the file selected.</span></span>

<span data-ttu-id="6d004-113">La boîte de dialogue **Ouvrir les fichiers** est filtrée pour afficher uniquement les fichiers avec une extension .wav au moyen des paramètres de filtre :</span><span class="sxs-lookup"><span data-stu-id="6d004-113">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a><span data-ttu-id="6d004-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="6d004-114">Compiling the code</span></span>

1. <span data-ttu-id="6d004-115">Créez un nouveau projet d’application de Windows Forms C# dans Visual Studio et nommez-le **winsound**.</span><span class="sxs-lookup"><span data-stu-id="6d004-115">Create a new C# Windows Forms Application project in Visual Studio and name it **WinSound**.</span></span>

2. <span data-ttu-id="6d004-116">Copiez le code ci-dessus et collez-le sur le contenu du fichier *Form1.cs* .</span><span class="sxs-lookup"><span data-stu-id="6d004-116">Copy the code above, and paste it over the contents of the *Form1.cs* file.</span></span>

3. <span data-ttu-id="6d004-117">Copiez le code suivant et collez-le dans le fichier *Form1.Designer.cs* , dans la `InitializeComponent()` méthode, après tout code existant.</span><span class="sxs-lookup"><span data-stu-id="6d004-117">Copy the following code, and paste it in the *Form1.Designer.cs* file, in the `InitializeComponent()` method, after any existing code.</span></span>

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. <span data-ttu-id="6d004-118">Compilez, puis exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="6d004-118">Compile and run the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d004-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d004-119">See also</span></span>

- [<span data-ttu-id="6d004-120">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6d004-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6d004-121">Vue d'ensemble de l'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="6d004-121">Interoperability Overview</span></span>](interoperability-overview.md)
- [<span data-ttu-id="6d004-122">Présentation détaillée de l’appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="6d004-122">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="6d004-123">Marshaling de données à l’aide de l’appel de code managé</span><span class="sxs-lookup"><span data-stu-id="6d004-123">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
