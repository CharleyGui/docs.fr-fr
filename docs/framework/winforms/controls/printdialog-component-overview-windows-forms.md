---
title: Vue d’ensemble du composant PrintDialog
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0ed7f7a1f9770f71b75ae744a056b6943335c852
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728668"
---
# <a name="printdialog-component-overview-windows-forms"></a>Vue d'ensemble du composant PrintDialog (Windows Forms)

Le composant [PrintDialog](printdialog-component-windows-forms.md) Windows Forms est une boîte de dialogue préconfigurée qui permet de sélectionner une imprimante, de choisir les pages à imprimer et d’autres paramètres relatifs à l’impression dans les applications Windows. Utilisez-le comme un moyen simple de sélectionner une imprimante ou des paramètres d'impression au lieu de configurer votre propre boîte de dialogue. Vous pouvez autoriser les utilisateurs à imprimer plusieurs parties de leurs documents : imprimer tout, imprimer une plage de pages sélectionnée ou imprimer une sélection. En vous appuyant sur des boîtes de dialogue Windows standard, vous pouvez créer des applications dont la fonction de base est immédiatement familière aux utilisateurs. Le composant <xref:System.Windows.Forms.PrintDialog> hérite de la classe <xref:System.Windows.Forms.CommonDialog>.

## <a name="working-with-the-component"></a>Utilisation du composant

Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue au moment de l’exécution. Ce composant a des propriétés qui sont liées à un travail d’impression unique (<xref:System.Drawing.Printing.PrintDocument> classe) ou aux paramètres d’une imprimante (<xref:System.Drawing.Printing.PrinterSettings> classe). L’une ou l’autre, à son tour, peut être partagée par plusieurs imprimantes.

Lorsqu’il est ajouté à un formulaire, le composant <xref:System.Windows.Forms.PrintDialog> s’affiche dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.PrintDialog>
- [PrintDialog, composant](printdialog-component-windows-forms.md)
