---
title: Activer l’affichage en mosaïque dans le contrôle ListView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: a0429efaab14995ab1e3f3b0dfd91db61de72fbf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745807"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Comment : activer l'affichage en mosaïque dans un contrôle ListView Windows Forms à l'aide du concepteur
La fonctionnalité d’affichage en mosaïque du contrôle <xref:System.Windows.Forms.ListView> vous permet de fournir un équilibre visuel entre les informations graphiques et textuelles. Les informations textuelles affichées pour un élément dans l'affichage en mosaïque sont identiques aux informations de colonne définies pour le mode Détails. L’affichage en mosaïque fonctionne en association avec les fonctionnalités de regroupement ou de marque d’insertion dans le contrôle <xref:System.Windows.Forms.ListView>.

 L’affichage en mosaïque utilise une icône 32 x 32 et plusieurs lignes de texte, comme illustré dans l’image suivante.

 ![Affichage en mosaïque dans un contrôle ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Texte et icônes de l'affichage en mosaïque")

 Les propriétés et les méthodes de l’affichage en mosaïque vous permettent de spécifier les champs de colonne à afficher pour chaque élément, et de contrôler collectivement la taille et l’apparence de tous les éléments d’une fenêtre d’affichage en mosaïque. Pour plus de clarté, la première ligne de texte dans une vignette est toujours le nom de l’élément ; elle ne peut pas être modifiée.

 La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.ListView>. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-set-tile-view-in-the-designer"></a>Pour définir l’affichage en mosaïque dans le concepteur

1. Dans Visual Studio, sélectionnez le contrôle <xref:System.Windows.Forms.ListView> de votre formulaire.

2. Dans la fenêtre **Propriétés** , sélectionnez la propriété <xref:System.Windows.Forms.ListView.View%2A> et choisissez **mosaïque**.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
