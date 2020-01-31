---
title: Dimensionner un contrôle Label pour l’adapter à son contenu
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 6a563693feaa5074f5d13f0b82cc4d0305a79c23
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743773"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Comment : dimensionner un contrôle Label Windows Forms en fonction de son contenu
Le contrôle Windows Forms <xref:System.Windows.Forms.Label> peut être une seule ligne ou plusieurs lignes, et sa taille peut être fixe ou peut se redimensionner automatiquement pour s’adapter à sa légende. La propriété <xref:System.Windows.Forms.Label.AutoSize%2A> vous permet de dimensionner les contrôles pour qu’ils s’ajustent aux légendes les plus grandes ou les plus petites, ce qui est particulièrement utile si la légende change au moment de l’exécution.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Pour faire en sorte qu’un contrôle Label se redimensionne dynamiquement pour s’adapter à son contenu  
  
1. Affectez à sa propriété <xref:System.Windows.Forms.Label.AutoSize%2A> la valeur `true`.  
  
 Si <xref:System.Windows.Forms.Label.AutoSize%2A> a la valeur `false`, les mots spécifiés dans la propriété <xref:System.Windows.Forms.Label.Text%2A> sont renvoyés à la ligne suivante, si possible, mais le contrôle ne s’agrandit pas.  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour créer des touches d'accès rapide à l'aide des contrôles Label Windows Forms](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Vue d'ensemble du contrôle Label](label-control-overview-windows-forms.md)
- [Label, contrôle](label-control-windows-forms.md)
