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
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Comment : créer une visionneuse de documents HTML dans une application Windows Forms
Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.WebBrowser> pour afficher et imprimer des documents HTML sans fournir toutes les fonctionnalités d’un navigateur Web Internet. Cela est utile lorsque vous souhaitez tirer parti des fonctionnalités de mise en forme du HTML, mais ne souhaitez pas que vos utilisateurs chargent des pages Web arbitraires qui peuvent contenir des contrôles Web non fiables ou du code de script potentiellement malveillant. Vous souhaiterez peut-être limiter la capacité du contrôle <xref:System.Windows.Forms.WebBrowser> de cette manière, par exemple, pour l’utiliser en tant qu’afficheur de messages HTML ou pour fournir une aide au format HTML dans votre application.  
  
### <a name="to-create-an-html-document-viewer"></a>Pour créer une visionneuse de documents HTML  
  
1. Affectez à la propriété <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> la valeur `false` pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> d’ouvrir les fichiers déposés sur celui-ci.  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2. Affectez à la propriété <xref:System.Windows.Forms.WebBrowser.Url%2A> l’emplacement du fichier initial à afficher.  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- un contrôle <xref:System.Windows.Forms.WebBrowser> nommé `webBrowser1` ;  
  
- des références aux assemblys `System` et `System.Windows.Forms`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [Vue d’ensemble du contrôle WebBrowser](webbrowser-control-overview.md)
- [Sécurité WebBrowser](webbrowser-security.md)
- [Guide pratique pour naviguer vers une URL avec un contrôle WebBrowser](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Guide pratique pour imprimer avec un contrôle WebBrowser](how-to-print-with-a-webbrowser-control.md)
