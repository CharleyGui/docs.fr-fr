---
title: Vue d'ensemble du composant SaveFileDialog
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 7609c29b7e932ecee7dc8a289617094bd8d480e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743101"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>Vue d'ensemble du composant SaveFileDialog (Windows Forms)

Le composant Windows Forms <xref:System.Windows.Forms.SaveFileDialog>  est une boîte de dialogue préconfigurée. Il est identique à la boîte de dialogue standard **enregistrer le fichier** utilisée par Windows. Il hérite de la classe <xref:System.Windows.Forms.CommonDialog>.

## <a name="working-with-the-savefiledialog-component"></a>Utilisation du composant SaveFileDialog

Utilisez-le comme solution simple pour permettre aux utilisateurs d’enregistrer des fichiers au lieu de configurer votre propre boîte de dialogue. En vous appuyant sur les boîtes de dialogue Windows standard, les fonctionnalités de base des applications que vous créez sont immédiatement familières aux utilisateurs. Sachez toutefois que lorsque vous utilisez le composant <xref:System.Windows.Forms.SaveFileDialog>, vous devez écrire votre propre logique d’enregistrement des fichiers.

Vous pouvez utiliser la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue au moment de l’exécution. Vous pouvez ouvrir un fichier en mode lecture/écriture à l’aide de la méthode <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>.

Lorsqu’il est ajouté à un formulaire, le composant <xref:System.Windows.Forms.SaveFileDialog> s’affiche dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.SaveFileDialog>
- [SaveFileDialog, composant](savefiledialog-component-windows-forms.md)
