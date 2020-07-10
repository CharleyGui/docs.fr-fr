---
title: 'Comment : imprimer un Windows Form'
description: Découvrez comment imprimer par programmation une copie du Windows Form actuel à l’aide de la méthode CopyFromScreen.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: b59ea4b5347903b36a166c4f8ac0d8d7db18635e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174690"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="794a3-103">Comment : imprimer un Windows Form</span><span class="sxs-lookup"><span data-stu-id="794a3-103">How to: Print a Windows Form</span></span>
<span data-ttu-id="794a3-104">Dans le cadre du processus de développement, vous voudrez généralement imprimer une copie de votre Windows Form.</span><span class="sxs-lookup"><span data-stu-id="794a3-104">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="794a3-105">L’exemple de code suivant montre comment imprimer une copie du formulaire actuel à l’aide de la <xref:System.Drawing.Graphics.CopyFromScreen%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="794a3-105">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="794a3-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="794a3-106">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="794a3-107">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="794a3-107">Robust Programming</span></span>  
 <span data-ttu-id="794a3-108">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="794a3-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="794a3-109">Vous n’êtes pas autorisé à accéder à l’imprimante.</span><span class="sxs-lookup"><span data-stu-id="794a3-109">You do not have permission to access the printer.</span></span>  
  
- <span data-ttu-id="794a3-110">Aucune imprimante n’est installée.</span><span class="sxs-lookup"><span data-stu-id="794a3-110">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="794a3-111">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="794a3-111">.NET Framework Security</span></span>  
 <span data-ttu-id="794a3-112">Pour exécuter cet exemple de code, vous devez avoir l’autorisation d’accéder à l’imprimante que vous utilisez avec votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="794a3-112">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="794a3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="794a3-113">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="794a3-114">Guide pratique pour rendre des images avec GDI+</span><span class="sxs-lookup"><span data-stu-id="794a3-114">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="794a3-115">Comment : imprimer des graphiques dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="794a3-115">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)
