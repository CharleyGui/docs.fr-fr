---
title: 'Comment : configurer Visual Studio pour déboguer une application de navigateur XAML et appeler un service Web'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: d8cfae2fb47876d578c51e5f4acdfe0c31e752fe
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460909"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Comment : configurer Visual Studio pour déboguer une application de navigateur XAML et appeler un service Web
Les applications de navigateur XAML (XBAP) s’exécutent dans un bac à sable (sandbox) de sécurité de confiance partielle qui est limité au jeu d’autorisations de la zone Internet. Ce jeu d’autorisations restreint les appels de service Web aux seuls services Web situés sur le site d’origine de l’application XBAP. Toutefois, lorsqu’un XBAP est débogué à partir de Visual Studio 2005, il n’est pas considéré comme ayant le même site d’origine que le service Web auquel il fait référence. Cela entraîne le déclenchement d’exceptions de sécurité lorsque l’application XBAP tente d’appeler le service Web. Toutefois, un projet d’application de navigateur XAML (WPF) Visual Studio 2005 peut être configuré pour simuler le même site d’origine que le service Web qu’il appelle pendant le débogage. Cela permet à l’application XBAP d’appeler sans risque le service Web sans provoquer d’exceptions de sécurité.

## <a name="configuring-visual-studio"></a>Configuration de Visual Studio
 Pour configurer Visual Studio 2005 afin de déboguer une application XBAP qui appelle un service Web :

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Dans le **Concepteur de projets**, cliquez sur l’onglet **Déboguer** .

3. Dans la section **action de démarrage** , sélectionnez Démarrer le **programme externe** , puis entrez les informations suivantes :

     `C:\WINDOWS\System32\PresentationHost.exe`

4. Dans la section **options de démarrage** , entrez ce qui suit dans la zone de texte arguments de ligne de **commande** :

     `-debug`  *nom de fichier*

     La valeur de *nom de fichier* pour le paramètre **-Debug** est le nom de fichier. XBAP ; par exemple :

     `-debug c:\example.xbap`

> [!NOTE]
> Il s’agit de la configuration par défaut pour les solutions créées avec le modèle de projet d’application de navigateur XAML (WPF) Visual Studio 2005.

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Dans le **Concepteur de projets**, cliquez sur l’onglet **Déboguer** .

3. Dans la section **options de démarrage** , ajoutez le paramètre de ligne de commande suivant à la zone de texte arguments de ligne de **commande** :

     `-debugSecurityZoneURL`  *URL*

     La valeur de l' *URL* pour le paramètre **-DEBUGSECURITYZONEURL** est l’URL de l’emplacement que vous souhaitez simuler comme étant le site d’origine de votre application.

 Par exemple, considérez une application de navigateur XAML (XBAP) qui utilise un service Web avec l’URL suivante :

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 L’URL du site d’origine pour ce service Web est la suivante :

 `http://services.msdn.microsoft.com`

 Par conséquent, le paramètre de ligne de commande Complete **-DebugSecurityZoneURL** et la valeur est :

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Voir aussi

- [Hôte WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
