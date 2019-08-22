---
title: 'Procédure : définir l’image affichée par un contrôle Windows Forms'
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
ms.openlocfilehash: b1b1dbbb50c3b19cf8d8a7d7030d0bc168afb6a7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666186"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="19d12-102">Procédure : Définir l’image affichée par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19d12-102">How to: Set the image displayed by a Windows Forms control</span></span>

<span data-ttu-id="19d12-103">Plusieurs contrôles de Windows Forms peuvent afficher des images.</span><span class="sxs-lookup"><span data-stu-id="19d12-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="19d12-104">Ces images peuvent être des icônes qui clarifient l’objectif du contrôle, par exemple une icône de disquette sur un bouton indiquant la commande Enregistrer.</span><span class="sxs-lookup"><span data-stu-id="19d12-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the Save command.</span></span> <span data-ttu-id="19d12-105">Les icônes peuvent également être des images d’arrière-plan pour que le contrôle donne l’apparence et le comportement souhaités.</span><span class="sxs-lookup"><span data-stu-id="19d12-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>

## <a name="programmatic"></a><span data-ttu-id="19d12-106">Par programme</span><span class="sxs-lookup"><span data-stu-id="19d12-106">Programmatic</span></span>

<span data-ttu-id="19d12-107">Affectez à la `Image` propriété `BackgroundImage` ou au contrôle la valeur d' <xref:System.Drawing.Image>un objet de type.</span><span class="sxs-lookup"><span data-stu-id="19d12-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="19d12-108">En général, vous allez charger l’image à partir d’un fichier à <xref:System.Drawing.Image.FromFile%2A> l’aide de la méthode.</span><span class="sxs-lookup"><span data-stu-id="19d12-108">Generally, you'll be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>

<span data-ttu-id="19d12-109">Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est le dossier **Mes images** .</span><span class="sxs-lookup"><span data-stu-id="19d12-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="19d12-110">La plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="19d12-110">Most computers running the Windows operating system include this directory.</span></span> <span data-ttu-id="19d12-111">Cela permet également aux utilisateurs disposant de niveaux d’accès système minimaux d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="19d12-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="19d12-112">L’exemple de code suivant nécessite que vous disposiez déjà d’un <xref:System.Windows.Forms.PictureBox> formulaire avec un contrôle ajouté.</span><span class="sxs-lookup"><span data-stu-id="19d12-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>

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

## <a name="designer"></a><span data-ttu-id="19d12-113">Designer</span><span class="sxs-lookup"><span data-stu-id="19d12-113">Designer</span></span>

1. <span data-ttu-id="19d12-114">Dans la fenêtre **Propriétés** de Visual Studio, sélectionnez la **propriété image** ou **BackgroundImage** du contrôle, puis sélectionnez les points de suspension (![bouton de sélection dans Visual](./media/visual-studio-ellipsis-button.png)Studio) pour afficher la **sélection** Boîte de dialogue des ressources.</span><span class="sxs-lookup"><span data-stu-id="19d12-114">In the **Properties** window of Visual Studio, select the **Image** or **BackgroundImage** property of the control, and then select the ellipsis (![Ellipsis button in Visual Studio](./media/visual-studio-ellipsis-button.png)) to display the **Select Resource** dialog box.</span></span>

2. <span data-ttu-id="19d12-115">Sélectionnez l’image que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="19d12-115">Select the image you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="19d12-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19d12-116">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
