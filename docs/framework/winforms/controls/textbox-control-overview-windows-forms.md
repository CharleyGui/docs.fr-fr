---
title: Vue d'ensemble du contrôle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
ms.openlocfilehash: 06ab460d720d17331881b5ba653263160eaf3cb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742809"
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="4c26c-102">Vue d'ensemble du contrôle TextBox (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4c26c-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="4c26c-103">Les zones de texte Windows Forms sont utilisées pour obtenir l’entrée de l’utilisateur ou pour afficher du texte.</span><span class="sxs-lookup"><span data-stu-id="4c26c-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="4c26c-104">Le contrôle <xref:System.Windows.Forms.TextBox> est généralement utilisé pour le texte modifiable, bien qu’il puisse également être mis en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="4c26c-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="4c26c-105">Les zones de texte peuvent afficher plusieurs lignes, ajuster le texte à la taille du contrôle et ajouter une mise en forme de base.</span><span class="sxs-lookup"><span data-stu-id="4c26c-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="4c26c-106">Le contrôle <xref:System.Windows.Forms.TextBox> fournit un style de mise en forme unique pour le texte affiché ou entré dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="4c26c-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="4c26c-107">Pour afficher plusieurs types de texte mis en forme, utilisez le contrôle <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="4c26c-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="4c26c-108">Pour plus d’informations, consultez [vue d’ensemble du contrôle RichTextBox](richtextbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4c26c-108">For more information, see [RichTextBox Control Overview](richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="4c26c-109">Utilisation du contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="4c26c-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="4c26c-110">Le texte affiché par le contrôle est contenu dans la propriété <xref:System.Windows.Forms.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c26c-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="4c26c-111">Par défaut, vous pouvez entrer jusqu’à 2048 caractères dans une zone de texte.</span><span class="sxs-lookup"><span data-stu-id="4c26c-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="4c26c-112">Si vous affectez à la propriété <xref:System.Windows.Forms.TextBox.Multiline%2A> la valeur `true`, vous pouvez entrer jusqu’à 32 Ko de texte.</span><span class="sxs-lookup"><span data-stu-id="4c26c-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="4c26c-113">La propriété <xref:System.Windows.Forms.TextBox.Text%2A> peut être définie au moment du design à l’aide de la fenêtre Propriétés, au moment de l’exécution dans le code ou par l’entrée d’utilisateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4c26c-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="4c26c-114">Le contenu actuel d’une zone de texte peut être récupéré au moment de l’exécution en lisant la propriété <xref:System.Windows.Forms.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c26c-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="4c26c-115">L’exemple de code suivant définit le texte dans le contrôle au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4c26c-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="4c26c-116">La procédure `InitializeMyControl` ne s’exécute pas automatiquement ; elle doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="4c26c-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c26c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c26c-117">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="4c26c-118">Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4c26c-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="4c26c-119">Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4c26c-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="4c26c-120">Guide pratique pour créer une zone de texte en lecture seule</span><span class="sxs-lookup"><span data-stu-id="4c26c-120">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="4c26c-121">Guide pratique pour insérer des guillemets dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="4c26c-121">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="4c26c-122">Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4c26c-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="4c26c-123">Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4c26c-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="4c26c-124">TextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="4c26c-124">TextBox Control</span></span>](textbox-control-windows-forms.md)
