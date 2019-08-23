---
title: Vue d'ensemble du composant HelpProvider (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
ms.openlocfilehash: cefc590bb3011b282392504a78ac5c393c58493e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965697"
---
# <a name="helpprovider-component-overview-windows-forms"></a>Vue d'ensemble du composant HelpProvider (Windows Forms)
Le composant Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) est utilisé pour associer un fichier d’aide HTML Help 1. x (un fichier. chm, produit avec l’atelier d’aide HTML ou un fichier. htm) à votre application Windows. Vous pouvez fournir de l’aide de différentes manières:  
  
- Fournir une aide contextuelle pour les contrôles sur Windows Forms.  
  
- Fournissez une aide contextuelle sur une boîte de dialogue particulière ou des contrôles spécifiques sur une boîte de dialogue.  
  
- Ouvrir un fichier d’aide dans des zones spécifiques, telles que la page principale d’une table des matières, l’index ou une fonction de recherche.  
  
## <a name="using-the-help-provider"></a>Utilisation du fournisseur d’aide  
 L’ajout <xref:System.Windows.Forms.HelpProvider> d’un composant à votre Windows Form permet aux autres contrôles du formulaire d’exposer les propriétés <xref:System.Windows.Forms.HelpProvider> d’aide du composant. Cela vous permet de fournir de l’aide pour les contrôles de votre Windows Form. Vous pouvez associer un fichier <xref:System.Windows.Forms.HelpProvider> d’aide au composant à l’aide de la <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriété. Vous spécifiez le type d’aide fourni en <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> appelant et en fournissant une valeur <xref:System.Windows.Forms.HelpNavigator> de l’énumération pour le contrôle spécifié. Vous fournissez le mot clé ou la rubrique pour obtenir <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> de l’aide en appelant la méthode.  
  
 Si vous le souhaitez, pour associer une chaîne d’aide spécifique à un autre <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> contrôle, utilisez la méthode. La chaîne que vous associez à un contrôle à l’aide de cette méthode s’affiche dans une fenêtre indépendante quand l’utilisateur appuie sur la touche F1 pendant que le contrôle a le focus.  
  
 Si <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> n’a pas été défini, vous devez <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> utiliser pour fournir le texte d’aide. Si vous avez défini à <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> la fois et la chaîne d’aide, <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> l’aide basée sur est prioritaire.  
  
> [!NOTE]
> Vous pouvez rencontrer des problèmes lors de l’utilisation du chemin d’accès relatif lorsque vous spécifiez <xref:System.Windows.Forms.Help.ShowHelp%2A> le chemin <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> d’accès au <xref:System.Windows.Forms.HelpProvider> fichier d’aide dans la méthode ou la propriété du contrôle. Par conséquent, veillez à utiliser le chemin d’accès absolu du fichier pour spécifier le fichier d’aide.  
  
## <a name="see-also"></a>Voir aussi

- [Systèmes d’aide dans les applications Windows Forms](../advanced/help-systems-in-windows-forms-applications.md)
