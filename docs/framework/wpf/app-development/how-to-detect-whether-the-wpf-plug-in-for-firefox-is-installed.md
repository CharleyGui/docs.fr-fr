---
title: Détecter si le plug-in WPF de Firefox est installé
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: 91680859c1742e5d5443d626c81273a80504f4a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740398"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a>Comment : détecter si le plug-in WPF de Firefox est installé

Le plug-in Windows Presentation Foundation (WPF) pour Firefox permet aux applications de navigateur XAML (XBAP) et aux fichiers XAML libres de s’exécuter dans le navigateur Mozilla Firefox. Cette rubrique fournit un script écrit en HTML et JavaScript que les administrateurs peuvent utiliser pour déterminer si le plug-in WPF de Firefox est installé.

> [!NOTE]
> Pour plus d’informations sur l’installation, le déploiement et la détection de la .NET Framework, consultez [installer le .NET Framework pour les développeurs](../../install/guide-for-developers.md).

## <a name="example"></a>Exemple

Lorsque la .NET Framework 3,5 est installée, l’ordinateur client est configuré avec un plug-in WPF pour Firefox. L’exemple de script suivant recherche le plug-in WPF pour Firefox, puis affiche un message d’état approprié.

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

Si la vérification du plug-in WPF pour Firefox réussit, le message d’état suivant s’affiche :

`The WPF plug-in for Firefox is installed.`

Dans le cas contraire, le message d’état suivant s’affiche :

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a>Voir aussi

- [Détecter si .NET Framework 3.0 est installé](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [Détecter si .NET Framework 3.5 est installé](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [Vue d’ensemble des applications du navigateur XAML WPF](wpf-xaml-browser-applications-overview.md)
