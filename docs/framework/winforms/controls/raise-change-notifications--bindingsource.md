---
title: "Comment : générer des notifications de modifications à l'aide d'un BindingSource et de l'interface INotifyPropertyChanged"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 2fe4458aa43144a9c29ed67fd7bee99a37fe1434
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739682"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Comment : générer des notifications de modifications à l'aide d'un BindingSource et de l'interface INotifyPropertyChanged
Le <xref:System.Windows.Forms.BindingSource> composant détecte automatiquement les changements dans une source de <xref:System.ComponentModel.INotifyPropertyChanged> données <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> lorsque le type contenu dans la source de données implémente et soulève des événements lorsqu’une valeur de propriété est modifiée. Cette détection de modification est <xref:System.Windows.Forms.BindingSource> utile parce que les contrôles liés à la mise à jour automatique que les valeurs de source de données changent.  
  
> [!NOTE]
> Si votre source de données implémente <xref:System.ComponentModel.INotifyPropertyChanged> et que vous exécutez des opérations asynchrones, vous ne devez pas modifier la source de données sur un thread d'arrière-plan. Au lieu de cela, vous devez lire les données sur un thread d’arrière-plan et les fusionner dans une liste sur le thread d’interface utilisateur.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant illustre une implémentation simple de l'interface <xref:System.ComponentModel.INotifyPropertyChanged>. Il montre également comment <xref:System.Windows.Forms.BindingSource> transmet automatiquement une modification de source de données à un contrôle lié quand <xref:System.Windows.Forms.BindingSource> est lié à une liste du type <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Si vous utilisez l'attribut `CallerMemberName`, les appels à la méthode `NotifyPropertyChanged` ne doivent pas obligatoirement spécifier le nom de la propriété comme argument de chaîne. Pour plus d’informations, voir [Informations sur l’appelant ou](../../../csharp/language-reference/attributes/caller-information.md) informations sur [l’appelant (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblages System, System.Data, System.Drawing et System.Windows.Forms.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [Composante BindingSource](bindingsource-component.md)
- [Comment : générer des notifications de modifications à l'aide de la méthode ResetItem de BindingSource](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
