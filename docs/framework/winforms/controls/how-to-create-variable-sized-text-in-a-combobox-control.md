---
title: 'Procédure : créer du texte de taille variable dans un contrôle ComboBox'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
ms.openlocfilehash: 7c0dc40f6cac0af1f88e72089865caa3a17fcf2a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914748"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a><span data-ttu-id="e766a-102">Procédure : créer du texte de taille variable dans un contrôle ComboBox</span><span class="sxs-lookup"><span data-stu-id="e766a-102">How to: Create Variable Sized Text in a ComboBox Control</span></span>
<span data-ttu-id="e766a-103">Cet exemple illustre un dessin personnalisé de texte dans <xref:System.Windows.Forms.ComboBox> un contrôle.</span><span class="sxs-lookup"><span data-stu-id="e766a-103">This example demonstrates custom drawing of text in a <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="e766a-104">Lorsqu’un élément répond à un certain critère, il est dessiné dans une police plus grande et transformé en rouge.</span><span class="sxs-lookup"><span data-stu-id="e766a-104">When an item meets a certain criteria, it is drawn in a larger font and turned red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e766a-105">Exemples</span><span class="sxs-lookup"><span data-stu-id="e766a-105">Example</span></span>  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e766a-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e766a-106">Compiling the Code</span></span>  
 <span data-ttu-id="e766a-107">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="e766a-107">This example requires:</span></span>  
  
- <span data-ttu-id="e766a-108">Un Windows Form.</span><span class="sxs-lookup"><span data-stu-id="e766a-108">A Windows form.</span></span>  
  
- <span data-ttu-id="e766a-109">Contrôle nommé `ListBox1` avec trois éléments dans la <xref:System.Windows.Forms.ComboBox.Items%2A> propriété. <xref:System.Windows.Forms.ComboBox></span><span class="sxs-lookup"><span data-stu-id="e766a-109">A <xref:System.Windows.Forms.ComboBox> control named `ListBox1` with three items in the <xref:System.Windows.Forms.ComboBox.Items%2A> property.</span></span> <span data-ttu-id="e766a-110">Dans cet exemple, les trois éléments sont nommés `"One", Two", and Three"`.</span><span class="sxs-lookup"><span data-stu-id="e766a-110">In this example, the three items are named `"One", Two", and Three"`.</span></span> <span data-ttu-id="e766a-111">La <xref:System.Windows.Forms.ComboBox.DrawMode%2A> propriété de `ComboBox1` doit avoir la valeur <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.</span><span class="sxs-lookup"><span data-stu-id="e766a-111">The <xref:System.Windows.Forms.ComboBox.DrawMode%2A> property of `ComboBox1` must be set to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e766a-112">Cette technique est également applicable au <xref:System.Windows.Forms.ListBox> contrôle: vous pouvez remplacer un <xref:System.Windows.Forms.ListBox> pour le <xref:System.Windows.Forms.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="e766a-112">This technique is also applicable to the <xref:System.Windows.Forms.ListBox> control — you can substitute a <xref:System.Windows.Forms.ListBox> for the <xref:System.Windows.Forms.ComboBox>.</span></span>  
  
- <span data-ttu-id="e766a-113">Références aux espaces de noms <xref:System.Windows.Forms?displayProperty=nameWithType> et <xref:System.Drawing?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e766a-113">References to the <xref:System.Windows.Forms?displayProperty=nameWithType> and <xref:System.Drawing?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e766a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e766a-114">See also</span></span>

- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [<span data-ttu-id="e766a-115">Contrôles avec prise en charge intégrée du dessin owner-drawn</span><span class="sxs-lookup"><span data-stu-id="e766a-115">Controls with Built-In Owner-Drawing Support</span></span>](controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="e766a-116">ListBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="e766a-116">ListBox Control</span></span>](listbox-control-windows-forms.md)
- [<span data-ttu-id="e766a-117">ComboBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="e766a-117">ComboBox Control</span></span>](combobox-control-windows-forms.md)
