---
title: 'Comment : utiliser l’appel de code non managé pour lire un C# fichier Wave-Guide de programmation'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 6c2313f7b600bc1670c944f6a93868c1bc4c7c16
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039324"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="f185a-102">Comment : utiliser l'appel de code non managé pour lire un fichier audio (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f185a-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>

<span data-ttu-id="f185a-103">L’exemple de code C# suivant explique comment utiliser des services d’appel de code non managé pour lire un fichier audio sur le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="f185a-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>

## <a name="example"></a><span data-ttu-id="f185a-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f185a-104">Example</span></span>

<span data-ttu-id="f185a-105">Cet exemple de code utilise <xref:System.Runtime.InteropServices.DllImportAttribute> pour importer le point d’entrée de la méthode `PlaySound` de `winmm.dll` sous la forme `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="f185a-105">This example code uses <xref:System.Runtime.InteropServices.DllImportAttribute> to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="f185a-106">L’exemple utilise un formulaire Windows Form simple avec un bouton.</span><span class="sxs-lookup"><span data-stu-id="f185a-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="f185a-107">En cliquant sur le bouton, vous ouvrez une boîte de dialogue <xref:System.Windows.Forms.OpenFileDialog> Windows standard qui permet d’ouvrir un fichier à lire.</span><span class="sxs-lookup"><span data-stu-id="f185a-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="f185a-108">Lorsqu’un fichier Wave est sélectionné, il est lu à l’aide de la méthode `PlaySound()` de la bibliothèque *winmm. dll* .</span><span class="sxs-lookup"><span data-stu-id="f185a-108">When a wave file is selected, it is played by using the `PlaySound()` method of the *winmm.dll* library.</span></span> <span data-ttu-id="f185a-109">Pour plus d’informations sur cette méthode, consultez [Utilisation de la fonction PlaySound avec des fichiers audio Waveform](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="f185a-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="f185a-110">Recherchez et sélectionnez un fichier avec une extension .wav, puis cliquez sur **Ouvrir** pour lire le fichier audio à l’aide de l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="f185a-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="f185a-111">Une zone de texte affiche le chemin complet du fichier sélectionné.</span><span class="sxs-lookup"><span data-stu-id="f185a-111">A text box shows the full path of the file selected.</span></span>

<span data-ttu-id="f185a-112">La boîte de dialogue **Ouvrir les fichiers** est filtrée pour afficher uniquement les fichiers avec une extension .wav au moyen des paramètres de filtre :</span><span class="sxs-lookup"><span data-stu-id="f185a-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a><span data-ttu-id="f185a-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="f185a-113">Compiling the code</span></span>

1. <span data-ttu-id="f185a-114">Créez un nouveau C# Windows Forms projet d’application dans Visual Studio et nommez-le **winsound**.</span><span class="sxs-lookup"><span data-stu-id="f185a-114">Create a new C# Windows Forms Application project in Visual Studio and name it **WinSound**.</span></span>

2. <span data-ttu-id="f185a-115">Copiez le code ci-dessus et collez-le sur le contenu du fichier *Form1.cs* .</span><span class="sxs-lookup"><span data-stu-id="f185a-115">Copy the code above, and paste it over the contents of the *Form1.cs* file.</span></span>

3. <span data-ttu-id="f185a-116">Copiez le code suivant et collez-le dans le fichier *Form1.Designer.cs* , dans la méthode `InitializeComponent()`, après tout code existant.</span><span class="sxs-lookup"><span data-stu-id="f185a-116">Copy the following code, and paste it in the *Form1.Designer.cs* file, in the `InitializeComponent()` method, after any existing code.</span></span>

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. <span data-ttu-id="f185a-117">Compilez, puis exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="f185a-117">Compile and run the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="f185a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f185a-118">See also</span></span>

- [<span data-ttu-id="f185a-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f185a-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f185a-120">Vue d’ensemble de l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="f185a-120">Interoperability Overview</span></span>](interoperability-overview.md)
- [<span data-ttu-id="f185a-121">Présentation détaillée de l’appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="f185a-121">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="f185a-122">Marshaling de données à l’aide de l’appel de code managé</span><span class="sxs-lookup"><span data-stu-id="f185a-122">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
