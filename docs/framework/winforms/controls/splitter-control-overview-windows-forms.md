---
title: Vue d'ensemble du contrôle Splitter (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 934efd707f2a52da5ba604139c8e4510aad4606b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964455"
---
# <a name="splitter-control-overview-windows-forms"></a>Vue d'ensemble du contrôle Splitter (Windows Forms)
> [!IMPORTANT]
> Bien que <xref:System.Windows.Forms.SplitContainer> remplace et ajoute des fonctionnalités au contrôle <xref:System.Windows.Forms.Splitter> des versions antérieures, <xref:System.Windows.Forms.Splitter> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Les <xref:System.Windows.Forms.Splitter> contrôles Windows Forms sont utilisés pour redimensionner les contrôles ancrés au moment de l’exécution. Le <xref:System.Windows.Forms.Splitter> contrôle est souvent utilisé sur les formulaires avec des contrôles qui ont des longueurs variables de données à présenter, comme l’Explorateur Windows, dont les volets de données contiennent des informations de largeurs différentes à différents moments.  
  
## <a name="working-with-the-splitter-control"></a>Utilisation du contrôle Splitter  
 Quand l’utilisateur pointe le pointeur de la souris sur le bord non ancré d’un contrôle qui peut être redimensionné par un contrôle Splitter, le pointeur change d’apparence pour indiquer que le contrôle peut être redimensionné. Avec le contrôle Splitter, l’utilisateur peut redimensionner le contrôle ancré qui le précède immédiatement. Par conséquent, pour permettre à l’utilisateur de redimensionner un contrôle ancré au moment de l’exécution, ancrez le contrôle pour qu’il soit redimensionné sur un bord d’un conteneur, puis ancrez un contrôle Splitter au même côté de ce conteneur.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.SplitContainer>
- [Guide pratique : Ancrer les contrôles sur Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
