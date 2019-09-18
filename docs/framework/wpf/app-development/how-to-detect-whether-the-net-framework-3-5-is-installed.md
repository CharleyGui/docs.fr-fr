---
title: 'Procédure : Détecter si .NET Framework 3.5 est installé'
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: 18e5c819eb4deb62208280816d11dce0940d134d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053426"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a><span data-ttu-id="7991e-102">Procédure : Détecter si .NET Framework 3.5 est installé</span><span class="sxs-lookup"><span data-stu-id="7991e-102">How to: Detect Whether the .NET Framework 3.5 Is Installed</span></span>
<span data-ttu-id="7991e-103">Pour que les administrateurs puissent déployer des applications Windows Presentation Foundation (WPF) sur un système ciblant le .NET Framework 3,5, ils doivent d’abord confirmer que le Runtime .NET Framework 3,5 est présent.</span><span class="sxs-lookup"><span data-stu-id="7991e-103">Before administrators can deploy Windows Presentation Foundation (WPF) applications on a system that targets the .NET Framework 3.5, they must first confirm that the .NET Framework 3.5 runtime is present.</span></span> <span data-ttu-id="7991e-104">Cette rubrique fournit un script écrit en HTML/JavaScript que les administrateurs peuvent utiliser pour déterminer si le .NET Framework 3,5 est présent sur un système.</span><span class="sxs-lookup"><span data-stu-id="7991e-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the .NET Framework 3.5 is present on a system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7991e-105">Pour plus d’informations sur l’installation, le déploiement et la détection de la .NET Framework, consultez [installer le .NET Framework pour les développeurs](../../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="7991e-105">For more detailed information on installing, deploying, and detecting the .NET Framework, see [Install the .NET Framework for developers](../../install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7991e-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="7991e-106">Example</span></span>  
 <span data-ttu-id="7991e-107">Lorsque la .NET Framework 3,5 est installée, le MSI ajoute « .NET CLR » et le numéro de version à la chaîne UserAgent.</span><span class="sxs-lookup"><span data-stu-id="7991e-107">When the .NET Framework 3.5 is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="7991e-108">L’exemple suivant montre un script incorporé dans une page HTML simple.</span><span class="sxs-lookup"><span data-stu-id="7991e-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="7991e-109">Le script recherche la chaîne UserAgent pour déterminer si la .NET Framework 3,5 est installée et affiche un message d’État sur les résultats de la recherche.</span><span class="sxs-lookup"><span data-stu-id="7991e-109">The script searches the UserAgent string to determine whether the .NET Framework 3.5 is installed, and displays a status message on the results of the search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7991e-110">Ce script est conçu pour Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="7991e-110">This script is designed for Internet Explorer.</span></span> <span data-ttu-id="7991e-111">D’autres navigateurs peuvent ne pas inclure d’informations CLR .NET dans la chaîne UserAgent.</span><span class="sxs-lookup"><span data-stu-id="7991e-111">Other browsers may not include .NET CLR information in the UserAgent string.</span></span>  
  
```html  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.5</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.5.0.0";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.5."  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.5." +  
          " The required version is v" + dotNETRuntimeVersion + ".";  
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
  
 <span data-ttu-id="7991e-112">Si la recherche de la version « .NET CLR » réussit, le type de message d’état suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="7991e-112">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 <span data-ttu-id="7991e-113">Dans le cas contraire, le type de message d’état suivant s’affiche :</span><span class="sxs-lookup"><span data-stu-id="7991e-113">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a><span data-ttu-id="7991e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7991e-114">See also</span></span>

- [<span data-ttu-id="7991e-115">Détecter si .NET Framework 3.0 est installé</span><span class="sxs-lookup"><span data-stu-id="7991e-115">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
