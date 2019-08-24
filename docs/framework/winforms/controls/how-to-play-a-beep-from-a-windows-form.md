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
# <a name="how-to-play-a-beep-from-a-windows-form"></a>Procédure : émettre un bip sonore à partir d’un formulaire Windows
Cet exemple émet un signal sonore à l’exécution.

## <a name="example"></a>Exemple

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
> Le son joué dans l' C# exemple de code est déterminé par <xref:System.Media.SystemSounds.Beep%2A> le paramètre son du système. Pour plus d'informations, consultez <xref:System.Media.SystemSounds>.

## <a name="compiling-the-code"></a>Compilation du code
 Pour C#, cet exemple nécessite une référence à l' <xref:System.Media?displayProperty=nameWithType> espace de noms.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.Beep%2A>
- <xref:System.Media.SoundPlayer>
- [Guide pratique : Lire un son système à partir d’un Windows Form](how-to-play-a-system-sound-from-a-windows-form.md)
- [Guide pratique pour Émettre un son à partir d’un Windows Form](how-to-play-a-sound-from-a-windows-form.md)
