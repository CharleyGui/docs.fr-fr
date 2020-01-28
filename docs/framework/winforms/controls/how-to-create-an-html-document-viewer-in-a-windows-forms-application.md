---
title: Créer une visionneuse de documents HTML dans une application Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 913bc86af034645b4b8cf3d69da4c9def58fc19c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732849"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="9bd54-102">Comment : créer une visionneuse de documents HTML dans une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9bd54-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="9bd54-103">Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.WebBrowser> pour afficher et imprimer des documents HTML sans fournir toutes les fonctionnalités d’un navigateur Web Internet.</span><span class="sxs-lookup"><span data-stu-id="9bd54-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="9bd54-104">Cela est utile lorsque vous souhaitez tirer parti des fonctionnalités de mise en forme du HTML, mais ne souhaitez pas que vos utilisateurs chargent des pages Web arbitraires qui peuvent contenir des contrôles Web non fiables ou du code de script potentiellement malveillant.</span><span class="sxs-lookup"><span data-stu-id="9bd54-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="9bd54-105">Vous souhaiterez peut-être limiter la capacité du contrôle <xref:System.Windows.Forms.WebBrowser> de cette manière, par exemple, pour l’utiliser en tant qu’afficheur de messages HTML ou pour fournir une aide au format HTML dans votre application.</span><span class="sxs-lookup"><span data-stu-id="9bd54-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML email viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="9bd54-106">Pour créer une visionneuse de documents HTML</span><span class="sxs-lookup"><span data-stu-id="9bd54-106">To create an HTML document viewer</span></span>  
  
1. <span data-ttu-id="9bd54-107">Affectez à la propriété <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> la valeur `false` pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> d’ouvrir les fichiers déposés sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="9bd54-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2. <span data-ttu-id="9bd54-108">Affectez à la propriété <xref:System.Windows.Forms.WebBrowser.Url%2A> l’emplacement du fichier initial à afficher.</span><span class="sxs-lookup"><span data-stu-id="9bd54-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9bd54-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="9bd54-109">Compiling the Code</span></span>  
 <span data-ttu-id="9bd54-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="9bd54-110">This example requires:</span></span>  
  
- <span data-ttu-id="9bd54-111">un contrôle <xref:System.Windows.Forms.WebBrowser> nommé `webBrowser1` ;</span><span class="sxs-lookup"><span data-stu-id="9bd54-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
- <span data-ttu-id="9bd54-112">des références aux assemblys `System` et `System.Windows.Forms`.</span><span class="sxs-lookup"><span data-stu-id="9bd54-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd54-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bd54-113">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [<span data-ttu-id="9bd54-114">Vue d’ensemble du contrôle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="9bd54-114">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- [<span data-ttu-id="9bd54-115">Sécurité WebBrowser</span><span class="sxs-lookup"><span data-stu-id="9bd54-115">WebBrowser Security</span></span>](webbrowser-security.md)
- [<span data-ttu-id="9bd54-116">Guide pratique pour naviguer vers une URL avec un contrôle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="9bd54-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [<span data-ttu-id="9bd54-117">Guide pratique pour imprimer avec un contrôle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="9bd54-117">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
