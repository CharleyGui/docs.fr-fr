---
title: 'Comment : appeler une boîte de dialogue Imprimer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: f7ef3312d876324b44b055d70fd22e3fba075ec6
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095173"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="bdddb-102">Comment : appeler une boîte de dialogue Imprimer</span><span class="sxs-lookup"><span data-stu-id="bdddb-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="bdddb-103">Pour permettre l’impression à partir de votre application, vous pouvez simplement créer et ouvrir un objet <xref:System.Windows.Controls.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="bdddb-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdddb-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="bdddb-104">Example</span></span>  
 <span data-ttu-id="bdddb-105">Le contrôle <xref:System.Windows.Controls.PrintDialog> fournit un point d’entrée unique pour l’envoi de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], de configuration et d’un travail XPS.</span><span class="sxs-lookup"><span data-stu-id="bdddb-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and XPS job submission.</span></span> <span data-ttu-id="bdddb-106">Le contrôle est facile à utiliser et peut être instancié à l’aide d' [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] balisage ou du code.</span><span class="sxs-lookup"><span data-stu-id="bdddb-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="bdddb-107">L’exemple suivant montre comment instancier et ouvrir le contrôle dans le code et comment l’imprimer à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="bdddb-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="bdddb-108">Il montre également comment s’assurer que la boîte de dialogue donne à l’utilisateur la possibilité de définir une plage de pages spécifique.</span><span class="sxs-lookup"><span data-stu-id="bdddb-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="bdddb-109">L’exemple de code suppose qu’il existe un fichier FixedDocumentSequence. XPS à la racine du lecteur C :.</span><span class="sxs-lookup"><span data-stu-id="bdddb-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="bdddb-110">Une fois que la boîte de dialogue est ouverte, les utilisateurs peuvent choisir parmi les imprimantes installées sur leur ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bdddb-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="bdddb-111">Ils auront également la possibilité de sélectionner [Microsoft XPS document Writer](/windows/win32/printdocs/microsoft-xps-document-writer) pour créer un fichier XPS (XML Paper Specification) au lieu d’imprimer.</span><span class="sxs-lookup"><span data-stu-id="bdddb-111">They will also have the option of selecting the [Microsoft XPS Document Writer](/windows/win32/printdocs/microsoft-xps-document-writer) to create an XML Paper Specification (XPS) file instead of printing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdddb-112">Le contrôle <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> de WPF, qui est abordé dans cette rubrique, ne doit pas être confondu avec le composant <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="bdddb-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of WPF, which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="bdddb-113">Strictement parlant, vous pouvez utiliser la méthode <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> sans jamais ouvrir la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="bdddb-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="bdddb-114">Dans ce sens, le contrôle peut être utilisé comme composant d’impression invisible.</span><span class="sxs-lookup"><span data-stu-id="bdddb-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="bdddb-115">Toutefois, pour des raisons de performances, il serait préférable d’utiliser la méthode <xref:System.Printing.PrintQueue.AddJob%2A> ou l’une des nombreuses méthodes <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> et <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> de la <xref:System.Windows.Xps.XpsDocumentWriter>.</span><span class="sxs-lookup"><span data-stu-id="bdddb-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="bdddb-116">Pour plus d’informations à ce sujet, consultez [imprimer des fichiers XPS par programmation](how-to-programmatically-print-xps-files.md) et.</span><span class="sxs-lookup"><span data-stu-id="bdddb-116">For more about this, see [Programmatically Print XPS Files](how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdddb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdddb-117">See also</span></span>

- <xref:System.Windows.Controls.PrintDialog>
- [<span data-ttu-id="bdddb-118">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="bdddb-118">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="bdddb-119">Vue d’ensemble de l’impression</span><span class="sxs-lookup"><span data-stu-id="bdddb-119">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="bdddb-120">Microsoft XPS document Writer</span><span class="sxs-lookup"><span data-stu-id="bdddb-120">Microsoft XPS Document Writer</span></span>](/windows/win32/printdocs/microsoft-xps-document-writer)
