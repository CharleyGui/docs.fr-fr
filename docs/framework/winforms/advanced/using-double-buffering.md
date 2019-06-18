---
title: Utilisation de doubles tampons d'enregistrements
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: 5b22336221c7bdda3c9dd7adf23308a2b0bad450
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169917"
---
# <a name="using-double-buffering"></a>Utilisation de doubles tampons d'enregistrements
Vous pouvez utiliser des graphiques de double tampon pour réduire le scintillement dans vos applications qui contiennent des opérations de dessin complexes. Le .NET Framework contient une prise en charge intégrée de double tampon, ou vous pouvez gérer et restituer manuellement des graphiques.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Graphiques mis deux fois en mémoire tampon](double-buffered-graphics.md)  
 Introduit la double mise en mémoire tampon concept et les contours .NET Framework prise en charge.  
  
 [Guide pratique pour Réduire le scintillement des graphiques avec Double mise en tampon pour les formulaires et contrôles](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 Montre comment utiliser la double mise en mémoire tampon de prise en charge dans le .NET Framework de la valeur par défaut.  
  
 [Guide pratique pour Gérer manuellement des graphiques mis en mémoire tampon](how-to-manually-manage-buffered-graphics.md)  
 Montre comment gérer le mécanisme de double tampon dans les applications.  
  
 [Guide pratique pour Restituer manuellement des graphiques mis en mémoire tampon](how-to-manually-render-buffered-graphics.md)  
 Montre comment restituer des graphiques mis en mémoire tampon double.  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.Control.SetStyle%2A> Méthode de contrôle qui permet la double mise en tampon.  
  
 <xref:System.Drawing.BufferedGraphicsContext> Fournit des méthodes pour créer des mémoires tampons de graphiques.  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 Fournit l’accès au contexte graphique mis en mémoire tampon pour un domaine d’application.
