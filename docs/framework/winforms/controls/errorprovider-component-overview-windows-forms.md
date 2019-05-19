---
title: Vue d'ensemble du composant ErrorProvider (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: f2a97ab80cde00a47bbdf6830bdba325e1c9f3ef
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880984"
---
# <a name="errorprovider-component-overview-windows-forms"></a>Vue d'ensemble du composant ErrorProvider (Windows Forms)
Les formulaires Windows [ErrorProvider](errorprovider-component-windows-forms.md) composant est utilisé pour valider les entrées d’utilisateur sur un formulaire ou contrôle. Il est généralement utilisé conjointement avec la validation des entrées d’utilisateur sur un formulaire ou l’affichage des erreurs au sein d’un jeu de données. Un fournisseur d’erreur est une meilleure alternative que l’affichage d’un message d’erreur dans une boîte de message, car une fois que le message est fermé, le message d’erreur n’est plus visible. Le <xref:System.Windows.Forms.ErrorProvider> composant affiche une icône d’erreur (![un point d’exclamation blanc dans un cercle rouge.](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)) en regard du contrôle concerné, tel qu’une zone de texte ; lorsque l’utilisateur positionne le pointeur de la souris sur l’icône d’erreur, une info-bulle s’affiche, Affiche le message d’erreur.  
  
## <a name="key-properties"></a>Propriétés de clé  
 Le <xref:System.Windows.Forms.ErrorProvider> sont des propriétés de clé du composant <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, et <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Lorsque vous utilisez <xref:System.Windows.Forms.ErrorProvider> composant avec des contrôles liés aux données, le <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> propriété doit être définie sur le conteneur approprié (en général Windows Form) afin que le composant affiche une icône d’erreur sur le formulaire. Lorsque le composant est ajouté dans le concepteur, le <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> propriété est définie sur le formulaire conteneur ; si vous ajoutez le contrôle dans le code, vous devez la définir vous-même.  
  
 Le <xref:System.Windows.Forms.ErrorProvider.Icon%2A> propriété peut être définie sur une icône d’erreur personnalisée au lieu de la valeur par défaut. Lorsque le <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> propriété est définie, le <xref:System.Windows.Forms.ErrorProvider> composant peut afficher des messages d’erreur pour un jeu de données. La méthode clé pour le <xref:System.Windows.Forms.ErrorProvider> composant est le <xref:System.Windows.Forms.ErrorProvider.SetError%2A> (méthode), qui spécifie la chaîne de message d’erreur et où l’icône d’erreur doit apparaître.  
  
> [!NOTE]
>  Le <xref:System.Windows.Forms.ErrorProvider> composant ne fournit pas de prise en charge intégrée pour les clients d’accessibilité. Pour rendre votre application accessible lors de l’utilisation de ce composant, vous devez fournir un mécanisme de commentaires supplémentaire accessible.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ErrorProvider>
- [Guide pratique pour Afficher les erreurs au sein d’un jeu de données avec l’aide du composant ErrorProvider Windows Forms](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Guide pratique pour Afficher des icônes d’erreur pour la Validation de formulaire à l’aide du composant ErrorProvider Windows Forms](display-error-icons-for-form-validation-with-wf-errorprovider.md)
