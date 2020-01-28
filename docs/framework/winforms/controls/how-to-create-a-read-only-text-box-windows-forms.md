---
title: 'Comment : créer une zone de texte en lecture seule'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 17ae9524009c687cd62fb315f842e188e120ac68
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731269"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="46656-102">Comment : créer une zone de texte en lecture seule (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="46656-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="46656-103">Vous pouvez transformer une zone de texte modifiable Windows Forms en contrôle en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="46656-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="46656-104">Par exemple, la zone de texte peut afficher une valeur qui est généralement modifiée, mais peut ne pas l’être actuellement, en raison de l’état de l’application.</span><span class="sxs-lookup"><span data-stu-id="46656-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="46656-105">Pour créer une zone de texte en lecture seule</span><span class="sxs-lookup"><span data-stu-id="46656-105">To create a read-only text box</span></span>

1. <span data-ttu-id="46656-106">Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> du contrôle <xref:System.Windows.Forms.TextBox> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="46656-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="46656-107">Lorsque la propriété a la valeur `true`, les utilisateurs peuvent toujours faire défiler le texte et le mettre en surbrillance dans une zone de texte sans autoriser les modifications.</span><span class="sxs-lookup"><span data-stu-id="46656-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="46656-108">Une commande de **copie** est fonctionnelle dans une zone de texte, contrairement aux commandes **couper** et **coller** .</span><span class="sxs-lookup"><span data-stu-id="46656-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="46656-109">La propriété <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> affecte uniquement l’interaction de l’utilisateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="46656-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="46656-110">Vous pouvez toujours modifier le contenu de la zone de texte par programmation au moment de l’exécution en modifiant la propriété <xref:System.Windows.Forms.TextBox.Text%2A> de la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="46656-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="46656-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46656-111">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="46656-112">Vue d’ensemble du contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="46656-112">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="46656-113">Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46656-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="46656-114">Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46656-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="46656-115">Guide pratique pour insérer des guillemets dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="46656-115">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="46656-116">Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46656-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="46656-117">Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46656-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="46656-118">TextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="46656-118">TextBox Control</span></span>](textbox-control-windows-forms.md)
