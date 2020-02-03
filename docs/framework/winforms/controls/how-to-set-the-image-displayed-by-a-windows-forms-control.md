---
title: Définir l’image affichée par un contrôle
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 5df0068c8462bbaab0cb0135de1dd1b91ababe06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746871"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="e4777-102">Comment : définir l’image affichée par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e4777-102">How to: Set the image displayed by a Windows Forms control</span></span>

<span data-ttu-id="e4777-103">Plusieurs contrôles de Windows Forms peuvent afficher des images.</span><span class="sxs-lookup"><span data-stu-id="e4777-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="e4777-104">Ces images peuvent être des icônes qui clarifient l’objectif du contrôle, par exemple une icône de disquette sur un bouton indiquant la commande Enregistrer.</span><span class="sxs-lookup"><span data-stu-id="e4777-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the Save command.</span></span> <span data-ttu-id="e4777-105">Les icônes peuvent également être des images d’arrière-plan pour que le contrôle donne l’apparence et le comportement souhaités.</span><span class="sxs-lookup"><span data-stu-id="e4777-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>

## <a name="programmatic"></a><span data-ttu-id="e4777-106">Par programme</span><span class="sxs-lookup"><span data-stu-id="e4777-106">Programmatic</span></span>

<span data-ttu-id="e4777-107">Définissez la propriété `Image` ou `BackgroundImage` du contrôle sur un objet de type <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="e4777-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="e4777-108">En règle générale, vous chargez l’image à partir d’un fichier à l’aide de la méthode <xref:System.Drawing.Image.FromFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4777-108">Generally, you'll be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>

<span data-ttu-id="e4777-109">Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est le dossier **Mes images** .</span><span class="sxs-lookup"><span data-stu-id="e4777-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="e4777-110">La plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="e4777-110">Most computers running the Windows operating system include this directory.</span></span> <span data-ttu-id="e4777-111">Cela permet également aux utilisateurs disposant de niveaux d’accès système minimaux d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="e4777-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="e4777-112">L’exemple de code suivant nécessite que vous disposiez déjà d’un formulaire avec un contrôle <xref:System.Windows.Forms.PictureBox> ajouté.</span><span class="sxs-lookup"><span data-stu-id="e4777-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>

```vb
' Replace the image named below with your own icon.
PictureBox1.Image = Image.FromFile _
   (System.Environment.GetFolderPath _
   (System.Environment.SpecialFolder.MyPictures) _
   & "\Image.gif")
```

```csharp
// Replace the image named below with your own icon.
// Note the escape character used (@) when specifying the path.
pictureBox1.Image = Image.FromFile
   (System.Environment.GetFolderPath
   (System.Environment.SpecialFolder.MyPictures)
   + @"\Image.gif");
```

```cpp
// Replace the image named below with your own icon.
pictureBox1->Image = Image::FromFile(String::Concat
   (System::Environment::GetFolderPath
   (System::Environment::SpecialFolder::MyPictures),
   "\\Image.gif"));
```

## <a name="designer"></a><span data-ttu-id="e4777-113">Designer</span><span class="sxs-lookup"><span data-stu-id="e4777-113">Designer</span></span>

1. <span data-ttu-id="e4777-114">Dans la fenêtre **Propriétés** de Visual Studio, sélectionnez la propriété **image** ou **BackgroundImage** du contrôle, puis sélectionnez les points de suspension (![bouton de sélection dans Visual Studio](./media/visual-studio-ellipsis-button.png)) pour afficher la boîte de dialogue **Sélectionner une ressource** .</span><span class="sxs-lookup"><span data-stu-id="e4777-114">In the **Properties** window of Visual Studio, select the **Image** or **BackgroundImage** property of the control, and then select the ellipsis (![Ellipsis button in Visual Studio](./media/visual-studio-ellipsis-button.png)) to display the **Select Resource** dialog box.</span></span>

2. <span data-ttu-id="e4777-115">Sélectionnez l’image que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="e4777-115">Select the image you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4777-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4777-116">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
