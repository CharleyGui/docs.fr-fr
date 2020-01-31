---
title: Scénarios du contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: 160d967c6445fb753cb6c73babfb02a734a07e28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742462"
---
# <a name="datagridview-control-scenarios-windows-forms"></a>Scénarios du contrôle DataGridView (Windows Forms)
Avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez afficher des données tabulaires à partir de diverses sources de données. Pour des utilisations simples, vous pouvez remplir manuellement un <xref:System.Windows.Forms.DataGridView> et manipuler les données directement par le biais du contrôle. En règle générale, toutefois, vous allez stocker vos données dans une source de données externe et y lier le contrôle via un composant <xref:System.Windows.Forms.BindingSource>.  
  
 Cette rubrique décrit quelques-uns des scénarios courants qui impliquent le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>Scénario 1 : affichage de petites quantités de données  
 Vous n’avez pas besoin de stocker vos données dans une source de données externe pour les afficher dans le contrôle <xref:System.Windows.Forms.DataGridView>. Si vous travaillez avec une petite quantité de données, vous pouvez remplir le contrôle vous-même et manipuler les données par le biais du contrôle. C’est ce que l’on appelle le *mode indépendant*. Pour plus d’informations, consultez [Comment : créer un contrôle DataGridView Windows Forms indépendant](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Points clés du scénario  
  
- En mode indépendant, vous remplissez le contrôle manuellement.  
  
- Le mode indépendant est particulièrement adapté pour les petites quantités de données en lecture seule.  
  
- Le mode indépendant est également adapté aux tables similaires à des feuilles de calcul ou à des tables peu peuplées.  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>Scénario 2 : affichage et mise à jour des données stockées dans une source de données externe  
 Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.DataGridView> comme une interface utilisateur via laquelle les utilisateurs peuvent accéder aux données conservées dans une source de données telle qu’une table de base de données ou une collection d’objets métier. Pour plus d’informations, consultez [Comment : lier des données au contrôle DataGridView Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Points clés du scénario  
  
- Le mode lié vous permet de vous connecter à une source de données, de générer automatiquement des colonnes en fonction des propriétés de la source de données ou des colonnes de base de données, et de remplir automatiquement le contrôle.  
  
- Le mode lié est adapté à une forte interaction avec les données de l’utilisateur. Les données peuvent être mises en forme pour l’affichage, et les données spécifiées par l’utilisateur peuvent être analysées dans le format attendu par la source de données. Les erreurs de mise en forme des entrées de données et les erreurs de contrainte de base de données peuvent être détectées afin que les utilisateurs puissent être avertis et que des cellules erronées puissent être corrigées.  
  
- Des fonctionnalités supplémentaires, telles que le tri, le gel et la réorganisation des colonnes, permettent aux utilisateurs d’afficher les données de la manière la plus pratique pour leur flux de travail.  
  
- La prise en charge du presse-papiers permet aux utilisateurs de copier des données de votre application dans d’autres applications.  
  
## <a name="scenario-3-advanced-data"></a>Scénario 3 : données avancées  
 Si vous avez des besoins spéciaux que le modèle de liaison de données standard ne traite pas, vous pouvez gérer l’interaction entre le contrôle et vos données en implémentant le *mode virtuel*. L’implémentation du mode virtuel consiste à implémenter un ou plusieurs gestionnaires d’événements qui permettent au contrôle de demander des informations sur les cellules lorsque les informations sont nécessaires.  
  
 Par exemple, si vous travaillez avec de grandes quantités de données, vous souhaiterez peut-être implémenter le mode virtuel pour garantir une efficacité optimale. Le mode virtuel est également utile pour gérer les valeurs des colonnes indépendantes que vous affichez, ainsi que les colonnes extraites d’une autre source de données.  
  
 Pour plus d’informations sur le mode virtuel, consultez [procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Points clés du scénario  
  
- Le mode virtuel est adapté à l’affichage de très grandes quantités de données lorsque vous devez affiner les performances.  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>Scénario 4 : redimensionnement automatique des lignes et des colonnes  
 Lorsque vous affichez des données régulièrement mises à jour, vous pouvez redimensionner automatiquement les lignes et les colonnes pour vous assurer que tout le contenu est visible. Le contrôle <xref:System.Windows.Forms.DataGridView> fournit plusieurs options qui vous permettent d’activer ou de désactiver le redimensionnement manuel, de le redimensionner par programmation à des moments spécifiques ou de le redimensionner automatiquement chaque fois que le contenu est modifié. Pour plus d’informations, consultez [options de dimensionnement dans le contrôle DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Points clés du scénario  
  
- Le redimensionnement manuel permet aux utilisateurs d’ajuster la hauteur et la largeur des cellules.  
  
- Le redimensionnement automatique vous permet de conserver les tailles des cellules afin que le contenu des cellules ne soit jamais coupé.  
  
- Le redimensionnement par programmation vous permet de redimensionner des cellules à des moments spécifiques afin d’éviter une altération des performances du redimensionnement automatique continu.  
  
## <a name="scenario-5-simple-customization"></a>Scénario 5 : personnalisation simple  
 Le contrôle <xref:System.Windows.Forms.DataGridView> vous offre de nombreuses façons de modifier son apparence et son comportement de base. Pour plus d’informations, consultez [styles de cellule dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Points clés du scénario  
  
- les objets <xref:System.Windows.Forms.DataGridViewCellStyle> vous permettent de fournir des informations de couleur, de police, de mise en forme et de positionnement à plusieurs niveaux et à des éléments individuels du contrôle.  
  
- Les styles de cellules peuvent être superposés et partagés par plusieurs éléments, ce qui vous permet de réutiliser le code.  
  
## <a name="scenario-6-advanced-customization"></a>Scénario 6 : personnalisation avancée  
 Le contrôle <xref:System.Windows.Forms.DataGridView> vous offre de nombreuses façons de personnaliser son apparence et son comportement.  
  
### <a name="scenario-key-points"></a>Points clés du scénario  
  
- Vous pouvez fournir votre propre code de peinture de cellule. Pour plus d’informations, consultez [Comment : personnaliser l’apparence des cellules dans le contrôle DataGridView Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md).  
  
- Vous pouvez fournir votre propre peinture de ligne. Cela est utile, par exemple, pour créer des lignes avec du contenu qui s’étend sur plusieurs colonnes. Pour plus d’informations, consultez [Comment : personnaliser l’apparence des lignes dans le contrôle DataGridView Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md).  
  
- Vous pouvez implémenter vos propres classes de cellule et de colonne pour personnaliser l’apparence des cellules. Pour plus d’informations, consultez [Comment : personnaliser des cellules et des colonnes dans le contrôle DataGridView Windows Forms en étendant leur comportement et leur apparence](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
- Vous pouvez implémenter vos propres classes de cellule et de colonne pour héberger des contrôles autres que ceux fournis par les types de colonne intégrés. Pour plus d’informations, consultez [Comment : héberger des contrôles dans Windows Forms des cellules DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Vue d’ensemble du contrôle DataGridView](datagridview-control-overview-windows-forms.md)
