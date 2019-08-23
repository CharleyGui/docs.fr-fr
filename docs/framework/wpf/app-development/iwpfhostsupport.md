---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 994e5146e9cf49a9b31396d0b51e7be83bbb3cfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964786"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Les applications qui [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] hébergent du contenu via PresentationHost. exe implémentent cette interface pour fournir un point d’intégration entre l’hôte et PresentationHost. exe.  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]les applications telles que les navigateurs Web [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] peuvent héberger [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] du contenu, y compris le XAML libre. Pour héberger [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] du [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] contenu, les applications créent une instance du [contrôle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911). Pour être hébergé, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] crée une instance de PresentationHost. exe, qui fournit le contenu [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] hébergé à l’hôte pour qu’il s’affiche dans le [contrôle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).  
  
 L’intégration activée par `IWpfHostSupport` permet à PresentationHost. exe d’effectuer les opérations suivantes:  
  
- Détectez et inscrivez-vous auprès des périphériques d’entrée bruts (périphériques d’interface utilisateur) qui intéressent l’application hôte.  
  
- Recevoir des messages d’entrée des périphériques d’entrée bruts inscrits et transférer les messages appropriés à l’application hôte.  
  
- Interrogez l’application hôte pour obtenir des interfaces utilisateur de progression et d’erreur personnalisées.  
  
> [!NOTE]
> Cette API est conçue et pris en charge uniquement sur l'ordinateur client local  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|Permet à PresentationHost.exe de découvrir les périphériques d'entrée brute (périphériques d'interface utilisateur) qui intéressent l'application hôte.|  
|[FilterInputMessage](filterinputmessage.md)|Appelé par PresentationHost.exe chaque fois qu'un message est reçu, à moins que E_NOTIMPL soit retourné.|  
|[GetCustomUI](getcustomui.md)|Par défaut, PresentationHost. exe fournit ses propres paramètres de progression et d’erreur de déploiement qui sont affichés lorsque le contenu WPF est déployé.|
