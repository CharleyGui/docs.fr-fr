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
ms.openlocfilehash: c053c14bb06d1bb28c7b7e6652ccc6e41af9c4e5
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170607"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Contrôles avec prise en charge intégrée des dessins owner-drawn
Le dessin owner-drawn dans Windows Forms, qui est également appelé dessin personnalisé, est une technique permettant de changer l’apparence visuelle de certains contrôles.  
  
> [!NOTE]
>  Le mot « contrôle » dans cette rubrique est utilisé pour désigner les classes qui dérivent soit <xref:System.Windows.Forms.Control> ou <xref:System.ComponentModel.Component>.  
  
 En règle générale, Windows gère automatiquement la peinture à l’aide des paramètres de propriété tels que <xref:System.Windows.Forms.Control.BackColor%2A> pour déterminer l’apparence d’un contrôle. Avec le dessin owner-drawn, vous contrôlez le processus de dessin, en changeant l’apparence des éléments qui ne sont pas disponibles via des propriétés. Par exemple, de nombreux contrôles vous permettent de définir la couleur du texte qui s’affiche, mais vous êtes limité à une seule couleur. Le dessin owner-drawn vous permet d’effectuer des opérations comme afficher une partie du texte en noir et une autre en rouge.  
  
 Dans la pratique, le dessin owner-drawn est similaire au dessin de graphiques dans un formulaire. Par exemple, vous pouvez utiliser des méthodes graphiques dans un gestionnaire pour le formulaire <xref:System.Windows.Forms.Control.Paint> événement pour émuler un `ListBox` contrôle, mais vous seriez obligé d’écrire votre propre code pour gérer toutes les interactions utilisateur. Avec le dessin owner-drawn, le contrôle utilise votre code pour dessiner son contenu, mais il conserve par ailleurs toutes ses capacités intrinsèques. Vous pouvez utiliser des méthodes graphiques pour dessiner chaque élément du contrôle ou pour personnaliser certains aspects de chaque élément, tout en utilisant l’apparence par défaut pour d’autres aspects de chaque élément.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Dessin owner-drawn dans les contrôles Windows Forms  
 Pour effectuer du dessin owner-drawn dans les contrôles qui le prennent en charge, vous définissez généralement une propriété, et vous gérez un ou plusieurs événements.  
  
 La plupart des contrôles qui prennent en charge le dessin owner-drawn ont une propriété `OwnerDraw` ou `DrawMode` qui indique si le contrôle déclenche son ou ses événements de dessin quand il se dessine lui-même.  
  
 Les contrôles qui n’ont pas une propriété `OwnerDraw` ou `DrawMode` incluent le contrôle `DataGridView`, qui fournit des événements de dessin qui se produisent automatiquement, et le contrôle `ToolStrip`, qui est dessiné à l’aide d’une classe de rendu externe qui a ses propres événements de dessin.  
  
 Il existe de nombreux types d’événements de dessin, mais un événement de dessin se produit généralement pour dessiner un élément dans un contrôle. Le gestionnaire d’événements reçoit un objet `EventArgs` qui contient des informations sur l’élément dessiné et des outils que vous pouvez utiliser pour le dessiner. Par exemple, cet objet contient en général, numéro d’index de l’élément dans sa collection parente, un <xref:System.Drawing.Rectangle> qui indique l’élément affiche des limites et un <xref:System.Drawing.Graphics> pour appeler les méthodes de peinture. Pour certains événements, l’objet `EventArgs` fournit plus d’informations sur l’élément sur les méthodes que vous pouvez appeler pour dessiner certains aspects de l’élément par défaut, comme l’arrière-plan ou un rectangle de focus.  
  
 Pour créer un contrôle réutilisable contenant vos personnalisations owner-drawn, créez une classe qui dérive d’une classe de contrôle prenant en charge le dessin owner-drawn. Au lieu de gérer les événements de dessin, incluez votre code de dessin owner-drawn dans la ou les méthodes `On`*nom_événement* appropriées de la nouvelle classe. Vérifiez que vous appelez dans ce cas la ou les méthodes `On`*nom_événement* de la classe de base, pour que les utilisateurs de votre contrôle puissent gérer les événements de dessin owner-drawn et fournir une personnalisation supplémentaire.  
  
 Les contrôles Windows Forms suivants prennent en charge le dessin owner-drawn dans toutes les versions du .NET Framework :  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <xref:System.Windows.Forms.MenuItem> (utilisé par <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu>)  
  
- <xref:System.Windows.Forms.TabControl>  
  
 Les contrôles suivants prennent en charge le dessin owner-drawn uniquement dans le .NET Framework 2.0 :  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 Les contrôles suivants prennent en charge le dessin owner-drawn et sont Nouveautés dans .NET Framework 2.0 :  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 Les sections suivantes contiennent des informations détaillées supplémentaires pour chacun de ces contrôles.  
  
### <a name="listbox-and-combobox-controls"></a>Contrôles Edit et Combobox  
 Le <xref:System.Windows.Forms.ListBox> et <xref:System.Windows.Forms.ComboBox> vous permettent de dessiner des éléments individuels dans le contrôle tous dans la même taille ou dans des tailles différentes.  
  
> [!NOTE]
>  Bien que le <xref:System.Windows.Forms.CheckedListBox> contrôle est dérivé le <xref:System.Windows.Forms.ListBox> contrôle, il ne prend pas en charge owner-drawn.  
  
 Pour dessiner chaque élément de la même taille, définissez la `DrawMode` propriété <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> et gérer le `DrawItem` événement.  
  
 Pour dessiner chaque élément à l’aide d’une taille différente, définissez la `DrawMode` propriété <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> et gérer à la fois le `MeasureItem` et `DrawItem` événements. L’événement `MeasureItem` vous permet d’indiquer la taille d’un élément avant que l’événement `DrawItem` se produise pour cet élément.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques suivantes :  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [Guide pratique pour Créer du texte de taille Variable dans un contrôle ComboBox](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>MenuItem, composant  
 Le <xref:System.Windows.Forms.MenuItem> composant représente un élément de menu unique dans un <xref:System.Windows.Forms.MainMenu> ou <xref:System.Windows.Forms.ContextMenu> composant.  
  
 Pour dessiner un <xref:System.Windows.Forms.MenuItem>, définissez son `OwnerDraw` propriété `true` et gérer ses `DrawItem` événement. Pour personnaliser la taille de l’élément de menu avant que l’événement `DrawItem` se produise, gérez l’événement `MeasureItem` de l’élément.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl, contrôle  
 Le <xref:System.Windows.Forms.TabControl> contrôle vous permet de dessiner des onglets individuels dans le contrôle. Dessin owner-drawn affecte uniquement les onglets ; le <xref:System.Windows.Forms.TabPage> contenu n’est pas affecté.  
  
 Pour dessiner chaque onglet dans un <xref:System.Windows.Forms.TabControl>, définissez le `DrawMode` propriété <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> et gérer le `DrawItem` événement. Cet événement se produit une fois pour chaque onglet uniquement quand l’onglet est visible dans le contrôle.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip, composant  
 Le <xref:System.Windows.Forms.ToolTip> composant vous permet de dessiner l’info-bulle entière lorsqu’elle est affichée.  
  
 Pour dessiner un <xref:System.Windows.Forms.ToolTip>, définissez son `OwnerDraw` propriété `true` et gérer ses `Draw` événement. Pour personnaliser la taille de la <xref:System.Windows.Forms.ToolTip> avant la `Draw` événement se produise, gérez le `Popup` .PreviewKeyDown et définir le <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> propriété dans le Gestionnaire d’événements.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>Contrôle ListView  
 Le <xref:System.Windows.Forms.ListView> contrôle vous permet de dessiner des éléments individuels, des sous-éléments et des en-têtes de colonnes dans le contrôle.  
  
 Pour activer le dessin owner-drawn dans le contrôle, définissez la propriété `OwnerDraw` sur `true`.  
  
 Pour dessiner chaque élément dans le contrôle, gérez l’événement `DrawItem`.  
  
 Pour dessiner chaque sous-élément ou en-tête de colonne dans le contrôle lorsque la <xref:System.Windows.Forms.ListView.View%2A> propriété est définie sur <xref:System.Windows.Forms.View.Details>, gérer la `DrawSubItem` et `DrawColumnHeader` événements.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView, contrôle  
 Le <xref:System.Windows.Forms.TreeView> contrôle vous permet de dessiner des nœuds individuels dans le contrôle.  
  
 Pour dessiner uniquement le texte affiché dans chaque nœud, définissez la `DrawMode` propriété <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> et gérer le `DrawNode` événement pour dessiner le texte.  
  
 Pour dessiner tous les éléments de chaque nœud, définissez la `DrawMode` propriété <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> et gérer le `DrawNode` événements pour dessiner les éléments vous avez besoin, comme texte, des icônes, cases à cocher, signes, plus et moins et les lignes qui connectent les nœuds.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView, contrôle  
 Le <xref:System.Windows.Forms.DataGridView> contrôle vous permet de dessiner des cellules et des lignes dans le contrôle.  
  
 Pour dessiner des cellules individuelles, gérez l’événement `CellPainting`.  
  
 Pour dessiner des lignes individuelles ou des éléments de ligne, gérez un des événements `RowPrePaint` ou `RowPostPaint`, ou les deux. L’événement `RowPrePaint` se produit avant le dessin des cellules d’une ligne, et l’événement se produit `RowPostPaint` après le dessin des cellules. Vous pouvez gérer ces deux événements et l’événement `CellPainting` pour dessiner séparément l’arrière-plan de la ligne, les cellules individuelles et le premier plan de la ligne, ou vous pouvez fournir des personnalisations spécifiques là où vous en avez besoin et utiliser l’affichage par défaut pour les autres éléments de la ligne.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques suivantes :  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [Guide pratique pour Personnaliser l’apparence des cellules dans le contrôle de DataGridView Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [Guide pratique pour Personnaliser l’apparence des lignes dans le contrôle de DataGridView Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip, contrôle  
 <xref:System.Windows.Forms.ToolStrip> et les contrôles dérivés vous permettent de personnaliser n’importe quel aspect de leur apparence.  
  
 Pour fournir un rendu personnalisé pour <xref:System.Windows.Forms.ToolStrip> contrôles, définir le `Renderer` propriété d’un <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, ou <xref:System.Windows.Forms.ToolStripContentPanel> à un `ToolStripRenderer` de l’objet et de gérer une ou plusieurs des nombreux événements de dessin fournis par le `ToolStripRenderer` classe. Vous pouvez également définir un `Renderer` propriété à une instance de votre propre classe dérivée de `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, ou <xref:System.Windows.Forms.ToolStripSystemRenderer> qui implémente ou remplace spécifique `On` *EventName* méthodes.  
  
 Pour plus d’informations, notamment des exemples de code, consultez les rubriques suivantes :  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [Guide pratique pour Créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans les Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [Guide pratique pour Personnaliser le dessin d’un contrôle ToolStrip](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Voir aussi

- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
