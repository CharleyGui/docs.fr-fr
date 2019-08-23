---
title: 'Procédure : Configurer Visual Studio pour déboguer une application de navigateur XAML et appeler un service web'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: e41dd46e4ddbdcde6448c68b4f9fb2e073baca43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958684"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Procédure : Configurer Visual Studio pour déboguer une application de navigateur XAML et appeler un service web
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]Exécutez dans un bac à sable (sandbox) de sécurité de confiance partielle qui est limité au jeu d’autorisations de la zone Internet. Ce jeu d’autorisations restreint les appels de service Web aux seuls services Web situés sur le site [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] d’origine de l’application. Toutefois, [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] lorsqu’un est débogué à partir de Visual Studio 2005, il n’est pas considéré comme ayant le même site d’origine que le service Web auquel il fait référence. Cela entraîne le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] déclenchement d’exceptions de sécurité lorsque tente d’appeler le service Web. Toutefois, un projet Visual Studio [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] 2005 peut être configuré pour simuler le même site d’origine que le service Web qu’il appelle pendant le débogage. Cela permet [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] à d’appeler en toute sécurité le service Web sans provoquer d’exceptions de sécurité.

## <a name="configuring-visual-studio"></a>Configuration de Visual Studio
 Pour configurer Visual Studio 2005 afin de déboguer un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] qui appelle un service Web:

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Dans le **Concepteur de projets**, cliquez sur l’onglet Déboguer.

3. Dans la section **action de démarrage** , sélectionnez Démarrer le **programme externe** , puis entrez les informations suivantes:

     `C:\WINDOWS\System32\PresentationHost.exe`

4. Dans la section **options de démarrage** , entrez ce qui suit dans la zone de texte arguments de ligne de **commande** :

     `-debug`  *filename*

     La valeur de *nom de fichier* pour le paramètre **-Debug** est le nom de fichier. XBAP; par exemple:

     `-debug c:\example.xbap`

> [!NOTE]
> Il s’agit de la configuration par défaut pour les solutions créées avec le modèle [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] de projet Visual Studio 2005.

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Dans le **Concepteur de projets**, cliquez sur l’onglet Déboguer.

3. Dans la section **options de démarrage** , ajoutez le paramètre de ligne de commande suivant à la zone de texte arguments de ligne de **commande** :

     `-debugSecurityZoneURL`  *URL*

     La valeur de l' *URL* pour le paramètre **-DebugSecurityZoneURL** est le [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] pour l’emplacement que vous souhaitez simuler comme étant le site d’origine de votre application.

 Par exemple, imaginez un [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] qui utilise un service Web avec les éléments suivants: [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 Le site d’origine [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] pour ce service Web est le suivant:

 `http://services.msdn.microsoft.com`

 Par conséquent, le paramètre de ligne de commande Complete **-DebugSecurityZoneURL** et la valeur est:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Voir aussi

- [Hôte WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
