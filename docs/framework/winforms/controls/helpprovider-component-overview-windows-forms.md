---
title: Vue d'ensemble du composant HelpProvider
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
ms.openlocfilehash: 74d35dfa39a605cb1e1e85cc3aeda834e1c60669
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738726"
---
# <a name="helpprovider-component-overview-windows-forms"></a>Vue d'ensemble du composant HelpProvider (Windows Forms)
Le composant Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) est utilisé pour associer un fichier d’aide HTML Help 1. x (un fichier. chm, produit avec l’atelier d’aide HTML ou un fichier. htm) à votre application Windows. Vous pouvez fournir de l’aide de différentes manières :  
  
- Fournir une aide contextuelle pour les contrôles sur Windows Forms.  
  
- Fournissez une aide contextuelle sur une boîte de dialogue particulière ou des contrôles spécifiques sur une boîte de dialogue.  
  
- Ouvrir un fichier d’aide dans des zones spécifiques, telles que la page principale d’une table des matières, l’index ou une fonction de recherche.  
  
## <a name="using-the-help-provider"></a>Utilisation du fournisseur d’aide  
 L’ajout d’un composant <xref:System.Windows.Forms.HelpProvider> à votre Windows Form permet aux autres contrôles du formulaire d’exposer les propriétés d’aide du composant <xref:System.Windows.Forms.HelpProvider>. Cela vous permet de fournir de l’aide pour les contrôles de votre Windows Form. Vous pouvez associer un fichier d’aide au composant <xref:System.Windows.Forms.HelpProvider> à l’aide de la propriété <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A>. Vous spécifiez le type d’aide fourni en appelant <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> et en fournissant une valeur à partir de l’énumération <xref:System.Windows.Forms.HelpNavigator> pour le contrôle spécifié. Vous fournissez le mot clé ou la rubrique pour obtenir de l’aide en appelant la méthode <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A>.  
  
 Si vous le souhaitez, pour associer une chaîne d’aide spécifique à un autre contrôle, utilisez la méthode <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A>. La chaîne que vous associez à un contrôle à l’aide de cette méthode s’affiche dans une fenêtre indépendante quand l’utilisateur appuie sur la touche F1 pendant que le contrôle a le focus.  
  
 Si <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> n’a pas été défini, vous devez utiliser <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> pour fournir le texte d’aide. Si vous avez défini à la fois <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> et la chaîne d’aide, l’aide basée sur <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> sera prioritaire.  
  
> [!NOTE]
> Vous pouvez rencontrer des problèmes lors de l’utilisation du chemin d’accès relatif lorsque vous spécifiez le chemin d’accès au fichier d’aide dans la méthode <xref:System.Windows.Forms.Help.ShowHelp%2A> ou <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriété du contrôle <xref:System.Windows.Forms.HelpProvider>. Par conséquent, veillez à utiliser le chemin d’accès absolu du fichier pour spécifier le fichier d’aide.  
  
## <a name="see-also"></a>Voir aussi

- [Systèmes d’aide dans les applications Windows Forms](../advanced/help-systems-in-windows-forms-applications.md)
