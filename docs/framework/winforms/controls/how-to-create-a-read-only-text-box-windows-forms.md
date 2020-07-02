---
title: 'Comment : créer une zone de texte en lecture seule'
description: En savoir plus sur la transformation d’une zone de texte modifiable Windows Forms en une zone de texte Windows Forms en lecture seule.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 5baa7c66d5f16560a4ea23861d563b099592957f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619362"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="30cf7-103">Comment : créer une zone de texte en lecture seule (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="30cf7-103">How to: Create a Read-Only Text Box (Windows Forms)</span></span>

<span data-ttu-id="30cf7-104">Vous pouvez transformer une zone de texte modifiable Windows Forms en contrôle en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="30cf7-104">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="30cf7-105">Par exemple, la zone de texte peut afficher une valeur qui est généralement modifiée, mais peut ne pas l’être actuellement, en raison de l’état de l’application.</span><span class="sxs-lookup"><span data-stu-id="30cf7-105">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>

## <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="30cf7-106">Pour créer une zone de texte en lecture seule</span><span class="sxs-lookup"><span data-stu-id="30cf7-106">To create a read-only text box</span></span>

1. <span data-ttu-id="30cf7-107">Affectez <xref:System.Windows.Forms.TextBox> à la propriété du contrôle la valeur <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="30cf7-107">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="30cf7-108">Lorsque la propriété a la valeur `true` , les utilisateurs peuvent toujours faire défiler et mettre en surbrillance du texte dans une zone de texte sans autoriser les modifications.</span><span class="sxs-lookup"><span data-stu-id="30cf7-108">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="30cf7-109">Une commande de **copie** est fonctionnelle dans une zone de texte, contrairement aux commandes **couper** et **coller** .</span><span class="sxs-lookup"><span data-stu-id="30cf7-109">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>

    > [!NOTE]
    > <span data-ttu-id="30cf7-110">La <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriété affecte uniquement l’interaction avec l’utilisateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="30cf7-110">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="30cf7-111">Vous pouvez toujours modifier le contenu de la zone de texte par programmation au moment de l’exécution en modifiant la <xref:System.Windows.Forms.TextBox.Text%2A> propriété de la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="30cf7-111">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>

## <a name="see-also"></a><span data-ttu-id="30cf7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30cf7-112">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="30cf7-113">Vue d'ensemble du contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="30cf7-113">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="30cf7-114">Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30cf7-114">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="30cf7-115">Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30cf7-115">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="30cf7-116">Comment : insérer des guillemets dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="30cf7-116">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="30cf7-117">Comment : sélectionner du texte dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30cf7-117">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="30cf7-118">Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30cf7-118">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="30cf7-119">TextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="30cf7-119">TextBox Control</span></span>](textbox-control-windows-forms.md)
