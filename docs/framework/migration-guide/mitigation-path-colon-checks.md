---
title: 'Atténuation : Vérifications des signes deux-points dans les chemins d’accès'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: e88643fea3bd507289436f41880a2de34117884f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457895"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="fd1a0-102">Atténuation : Vérifications des signes deux-points dans les chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="fd1a0-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="fd1a0-103">À compter des applications qui ciblent .NET Framework 4.6.2, plusieurs modifications ont été apportées pour prendre en charge les chemins d’accès non pris en charge précédemment (à la fois en termes de longueur et de format).</span><span class="sxs-lookup"><span data-stu-id="fd1a0-103">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="fd1a0-104">En particulier, les vérifications de bonne syntaxe de séparateur de lecteur (le signe deux-points) ont été rendues plus correctes.</span><span class="sxs-lookup"><span data-stu-id="fd1a0-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="fd1a0-105">Impact</span><span class="sxs-lookup"><span data-stu-id="fd1a0-105">Impact</span></span>  
 <span data-ttu-id="fd1a0-106">Ces modifications bloquent certains chemins d’URI que les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> prenaient précédemment en charge.</span><span class="sxs-lookup"><span data-stu-id="fd1a0-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="fd1a0-107">Atténuation</span><span class="sxs-lookup"><span data-stu-id="fd1a0-107">Mitigation</span></span>  
 <span data-ttu-id="fd1a0-108">Pour contourner le problème d’un chemin précédemment acceptable qui n’est plus pris en charge par les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="fd1a0-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="fd1a0-109">Supprimez manuellement le schéma à partir d’une URL.</span><span class="sxs-lookup"><span data-stu-id="fd1a0-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="fd1a0-110">Par exemple, supprimez `file://` à partir d’une URL.</span><span class="sxs-lookup"><span data-stu-id="fd1a0-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="fd1a0-111">Passez l’URI à un constructeur <xref:System.Uri> et récupérez la valeur de la propriété <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd1a0-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="fd1a0-112">Refusez la nouvelle normalisation de chemin d’accès en affectant à `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="fd1a0-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fd1a0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd1a0-113">See also</span></span>

- [<span data-ttu-id="fd1a0-114">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="fd1a0-114">Application compatibility</span></span>](application-compatibility.md)
