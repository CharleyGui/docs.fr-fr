---
title: 'Procédure : Raccorder une commande à un contrôle sans prise en charge de commande'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
ms.openlocfilehash: 3ae45c9a9e33a3cb53ada6e1e5430ae0f9e6c198
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "71263303"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>Procédure : Raccorder une commande à un contrôle sans prise en charge de commande
L’exemple suivant montre comment raccorder <xref:System.Windows.Input.RoutedCommand> à un <xref:System.Windows.Controls.Control> qui n’a pas de prise en charge intégrée de la commande.  Pour obtenir un exemple complet qui raccorde des commandes à plusieurs sources, consultez l’exemple [Créer un exemple RoutedCommand personnalisé](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="example"></a>Exemple  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit une bibliothèque de commandes courantes que les programmeurs d’applications rencontrent régulièrement.  Les classes qui constituent la bibliothèque de commandes sont : <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands> et <xref:System.Windows.Documents.EditingCommands>.  
  
 Les objets statiques <xref:System.Windows.Input.RoutedCommand> qui composent ces classes ne fournissent pas de logique de commande.  La logique de la commande est associée à la commande avec <xref:System.Windows.Input.CommandBinding>.  De nombreux contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont une prise en charge intégrée de certaines commandes de la bibliothèque de commandes.  <xref:System.Windows.Controls.TextBox>, par exemple, prend en charge de nombreuses commandes d’édition de l’application, par exemple <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A> et <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Le développeur d’application n’a aucune action spéciale à effectuer pour que ces commandes fonctionnent avec ces contrôles.  Si <xref:System.Windows.Controls.TextBox> est la cible de commande au moment de l’exécution de la commande, il gère la commande à l’aide de <xref:System.Windows.Input.CommandBinding>, qui est intégré au contrôle.  
  
 L’exemple suivant montre comment utiliser <xref:System.Windows.Controls.Button> en tant que source de commande pour la commande <xref:System.Windows.Input.ApplicationCommands.Open%2A>.  Un <xref:System.Windows.Input.CommandBinding> est créé pour associer le <xref:System.Windows.Input.CanExecuteRoutedEventHandler> spécifié et <xref:System.Windows.Input.CanExecuteRoutedEventHandler> à <xref:System.Windows.Input.RoutedCommand>.  
  
 Tout d’abord, la source de commande est créée.  <xref:System.Windows.Controls.Button> est utilisé comme source de commande.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 <xref:System.Windows.Input.ExecutedRoutedEventHandler> et <xref:System.Windows.Input.CanExecuteRoutedEventHandler> sont ensuite créés.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> ouvre simplement <xref:System.Windows.MessageBox> pour indiquer que la commande a été exécutée.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> affecte à la propriété <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> la valeur `true`.  Normalement, le gestionnaire d’exécution effectue des vérifications plus robustes pour déterminer si la commande peut s’exécuter sur la cible de commande actuelle.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 Enfin, <xref:System.Windows.Input.CommandBinding> est créé à la racine <xref:System.Windows.Window> de l’application qui associe les gestionnaires d’événements routés à la commande <xref:System.Windows.Input.ApplicationCommands.Open%2A>.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des commandes](commanding-overview.md)
- [Raccorder une commande à un contrôle avec prise en charge de commande](how-to-hook-up-a-command-to-a-control-with-command-support.md)
