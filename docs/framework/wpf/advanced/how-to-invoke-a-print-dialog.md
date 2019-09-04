---
title: 'Procédure : Appeler une boîte de dialogue Imprimer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 4bad8158925fea8af529f70f92aad74e2a6bbec0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254113"
---
# <a name="how-to-invoke-a-print-dialog"></a>Procédure : Appeler une boîte de dialogue Imprimer
Pour offrir la possibilité d’imprimer à partir de votre application, vous pouvez simplement créer et <xref:System.Windows.Controls.PrintDialog> ouvrir un objet.  
  
## <a name="example"></a>Exemples  
 Le <xref:System.Windows.Controls.PrintDialog> contrôle fournit un point d’entrée unique [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]pour, la configuration et l’envoi d’un travail XPS. Le contrôle est facile à utiliser et peut être instancié à l’aide [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] du balisage ou du code. L’exemple suivant montre comment instancier et ouvrir le contrôle dans le code et comment l’imprimer à partir de celui-ci. Il montre également comment s’assurer que la boîte de dialogue donne à l’utilisateur la possibilité de définir une plage de pages spécifique. L’exemple de code suppose qu’il existe un fichier FixedDocumentSequence. XPS à la racine du lecteur C :.  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Une fois que la boîte de dialogue est ouverte, les utilisateurs peuvent choisir parmi les imprimantes installées sur leur ordinateur. Ils auront également la possibilité de sélectionner [Microsoft XPS document Writer](https://go.microsoft.com/fwlink/?LinkId=147319) pour créer un fichier XPS (XML Paper Specification) au lieu d’imprimer.  
  
> [!NOTE]
> Le <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> contrôle de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], qui est abordé dans cette rubrique, ne doit pas être confondu avec <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> le composant de Windows Forms.  
  
 Strictement parlant, vous pouvez utiliser la <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> méthode sans jamais ouvrir la boîte de dialogue. Dans ce sens, le contrôle peut être utilisé comme composant d’impression invisible. Toutefois, pour des raisons de performances, il serait préférable d’utiliser <xref:System.Printing.PrintQueue.AddJob%2A> la méthode ou l’une des <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> nombreuses <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> méthodes et de <xref:System.Windows.Xps.XpsDocumentWriter>. Pour plus d’informations à ce sujet, consultez [imprimer des fichiers XPS par programmation](how-to-programmatically-print-xps-files.md) et.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.PrintDialog>
- [Documents dans WPF](documents-in-wpf.md)
- [Vue d’ensemble de l’impression](printing-overview.md)
- [Microsoft XPS document Writer](https://go.microsoft.com/fwlink/?LinkId=147319)
