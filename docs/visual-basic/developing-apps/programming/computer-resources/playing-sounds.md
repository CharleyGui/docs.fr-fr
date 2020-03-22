---
title: Lecture de sons
ms.date: 07/20/2015
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
ms.openlocfilehash: 416fedd011ff35d2b32d1b64932e3908a73ed14e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345520"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="f6229-102">Lecture de sons (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6229-102">Playing Sounds (Visual Basic)</span></span>

<span data-ttu-id="f6229-103">L’objet `My.Computer.Audio` fournit des méthodes permettant de lire des sons.</span><span class="sxs-lookup"><span data-stu-id="f6229-103">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="f6229-104">Lecture de sons</span><span class="sxs-lookup"><span data-stu-id="f6229-104">Playing Sounds</span></span>  

 <span data-ttu-id="f6229-105">Avec la lecture en arrière-plan, l’application peut exécuter du code pendant la lecture d’un son.</span><span class="sxs-lookup"><span data-stu-id="f6229-105">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="f6229-106">La méthode `My.Computer.Audio.Play` permet à l’application de lire un seul fond sonore à la fois. Quand elle lit un nouveau fond sonore, l’application arrête la lecture du fond sonore précédent.</span><span class="sxs-lookup"><span data-stu-id="f6229-106">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="f6229-107">L’application peut également lire un son et attendre qu’il s’arrête.</span><span class="sxs-lookup"><span data-stu-id="f6229-107">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="f6229-108">Dans l’exemple suivant, la méthode `My.Computer.Audio.Play` lit un son.</span><span class="sxs-lookup"><span data-stu-id="f6229-108">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="f6229-109">Quand `AudioPlayMode.WaitToComplete` est spécifié, `My.Computer.Audio.Play` attend que le son s’arrête pour que l’exécution du code appelant continue.</span><span class="sxs-lookup"><span data-stu-id="f6229-109">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="f6229-110">Si vous utilisez cet exemple, assurez-vous que le nom de fichier fait référence à un fichier son .wav enregistré sur votre ordinateur</span><span class="sxs-lookup"><span data-stu-id="f6229-110">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="f6229-111">Dans l’exemple suivant, la méthode `My.Computer.Audio.Play` lit un son.</span><span class="sxs-lookup"><span data-stu-id="f6229-111">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="f6229-112">Si vous utilisez cet exemple, assurez-vous que les ressources d’application incluent un fichier son .wav nommé Waterfall.</span><span class="sxs-lookup"><span data-stu-id="f6229-112">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="f6229-113">Lecture de sons en boucle</span><span class="sxs-lookup"><span data-stu-id="f6229-113">Playing Looping Sounds</span></span>  

 <span data-ttu-id="f6229-114">Dans l’exemple suivant, la méthode `My.Computer.Audio.Play` lit le son spécifié en arrière-plan quand `PlayMode.BackgroundLoop` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="f6229-114">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="f6229-115">Si vous utilisez cet exemple, assurez-vous que le nom de fichier fait référence à un fichier son .wav enregistré sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f6229-115">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="f6229-116">Dans l’exemple suivant, la méthode `My.Computer.Audio.Play` lit le son spécifié en arrière-plan quand `PlayMode.BackgroundLoop` est spécifié.</span><span class="sxs-lookup"><span data-stu-id="f6229-116">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="f6229-117">Si vous utilisez cet exemple, assurez-vous que les ressources d’application incluent un fichier son .wav nommé Waterfall.</span><span class="sxs-lookup"><span data-stu-id="f6229-117">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="f6229-118">L’exemple de code précédent est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="f6229-118">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="f6229-119">Dans le sélecteur d’extraits de code, il se trouve dans **Applications Windows Forms > Son**.</span><span class="sxs-lookup"><span data-stu-id="f6229-119">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="f6229-120">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="f6229-120">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="f6229-121">En général, quand une application lit un son en boucle, elle doit finir par l’arrêter.</span><span class="sxs-lookup"><span data-stu-id="f6229-121">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="f6229-122">Arrêt de la lecture de sons en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="f6229-122">Stopping the Playing of Sounds in the Background</span></span>  

 <span data-ttu-id="f6229-123">Utilisez la méthode `My.Computer.Audio.Stop` pour arrêter la lecture en arrière-plan ou en boucle d’un son dans l’application.</span><span class="sxs-lookup"><span data-stu-id="f6229-123">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="f6229-124">En général, quand une application lit un son en boucle, elle doit l’arrêter à un certain point.</span><span class="sxs-lookup"><span data-stu-id="f6229-124">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="f6229-125">L’exemple suivant arrête un son qui est lu en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="f6229-125">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="f6229-126">L’exemple de code précédent est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="f6229-126">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="f6229-127">Dans le sélecteur d’extraits de code, il se trouve dans **Applications Windows Forms > Son**.</span><span class="sxs-lookup"><span data-stu-id="f6229-127">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="f6229-128">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="f6229-128">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="f6229-129">Lecture de sons système</span><span class="sxs-lookup"><span data-stu-id="f6229-129">Playing System Sounds</span></span>  

 <span data-ttu-id="f6229-130">Utilisez la méthode `My.Computer.Audio.PlaySystemSound` pour lire le son système spécifié.</span><span class="sxs-lookup"><span data-stu-id="f6229-130">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="f6229-131">La méthode `My.Computer.Audio.PlaySystemSound` prend comme paramètre l’un des membres partagés de la classe <xref:System.Media.SystemSound>.</span><span class="sxs-lookup"><span data-stu-id="f6229-131">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="f6229-132">Le son système <xref:System.Media.SystemSounds.Asterisk%2A> indique généralement des erreurs.</span><span class="sxs-lookup"><span data-stu-id="f6229-132">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="f6229-133">L’exemple suivant utilise la méthode `My.Computer.Audio.PlaySystemSound` pour lire un son système.</span><span class="sxs-lookup"><span data-stu-id="f6229-133">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="f6229-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6229-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
