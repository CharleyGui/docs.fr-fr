---
title: 'Procédure : donner à votre contrôle un arrière-plan transparent'
ms.date: 03/30/2017
helpviewer_keywords:
- transparent backgrounds [Windows Forms], custom controls
- custom controls [Windows Forms], transparent background
- transparency [Windows Forms], Windows Forms custom controls
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
ms.openlocfilehash: a82807ea3873b2217d1f05f6c720c599ea79abdd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966641"
---
# <a name="how-to-give-your-control-a-transparent-background"></a>Procédure : donner à votre contrôle un arrière-plan transparent
Dans les versions antérieures de .NET Framework, les contrôles ne prenaient pas en charge la définition de couleurs d’arrière-plan transparentes sans définition préalable de la méthode <xref:System.Windows.Forms.Control.SetStyle%2A> dans le constructeur du formulaire. Dans la version actuelle de l’infrastructure, vous pouvez affecter <xref:System.Drawing.Color.Transparent%2A> comme couleur d’arrière-plan de la plupart des contrôles  dans la fenêtre **Propriétés** au moment du design ou dans le code dans le constructeur du formulaire.  
  
> [!NOTE]
> Les contrôles Windows Forms ne prennent pas en charge la véritable transparence. L’arrière-plan d’un contrôle Windows Forms transparent est peint par son parent.  
  
> [!NOTE]
> Le contrôle <xref:System.Windows.Controls.Button> ne prend pas en charge une couleur d’arrière-plan transparente même quand la propriété <xref:System.Windows.Forms.ButtonBase.BackColor%2A> a la valeur <xref:System.Drawing.Color.Transparent%2A>.  
  
### <a name="to-give-your-control-a-transparent-backcolor"></a>Pour affecter un arrière-plan transparent à votre contrôle  
  
- Dans la fenêtre Propriétés, choisissez la propriété <xref:System.Windows.Forms.ButtonBase.BackColor%2A> et affectez-lui la valeur <xref:System.Drawing.Color.Transparent%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Color.FromArgb%2A>
- [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](developing-custom-windows-forms-controls.md)
- [Utilisation de classes graphiques managées](../advanced/using-managed-graphics-classes.md)
- [Guide pratique : Dessiner des lignes opaques et translucides](../advanced/how-to-draw-opaque-and-semitransparent-lines.md)
