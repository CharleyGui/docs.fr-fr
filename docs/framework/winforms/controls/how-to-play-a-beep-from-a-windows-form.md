---
title: 'Procédure : émettre un bip sonore à partir d’un formulaire Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], beep
- Windows Forms, sounds
- sounds [Windows Forms], playing
- forms [Windows Forms], sounds
- examples [Windows Forms], sounds
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
ms.openlocfilehash: 7fecc5d5b7259b743926713f87d9303596803582
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015809"
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="25a77-102">Procédure : émettre un bip sonore à partir d’un formulaire Windows</span><span class="sxs-lookup"><span data-stu-id="25a77-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="25a77-103">Cet exemple émet un signal sonore à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="25a77-103">This example plays a beep at run time.</span></span>

## <a name="example"></a><span data-ttu-id="25a77-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="25a77-104">Example</span></span>

```vb
Public Sub OnePing()
    Beep()
End Sub
```

```csharp
public void onePing()
{
    SystemSounds.Beep.Play();
}
```

> [!NOTE]
> <span data-ttu-id="25a77-105">Le son joué dans l' C# exemple de code est déterminé par <xref:System.Media.SystemSounds.Beep%2A> le paramètre son du système.</span><span class="sxs-lookup"><span data-stu-id="25a77-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="25a77-106">Pour plus d'informations, consultez <xref:System.Media.SystemSounds>.</span><span class="sxs-lookup"><span data-stu-id="25a77-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="25a77-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="25a77-107">Compiling the Code</span></span>
 <span data-ttu-id="25a77-108">Pour C#, cet exemple nécessite une référence à l' <xref:System.Media?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="25a77-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="25a77-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25a77-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="25a77-110">Guide pratique : Lire un son système à partir d’un Windows Form</span><span class="sxs-lookup"><span data-stu-id="25a77-110">How to: Play a System Sound from a Windows Form</span></span>](how-to-play-a-system-sound-from-a-windows-form.md)
- [<span data-ttu-id="25a77-111">Guide pratique pour Émettre un son à partir d’un Windows Form</span><span class="sxs-lookup"><span data-stu-id="25a77-111">How to: Play a Sound from a Windows Form</span></span>](how-to-play-a-sound-from-a-windows-form.md)
