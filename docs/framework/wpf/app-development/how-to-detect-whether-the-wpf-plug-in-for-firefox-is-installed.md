---
title: 'Comment : détecter si le plug-in WPF de Firefox est installé'
ms.date: 03/30/2017
helpviewer_keywords:
- plug-in for Firefox [WPF]
- detecting Firefox installation [WPF]
- checking for the Firefox plug-in [WPF]
- Firefox [WPF], detecting installation
- detecting whether the WPF plug-in for Firefox is installed [WPF]
ms.assetid: 5f839373-e3fb-44f1-88ad-4a0761f02189
ms.openlocfilehash: fdc7b516c316c7efc7056b549baf43191a5aedd1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423746"
---
# <a name="how-to-detect-whether-the-wpf-plug-in-for-firefox-is-installed"></a><span data-ttu-id="6b288-102">Comment : détecter si le plug-in WPF de Firefox est installé</span><span class="sxs-lookup"><span data-stu-id="6b288-102">How to: Detect Whether the WPF Plug-In for Firefox Is Installed</span></span>

<span data-ttu-id="6b288-103">Le plug-in Windows Presentation Foundation (WPF) pour Firefox permet aux applications de navigateur XAML (XBAP) et aux fichiers XAML libres de s’exécuter dans le navigateur Mozilla Firefox.</span><span class="sxs-lookup"><span data-stu-id="6b288-103">The Windows Presentation Foundation (WPF) plug-in for Firefox enables XAML browser applications (XBAPs) and loose XAML files to run in the Mozilla Firefox browser.</span></span> <span data-ttu-id="6b288-104">Cette rubrique fournit un script écrit en HTML et JavaScript que les administrateurs peuvent utiliser pour déterminer si le plug-in WPF de Firefox est installé.</span><span class="sxs-lookup"><span data-stu-id="6b288-104">This topic provides a script written in HTML and JavaScript that administrators can use to determine whether the WPF plug-in for Firefox is installed.</span></span>

> [!NOTE]
> <span data-ttu-id="6b288-105">Pour plus d’informations sur l’installation, le déploiement et la détection de la .NET Framework, consultez [installer le .NET Framework pour les développeurs](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="6b288-105">For more information about installing, deploying, and detecting the .NET Framework, see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>

## <a name="example"></a><span data-ttu-id="6b288-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="6b288-106">Example</span></span>

<span data-ttu-id="6b288-107">Lorsque la .NET Framework 3,5 est installée, l’ordinateur client est configuré avec un plug-in WPF pour Firefox.</span><span class="sxs-lookup"><span data-stu-id="6b288-107">When the .NET Framework 3.5 is installed, the client computer is configured with a WPF plug-in for Firefox.</span></span> <span data-ttu-id="6b288-108">L’exemple de script suivant recherche le plug-in WPF pour Firefox, puis affiche un message d’état approprié.</span><span class="sxs-lookup"><span data-stu-id="6b288-108">The following example script checks for the WPF plug-in for Firefox and then displays an appropriate status message.</span></span>

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

<span data-ttu-id="6b288-109">Si la vérification du plug-in WPF pour Firefox réussit, le message d’état suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="6b288-109">If the check for the WPF plug-in for Firefox is successful, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is installed.`

<span data-ttu-id="6b288-110">Dans le cas contraire, le message d’état suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="6b288-110">Otherwise, the following status message is displayed:</span></span>

`The WPF plug-in for Firefox is not installed. Please install or reinstall the .NET Framework 3.5.`

## <a name="see-also"></a><span data-ttu-id="6b288-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b288-111">See also</span></span>

- [<span data-ttu-id="6b288-112">Détecter si .NET Framework 3.0 est installé</span><span class="sxs-lookup"><span data-stu-id="6b288-112">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
- [<span data-ttu-id="6b288-113">Détecter si .NET Framework 3.5 est installé</span><span class="sxs-lookup"><span data-stu-id="6b288-113">Detect Whether the .NET Framework 3.5 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-5-is-installed.md)
- [<span data-ttu-id="6b288-114">Vue d’ensemble des applications du navigateur XAML WPF</span><span class="sxs-lookup"><span data-stu-id="6b288-114">WPF XAML Browser Applications Overview</span></span>](wpf-xaml-browser-applications-overview.md)
