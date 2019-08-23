---
title: 'Procédure : partager des données liées entre formulaires à l’aide du composant BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: aa497194fd4ac65f48773a45175333a1d862b453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956075"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a>Procédure : partager des données liées entre formulaires à l’aide du composant BindingSource
Vous pouvez facilement partager des données entre des formulaires à l'aide du composant <xref:System.Windows.Forms.BindingSource>. Par exemple, vous souhaiterez peut-être afficher un formulaire en lecture seule qui résume les données de la source de données et un autre formulaire modifiable qui contient des informations détaillées sur l'élément actuellement sélectionné dans la source de données. Cet exemple illustre ce scénario.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant montre comment partager un <xref:System.Windows.Forms.BindingSource> et ses données liées entre des formulaires. Dans cet exemple, le <xref:System.Windows.Forms.BindingSource> partagé est passé au constructeur du formulaire enfant. Le formulaire enfant permet à l'utilisateur de modifier les données de l'élément actuellement sélectionné dans le formulaire principal.  
  
> [!NOTE]
> L'événement <xref:System.Windows.Forms.BindingSource.BindingComplete> pour le composant <xref:System.Windows.Forms.BindingSource> est géré dans l'exemple pour garantir que les deux formulaires restent synchronisés. Pour plus d’informations sur la raison de cette opération [, consultez Procédure: Assurez-vous que plusieurs contrôles liés à la même source](../multiple-controls-bound-to-data-source-synchronized.md)de données restent synchronisés.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System, System.Windows.Forms, System.Drawing, System.Data et System.Xml.  
  
## <a name="see-also"></a>Voir aussi

- [BindingSource, composant](bindingsource-component.md)
- [Liaison de données Windows Forms](../windows-forms-data-binding.md)
- [Guide pratique pour Gérer les erreurs et les exceptions qui se produisent avec DataBinding](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
