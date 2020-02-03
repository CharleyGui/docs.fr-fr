---
title: Vue d'ensemble du contrôle Splitter
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 3d6da8daf9bb0e8df4f69554a87725a7ddb65acb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742891"
---
# <a name="splitter-control-overview-windows-forms"></a>Vue d'ensemble du contrôle Splitter (Windows Forms)
> [!IMPORTANT]
> Bien que <xref:System.Windows.Forms.SplitContainer> remplace et ajoute des fonctionnalités au contrôle <xref:System.Windows.Forms.Splitter> des versions antérieures, <xref:System.Windows.Forms.Splitter> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Les contrôles de <xref:System.Windows.Forms.Splitter> Windows Forms sont utilisés pour redimensionner les contrôles ancrés au moment de l’exécution. Le contrôle <xref:System.Windows.Forms.Splitter> est souvent utilisé sur les formulaires avec des contrôles qui ont des longueurs différentes de données à présenter, comme l’Explorateur Windows, dont les volets de données contiennent des informations de largeurs différentes à différents moments.  
  
## <a name="working-with-the-splitter-control"></a>Utilisation du contrôle Splitter  
 Quand l’utilisateur pointe le pointeur de la souris sur le bord non ancré d’un contrôle qui peut être redimensionné par un contrôle Splitter, le pointeur change d’apparence pour indiquer que le contrôle peut être redimensionné. Avec le contrôle Splitter, l’utilisateur peut redimensionner le contrôle ancré qui le précède immédiatement. Par conséquent, pour permettre à l’utilisateur de redimensionner un contrôle ancré au moment de l’exécution, ancrez le contrôle pour qu’il soit redimensionné sur un bord d’un conteneur, puis ancrez un contrôle Splitter au même côté de ce conteneur.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.SplitContainer>
- [Guide pratique pour fixer des contrôles sur des Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
