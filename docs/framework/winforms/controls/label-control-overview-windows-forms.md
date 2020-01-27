---
title: Vue d'ensemble du contrôle Label
ms.date: 03/30/2017
f1_keywords:
- Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
ms.openlocfilehash: 1ca14553c7cb51d2b7a329950aeaec4c0439762a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745287"
---
# <a name="label-control-overview-windows-forms"></a>Vue d'ensemble du contrôle Label (Windows Forms)
Les contrôles de <xref:System.Windows.Forms.Label> Windows Forms sont utilisés pour afficher du texte ou des images qui ne peuvent pas être modifiés par l’utilisateur. Ils sont utilisés pour identifier des objets sur un formulaire — pour fournir une description de ce que fait un certain contrôle en cas de clic, par exemple, ou pour afficher des informations en réponse à un événement ou à un processus d’exécution dans votre application. Par exemple, vous pouvez utiliser des étiquettes pour ajouter des légendes descriptives à des zones de texte, des zones de liste, des zones de liste modifiable, et ainsi de suite. Vous pouvez également écrire du code qui modifie le texte affiché par une étiquette en réponse aux événements au moment de l’exécution. Par exemple, si votre application prend quelques minutes pour traiter une modification, vous pouvez afficher un message d’état de traitement dans une étiquette.  
  
## <a name="working-with-the-label-control"></a>Utilisation du contrôle Label  
 Étant donné que le contrôle <xref:System.Windows.Forms.Label> ne peut pas recevoir le focus, il peut également être utilisé pour créer des clés d’accès pour d’autres contrôles. Une clé d’accès permet à un utilisateur de sélectionner l’autre contrôle en appuyant sur la touche ALT avec la touche d’accès. Pour plus d’informations, consultez [création de clés d’accès pour les contrôles Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md) et [Comment : créer des clés d’accès avec Windows Forms contrôles Label](how-to-create-access-keys-with-windows-forms-label-controls.md).  
  
 La légende affichée dans l’étiquette est contenue dans la propriété <xref:System.Windows.Forms.Label.Text%2A>. La propriété <xref:System.Windows.Forms.Label.TextAlign%2A> vous permet de définir l’alignement du texte dans l’étiquette. Pour plus d’informations, consultez [Comment : définir le texte affiché par un contrôle Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Label>
- [Guide pratique pour dimensionner un contrôle Label Windows Forms en fonction de son contenu](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Guide pratique pour créer des touches d'accès rapide à l'aide des contrôles Label Windows Forms](how-to-create-access-keys-with-windows-forms-label-controls.md)
