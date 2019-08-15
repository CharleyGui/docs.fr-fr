---
title: 'Procédure : étendre des lignes et des colonnes dans un contrôle TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: a215b2b4e05bab5c81d2779d4b67d5b9d57b6ba5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039702"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Procédure : étendre des lignes et des colonnes dans un contrôle TableLayoutPanel
Les contrôles d' <xref:System.Windows.Forms.TableLayoutPanel> un contrôle peuvent couvrir des lignes et des colonnes adjacentes.

## <a name="to-span-columns-and-rows"></a>Pour étendre les colonnes et les lignes

1. Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.

2. Faites glisser <xref:System.Windows.Forms.Button> un contrôle de la **boîte à outils** vers la cellule supérieure <xref:System.Windows.Forms.TableLayoutPanel> gauche du contrôle.

3. Affectez <xref:System.Windows.Forms.Button> à la propriété **ColumnSpan** du contrôle la valeur **2**. Notez que le <xref:System.Windows.Forms.Button> contrôle s’étend sur la première et la deuxième colonne.

4. Affectez <xref:System.Windows.Forms.Button> à la propriété **RowSpan** du contrôle la valeur **2**. Notez que le <xref:System.Windows.Forms.Button> contrôle s’étend sur la première et la deuxième ligne.

5. Affectez <xref:System.Windows.Forms.Button> à la propriété **ColumnSpan** du contrôle la valeur **1**. Notez que le <xref:System.Windows.Forms.Button> contrôle se déplace dans la première colonne et s’étend sur la première et la deuxième ligne.

## <a name="see-also"></a>Voir aussi

- [TableLayoutPanel, contrôle](tablelayoutpanel-control-windows-forms.md)
