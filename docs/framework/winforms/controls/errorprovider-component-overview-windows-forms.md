---
title: Vue d'ensemble du composant ErrorProvider
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: b66e97d97d0d8c2ea4e9bdba29f8ff35e486e1f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745794"
---
# <a name="errorprovider-component-overview-windows-forms"></a>Vue d'ensemble du composant ErrorProvider (Windows Forms)
Le Windows Forms composant [ErrorProvider](errorprovider-component-windows-forms.md) est utilisé pour valider l’entrée d’utilisateur sur un formulaire ou un contrôle. Elle est généralement utilisée conjointement avec la validation de l’entrée d’utilisateur sur un formulaire ou l’affichage d’erreurs dans un jeu de données. Un fournisseur d’erreur est une meilleure alternative que l’affichage d’un message d’erreur dans une boîte de message, car une fois qu’une boîte de message est fermée, le message d’erreur n’est plus visible. Le composant <xref:System.Windows.Forms.ErrorProvider> affiche une icône d’erreur (![un point d’exclamation blanc à l’intérieur d’un cercle rouge.](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)) en regard du contrôle approprié, tel qu’une zone de texte ; Lorsque l’utilisateur place le pointeur de la souris sur l’icône d’erreur, une info-bulle apparaît et affiche la chaîne du message d’erreur.  
  
## <a name="key-properties"></a>Propriétés de clé  
 Les propriétés de clé du composant <xref:System.Windows.Forms.ErrorProvider> sont <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>et <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Lorsque vous utilisez <xref:System.Windows.Forms.ErrorProvider> composant avec des contrôles liés aux données, la propriété <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> doit être définie sur le conteneur approprié (généralement le Windows Form) pour que le composant affiche une icône d’erreur dans le formulaire. Lorsque le composant est ajouté dans le concepteur, la propriété <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> est définie sur le formulaire conteneur ; Si vous ajoutez le contrôle dans le code, vous devez le définir vous-même.  
  
 La propriété <xref:System.Windows.Forms.ErrorProvider.Icon%2A> peut être définie sur une icône d’erreur personnalisée au lieu de la valeur par défaut. Lorsque la propriété <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> est définie, le composant <xref:System.Windows.Forms.ErrorProvider> peut afficher des messages d’erreur pour un jeu de données. La méthode clé du composant <xref:System.Windows.Forms.ErrorProvider> est la méthode <xref:System.Windows.Forms.ErrorProvider.SetError%2A>, qui spécifie la chaîne du message d’erreur et l’emplacement où l’icône d’erreur doit apparaître.  
  
> [!NOTE]
> Le composant <xref:System.Windows.Forms.ErrorProvider> ne fournit pas de prise en charge intégrée pour les clients d’accessibilité. Pour que votre application soit accessible lors de l’utilisation de ce composant, vous devez fournir un mécanisme de commentaires supplémentaire et accessible.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ErrorProvider>
- [Guide pratique pour afficher des erreurs d'un groupe de données à l'aide du composant ErrorProvider Windows Forms](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Guide pratique pour afficher des icônes d’erreur pour la validation de formulaire à l’aide du composant ErrorProvider Windows Forms](display-error-icons-for-form-validation-with-wf-errorprovider.md)
