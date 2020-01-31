---
title: Vue d’ensemble du contrôle SplitContainer
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 5cb5240ed4ebe3e27c20844681068711c222e9a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742923"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>Vue d'ensemble du contrôle SplitContainer (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.SplitContainer> peut être considéré comme un composite ; il s'agit de deux panneaux séparés par une barre mobile. Quand le pointeur de la souris est sur la barre, il change de forme pour montrer que la barre est mobile.  
  
> [!IMPORTANT]
> Dans la **boîte à outils**, <xref:System.Windows.Forms.SplitContainer> contrôle remplace le contrôle <xref:System.Windows.Forms.Splitter> qui était dans la version précédente de Visual Studio. Il vaut beaucoup mieux utiliser le contrôle <xref:System.Windows.Forms.SplitContainer> que le contrôle <xref:System.Windows.Forms.Splitter>. La classe <xref:System.Windows.Forms.Splitter> est toujours incluse dans .NET Framework pour la compatibilité avec les applications existantes, mais nous vous encourageons vivement à utiliser le contrôle <xref:System.Windows.Forms.SplitContainer> pour les nouveaux projets.  
  
 Avec le contrôle <xref:System.Windows.Forms.SplitContainer>, vous pouvez créer des interfaces utilisateur complexes. souvent, une sélection dans un panneau détermine les objets qui sont affichés dans l’autre panneau. Cette disposition est très efficace pour afficher et parcourir des informations. Le fait d’avoir deux panneaux vous permet d’agréger des informations dans des zones, et la barre, ou « Splitter », permet aux utilisateurs de redimensionner facilement les panneaux.  
  
 Plusieurs contrôles de <xref:System.Windows.Forms.SplitContainer> peuvent également être imbriqués, le deuxième <xref:System.Windows.Forms.SplitContainer> contrôle orienté horizontalement, pour créer des panneaux supérieurs et inférieurs.  
  
 Sachez que le contrôle <xref:System.Windows.Forms.SplitContainer> est accessible par le clavier par défaut ; les utilisateurs peuvent appuyer sur les touches de direction pour déplacer le séparateur si la propriété <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> est définie sur `false`.  
  
 La propriété <xref:System.Windows.Forms.SplitContainer.Orientation%2A> du contrôle <xref:System.Windows.Forms.SplitContainer> détermine la direction du séparateur, et non le contrôle lui-même. Par conséquent, lorsque cette propriété a la valeur <xref:System.Windows.Forms.Orientation.Vertical>, le séparateur s’exécute de haut en bas, créant ainsi des panneaux de gauche et de droite.  
  
 En outre, sachez que la valeur de la propriété <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> varie en fonction de la valeur de la propriété <xref:System.Windows.Forms.SplitContainer.Orientation%2A>. Pour plus d’informations, consultez <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> propriété.  
  
 Vous pouvez également limiter la taille et le déplacement du contrôle <xref:System.Windows.Forms.SplitContainer>. La propriété <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> détermine le panneau qui conservera la même taille après le redimensionnement du contrôle <xref:System.Windows.Forms.SplitContainer>, et la propriété <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> détermine si le séparateur est déplaçable par le clavier ou la souris.  
  
> [!NOTE]
> Même si la propriété <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> est définie sur `true`, le séparateur peut toujours être déplacé par programme ; par exemple, à l’aide de la propriété <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>.  
  
 Enfin, chaque panneau du contrôle <xref:System.Windows.Forms.SplitContainer> possède des propriétés permettant de déterminer sa taille individuelle.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Propriétés, méthodes et événements couramment utilisés  
  
|Name|Description|  
|----------|-----------------|  
|Propriété<xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>|Détermine le panneau qui conservera la même taille après le redimensionnement du contrôle <xref:System.Windows.Forms.SplitContainer>.|  
|Propriété<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>|Détermine si le séparateur peut être déplacé à l’aide du clavier ou de la souris.|  
|Propriété<xref:System.Windows.Forms.SplitContainer.Orientation%2A>|Détermine si le séparateur est organisé verticalement ou horizontalement.|  
|Propriété<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>|Détermine la distance en pixels entre le bord supérieur gauche et la barre de fractionnement déplaçable.|  
|Propriété<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>|Détermine la distance minimale, en pixels, que le séparateur peut déplacer par l’utilisateur.|  
|Propriété<xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A>|Détermine l’épaisseur, en pixels, du séparateur.|  
|Événement<xref:System.Windows.Forms.SplitContainer.SplitterMoving>|Se produit lorsque le séparateur est déplacé.|  
|Événement<xref:System.Windows.Forms.SplitContainer.SplitterMoved>|Se produit lorsque le séparateur a été déplacé.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer, contrôle](splitcontainer-control-windows-forms.md)
- [SplitContainer, exemple de contrôle](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/0ffz7d1b(v=vs.90))
