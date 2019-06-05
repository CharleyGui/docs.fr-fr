---
title: 'Procédure : Détecter si le plug-in WPF de Firefox est installé'
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: f84a0a2af43931b3ada1f674390ec5d841b79a1c
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690419"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Procédure : Détecter si le plug-in WPF de Firefox est installé

Windows Presentation Foundation (WPF) plug-in de Firefox permet [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] et perdre les fichiers XAML à exécuter dans le navigateur Mozilla Firefox. Cette rubrique fournit un script écrit en HTML et JavaScript, les administrateurs peuvent utiliser pour déterminer si le WPF plug-in de Firefox est installé.

> [!NOTE]
> Pour plus d’informations sur l’installation, déploiement et la détection du .NET Framework, consultez [installer le .NET Framework pour les développeurs](../../install/guide-for-developers.md).

## <a name="example"></a>Exemple

Lorsque le .NET Framework 3.5 est installé, l’ordinateur client est configuré avec un plug-in WPF de Firefox. L’exemple de script suivant vérifie le plug-in WPF de Firefox, puis affiche un message d’état approprié.

```html
<HTML>

  <HEAD>
    <TITLE>Test for the WPF plug-in for Firefox</TITLE>
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />
    <SCRIPT type="text/javascript">
    <!--
    function OnLoad()
    {

       // Check for the WPF plug-in for Firefox and report
       var msg = "The WPF plug-in for Firefox is ";
       var wpfPlugin = navigator.plugins["Windows Presentation Foundation"];
       if( wpfPlugin != null ) {
          document.writeln(msg + " installed.");
       }
       else {
          document.writeln(msg + " not installed. Please install or reinstall the .NET Framework 3.5.");
       }
    }
    -->
    </SCRIPT>
  </HEAD>

  <BODY onload="OnLoad()" />

</HTML>
```

Si la vérification pour le plug-in WPF de Firefox est réussie, le message d’état suivant s’affiche :

`The WPF plug-in for Firefox is installed.`

Sinon, le message d’état suivant s’affiche :

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a>Voir aussi

- [Détecter si .NET Framework 3.0 est installé](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [Détecter si .NET Framework 3.5 est installé](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [Vue d’ensemble des applications du navigateur XAML WPF](wpf-xaml-browser-applications-overview.md)
