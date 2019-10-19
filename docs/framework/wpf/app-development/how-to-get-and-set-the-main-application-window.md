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
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="31474-102">Comment : récupérer et définir la fenêtre principale de l’application</span><span class="sxs-lookup"><span data-stu-id="31474-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="31474-103">Cet exemple montre comment récupérer et définir la fenêtre principale de l’application.</span><span class="sxs-lookup"><span data-stu-id="31474-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31474-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="31474-104">Example</span></span>  
 <span data-ttu-id="31474-105">La première <xref:System.Windows.Window> instanciée dans une application Windows Presentation Foundation (WPF) est automatiquement définie par <xref:System.Windows.Application> en tant que fenêtre d’application principale.</span><span class="sxs-lookup"><span data-stu-id="31474-105">The first <xref:System.Windows.Window> that is instantiated within a Windows Presentation Foundation (WPF) application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="31474-106">La première <xref:System.Windows.Window> à instancier est probablement la fenêtre spécifiée comme URI (Uniform Resource Identifier) de démarrage (consultez <xref:System.Windows.Application.StartupUri%2A>).</span><span class="sxs-lookup"><span data-stu-id="31474-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup uniform resource identifier (URI) (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="31474-107">La première <xref:System.Windows.Window> peut également être instanciée à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="31474-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="31474-108">Par exemple, l’ouverture d’une fenêtre pendant le démarrage de l’application, comme suit :</span><span class="sxs-lookup"><span data-stu-id="31474-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="31474-109">Parfois, la première <xref:System.Windows.Window> instanciée n’est pas en fait la fenêtre d’application principale, par exemple un écran de démarrage.</span><span class="sxs-lookup"><span data-stu-id="31474-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="31474-110">Dans ce cas, vous pouvez spécifier la fenêtre d’application principale à l’aide du balisage, comme suit :</span><span class="sxs-lookup"><span data-stu-id="31474-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="31474-111">Si la fenêtre principale est spécifiée automatiquement ou manuellement, vous pouvez récupérer la fenêtre principale à partir de <xref:System.Windows.Application.MainWindow%2A> à l’aide du code suivant, comme suit :</span><span class="sxs-lookup"><span data-stu-id="31474-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
