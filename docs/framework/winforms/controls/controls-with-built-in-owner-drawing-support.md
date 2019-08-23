---
title: Contrôles avec prise en charge intégrée des dessins owner-drawn
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
ms.openlocfilehash: f0d4b99f9ee0134fc7334a941dd5ef4fd7ba3df3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930192"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Contrôles avec prise en charge intégrée des dessins owner-drawn
Le dessin owner-drawn dans Windows Forms, qui est également appelé dessin personnalisé, est une technique permettant de changer l’apparence visuelle de certains contrôles.  
  
> [!NOTE]
> Le mot «contrôle» dans cette rubrique est utilisé pour signifier les classes qui dérivent <xref:System.ComponentModel.Component>de <xref:System.Windows.Forms.Control> ou de.  
  
 En général, Windows gère automatiquement la peinture en utilisant des paramètres <xref:System.Windows.Forms.Control.BackColor%2A> de propriété tels que pour déterminer l’apparence d’un contrôle. Avec le dessin owner-drawn, vous contrôlez le processus de dessin, en changeant l’apparence des éléments qui ne sont pas disponibles via des propriétés. Par exemple, de nombreux contrôles vous permettent de définir la couleur du texte qui s’affiche, mais vous êtes limité à une seule couleur. Le dessin owner-drawn vous permet d’effectuer des opérations comme afficher une partie du texte en noir et une autre en rouge.  
  
 Dans la pratique, le dessin owner-drawn est similaire au dessin de graphiques dans un formulaire. Par exemple, vous pouvez utiliser des méthodes graphiques dans un gestionnaire pour que l' <xref:System.Windows.Forms.Control.Paint> événement du formulaire émule `ListBox` un contrôle, mais vous devez écrire votre propre code pour gérer toutes les interactions de l’utilisateur. Avec le dessin owner-drawn, le contrôle utilise votre code pour dessiner son contenu, mais il conserve par ailleurs toutes ses capacités intrinsèques. Vous pouvez utiliser des méthodes graphiques pour dessiner chaque élément du contrôle ou pour personnaliser certains aspects de chaque élément, tout en utilisant l’apparence par défaut pour d’autres aspects de chaque élément.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Dessin owner-drawn dans les contrôles Windows Forms  
 Pour effectuer du dessin owner-drawn dans les contrôles qui le prennent en charge, vous définissez généralement une propriété, et vous gérez un ou plusieurs événements.  
  
 La plupart des contrôles qui prennent en charge le dessin owner-drawn ont une propriété `OwnerDraw` ou `DrawMode` qui indique si le contrôle déclenche son ou ses événements de dessin quand il se dessine lui-même.  
  
 Les contrôles qui n’ont pas une propriété `OwnerDraw` ou `DrawMode` incluent le contrôle `DataGridView`, qui fournit des événements de dessin qui se produisent automatiquement, et le contrôle `ToolStrip`, qui est dessiné à l’aide d’une classe de rendu externe qui a ses propres événements de dessin.  
  
 Il existe de nombreux types d’événements de dessin, mais un événement de dessin se produit généralement pour dessiner un élément dans un contrôle. Le gestionnaire d’événements reçoit un objet `EventArgs` qui contient des informations sur l’élément dessiné et des outils que vous pouvez utiliser pour le dessiner. Par exemple, cet objet contient généralement le numéro d’index de l’élément dans sa collection parent <xref:System.Drawing.Rectangle> , un qui indique les limites d’affichage de l' <xref:System.Drawing.Graphics> élément et un objet pour appeler les méthodes de peinture. Pour certains événements, l’objet `EventArgs` fournit plus d’informations sur l’élément sur les méthodes que vous pouvez appeler pour dessiner certains aspects de l’élément par défaut, comme l’arrière-plan ou un rectangle de focus.  
  
 Pour créer un contrôle réutilisable contenant vos personnalisations owner-drawn, créez une classe qui dérive d’une classe de contrôle prenant en charge le dessin owner-drawn. Au lieu de gérer les événements de dessin, incluez votre code de dessin owner-drawn dans la ou les méthodes `On`*nom_événement* appropriées de la nouvelle classe. Vérifiez que vous appelez dans ce cas la ou les méthodes `On`*nom_événement* de la classe de base, pour que les utilisateurs de votre contrôle puissent gérer les événements de dessin owner-drawn et fournir une personnalisation supplémentaire.  
  
 Les contrôles Windows Forms suivants prennent en charge le dessin owner-drawn dans toutes les versions du .NET Framework :  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <xref:System.Windows.Forms.MenuItem>(utilisé par <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu>)  
  
- <xref:System.Windows.Forms.TabControl>  
  
 Les contrôles suivants prennent en charge le dessin owner-drawn uniquement dans .NET Framework 2,0:  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 Les contrôles suivants prennent en charge le dessin owner-drawn et sont nouveaux dans .NET Framework 2,0:  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 Les sections suivantes contiennent des informations détaillées supplémentaires pour chacun de ces contrôles.  
  
### <a name="listbox-and-combobox-controls"></a>Contrôles Edit et Combobox  
 Les <xref:System.Windows.Forms.ListBox> contrôles <xref:System.Windows.Forms.ComboBox> et vous permettent de dessiner des éléments individuels dans le contrôle, soit tous dans une seule taille, soit à des tailles différentes.  
  
> [!NOTE]
> Bien que <xref:System.Windows.Forms.CheckedListBox> le contrôle soit dérivé <xref:System.Windows.Forms.ListBox> du contrôle, il ne prend pas en charge le dessin owner-drawn.  
  
 Pour dessiner chaque élément de la même taille, affectez `DrawMode` à <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> la propriété la `DrawItem` valeur et gérez l’événement.  
  
 Pour dessiner chaque élément en utilisant une taille différente `DrawMode` , affectez à <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> la propriété la valeur et `DrawItem` gérez `MeasureItem` les événements et. L’événement `MeasureItem` vous permet d’indiquer la taille d’un élément avant que l’événement `DrawItem` se produise pour cet élément.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques suivantes :  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [Guide pratique pour Créer du texte de taille variable dans un contrôle ComboBox](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>MenuItem, composant  
 Le <xref:System.Windows.Forms.MenuItem> composant représente un élément de menu unique dans <xref:System.Windows.Forms.MainMenu> un <xref:System.Windows.Forms.ContextMenu> composant ou.  
  
 Pour dessiner un <xref:System.Windows.Forms.MenuItem>, définissez sa `OwnerDraw` propriété sur `true` et gérez son `DrawItem` événement. Pour personnaliser la taille de l’élément de menu avant que l’événement `DrawItem` se produise, gérez l’événement `MeasureItem` de l’élément.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl, contrôle  
 Le <xref:System.Windows.Forms.TabControl> contrôle vous permet de dessiner des onglets individuels dans le contrôle. Le dessin owner-drawn affecte uniquement les onglets; le <xref:System.Windows.Forms.TabPage> contenu n’est pas affecté.  
  
 Pour dessiner chaque onglet dans un <xref:System.Windows.Forms.TabControl>, affectez `DrawMode` à <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> la propriété la valeur `DrawItem` et gérez l’événement. Cet événement se produit une fois pour chaque onglet uniquement quand l’onglet est visible dans le contrôle.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip, composant  
 Le <xref:System.Windows.Forms.ToolTip> composant vous permet de dessiner la totalité de l’info-bulle lorsqu’elle est affichée.  
  
 Pour dessiner un <xref:System.Windows.Forms.ToolTip>, définissez sa `OwnerDraw` propriété sur `true` et gérez son `Draw` événement. Pour personnaliser la <xref:System.Windows.Forms.ToolTip> taille du avant que l' `Draw` événement se produise, gérez l' `Popup` événement et <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> définissez la propriété dans le gestionnaire d’événements.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>Contrôle ListView  
 Le <xref:System.Windows.Forms.ListView> contrôle vous permet de dessiner des éléments individuels, des sous-éléments et des en-têtes de colonnes dans le contrôle.  
  
 Pour activer le dessin owner-drawn dans le contrôle, définissez la propriété `OwnerDraw` sur `true`.  
  
 Pour dessiner chaque élément dans le contrôle, gérez l’événement `DrawItem`.  
  
 Pour dessiner chaque sous-élément ou en-tête de colonne <xref:System.Windows.Forms.ListView.View%2A> dans le contrôle lorsque la propriété a `DrawSubItem` la `DrawColumnHeader` <xref:System.Windows.Forms.View.Details>valeur, gérez les événements et.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView, contrôle  
 Le <xref:System.Windows.Forms.TreeView> contrôle vous permet de dessiner des nœuds individuels dans le contrôle.  
  
 Pour dessiner uniquement le texte affiché dans chaque nœud, affectez `DrawMode` à <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> la propriété la valeur `DrawNode` et gérez l’événement pour dessiner le texte.  
  
 Pour dessiner tous les éléments de chaque nœud, définissez `DrawMode` la propriété <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> sur et gérez `DrawNode` l’événement pour dessiner les éléments dont vous avez besoin, tels que le texte, les icônes, les cases à cocher, les signes plus et moins, et les lignes qui connectent les nœuds.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView, contrôle  
 Le <xref:System.Windows.Forms.DataGridView> contrôle vous permet de dessiner des cellules et des lignes individuelles dans le contrôle.  
  
 Pour dessiner des cellules individuelles, gérez l’événement `CellPainting`.  
  
 Pour dessiner des lignes individuelles ou des éléments de ligne, gérez un des événements `RowPrePaint` ou `RowPostPaint`, ou les deux. L’événement `RowPrePaint` se produit avant le dessin des cellules d’une ligne, et l’événement se produit `RowPostPaint` après le dessin des cellules. Vous pouvez gérer ces deux événements et l’événement `CellPainting` pour dessiner séparément l’arrière-plan de la ligne, les cellules individuelles et le premier plan de la ligne, ou vous pouvez fournir des personnalisations spécifiques là où vous en avez besoin et utiliser l’affichage par défaut pour les autres éléments de la ligne.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques suivantes :  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [Guide pratique : Personnaliser l’apparence des cellules dans le contrôle DataGridView Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [Guide pratique : Personnaliser l’apparence des lignes dans le contrôle DataGridView Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip, contrôle  
 <xref:System.Windows.Forms.ToolStrip>et les contrôles dérivés vous permettent de personnaliser tous les aspects de leur apparence.  
  
 Pour fournir un rendu personnalisé <xref:System.Windows.Forms.ToolStrip> pour les contrôles, `Renderer` définissez la <xref:System.Windows.Forms.ToolStripPanel>propriété <xref:System.Windows.Forms.ToolStrip>d' <xref:System.Windows.Forms.ToolStripManager>un,, <xref:System.Windows.Forms.ToolStripContentPanel> ou sur `ToolStripRenderer` un objet et gérez un ou plusieurs des nombreux événements de dessin fournis par le `ToolStripRenderer` classe. Vous pouvez également définir une `Renderer` propriété sur une instance de votre propre classe dérivée `ToolStripRenderer`de <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, ou <xref:System.Windows.Forms.ToolStripSystemRenderer> qui implémente ou substitue des méthodes `On` *EventName* spécifiques.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques suivantes :  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [Guide pratique pour Créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [Guide pratique : Dessiner un contrôle ToolStrip personnalisé](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Voir aussi

- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
