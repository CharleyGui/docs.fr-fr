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
# <a name="webbrowser-security"></a>Sécurité WebBrowser
Le contrôle <xref:System.Windows.Forms.WebBrowser> est conçu pour fonctionner en mode de confiance totale uniquement. Le contenu HTML affiché dans le contrôle peut provenir de serveurs Web externes et peut contenir du code non managé sous la forme de scripts ou de contrôles Web. Si vous utilisez le contrôle <xref:System.Windows.Forms.WebBrowser> dans ce cas, le contrôle n’est pas moins sécurisé qu’Internet Explorer, mais le contrôle <xref:System.Windows.Forms.WebBrowser> managé n’empêche pas l’exécution de ce code non managé.  
  
 Pour plus d’informations sur les problèmes de sécurité liés au contrôle de `WebBrowser` ActiveX sous-jacent, consultez [contrôle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.WebBrowser>
- [Vue d’ensemble du contrôle WebBrowser](webbrowser-control-overview.md)
- [WebBrowser, contrôle](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85))
