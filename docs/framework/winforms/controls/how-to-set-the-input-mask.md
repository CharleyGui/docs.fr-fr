---
title: 'Procédure : définir le masque d’entrée'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06dee48765653ac7a659246cc3dfe865c795ca21
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949149"
---
# <a name="how-to-set-the-input-mask"></a>Procédure : définir le masque d’entrée
Le contrôle de zone de texte masquée est un contrôle de zone de texte amélioré qui prend en charge une syntaxe déclarative pour accepter ou rejeter les entrées d’utilisateur. En définissant la propriété Mask, vous pouvez spécifier l’entrée utilisateur autorisée sans écrire de logique de validation personnalisée dans votre application. Pour plus d’informations, consultez la section Notes de <xref:System.Windows.Forms.MaskedTextBox> la classe.  
  
## <a name="setting-the-mask-property-manually"></a>Définition manuelle de la propriété Mask  
 Si vous êtes familiarisé avec les caractères pris en charge par la propriété Mask, vous pouvez l’entrer manuellement. Pour obtenir un résumé des caractères pris en charge par la propriété Mask, consultez la section Notes <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> de la propriété.  
  
### <a name="to-set-the-mask-property-manually"></a>Pour définir manuellement la propriété Mask  
  
1. En mode **conception** , sélectionnez un <xref:System.Windows.Forms.MaskedTextBox>.  
  
2. Dans la fenêtre **Propriétés** , recherchez la <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété.  
  
3. Tapez le masque de votre choix. Par exemple, tapez `###`.  
  
## <a name="using-the-input-mask-dialog-box"></a>Utilisation de la boîte de dialogue masque de saisie  
 La boîte de dialogue masque de saisie fournit des masques d’entrée prédéfinis. Vous pouvez également modifier les masques prédéfinis ou entrer votre propre masque manuellement.  
  
### <a name="to-open-the-input-mask-dialog-box"></a>Pour ouvrir la boîte de dialogue masque de saisie  
  
1. En mode **conception** , sélectionnez un <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1. Cliquez sur la balise active pour ouvrir le panneau **tâches MaskedTextBox** .  
  
    2. Cliquez sur **définir un masque**.  
  
     \- ou -  
  
    1. Dans la fenêtre **Propriétés** , sélectionnez la <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété.  
  
    2. Cliquez sur le bouton de sélection dans la colonne valeur de la propriété.  
  
     La boîte de dialogue **masque de saisie** s’affiche.  
  
### <a name="to-use-the-input-mask-dialog-box"></a>Pour utiliser la boîte de dialogue masque de saisie  
  
1. Facultatif Cliquez sur l’un des masques prédéfinis dans la liste.  
  
2. Facultatif Modifiez le masque prédéfini dans la zone **masque** .  
  
3. Facultatif Tapez un nouveau masque dans la zone **masque** . Autrement dit, il n’est pas nécessaire d’utiliser l’un des masques prédéfinis.  
  
    > [!NOTE]
    > La zone aperçu affiche les caractères que l’utilisateur voit dans le <xref:System.Windows.Forms.MaskedTextBox>. Ces caractères sont un guide permettant à l’utilisateur d’entrer les données correctement.  
  
4. Activez ou désactivez la case à cocher **Utiliser ValidatingType** . La case à cocher **utiliser le ValidatingType** spécifie si un type de données est utilisé pour vérifier les données entrées par l’utilisateur. Pour plus d'informations, consultez la propriété <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>.  
  
5. Cliquez sur **OK**.  
  
     Le masque est entré dans la propriété **masque** de la fenêtre **Propriétés** .  
  
## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Utilisation du contrôle MaskedTextBox](walkthrough-working-with-the-maskedtextbox-control.md)
