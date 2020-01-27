---
title: Vue d'ensemble du composant OpenFileDialog
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728436"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>Vue d'ensemble du composant OpenFileDialog (Windows Forms)

Le composant Windows Forms <xref:System.Windows.Forms.OpenFileDialog>  est une boîte de dialogue préconfigurée. Il s’agit de la même boîte de dialogue **ouvrir le fichier** que celle exposée par le système d’exploitation Windows. Il hérite de la classe <xref:System.Windows.Forms.CommonDialog>.

## <a name="use-this-component"></a>Utiliser ce composant

Utilisez ce composant dans votre application Windows comme solution simple pour la sélection de fichiers au lieu de configurer votre propre boîte de dialogue. En vous appuyant sur des boîtes de dialogue Windows standard, vous pouvez créer des applications dont la fonction de base est immédiatement familière aux utilisateurs. Sachez toutefois que lorsque vous utilisez le composant <xref:System.Windows.Forms.OpenFileDialog>, vous devez écrire votre propre logique d’ouverture de fichier.

Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue au moment de l’exécution. Vous pouvez permettre aux utilisateurs de sélectionner plusieurs fichiers à ouvrir avec la propriété <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>. En outre, vous pouvez utiliser la propriété <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> pour déterminer si une case à cocher en lecture seule apparaît dans la boîte de dialogue. La propriété <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> indique si la case à cocher en lecture seule est activée. Enfin, la propriété <xref:System.Windows.Forms.FileDialog.Filter%2A> définit la chaîne de filtre de nom de fichier actuelle, qui détermine les choix qui s’affichent dans la zone « types de fichiers » de la boîte de dialogue.

Lorsqu’il est ajouté à un formulaire, le composant <xref:System.Windows.Forms.OpenFileDialog> s’affiche dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog, composant](openfiledialog-component-windows-forms.md)
