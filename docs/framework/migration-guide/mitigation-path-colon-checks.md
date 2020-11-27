---
title: 'Atténuation : Vérifications des signes deux-points dans les chemins d’accès'
description: En savoir plus sur les modifications apportées à .NET Framework 4.6.2 afin de prendre en charge les vérifications de la syntaxe de séparateur de lecteur appropriée (le signe deux-points).
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: 03f1c7249549aae7e3bef986c97fb5f320fbeb2f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283456"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="ba080-103">Atténuation : Vérifications des signes deux-points dans les chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="ba080-103">Mitigation: Path Colon Checks</span></span>

<span data-ttu-id="ba080-104">À compter des applications qui ciblent .NET Framework 4.6.2, plusieurs modifications ont été apportées pour prendre en charge les chemins d’accès non pris en charge précédemment (à la fois en termes de longueur et de format).</span><span class="sxs-lookup"><span data-stu-id="ba080-104">Starting with apps that target the .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="ba080-105">En particulier, les vérifications de bonne syntaxe de séparateur de lecteur (le signe deux-points) ont été rendues plus correctes.</span><span class="sxs-lookup"><span data-stu-id="ba080-105">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ba080-106">Impact</span><span class="sxs-lookup"><span data-stu-id="ba080-106">Impact</span></span>  

 <span data-ttu-id="ba080-107">Ces modifications bloquent certains chemins d’URI que les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> prenaient précédemment en charge.</span><span class="sxs-lookup"><span data-stu-id="ba080-107">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ba080-108">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="ba080-108">Mitigation</span></span>  

 <span data-ttu-id="ba080-109">Pour contourner le problème d’un chemin précédemment acceptable qui n’est plus pris en charge par les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ba080-109">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="ba080-110">Supprimez manuellement le schéma à partir d’une URL.</span><span class="sxs-lookup"><span data-stu-id="ba080-110">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="ba080-111">Par exemple, supprimez `file://` à partir d’une URL.</span><span class="sxs-lookup"><span data-stu-id="ba080-111">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="ba080-112">Passez l’URI à un constructeur <xref:System.Uri> et récupérez la valeur de la propriété <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ba080-112">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="ba080-113">Refusez la nouvelle normalisation de chemin d’accès en affectant à `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="ba080-113">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ba080-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba080-114">See also</span></span>

- [<span data-ttu-id="ba080-115">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="ba080-115">Application compatibility</span></span>](application-compatibility.md)
