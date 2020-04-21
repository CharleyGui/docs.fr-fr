---
title: Windows forme des améliorations d’accessibilité
description: Découvrez comment les formulaires Windows Core .NET tentent d’améliorer l’accessibilité par rapport aux formulaires Windows-cadre .NET.
ms.date: 04/20/2020
helpviewer_keywords:
- Windows Forms accessibility
- accessibility
author: M-Lipin
ms.openlocfilehash: 30eb8b3bd0aaf646ea23f4f036e822f9bba78dc4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739751"
---
# <a name="accessibility-improvements-in-windows-forms-controls-for-net-core-30"></a>Améliorations d’accessibilité dans les contrôles des formulaires Windows pour .NET Core 3.0

Windows Forms continue d’améliorer son fonctionnement avec les technologies d’accessibilité afin de mieux prendre en charge les clients de Windows Forms. Ces améliorations incluent notamment les changements suivants :

- Changements dans divers domaines d’interaction avec les applications des clients d’accessibilité, y compris Narrateur.
- Changements dans la hiérarchie accessible (amélioration de la navigation dans l’arborescence UI Automation).
- Changements dans la navigation du clavier.

> [!IMPORTANT]
> Les modifications d’accessibilité apportées dans le cadre .NET 4.7.1 par .NET Framework 4.8 sont incluses dans .NET Core 3.0 et plus, et sont activées par défaut. Le cadre .NET a pris en charge les commutateurs de compatibilité qui permettaient aux applications de se retirer du nouveau comportement d’accessibilité. D’autre part, .NET Core ne prend pas en charge ces paramètres et ne permet pas aux applications de se retirer du comportement d’accessibilité.
  
À partir de .NET Core 3.0, les applications Windows Forms bénéficient de toutes les nouvelles fonctionnalités d’accessibilité (introduites dans .NET Framework 4.7.1 - 4.8) sans configuration supplémentaire.

## <a name="listbox-accessibility-support"></a>Support ListBox Accessibilité

Les modifications suivantes <xref:System.Windows.Forms.ListBox> s’appliquent au contrôle :

- Prise en charge `ListBox` de contrôle de l’interface utilisateur activée par l’interface utilisateur.
- Améliorer `ListBox` le soutien <xref:System.Windows.Automation.ScrollItemPattern> à `ListBox` l’accessibilité en ajoutant les éléments et en améliorant l’élévation et la manipulation des événements d’accessibilité et la navigation Narrator à travers les éléments (la navigation de verrouillage des bouchons n’est pas correcte et ne jette pas la navigation en dehors du contrôle involontairement).

## <a name="checkedlistbox-accessibility-support"></a>Support d’accessibilité CheckedListBox

Les modifications suivantes <xref:System.Windows.Forms.CheckedListBox> s’appliquent au contrôle :

- Bounds corrigées `CheckedListBox` fournies par les propriétés d’accessibilité pour les entrées.
- Amélioration `ListBox` de `CheckedListBox` l’ensemble et de l’accessibilité : la valeur des propriétés corrigées et le modèle d’événement.

## <a name="combobox-accessibility-support"></a>Support d’accessibilité ComboBox

Les modifications suivantes <xref:System.Windows.Forms.ComboBox> s’appliquent au contrôle :

- Mise à jour `ComboBox` du processus d’obtention d’objets d’accessibilité des éléments pour permettre de générer <xref:System.Object.GetHashCode%2A> des pièces d’ID pour les articles au lieu d’obtenir des codes de hachage à partir d’éléments, ce qui peut être dangereux au cas où la fonction est remplacée.

## <a name="datagridview-accessibility-support"></a>Support d’accessibilité DataGridView

Les modifications suivantes <xref:System.Windows.Forms.DataGridView> s’appliquent au contrôle :

- Corrigé `DataGridView.Bounds` par les propriétés d’accessibilité pour les colonnes, les lignes, les cellules et les en-têtes correspondants, amélioration des performances du calcul du rectangle de délimitation. Toutes les limites d’accessibilité sont représentées correctement en tenant compte des limites de l’ensemble du contrôle, ainsi que de son viewport.
- Valeur `Value.IsReadOnly` de propriété corrigée fournissant pour des applications accessibles de client. La propriété affiche `IsReadOnly` maintenant un statut correct pour les cellules.
- Correction du <xref:System.Windows.Forms.DataGridView.CellParsing> problème avec la levée d’événements pour le premier changement de cellule. La valeur cellulaire peut être modifiée `DataGridView` sans aucun problème, y compris la première interaction de contrôle.
- Amélioration `DataGridView` du contraste de couleur de fond lors de l’utilisation de thèmes Windows High Contrast. Modification `DataGridView` de la couleur du dos par défaut lors de l’utilisation de thèmes HC-1, HC-2 et HC Black.

## <a name="propertygrid-accessibility-support"></a>Soutien à l’accessibilité PropertyGrid

Les modifications suivantes <xref:System.Windows.Forms.PropertyGrid> s’appliquent au contrôle :

- Corrigé `PropertyGrid.Bounds` fourni par les propriétés d’accessibilité pour les entrées de grille, amélioration des performances du calcul du rectangle de délimitation. Pour l’instant, toutes les limites d’accessibilité sont représentées correctement en tenant compte des limites de l’ensemble du contrôle, ainsi que de son viewport.
- Noms et descriptions accessibles corrigés des sous-controverses pour ne pas inclure les noms de type de contrôle et pour éviter la double annonce pour les noms de type de contrôle.

## <a name="toolstrip-accessibility-support"></a>Appui à l’accessibilité ToolStrip

Les modifications suivantes <xref:System.Windows.Forms.ToolStrip> s’appliquent au contrôle :

- Amélioration de `ToolStrip` `MenuStrip`la `StatusStrip` navigation à travers , , et les éléments. Navigation `ToolStrip` `MenuStrip` corrigée et décalée, rétro-looping les éléments de menu lorsque le décalage-tab up-arrow est pressé, qui navigue à l’élément de menu inférieur.
- Amélioration `MenuStrip` de la navigation accessible, des types de contrôle accessibles au menu corrigé pour les sous-hommes pour faire sous-genre de type 'Menu' au lieu de 'MenuItem'.

## <a name="printpreviewcontrol-and-printpreviewdialog-accessibility-support"></a>Support d’accessibilité PrintPreviewControl et PrintPreviewDialog

Les modifications suivantes s’appliquent aux commandes d’impression :

- Amélioration de la navigation accessible (y compris la navigation Narrateur) grâce à des éléments de menu.
- Amélioration du soutien des thèmes à contraste élevé et a rendu l’élément de contrôle plus contrasté.

## <a name="stringcollectioneditor-accessibility-support"></a>Soutien à l’accessibilité stringCollectionEditor

Windows Forms designer utilise maintenant l’éditeur de la collection de cordes avec un meilleur support d’accessibilité.

## <a name="monthcalendar-accessibility-support-available-in-net-core-31"></a>MonthCalendar Soutien à l’accessibilité (disponible en .NET Core 3.1)

Les modifications suivantes <xref:System.Windows.Forms.MonthCalendar> s’appliquent au contrôle :

- Ajout de fournisseurs de `MonthCalendar` serveurs UI Automation pour contrôler, ajouté le modèle UI Automation Grid et les fournisseurs de modèles de table.
- Changement de type _de contrôle_ accessible au calendrier du type de contrôle accessible au _calendrier,_ `MonthCalendar` sauf le cas où le contrôle a un contrôle d’étiquette précédent qui définit `MonthCalendar` le nom accessible de contrôle, dans ce cas spécifique, le type de contrôle accessible devient _table._
- Amélioration de l’annonce de la date de `MonthCalendar` contrôle choisie.
- Amélioration `MonthCalendar` du soutien de contrôle pour les lecteurs d’écran et autres outils d’accessibilité. En ce moment, les utilisateurs peuvent naviguer dans les éléments de contrôle et interagir avec ces éléments à l’aide d’entrées clavier uniquement. Avec Narrator, utilisez des touches CAPS et flèches pour naviguer à travers les éléments de contrôle et CAPS - Entrez pour invoquer l’action par défaut de l’élément.
- Amélioration de la `MonthCalendar` navigation des clés de flèche à travers les éléments de l’enfant avec un rectangle de mise au point : rectangle de mise au point bleu pour Narrateur.
- Amélioration de l’accessibilité `MonthCalendar` pour les `MonthCalendar` mesures de test à succès pour les éléments de contrôle afin de permettre d’obtenir l’élément accessible à l’enfant par les coordonnées fournies.

## <a name="tooltips-accessibility-available-in-net-core-31"></a>ToolTips accessibilité (disponible en .NET Core 3.1)

- Capacité supplémentaire d’annoncer un texte tooltip par des applications de lecteur d’écran telles que NVDA et Narrateur. L’application de lecteur d’écran peut maintenant annoncer le texte du clavier ou de la souris tooltip de n’importe quel contrôle de formulaires de Windows qui a configuré pour afficher des outils.

## <a name="ui-automation-support-for-datagridview-propertygrid-listbox-combobox-toolstrip-and-other-controls"></a>Support d’automatisation de l’interface utilisateur pour DataGridView, PropertyGrid, ListBox, ComboBox, ToolStrip et d’autres contrôles

Le support UI Automation est activé pour les contrôles à l’heure d’exécution, mais n’est pas utilisé pendant le temps de conception. Pour une vue d’ensemble d’UI Automation, consultez la [Vue d’ensemble d’UI Automation](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).

## <a name="see-also"></a>Voir aussi

- [Pratiques exemplaires en matière d’accessibilité](../ui-automation/accessibility-best-practices.md).
