---
title: Vue d'ensemble du composant ImageList
ms.date: 03/30/2017
f1_keywords:
- ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
ms.openlocfilehash: b46204375cb046d637f4c9e1d888f37d10ea1f57
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728101"
---
# <a name="imagelist-component-overview-windows-forms"></a>Vue d'ensemble du composant ImageList (Windows Forms)

Le composant Windows Forms <xref:System.Windows.Forms.ImageList> sert à stocker des images, qui peuvent ensuite être affichées par des contrôles. Une liste d'images vous permet d'écrire du code pour un catalogue d'images unique et cohérent. Par exemple, vous pouvez faire pivoter les images affichées par un contrôle <xref:System.Windows.Forms.Button> simplement en modifiant la propriété <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> ou <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> du bouton. Vous pouvez aussi associer la même liste d'images à plusieurs contrôles. Par exemple, si vous utilisez à la fois un contrôle <xref:System.Windows.Forms.ListView> et un contrôle <xref:System.Windows.Forms.TreeView> pour afficher la même liste de fichiers, la modification de l'icône d'un fichier dans la liste d'images provoque l'affichage de la nouvelle icône dans les deux vues.

## <a name="using-imagelist-with-controls"></a>Utilisation d'ImageList avec des contrôles

Vous pouvez utiliser une liste d'images avec n'importe quel contrôle ayant une propriété `ImageList` ou, dans le cas du contrôle <xref:System.Windows.Forms.ListView>, les propriétés <xref:System.Windows.Forms.ListView.SmallImageList%2A> et <xref:System.Windows.Forms.ListView.LargeImageList%2A>. Les contrôles qui peuvent être associés à une liste d'images sont, entre autres, les contrôles <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton> et <xref:System.Windows.Forms.Label>. Pour associer la liste d'images à un contrôle, affectez comme valeur de la propriété `ImageList` du contrôle le nom du composant <xref:System.Windows.Forms.ImageList>.

## <a name="key-properties"></a>Propriétés de clé

La principale propriété du composant <xref:System.Windows.Forms.ImageList> est <xref:System.Windows.Forms.ImageList.Images%2A>, qui contient les images devant être utilisées par le contrôle associé. Chaque image est accessible par sa valeur d'index ou par sa clé. La propriété <xref:System.Windows.Forms.ImageList.ColorDepth%2A> détermine le nombre de couleurs avec lesquelles les images sont affichées. Les images sont toutes affichées à la même taille, définie par la propriété <xref:System.Windows.Forms.ImageList.ImageSize%2A>. Les images plus grandes seront ajustées.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ImageList>
- [Guide pratique pour ajouter ou supprimer des images avec le composant ImageList Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
