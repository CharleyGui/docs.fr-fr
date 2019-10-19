---
title: 'Comment : récupérer et définir la fenêtre principale de l’application'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows objects [WPF], setting
- setting windows objects [WPF]
- windows objects [WPF], getting
- getting windows objects [WPF]
ms.assetid: ec902bc4-4a59-46f5-8ec1-963b46789356
ms.openlocfilehash: 5894761c4b6258cbf90d369a722ffc5abca51885
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582555"
---
# <a name="how-to-get-and-set-the-main-application-window"></a>Comment : récupérer et définir la fenêtre principale de l’application
Cet exemple montre comment récupérer et définir la fenêtre principale de l’application.  
  
## <a name="example"></a>Exemple  
 La première <xref:System.Windows.Window> instanciée dans une application Windows Presentation Foundation (WPF) est automatiquement définie par <xref:System.Windows.Application> en tant que fenêtre d’application principale. La première <xref:System.Windows.Window> à instancier est probablement la fenêtre spécifiée comme URI (Uniform Resource Identifier) de démarrage (consultez <xref:System.Windows.Application.StartupUri%2A>).  
  
 La première <xref:System.Windows.Window> peut également être instanciée à l’aide de code. Par exemple, l’ouverture d’une fenêtre pendant le démarrage de l’application, comme suit :  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 Parfois, la première <xref:System.Windows.Window> instanciée n’est pas en fait la fenêtre d’application principale, par exemple un écran de démarrage. Dans ce cas, vous pouvez spécifier la fenêtre d’application principale à l’aide du balisage, comme suit :  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 Si la fenêtre principale est spécifiée automatiquement ou manuellement, vous pouvez récupérer la fenêtre principale à partir de <xref:System.Windows.Application.MainWindow%2A> à l’aide du code suivant, comme suit :  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
