---
title: 'Comment : détecter si .NET Framework 3.0 est installé'
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: 41010e615b6b3d10ebf6adc0e3f871873e94f409
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124453"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="0fe2d-102">Comment : détecter si .NET Framework 3.0 est installé</span><span class="sxs-lookup"><span data-stu-id="0fe2d-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="0fe2d-103">Pour que les administrateurs puissent déployer des applications Microsoft .NET Framework sur un système, ils doivent d’abord confirmer que le Runtime .NET Framework est présent.</span><span class="sxs-lookup"><span data-stu-id="0fe2d-103">Before administrators can deploy Microsoft .NET Framework applications on a system, they must first confirm that the .NET Framework runtime is present.</span></span> <span data-ttu-id="0fe2d-104">Cette rubrique fournit un script écrit en HTML/JavaScript que les administrateurs peuvent utiliser pour déterminer si le .NET Framework est présent sur un système.</span><span class="sxs-lookup"><span data-stu-id="0fe2d-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the .NET Framework is present on a system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0fe2d-105">Pour plus d’informations sur l’installation, le déploiement et la détection de l’infrastructure Microsoft .NET, consultez la discussion consacrée au [déploiement de Microsoft .NET Framework Version 3,0](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480198(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="0fe2d-105">For more detailed information on installing, deploying, and detecting the Microsoft .NET Framework, see the discussion in [Deploying Microsoft .NET Framework Version 3.0](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480198(v=msdn.10)).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="0fe2d-106">Détection de la chaîne de l’agent utilisateur « .NET CLR »</span><span class="sxs-lookup"><span data-stu-id="0fe2d-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="0fe2d-107">Lorsque .NET Framework est installé, le MSI ajoute « .NET CLR » et le numéro de version à la chaîne UserAgent.</span><span class="sxs-lookup"><span data-stu-id="0fe2d-107">When .NET Framework is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="0fe2d-108">L’exemple suivant montre un script incorporé dans une page HTML simple.</span><span class="sxs-lookup"><span data-stu-id="0fe2d-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="0fe2d-109">Le script recherche la chaîne UserAgent pour déterminer si .NET Framework est installé et affiche un message d’État sur les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="0fe2d-109">The script searches the UserAgent string to determine whether .NET Framework is installed, and displays a status message on the results of the search.</span></span>  
  
```html  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.0</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.0.04425.00";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.0: "   
          + dotNETRuntimeVersion  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.0."  
      }  
      result.innerText += "\n\nThis machine's userAgent string is: " +   
        navigator.userAgent + ".";  
    }  
  
    //  
    // Retrieve the version from the user agent string and   
    // compare with the specified version.  
    //  
    function HasRuntimeVersion(versionToCheck)  
    {  
      var userAgentString =   
        navigator.userAgent.match(/.NET CLR [0-9.]+/g);  
  
      if (userAgentString != null)  
      {  
        var i;  
  
        for (i = 0; i < userAgentString.length; ++i)  
        {  
          if (CompareVersions(GetVersion(versionToCheck),   
            GetVersion(userAgentString[i])) <= 0)  
            return true;  
        }  
      }  
  
      return false;  
    }  
  
    //  
    // Extract the numeric part of the version string.  
    //  
    function GetVersion(versionString)  
    {  
      var numericString =   
        versionString.match(/([0-9]+)\.([0-9]+)\.([0-9]+)/i);  
      return numericString.slice(1);  
    }  
  
    //  
    // Compare the 2 version strings by converting them to numeric format.  
    //  
    function CompareVersions(version1, version2)  
    {  
      for (i = 0; i < version1.length; ++i)  
      {  
        var number1 = new Number(version1[i]);  
        var number2 = new Number(version2[i]);  
  
        if (number1 < number2)  
          return -1;  
  
        if (number1 > number2)  
          return 1;  
      }  
  
      return 0;  
    }  
  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY>  
    <div id="result" />  
  </BODY>  
</HTML>  
```  
  
 <span data-ttu-id="0fe2d-110">Si la recherche de la version « .NET CLR » réussit, le type de message d’état suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="0fe2d-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="0fe2d-111">Dans le cas contraire, le type de message d’état suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="0fe2d-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
