---
title: Guide pratique pour refuser la mise à niveau automatique de la boîte de dialogue Fichier
ms.date: 03/30/2017
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
ms.openlocfilehash: 154953680426f98a9506feb0b8f4de25c873b795
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959680"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Guide pratique pour refuser la mise à niveau automatique de la boîte de dialogue Fichier
Lorsque les classes <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> sont utilisées dans une application, leur apparence et leur comportement dépendent de la version de Windows sur laquelle l’application s’exécute. Quand une application créée sur la .NET Framework 2,0 ou une version antérieure s’affiche sur Windows Vista, <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> sont automatiquement affichées avec l’apparence et le comportement de Windows Vista. À partir de la .NET Framework 3,0, vous pouvez refuser la mise à niveau automatique pour afficher les <xref:System.Windows.Forms.OpenFileDialog> et les <xref:System.Windows.Forms.SaveFileDialog> avec une apparence et un comportement de style Windows XP.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Pour refuser la mise à niveau automatique de la boîte de dialogue Fichier  
  
1. Définissez la propriété <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> de <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog> sur `false` avant d’afficher la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FileDialog>
