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
ms.openlocfilehash: 3cfd3f306d4a18ce8a194b5197060fbca1d157d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965285"
---
# <a name="errorprovider-component-overview-windows-forms"></a>Vue d'ensemble du composant ErrorProvider (Windows Forms)
Le Windows Forms composant [ErrorProvider](errorprovider-component-windows-forms.md) est utilisé pour valider l’entrée d’utilisateur sur un formulaire ou un contrôle. Elle est généralement utilisée conjointement avec la validation de l’entrée d’utilisateur sur un formulaire ou l’affichage d’erreurs dans un jeu de données. Un fournisseur d’erreur est une meilleure alternative que l’affichage d’un message d’erreur dans une boîte de message, car une fois qu’une boîte de message est fermée, le message d’erreur n’est plus visible. Le <xref:System.Windows.Forms.ErrorProvider> composant affiche une icône d’erreur![(un point d’exclamation blanc](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)à l’intérieur d’un cercle rouge) à côté du contrôle approprié, par exemple une zone de texte. lorsque l’utilisateur positionne le pointeur de la souris sur l’icône d’erreur, une info-bulle s’affiche. affiche la chaîne du message d’erreur.  
  
## <a name="key-properties"></a>Propriétés de clé  
 Les <xref:System.Windows.Forms.ErrorProvider> propriétés de clé du composant <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>sont <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, et <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Lorsque vous <xref:System.Windows.Forms.ErrorProvider> utilisez un composant avec des contrôles liés aux <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> données, la propriété doit être définie sur le conteneur approprié (généralement le Windows Form) pour que le composant affiche une icône d’erreur dans le formulaire. Lorsque le composant est ajouté dans le concepteur, la <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> propriété est définie sur le formulaire conteneur; si vous ajoutez le contrôle dans le code, vous devez le définir vous-même.  
  
 La <xref:System.Windows.Forms.ErrorProvider.Icon%2A> propriété peut être définie sur une icône d’erreur personnalisée au lieu de la valeur par défaut. Lorsque la <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> propriété est définie, le <xref:System.Windows.Forms.ErrorProvider> composant peut afficher des messages d’erreur pour un DataSet. La méthode clé du <xref:System.Windows.Forms.ErrorProvider> composant est la <xref:System.Windows.Forms.ErrorProvider.SetError%2A> méthode, qui spécifie la chaîne du message d’erreur et l’emplacement où l’icône d’erreur doit apparaître.  
  
> [!NOTE]
> Le <xref:System.Windows.Forms.ErrorProvider> composant ne fournit pas de prise en charge intégrée pour les clients d’accessibilité. Pour que votre application soit accessible lors de l’utilisation de ce composant, vous devez fournir un mécanisme de commentaires supplémentaire et accessible.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ErrorProvider>
- [Guide pratique pour Afficher les erreurs dans un DataSet avec le composant Windows Forms ErrorProvider](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Guide pratique pour Afficher les icônes d’erreur pour la validation de formulaire avec le composant ErrorProvider Windows Forms](display-error-icons-for-form-validation-with-wf-errorprovider.md)
