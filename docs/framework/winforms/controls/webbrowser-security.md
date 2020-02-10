---
title: Sécurité WebBrowser
ms.date: 03/30/2017
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
ms.openlocfilehash: b25cabca050d06dbfe97c563eb56622d1f21be54
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095253"
---
# <a name="webbrowser-security"></a><span data-ttu-id="ba7d4-102">Sécurité WebBrowser</span><span class="sxs-lookup"><span data-stu-id="ba7d4-102">WebBrowser Security</span></span>
<span data-ttu-id="ba7d4-103">Le contrôle <xref:System.Windows.Forms.WebBrowser> est conçu pour fonctionner en mode de confiance totale uniquement.</span><span class="sxs-lookup"><span data-stu-id="ba7d4-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="ba7d4-104">Le contenu HTML affiché dans le contrôle peut provenir de serveurs Web externes et peut contenir du code non managé sous la forme de scripts ou de contrôles Web.</span><span class="sxs-lookup"><span data-stu-id="ba7d4-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="ba7d4-105">Si vous utilisez le contrôle <xref:System.Windows.Forms.WebBrowser> dans ce cas, le contrôle n’est pas moins sécurisé qu’Internet Explorer, mais le contrôle <xref:System.Windows.Forms.WebBrowser> managé n’empêche pas l’exécution de ce code non managé.</span><span class="sxs-lookup"><span data-stu-id="ba7d4-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="ba7d4-106">Pour plus d’informations sur les problèmes de sécurité liés au contrôle de `WebBrowser` ActiveX sous-jacent, consultez [contrôle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ba7d4-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba7d4-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba7d4-107">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="ba7d4-108">Vue d’ensemble du contrôle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="ba7d4-108">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- <span data-ttu-id="ba7d4-109">[WebBrowser, contrôle](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ba7d4-109">[WebBrowser Control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))</span></span>
