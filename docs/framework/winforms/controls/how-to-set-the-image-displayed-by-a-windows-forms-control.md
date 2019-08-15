---
title: 'Procédure : définir l’image affichée par un contrôle Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: 99bde4fac7b3057358c7e6a8550efdb4cc351eb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037878"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="b4aac-102">Procédure : Définir l’image affichée par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4aac-102">How to: Set the image displayed by a Windows Forms control</span></span>

<span data-ttu-id="b4aac-103">Plusieurs contrôles de Windows Forms peuvent afficher des images.</span><span class="sxs-lookup"><span data-stu-id="b4aac-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="b4aac-104">Ces images peuvent être des icônes qui clarifient l’objectif du contrôle, par exemple une icône de disquette sur un bouton indiquant la commande **Enregistrer** .</span><span class="sxs-lookup"><span data-stu-id="b4aac-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="b4aac-105">Les icônes peuvent également être des images d’arrière-plan pour que le contrôle donne l’apparence et le comportement souhaités.</span><span class="sxs-lookup"><span data-stu-id="b4aac-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>

## <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="b4aac-106">Pour définir l’image affichée par un contrôle</span><span class="sxs-lookup"><span data-stu-id="b4aac-106">To set the image displayed by a control</span></span>

1. <span data-ttu-id="b4aac-107">Affectez à la `Image` propriété `BackgroundImage` ou au contrôle la valeur d' <xref:System.Drawing.Image>un objet de type.</span><span class="sxs-lookup"><span data-stu-id="b4aac-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="b4aac-108">En général, vous allez charger l’image à partir d’un fichier à <xref:System.Drawing.Image.FromFile%2A> l’aide de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b4aac-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>

     <span data-ttu-id="b4aac-109">Dans l’exemple de code suivant, le chemin d’accès défini pour l’emplacement de l’image est le dossier **Mes images** .</span><span class="sxs-lookup"><span data-stu-id="b4aac-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="b4aac-110">La plupart des ordinateurs exécutant le système d’exploitation Windows comporteront ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="b4aac-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="b4aac-111">Cela permet également aux utilisateurs disposant de niveaux d’accès système minimaux d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="b4aac-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="b4aac-112">L’exemple de code suivant nécessite que vous disposiez déjà d’un <xref:System.Windows.Forms.PictureBox> formulaire avec un contrôle ajouté.</span><span class="sxs-lookup"><span data-stu-id="b4aac-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>

    ```vb
    ' Replace the image named below
    ' with an icon of your own choosing.
    PictureBox1.Image = Image.FromFile _
       (System.Environment.GetFolderPath _
       (System.Environment.SpecialFolder.MyPictures) _
       & "\Image.gif")
    ```

    ```csharp
    // Replace the image named below
    // with an icon of your own choosing.
    // Note the escape character used (@) when specifying the path.
    pictureBox1.Image = Image.FromFile
       (System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.MyPictures)
       + @"\Image.gif");
    ```

    ```cpp
    // Replace the image named below
    // with an icon of your own choosing.
    pictureBox1->Image = Image::FromFile(String::Concat
       (System::Environment::GetFolderPath
       (System::Environment::SpecialFolder::MyPictures),
       "\\Image.gif"));
    ```

## <a name="see-also"></a><span data-ttu-id="b4aac-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4aac-113">See also</span></span>

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
