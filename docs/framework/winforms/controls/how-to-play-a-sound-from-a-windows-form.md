---
title: 'Procédure : émettre un signal sonore à partir d’un formulaire Windows'
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
ms.openlocfilehash: 68a68f05b847877641132e540995f6b14bb6e065
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015797"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="ea82d-102">Procédure : émettre un signal sonore à partir d’un formulaire Windows</span><span class="sxs-lookup"><span data-stu-id="ea82d-102">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="ea82d-103">Cet exemple émet un son à un chemin donné au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ea82d-103">This example plays a sound at a given path at run time.</span></span>

## <a name="example"></a><span data-ttu-id="ea82d-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="ea82d-104">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="ea82d-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="ea82d-105">Compiling the Code</span></span>
 <span data-ttu-id="ea82d-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="ea82d-106">This example requires:</span></span>

- <span data-ttu-id="ea82d-107">que vous remplaciez le nom de fichier `"c:\Windows\Media\chimes.wav"` par un nom de fichier valide.</span><span class="sxs-lookup"><span data-stu-id="ea82d-107">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>

- <span data-ttu-id="ea82d-108">(C#) Référence à l' <xref:System.Media?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ea82d-108">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="ea82d-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="ea82d-109">Robust Programming</span></span>
 <span data-ttu-id="ea82d-110">Les opérations de fichiers doivent être placées dans des blocs de gestion des exceptions structurés appropriés.</span><span class="sxs-lookup"><span data-stu-id="ea82d-110">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>

 <span data-ttu-id="ea82d-111">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="ea82d-111">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="ea82d-112">Le chemin d'accès est mal formé.</span><span class="sxs-lookup"><span data-stu-id="ea82d-112">The path name is malformed.</span></span> <span data-ttu-id="ea82d-113">Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (classe <xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="ea82d-113">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>

- <span data-ttu-id="ea82d-114">Le chemin d'accès est en lecture seule (classe <xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ea82d-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>

- <span data-ttu-id="ea82d-115">Le nom du chemin d'accès est `null` (classe <xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="ea82d-115">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>

- <span data-ttu-id="ea82d-116">Le nom du chemin d'accès est trop long (classe <xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="ea82d-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>

- <span data-ttu-id="ea82d-117">Le chemin d'accès n'est pas valide (classe <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="ea82d-117">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>

- <span data-ttu-id="ea82d-118">Le chemin d’accès est uniquement un signe deux-points<xref:System.NotSupportedException> , «:» (classe).</span><span class="sxs-lookup"><span data-stu-id="ea82d-118">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="ea82d-119">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ea82d-119">.NET Framework Security</span></span>
 <span data-ttu-id="ea82d-120">Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu.</span><span class="sxs-lookup"><span data-stu-id="ea82d-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="ea82d-121">Par exemple, le fichier `Form1.vb` peut ne pas être un fichier source Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ea82d-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="ea82d-122">Vérifiez toutes les entrées avant d'utiliser les données dans votre application.</span><span class="sxs-lookup"><span data-stu-id="ea82d-122">Verify all inputs before using the data in your application.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea82d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea82d-123">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="ea82d-124">Guide pratique : Charger un son de façon asynchrone dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="ea82d-124">How to: Load a Sound Asynchronously within a Windows Form</span></span>](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
