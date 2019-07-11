---
title: 'Procédure : définir le masque d’entrée'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: ac747bf46c4dd1451e58615b1ec0311d75c899e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760481"
---
# <a name="how-to-set-the-input-mask"></a>Procédure : définir le masque d’entrée
Le contrôle de zone de texte masquée est un contrôle de zone de texte amélioré qui prend en charge une syntaxe déclarative pour accepter ou rejeter l’entrée d’utilisateur. En définissant la propriété Mask, vous pouvez spécifier l’entrée d’utilisateur autorisée sans écrire la logique de validation personnalisée dans votre application. Pour plus d’informations, consultez la section Notes de la <xref:System.Windows.Forms.MaskedTextBox> classe.  
  
## <a name="setting-the-mask-property-manually"></a>Définissez la propriété Mask manuellement  
 Si vous êtes familiarisé avec les caractères qui prend en charge de la propriété Mask, vous pouvez l’entrer manuellement. Pour obtenir un résumé des caractères qui prend en charge de la propriété Mask, consultez la section Notes de la <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété.  
  
### <a name="to-set-the-mask-property-manually"></a>Pour définir la propriété Mask manuellement  
  
1. Dans **conception** afficher, sélectionnez un <xref:System.Windows.Forms.MaskedTextBox>.  
  
2. Dans le **propriétés** fenêtre, recherchez le <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété.  
  
3. Tapez le masque que vous souhaitez. Par exemple, tapez `###`.  
  
## <a name="using-the-input-mask-dialog-box"></a>À l’aide de la boîte de dialogue de masque de saisie  
 La boîte de dialogue de masque de saisie fournit des masques d’entrée prédéfinis. Vous pouvez également modifier les masques prédéfinis ou entrer votre propre masque manuellement.  
  
### <a name="to-open-the-input-mask-dialog-box"></a>Pour ouvrir la boîte de dialogue de masque d’entrée  
  
1. Dans **conception** afficher, sélectionnez un <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1. Cliquez sur la balise active pour ouvrir le **tâches MaskedTextBox** Panneau de configuration.  
  
    2. Cliquez sur **définir le masque**.  
  
     \- ou -  
  
    1. Dans le **propriétés** fenêtre, sélectionnez le <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété.  
  
    2. Cliquez sur le bouton de sélection dans la colonne de valeur de propriété.  
  
     Le **masque d’entrée** boîte de dialogue s’affiche.  
  
### <a name="to-use-the-input-mask-dialog-box"></a>Pour utiliser la boîte de dialogue de masque d’entrée  
  
1. (Facultatif) Cliquez sur un des masques prédéfinis dans la liste.  
  
2. (Facultatif) Modifiez le masque prédéfini dans le **masque** boîte.  
  
3. (Facultatif) Tapez un nouveau masque dans le **masque** boîte. Autrement dit, il est inutile d’utiliser un des masques prédéfinis.  
  
    > [!NOTE]
    >  La zone Aperçu affiche les caractères que l’utilisateur voit dans le <xref:System.Windows.Forms.MaskedTextBox>. Ces caractères sont un guide pour aider l’utilisateur à entrer les données correctement.  
  
4. Activez ou désactivez le **Utiliser ValidatingType** case à cocher. Le **Utiliser ValidatingType** case à cocher spécifie si un type de données est utilisé pour vérifier les données entrées par l’utilisateur. Pour plus d'informations, consultez la propriété <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>.  
  
5. Cliquez sur **OK**.  
  
     Le masque est entré dans le **masque** propriété dans le **propriétés** fenêtre.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Utilisation du contrôle MaskedTextBox](walkthrough-working-with-the-maskedtextbox-control.md)
