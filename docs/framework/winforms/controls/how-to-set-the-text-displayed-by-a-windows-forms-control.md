---
title: Définir le texte affiché par un contrôle
description: Découvrez comment définir le texte affiché par un contrôle Windows Forms. Définissez ou retournez le texte à l’aide de la propriété Text ou modifiez la police à l’aide de la propriété font.
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: 35bae5830bfee8ab91f7b6c7b9dcc6d6b8db00ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622846"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="a8d66-104">Comment : définir le texte affiché par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8d66-104">How to: Set the text displayed by a Windows Forms control</span></span>

<span data-ttu-id="a8d66-105">Les contrôles Windows Forms affichent généralement du texte lié à la fonction principale du contrôle.</span><span class="sxs-lookup"><span data-stu-id="a8d66-105">Windows Forms controls usually display some text that's related to the primary function of the control.</span></span> <span data-ttu-id="a8d66-106">Par exemple, un <xref:System.Windows.Forms.Button> contrôle affiche généralement une légende qui indique l’action qui sera exécutée si l’utilisateur clique sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="a8d66-106">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed if the button is clicked.</span></span> <span data-ttu-id="a8d66-107">Pour tous les contrôles, vous pouvez définir ou retourner le texte à l'aide de la propriété <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8d66-107">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="a8d66-108">Vous pouvez modifier la police en utilisant la propriété <xref:System.Windows.Forms.Control.Font%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8d66-108">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>

<span data-ttu-id="a8d66-109">Vous pouvez également définir le texte à l’aide du [Concepteur](#designer).</span><span class="sxs-lookup"><span data-stu-id="a8d66-109">You can also set the text by using the [designer](#designer).</span></span>

## <a name="programmatic"></a><span data-ttu-id="a8d66-110">Par programme</span><span class="sxs-lookup"><span data-stu-id="a8d66-110">Programmatic</span></span>

1. <span data-ttu-id="a8d66-111">Affectez une chaîne comme valeur de la propriété <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8d66-111">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>

   <span data-ttu-id="a8d66-112">Pour créer une clé d’accès soulignée, incluez une esperluette (&) avant la lettre qui sera la touche d’accès.</span><span class="sxs-lookup"><span data-stu-id="a8d66-112">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>

2. <span data-ttu-id="a8d66-113">Affectez un objet de type <xref:System.Drawing.Font> comme valeur de la propriété <xref:System.Windows.Forms.Control.Font%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8d66-113">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>

    ```vb
    Button1.Text = "Click here to save changes"
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)
    ```

    ```csharp
    button1.Text = "Click here to save changes";
    button1.Font = new Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point);
    ```

    ```cpp
    button1->Text = "Click here to save changes";
    button1->Font = new System::Drawing::Font("Arial", 10, FontStyle::Bold, GraphicsUnit::Point);
    ```

    > [!NOTE]
    > <span data-ttu-id="a8d66-114">Vous pouvez utiliser un caractère d'échappement pour afficher un caractère spécial dans des éléments d'interface utilisateur qui l'interpréteraient normalement différemment, tels que des éléments de menu.</span><span class="sxs-lookup"><span data-stu-id="a8d66-114">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="a8d66-115">Par exemple, la ligne de code suivante définit le texte de l’élément de menu pour qu’il Lise « & Now pour un élément totalement différent » :</span><span class="sxs-lookup"><span data-stu-id="a8d66-115">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a><span data-ttu-id="a8d66-116">Concepteur</span><span class="sxs-lookup"><span data-stu-id="a8d66-116">Designer</span></span>

1. <span data-ttu-id="a8d66-117">Dans la fenêtre **Propriétés** de Visual Studio, définissez la propriété **Text** du contrôle sur une chaîne appropriée.</span><span class="sxs-lookup"><span data-stu-id="a8d66-117">In the **Properties** window in Visual Studio, set the **Text** property of the control to an appropriate string.</span></span>

   <span data-ttu-id="a8d66-118">Pour créer une touche de raccourci soulignée, incluez une esperluette (&) avant la lettre qui sera la touche de raccourci.</span><span class="sxs-lookup"><span data-stu-id="a8d66-118">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>

2. <span data-ttu-id="a8d66-119">Dans la fenêtre **Propriétés** , sélectionnez le bouton de sélection ( ![ bouton de sélection (...) dans le fenêtre Propriétés de Visual Studio ](./media/visual-studio-ellipsis-button.png) ) en regard de la propriété **font** .</span><span class="sxs-lookup"><span data-stu-id="a8d66-119">In the **Properties** window, select the ellipsis button (![Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) next to the **Font** property.</span></span>

   <span data-ttu-id="a8d66-120">Dans la boîte de dialogue police standard, sélectionnez la police, le style de police, la taille, les effets (tels que le barré ou le soulignement) et le script souhaité.</span><span class="sxs-lookup"><span data-stu-id="a8d66-120">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8d66-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8d66-121">See also</span></span>

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a8d66-122">Guide pratique pour créer des touches d'accès rapide pour des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8d66-122">How to: Create Access Keys for Windows Forms Controls</span></span>](how-to-create-access-keys-for-windows-forms-controls.md)
- [<span data-ttu-id="a8d66-123">Comment : répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8d66-123">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
