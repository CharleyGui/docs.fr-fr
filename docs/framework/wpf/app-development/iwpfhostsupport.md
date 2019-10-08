---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 85309e46403b2f22f9afb760d4c4ae370c39246b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004092"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Les applications qui hébergent du contenu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] via PresentationHost. exe implémentent cette interface pour fournir un point d’intégration entre l’hôte et PresentationHost. exe.  
  
## <a name="remarks"></a>Notes  
 les applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], telles que les navigateurs Web, peuvent héberger du contenu WPF, y compris [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] et du code XAML libre. Pour héberger du contenu WPF, les applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] créent une instance du [contrôle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911). Pour être hébergé, WPF crée une instance de PresentationHost. exe, qui fournit le contenu WPF hébergé à l’hôte en vue de son affichage dans le [contrôle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).  
  
 L’intégration activée par `IWpfHostSupport` permet à PresentationHost. exe d’effectuer les opérations suivantes :  
  
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
