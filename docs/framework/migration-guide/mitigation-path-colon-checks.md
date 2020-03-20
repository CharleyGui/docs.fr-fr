---
title: 'Atténuation : Vérifications des signes deux-points dans les chemins d’accès'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: c6e1106b6f5d8457417992941b9f28712d484442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181243"
---
# <a name="mitigation-path-colon-checks"></a>Atténuation : Vérifications des signes deux-points dans les chemins d’accès
À compter des applications qui ciblent .NET Framework 4.6.2, plusieurs modifications ont été apportées pour prendre en charge les chemins d’accès non pris en charge précédemment (à la fois en termes de longueur et de format). En particulier, les vérifications de bonne syntaxe de séparateur de lecteur (le signe deux-points) ont été rendues plus correctes.  
  
## <a name="impact"></a>Impact  
 Ces modifications bloquent certains chemins d’URI que les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> prenaient précédemment en charge.  
  
## <a name="mitigation"></a>Limitation des risques  
 Pour contourner le problème d’un chemin précédemment acceptable qui n’est plus pris en charge par les méthodes <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>, effectuez les étapes suivantes :  
  
- Supprimez manuellement le schéma à partir d’une URL. Par exemple, supprimez `file://` à partir d’une URL.  
  
- Passez l’URI à un constructeur <xref:System.Uri> et récupérez la valeur de la propriété <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.  
  
- Refusez la nouvelle normalisation de chemin d’accès en affectant à `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> la valeur `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
