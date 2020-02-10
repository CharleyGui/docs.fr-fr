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
# <a name="how-to-invoke-a-print-dialog"></a>Comment : appeler une boîte de dialogue Imprimer
Pour permettre l’impression à partir de votre application, vous pouvez simplement créer et ouvrir un objet <xref:System.Windows.Controls.PrintDialog>.  
  
## <a name="example"></a>Exemple  
 Le contrôle <xref:System.Windows.Controls.PrintDialog> fournit un point d’entrée unique pour l’envoi de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], de configuration et d’un travail XPS. Le contrôle est facile à utiliser et peut être instancié à l’aide d' [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] balisage ou du code. L’exemple suivant montre comment instancier et ouvrir le contrôle dans le code et comment l’imprimer à partir de celui-ci. Il montre également comment s’assurer que la boîte de dialogue donne à l’utilisateur la possibilité de définir une plage de pages spécifique. L’exemple de code suppose qu’il existe un fichier FixedDocumentSequence. XPS à la racine du lecteur C :.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Une fois que la boîte de dialogue est ouverte, les utilisateurs peuvent choisir parmi les imprimantes installées sur leur ordinateur. Ils auront également la possibilité de sélectionner [Microsoft XPS document Writer](/windows/win32/printdocs/microsoft-xps-document-writer) pour créer un fichier XPS (XML Paper Specification) au lieu d’imprimer.  
  
> [!NOTE]
> Le contrôle <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> de WPF, qui est abordé dans cette rubrique, ne doit pas être confondu avec le composant <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> de Windows Forms.  
  
 Strictement parlant, vous pouvez utiliser la méthode <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> sans jamais ouvrir la boîte de dialogue. Dans ce sens, le contrôle peut être utilisé comme composant d’impression invisible. Toutefois, pour des raisons de performances, il serait préférable d’utiliser la méthode <xref:System.Printing.PrintQueue.AddJob%2A> ou l’une des nombreuses méthodes <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> et <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> de la <xref:System.Windows.Xps.XpsDocumentWriter>. Pour plus d’informations à ce sujet, consultez [imprimer des fichiers XPS par programmation](how-to-programmatically-print-xps-files.md) et.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.PrintDialog>
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d’ensemble de l’impression](printing-overview.md)
- [Microsoft XPS document Writer](/windows/win32/printdocs/microsoft-xps-document-writer)
