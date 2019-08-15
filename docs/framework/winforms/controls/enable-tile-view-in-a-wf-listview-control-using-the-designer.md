---
title: 'Procédure : activer le mode Mosaïque dans un contrôle ListView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 8a45a8a484bd373f53585b1b113a51e59b30fca2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040365"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Procédure : activer le mode Mosaïque dans un contrôle ListView Windows Forms à l’aide du concepteur
La fonctionnalité d’affichage en mosaïque <xref:System.Windows.Forms.ListView> du contrôle vous permet de fournir un équilibre visuel entre les informations graphiques et textuelles. Les informations textuelles affichées pour un élément dans l'affichage en mosaïque sont identiques aux informations de colonne définies pour le mode Détails. L’affichage en mosaïque fonctionne en association avec les fonctionnalités de regroupement ou de marque d' <xref:System.Windows.Forms.ListView> insertion dans le contrôle.

 L’affichage en mosaïque utilise une icône 32 x 32 et plusieurs lignes de texte, comme illustré dans l’image suivante.

 ![Affichage en mosaïque dans un contrôle ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Icônes et texte de l’affichage en mosaïque")

 Les propriétés et les méthodes de l’affichage en mosaïque vous permettent de spécifier les champs de colonne à afficher pour chaque élément, et de contrôler collectivement la taille et l’apparence de tous les éléments d’une fenêtre d’affichage en mosaïque. Pour plus de clarté, la première ligne de texte dans une vignette est toujours le nom de l’élément; elle ne peut pas être modifiée.

 La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.ListView> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

> [!NOTE]
> L'affichage en mosaïque est disponible uniquement sur [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quand votre application appelle la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Sur les systèmes d'exploitation antérieurs, tout code lié à l'affichage en mosaïque n'a aucun effet et le contrôle <xref:System.Windows.Forms.ListView> s'affiche en mode Grandes icônes. Pour plus d'informations, consultez <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.

## <a name="to-set-tile-view-in-the-designer"></a>Pour définir l’affichage en mosaïque dans le concepteur

1. Dans Visual Studio, sélectionnez le <xref:System.Windows.Forms.ListView> contrôle dans votre formulaire.

2. Dans la fenêtre **Propriétés** , sélectionnez la <xref:System.Windows.Forms.ListView.View%2A> propriété et choisissez **mosaïque**.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
