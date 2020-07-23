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
ms.openlocfilehash: 75a4160366766efbd19d6e8ae26fbec102e7f95b
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924498"
---
# <a name="how-to-invoke-a-print-dialog"></a>Comment : appeler une boîte de dialogue Imprimer
Pour offrir la possibilité d’imprimer à partir de votre application, vous pouvez simplement créer et ouvrir un <xref:System.Windows.Controls.PrintDialog> objet.  
  
## <a name="example"></a>Exemple  
 Le <xref:System.Windows.Controls.PrintDialog> contrôle fournit un point d’entrée unique pour [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , la configuration et l’envoi d’un travail XPS. Le contrôle est facile à utiliser et peut être instancié à l’aide du [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] balisage ou du code. L’exemple suivant montre comment instancier et ouvrir le contrôle dans le code et comment l’imprimer à partir de celui-ci. Il montre également comment s’assurer que la boîte de dialogue donne à l’utilisateur la possibilité de définir une plage de pages spécifique. L’exemple de code suppose qu’il existe un fichier FixedDocumentSequence. XPS à la racine du lecteur C :.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Une fois que la boîte de dialogue est ouverte, les utilisateurs peuvent choisir parmi les imprimantes installées sur leur ordinateur. Ils auront également la possibilité de sélectionner [Microsoft XPS document Writer](/windows/win32/printdocs/microsoft-xps-document-writer) pour créer un fichier XPS (XML Paper Specification) au lieu d’imprimer.  
  
> [!NOTE]
> Le <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> contrôle de WPF, qui est abordé dans cette rubrique, ne doit pas être confondu avec le <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> composant de Windows Forms.  
  
 Strictement parlant, vous pouvez utiliser la <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> méthode sans jamais ouvrir la boîte de dialogue. Dans ce sens, le contrôle peut être utilisé comme composant d’impression invisible. Toutefois, pour des raisons de performances, il serait préférable d’utiliser la <xref:System.Printing.PrintQueue.AddJob%2A> méthode ou l’une des <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> nombreuses <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> méthodes et de <xref:System.Windows.Xps.XpsDocumentWriter> . Pour plus d’informations à ce sujet, consultez [imprimer des fichiers XPS par programmation](how-to-programmatically-print-xps-files.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.PrintDialog>
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d'ensemble de l'impression](printing-overview.md)
- [Microsoft XPS Document Writer](/windows/win32/printdocs/microsoft-xps-document-writer)
