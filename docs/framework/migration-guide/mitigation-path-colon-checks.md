---
title: 'Atténuation : vérifications des signes deux-points dans les chemins d’accès'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6799e36ec312bf857a12293dc0be15e9cc21f55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648453"
---
# <a name="mitigation-path-colon-checks"></a><span data-ttu-id="5c1a2-102">Atténuation : vérifications des signes deux-points dans les chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="5c1a2-102">Mitigation: Path Colon Checks</span></span>
<span data-ttu-id="5c1a2-103">Plusieurs modifications ont été apportées pour prendre en charge les chemins d’accès non pris en charge précédemment (à la fois en termes de longueur et le format), à commencer par les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c1a2-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a number of changes were made to support previously unsupported paths (both in terms of length and format).</span></span> <span data-ttu-id="5c1a2-104">En particulier, les vérifications de bonne syntaxe de séparateur de lecteur (le signe deux-points) ont été rendues plus correctes.</span><span class="sxs-lookup"><span data-stu-id="5c1a2-104">In particular, checks for the proper drive separator syntax (the colon) were made more correct.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="5c1a2-105">Impact</span><span class="sxs-lookup"><span data-stu-id="5c1a2-105">Impact</span></span>  
 <span data-ttu-id="5c1a2-106">Ces modifications bloquent certains chemins d’URI que les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> prenaient précédemment en charge.</span><span class="sxs-lookup"><span data-stu-id="5c1a2-106">These changes block some URI paths the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods previously supported.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="5c1a2-107">Atténuation</span><span class="sxs-lookup"><span data-stu-id="5c1a2-107">Mitigation</span></span>  
 <span data-ttu-id="5c1a2-108">Pour contourner le problème d’un chemin précédemment acceptable qui n’est plus pris en charge par les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5c1a2-108">To work around the problem of a previously acceptable path that is no longer supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods, you can do the following:</span></span>  
  
- <span data-ttu-id="5c1a2-109">Supprimez manuellement le schéma à partir d’une URL.</span><span class="sxs-lookup"><span data-stu-id="5c1a2-109">Manually remove the scheme from a URL.</span></span> <span data-ttu-id="5c1a2-110">Par exemple, supprimez `file://` à partir d’une URL.</span><span class="sxs-lookup"><span data-stu-id="5c1a2-110">For example, remove `file://` from a URL.</span></span>  
  
- <span data-ttu-id="5c1a2-111">Passez l’URI à un constructeur <xref:System.Uri> et récupérez la valeur de la propriété <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5c1a2-111">Pass the URI to a <xref:System.Uri> constructor,  and retrieve the value of the <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> property.</span></span>  
  
- <span data-ttu-id="5c1a2-112">Refusez la nouvelle normalisation de chemin d’accès en affectant à `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="5c1a2-112">Opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> switch to `true`.</span></span>  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5c1a2-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c1a2-113">See also</span></span>

- [<span data-ttu-id="5c1a2-114">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="5c1a2-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
