---
title: Support bidirectionnel
ms.date: 09/30/2017
helpviewer_keywords:
- globalization [Windows Forms], bi-directional support in Windows
- Windows Forms, international
- localization [Windows Forms], bi-directional support in Windows
- bi-directional language support [Windows Forms], Windows applications
- Windows Forms, bi-directional support
ms.openlocfilehash: 8b2e842fc08be78b74cede85927352fafca7bc8f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742080"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Prise en charge bidirectionnelle pour les applications Windows Forms
Vous pouvez utiliser Visual Studio pour créer des applications Windows qui prennent en charge les langues bidirectionnelles (de droite à gauche), telles que l’arabe et l’hébreu. Cela comprend les formulaires standard, les boîtes de dialogue, les formulaires MDI et tous les contrôles que vous pouvez utiliser dans ces formulaires, c'est-à-dire tous les objets de l'espace de noms <xref:System.Windows.Forms.Control>.

## <a name="culture-support"></a>Prise en charge de la culture
 La culture et les paramètres de culture d'interface utilisateur déterminent comment une application gère les dates, heures, devises et autres informations. La prise en charge de la culture et de la culture d'interface utilisateur pour les langues bidirectionnelles est identique à celle des autres langues. Pour plus d’informations, consultez [classes spécifiques à la culture pour les Windows Forms et Web Forms globaux](/visualstudio/ide/globalizing-and-localizing-applications).

## <a name="righttoleft-and-righttoleftlayout-properties"></a>Propriétés RightToLeft et RightToLeftLayout
 La classe de base <xref:System.Windows.Forms.Control>, à partir de laquelle les formulaires dérivent, comprend une propriété <xref:System.Windows.Forms.Control.RightToLeft%2A> que vous pouvez définir pour modifier l'ordre de lecture d'un formulaire et de ses contrôles. Si vous définissez la propriété <xref:System.Windows.Forms.Control.RightToLeft%2A> du formulaire, par défaut les contrôles sur le formulaire héritent de ce paramètre. Toutefois, vous pouvez également définir la propriété <xref:System.Windows.Forms.Control.RightToLeft%2A> individuellement sur la plupart des contrôles. Consultez aussi [Comment : afficher du texte de droite à gauche dans les Windows Forms pour la globalisation](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100)).

 L'effet de la propriété <xref:System.Windows.Forms.Control.RightToLeft%2A> peut varier d'un contrôle à un autre. Dans certains contrôles, la propriété définit uniquement l'ordre de lecture, comme dans les contrôles <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.TreeView> et <xref:System.Windows.Forms.ToolTip>. Dans d'autres, la propriété <xref:System.Windows.Forms.Control.RightToLeft%2A> modifie à la fois l'ordre de lecture et la disposition. Cela comprend les contrôles <xref:System.Windows.Forms.RadioButton>, <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.CheckBox> D'autres contrôles exigent que la propriété <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> soit appliquée pour refléter sa disposition de droite à gauche. Le tableau suivant fournit des détails sur la manière dont les propriétés <xref:System.Windows.Forms.Control.RightToLeft%2A> et <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> affectent les différents contrôles Windows Forms.

|Contrôle/composant|Effet de la propriété RightToLeft|Effet de la propriété RightToLeftLayout|Nécessite l'effet miroir ?|
|------------------------|------------------------------------|------------------------------------------|-------------------------|
|<xref:System.Windows.Forms.Button>|Définit l'ordre de lecture de droite à gauche. Inverse <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>, <xref:System.Windows.Forms.ButtonBase.ImageAlign%2A>, et <xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|Aucun effet|Non|
|<xref:System.Windows.Forms.CheckBox>|La case à cocher est affichée à droite du texte|Aucun effet|Non|
|<xref:System.Windows.Forms.CheckedListBox>|Toutes les cases à cocher sont affichées à droite du texte|Aucun effet|Non|
|<xref:System.Windows.Forms.ColorDialog>|Pas affecté ; dépend de la langue du système d'exploitation|Aucun effet|Non|
|<xref:System.Windows.Forms.ComboBox>|Les éléments dans le contrôle de zone de liste déroulante sont alignés à droite|Aucun effet|Non|
|<xref:System.Windows.Forms.ContextMenu>|Apparaît aligné à droite avec l'ordre de lecture de droite à gauche|Aucun effet|Non|
|<xref:System.Windows.Forms.DataGrid>|Apparaît aligné à droite avec l'ordre de lecture de droite à gauche|Aucun effet|Non|
|<xref:System.Windows.Forms.DataGridView>|Affecte à la fois l'ordre de lecture de droite à gauche et la disposition des contrôles|Aucun effet|Non|
|<xref:System.Windows.Forms.DateTimePicker>|Pas affecté ; dépend de la langue du système d'exploitation|Applique un effet miroir sur le contrôle|Oui|
|<xref:System.Windows.Forms.DomainUpDown>|Aligne à gauche les boutons Haut et Bas|Aucun effet|Non|
|<xref:System.Windows.Forms.ErrorProvider>|Non pris en charge|Aucun effet|Non|
|<xref:System.Windows.Forms.FontDialog>|Dépend de la langue du système d'exploitation|Aucun effet|Non|
|<xref:System.Windows.Forms.Form>|Définit l'ordre de lecture de droite à gauche et inverse les barres de défilement|Applique un effet miroir sur le formulaire|Oui|
|<xref:System.Windows.Forms.GroupBox>|La légende est alignée à droite. Les contrôles enfants peuvent hériter de cette propriété.|Utilisez un <xref:System.Windows.Forms.TableLayoutPanel> dans le contrôle pour la prise en charge de l'effet miroir de droite à gauche|Non|
|<xref:System.Windows.Forms.HScrollBar>|Commence avec la case de défilement (curseur) alignée à droite|Aucun effet|Non|
|<xref:System.Windows.Forms.ImageList>|Non nécessaire|Aucun effet|Non|
|<xref:System.Windows.Forms.Label>|Aligné à droite. Inverse <xref:System.Windows.Forms.Label.TextAlign%2A> et <xref:System.Windows.Forms.Label.ImageAlign%2A>|Aucun effet|Non|
|<xref:System.Windows.Forms.LinkLabel>|Aligné à droite. Inverse <xref:System.Windows.Forms.Label.TextAlign%2A> et <xref:System.Windows.Forms.Label.ImageAlign%2A>|Aucun effet|Non|
|<xref:System.Windows.Forms.ListBox>|Les éléments sont alignés à droite|Aucun effet|Non|
|<xref:System.Windows.Forms.ListView>|Définit l'ordre de lecture de droite à gauche ; les éléments restent alignés à gauche|Applique un effet miroir sur le contrôle|Oui|
|<xref:System.Windows.Forms.MainMenu>|Aligné à droite avec l'ordre de lecture de droite à gauche au moment de l'exécution (et non au moment du design)|Aucun effet|Non|
|<xref:System.Windows.Forms.MaskedTextBox>|Affiche le texte de droite à gauche.|Aucun effet|Non|
|<xref:System.Windows.Forms.MonthCalendar>|Pas affecté ; dépend de la langue du système d'exploitation|Applique un effet miroir sur le contrôle|Oui|
|<xref:System.Windows.Forms.NotifyIcon>|Non pris en charge|Non pris en charge|Non|
|<xref:System.Windows.Forms.NumericUpDown>|Les boutons Haut et Bas sont alignés à gauche|Aucun effet|Non|
|<xref:System.Windows.Forms.OpenFileDialog>|Sur les systèmes d’exploitation de droite à gauche, la définition de la propriété <xref:System.Windows.Forms.Control.RightToLeft> du formulaire conteneur sur <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> localise la boîte de dialogue |Aucun effet|Non|
|<xref:System.Windows.Forms.PageSetupDialog>|Pas affecté ; dépend de la langue du système d'exploitation|Aucun effet|Non|
|<xref:System.Windows.Forms.Panel>|Les contrôles enfants peuvent hériter de cette propriété|Utilisez un <xref:System.Windows.Forms.TableLayoutPanel> dans le contrôle pour la prise en charge de l'effet miroir de droite à gauche|Oui|
|<xref:System.Windows.Forms.PictureBox>|Non pris en charge|Aucun effet|Non|
|<xref:System.Windows.Forms.PrintDialog>|Pas affecté ; dépend de la langue du système d'exploitation|Aucun effet|Non|
|<xref:System.Drawing.Printing.PrintDocument>|La barre de défilement verticale est alignée à gauche et la barre de défilement horizontale commence à gauche|Aucun effet|Non|
|<xref:System.Windows.Forms.PrintPreviewDialog>|Non pris en charge|Non pris en charge|Non|
|<xref:System.Windows.Forms.ProgressBar>|Non affecté par cette propriété|Applique un effet miroir sur le contrôle|Oui|
|<xref:System.Windows.Forms.RadioButton>|La case d'option est affichée à droite du texte|Aucun effet|Non|
|<xref:System.Windows.Forms.RichTextBox>|Les éléments du contrôle qui comportent du texte sont affichés de droite à gauche avec l'ordre de lecture de droite à gauche|Aucun effet|Non|
|<xref:System.Windows.Forms.SaveFileDialog>|Pas affecté ; dépend de la langue du système d'exploitation|Aucun effet|Non|
|<xref:System.Windows.Forms.SplitContainer>|La disposition du panneau est inversée ; la barre de défilement verticale est affichée à gauche ; la barre de défilement horizontale commence à droite|Utilisez un <xref:System.Windows.Forms.TableLayoutPanel> pour appliquer un effet miroir à l'ordre des contrôles enfants|Non|
|<xref:System.Windows.Forms.Splitter>|Non pris en charge|Aucun effet|Non|
|<xref:System.Windows.Forms.StatusBar>|Non pris en charge ; utilisez plutôt <xref:System.Windows.Forms.StatusStrip>|Aucun effet ; utilisez plutôt <xref:System.Windows.Forms.StatusStrip>|Non|
|<xref:System.Windows.Forms.TabControl>|Non affecté par cette propriété|Applique un effet miroir sur le contrôle|Oui|
|<xref:System.Windows.Forms.TextBox>|Affiche le texte de droite à gauche avec l'ordre de lecture de droite à gauche|Aucun effet|Non|
|<xref:System.Windows.Forms.Timer>|Non nécessaire|Non nécessaire|Non|
|<xref:System.Windows.Forms.ToolBar>|Non affecté par cette propriété ; utilisez plutôt <xref:System.Windows.Forms.ToolStrip>|Aucun effet ; utilisez plutôt <xref:System.Windows.Forms.ToolStrip>|Oui|
|<xref:System.Windows.Forms.ToolTip>|Définit l'ordre de lecture de droite à gauche|Aucun effet|Non|
|<xref:System.Windows.Forms.TrackBar>|Le défilement ou le suivi commence à droite ; quand <xref:System.Windows.Forms.TrackBar.Orientation%2A> est verticale, les graduations commencent à droite|Aucun effet|Non|
|<xref:System.Windows.Forms.TreeView>|Définit l'ordre de lecture de droite à gauche uniquement|Applique un effet miroir sur le contrôle|Oui|
|<xref:System.Windows.Forms.UserControl>|La barre de défilement verticale est affichée à gauche ; la barre de défilement horizontale possède un curseur à droite|Aucune prise en charge directe ; utilisez un <xref:System.Windows.Forms.TableLayoutPanel>|Non|
|<xref:System.Windows.Forms.VScrollBar>|Affiché sur le côté gauche plutôt que sur le côté droit des contrôles à défilement|Aucun effet|Non|

## <a name="encoding"></a>Encodage
 Les Windows Forms prennent en charge Unicode. Vous pouvez donc inclure n'importe quel jeu de caractères quand vous créez des applications bidirectionnelles. Toutefois, les contrôles Windows Forms ne prennent pas tous en charge Unicode sur toutes les plateformes.

## <a name="gdi"></a>GDI+
 Vous pouvez utiliser GDI+ pour dessiner du texte avec un ordre de lecture de droite à gauche. La méthode <xref:System.Drawing.Graphics.DrawString%2A>, qui sert à dessiner du texte, prend en charge un paramètre `StringFormat` auquel vous pouvez affecter comme valeur le membre <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> de l'énumération <xref:System.Drawing.StringFormatFlags> pour inverser le point d'origine du texte.

## <a name="common-dialog-boxes"></a>Boîtes de dialogue communes
 Les outils système tels que la boîte de dialogue Ouvrir le fichier sont sous le contrôle de Windows. Ils héritent des éléments linguistiques du système d'exploitation. Si vous utilisez une version de Windows avec les paramètres linguistiques corrects, ces boîtes de dialogue fonctionneront correctement avec les langues bidirectionnelles.

 De même, les boîtes de message passent par le système d'exploitation et prennent en charge le texte bidirectionnel. Les légendes des boutons des boîtes de message sont basées sur le paramètre de langue actif. Par défaut, les boîtes de message n'utilisent pas l'ordre de lecture de droite à gauche, mais vous pouvez spécifier un paramètre pour modifier l'ordre de lecture quand les boîtes de message sont affichées.

## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft, barres de défilement et ScrollableControl
 Il existe actuellement une limitation dans les Windows Forms qui empêche toutes les classes dérivées de <xref:System.Windows.Forms.ScrollableControl> de se comporter correctement quand la propriété <xref:System.Windows.Forms.Control.RightToLeft%2A> est activée et que <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> a la valeur <xref:System.Windows.Forms.RightToLeft.Yes>. Par exemple, supposez que vous placez un contrôle tel que <xref:System.Windows.Forms.Panel> ou une classe de conteneur dérivée de <xref:System.Windows.Forms.Panel> (telle que <xref:System.Windows.Forms.FlowLayoutPanel> ou <xref:System.Windows.Forms.TableLayoutPanel>) sur votre formulaire. Si vous affectez la valeur <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> à la propriété <xref:System.Windows.Forms.RightToLeft.Yes> sur le conteneur et que vous affectez ensuite la valeur <xref:System.Windows.Forms.Control.Anchor%2A> à la propriété <xref:System.Windows.Forms.AnchorStyles.Right> sur un ou plusieurs des contrôles à l'intérieur du conteneur, aucune barre de défilement n'est jamais affichée. La classe dérivée de <xref:System.Windows.Forms.ScrollableControl> se comporte comme si <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> avait la valeur <xref:System.Windows.Forms.RightToLeft.No>.

 Actuellement, la seule solution de contournement consiste à imbriquer le <xref:System.Windows.Forms.ScrollableControl> à l'intérieur d'un autre <xref:System.Windows.Forms.ScrollableControl>. Par exemple, si vous souhaitez que <xref:System.Windows.Forms.TableLayoutPanel> fonctionne dans cette situation, vous pouvez le placer à l'intérieur d'un contrôle <xref:System.Windows.Forms.Panel> et affecter la valeur <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> à la propriété <xref:System.Windows.Forms.Panel> sur le <xref:System.Windows.Forms.RightToLeft.Yes>.

## <a name="mirroring"></a>Mise en miroir
 Appliquer un *effet miroir* signifie inverser la disposition des éléments d'interface utilisateur pour qu'ils se présentent de droite à gauche. Dans un Windows Form en miroir, par exemple, les boutons Réduire, Agrandir et Fermer sont affichés tout à gauche dans la barre de titre, et non à droite.

 L'affectation de la valeur <xref:System.Windows.Forms.Control.RightToLeft%2A> à la propriété `true` d'un formulaire ou d'un contrôle inverse l'ordre de lecture des éléments sur un formulaire, mais ce paramètre n'inverse pas la disposition pour qu'elle soit de droite à gauche, autrement dit il ne provoque pas d'effet miroir. Par exemple, la définition de cette propriété ne déplace pas les boutons **Réduire**, **Agrandir** et **Fermer** de la barre de titre du formulaire vers le côté gauche du formulaire. De même, certains contrôles tels que le contrôle <xref:System.Windows.Forms.TreeView> nécessitent l'application de l'effet miroir pour modifier et adapter leur affichage à l'arabe ou l'hébreu. Vous pouvez appliquer un effet miroir sur ces contrôles en définissant la propriété <xref:System.Windows.Forms.Form.RightToLeftLayout%2A>.

 Vous pouvez créer des versions miroir des contrôles suivants :

- <xref:System.Windows.Forms.ColumnHeader.ListView%2A>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TabPage>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.TreeView>

 Certains contrôles sont scellés, ce qui signifie que vous ne pouvez pas dériver un nouveau contrôle à partir d'eux. Il s'agit entre autres des contrôles <xref:System.Windows.Forms.ImageList> et <xref:System.Windows.Forms.ProgressBar>.

## <a name="see-also"></a>Voir aussi

- [Prise en charge bidirectionnelle pour les applications web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/6eedwbtt(v=vs.100))
