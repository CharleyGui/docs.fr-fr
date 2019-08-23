---
title: 'Procédure : définir des retraits, des retraits négatifs et des paragraphes à puces avec le contrôle RichTextBox Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
ms.openlocfilehash: 9d095e3561cd346e6dbd99d1be7468f6ad5725a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960455"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="18f49-102">Procédure : définir des retraits, des retraits négatifs et des paragraphes à puces avec le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18f49-102">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="18f49-103">Le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms possède de nombreuses options de mise en forme du texte qu’il affiche.</span><span class="sxs-lookup"><span data-stu-id="18f49-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="18f49-104">Vous pouvez mettre en forme les paragraphes sélectionnés en tant que listes <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> à puces en définissant la propriété.</span><span class="sxs-lookup"><span data-stu-id="18f49-104">You can format selected paragraphs as bulleted lists by setting the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="18f49-105">Vous pouvez également utiliser les <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>propriétés <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, et <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> pour définir la mise en retrait des paragraphes par rapport aux bords gauche et droit du contrôle et le bord gauche des autres lignes de texte.</span><span class="sxs-lookup"><span data-stu-id="18f49-105">You can also use the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, and <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> properties to set the indentation of paragraphs relative to the left and right edges of the control, and the left edge of other lines of text.</span></span>  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a><span data-ttu-id="18f49-106">Pour mettre en forme un paragraphe sous forme de liste à puces</span><span class="sxs-lookup"><span data-stu-id="18f49-106">To format a paragraph as a bulleted list</span></span>  
  
1. <span data-ttu-id="18f49-107">Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="18f49-107">Set the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property to `true`.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a><span data-ttu-id="18f49-108">Pour mettre en retrait un paragraphe</span><span class="sxs-lookup"><span data-stu-id="18f49-108">To indent a paragraph</span></span>  
  
1. <span data-ttu-id="18f49-109">Affectez <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> à la propriété un entier représentant la distance en pixels entre le bord gauche du contrôle et le bord gauche du texte.</span><span class="sxs-lookup"><span data-stu-id="18f49-109">Set the <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> property to an integer representing the distance in pixels between the left edge of the control and the left edge of the text.</span></span>  
  
2. <span data-ttu-id="18f49-110">Affectez <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> à la propriété un entier représentant la distance en pixels entre le bord gauche de la première ligne de texte dans le paragraphe et le bord gauche des lignes suivantes dans le même paragraphe.</span><span class="sxs-lookup"><span data-stu-id="18f49-110">Set the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property to an integer representing the distance in pixels between the left edge of the first line of text in the paragraph and the left edge of subsequent lines in the same paragraph.</span></span> <span data-ttu-id="18f49-111">La valeur de la <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> propriété s’applique uniquement aux lignes d’un paragraphe qui sont renvoyées au-dessous de la première ligne.</span><span class="sxs-lookup"><span data-stu-id="18f49-111">The value of the <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> property only applies to lines in a paragraph that have wrapped below the first line.</span></span>  
  
3. <span data-ttu-id="18f49-112">Affectez <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> à la propriété un entier représentant la distance en pixels entre le bord droit du contrôle et le bord droit du texte.</span><span class="sxs-lookup"><span data-stu-id="18f49-112">Set the <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> property to an integer representing the distance in pixels between the right edge of the control and the right edge of the text.</span></span>  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="18f49-113">Toutes ces propriétés affectent tous les paragraphes contenant du texte sélectionné et également le texte tapé après le point d’insertion actif.</span><span class="sxs-lookup"><span data-stu-id="18f49-113">All these properties affect any paragraphs that contain selected text, and also the text that is typed after the current insertion point.</span></span> <span data-ttu-id="18f49-114">Par exemple, quand un utilisateur sélectionne un mot dans un paragraphe puis ajuste le retrait, les nouveaux paramètres s’appliquent à l’ensemble du paragraphe contenant ce mot et également à tous les paragraphes entrés ultérieurement après le paragraphe sélectionné.</span><span class="sxs-lookup"><span data-stu-id="18f49-114">For example, when a user selects a word within a paragraph and then adjusts the indentation, the new settings will apply to the entire paragraph that contains that word, and also to any paragraphs subsequently entered after the selected paragraph.</span></span> <span data-ttu-id="18f49-115">Pour plus d’informations sur la sélection de texte par <xref:System.Windows.Forms.TextBoxBase.Select%2A>programmation, consultez.</span><span class="sxs-lookup"><span data-stu-id="18f49-115">For information about selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18f49-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18f49-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="18f49-117">RichTextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="18f49-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="18f49-118">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18f49-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
