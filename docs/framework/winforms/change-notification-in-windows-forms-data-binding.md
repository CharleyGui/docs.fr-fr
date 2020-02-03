---
title: Notification de modifications dans la liaison de données
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: 2dffea46bf0db54d28ef55e507767d88bd29ebc2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746352"
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Notification de modifications dans la liaison de données Windows Forms
L’un des concepts les plus importants de la liaison de données Windows Forms est la *notification de modification*. Pour vous assurer que votre source de données et vos contrôles liés possèdent toujours les données les plus récentes, vous devez ajouter la notification de modification pour la liaison de données. En particulier, vous souhaitez vous assurer que les contrôles liés sont avertis des modifications apportées à leur source de données, et la source de données est avertie des modifications apportées aux propriétés liées d’un contrôle.  
  
 Il existe différents types de notifications de modification, selon le type de liaison de données :  
  
- Liaison simple, dans laquelle une propriété de contrôle unique est liée à une seule instance d’un objet.  
  
- Liaison basée sur une liste, qui peut inclure une propriété de contrôle unique liée à la propriété d’un élément dans une liste ou une propriété de contrôle liée à une liste d’objets.  
  
 En outre, si vous créez Windows Forms contrôles que vous souhaitez utiliser pour la liaison de données, vous devez appliquer le modèle de *PropertyName*Changed aux contrôles, afin que les modifications apportées à la propriété liée d’un contrôle soient propagées à la source de données.  
  
## <a name="change-notification-for-simple-binding"></a>Notification de modification pour liaison simple  
 Pour une liaison simple, les objets métier doivent fournir une notification de modification lorsque la valeur d’une propriété liée change. Pour ce faire, vous pouvez exposer un événement *PropertyName*Changed pour chaque propriété de votre objet métier et lier l’objet métier à des contrôles avec le <xref:System.Windows.Forms.BindingSource> ou à la méthode préférée dans laquelle votre objet métier implémente l’interface <xref:System.ComponentModel.INotifyPropertyChanged> et déclenche un événement <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> quand la valeur d’une propriété change. Pour plus d’informations, consultez [Comment : implémenter l’interface INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md). Lorsque vous utilisez des objets qui implémentent l’interface <xref:System.ComponentModel.INotifyPropertyChanged>, il n’est pas nécessaire d’utiliser la <xref:System.Windows.Forms.BindingSource> pour lier l’objet à un contrôle, mais l’utilisation de la <xref:System.Windows.Forms.BindingSource> est recommandée.  
  
## <a name="change-notification-for-list-based-binding"></a>Notification de modification pour la liaison basée sur une liste  
 Windows Forms dépend d’une liste liée pour fournir une modification de propriété (modification de la valeur d’une propriété d’élément de liste) et d’une liste modifiée (un élément est supprimé ou ajouté à la liste) à des contrôles liés. Par conséquent, les listes utilisées pour la liaison de données doivent implémenter le <xref:System.ComponentModel.IBindingList>, qui fournit les deux types de notification de modification. Le <xref:System.ComponentModel.BindingList%601> est une implémentation générique de <xref:System.ComponentModel.IBindingList> et est conçu pour être utilisé avec Windows Forms la liaison de données. Vous pouvez créer un <xref:System.ComponentModel.BindingList%601> qui contient un type d’objet métier qui implémente <xref:System.ComponentModel.INotifyPropertyChanged> et la liste convertit automatiquement les événements <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> en <xref:System.ComponentModel.IBindingList.ListChanged> événements. Si la liste liée n’est pas un <xref:System.ComponentModel.IBindingList>, vous devez lier la liste d’objets à Windows Forms contrôles à l’aide du composant <xref:System.Windows.Forms.BindingSource>. Le composant <xref:System.Windows.Forms.BindingSource> fournit une conversion de propriété en liste similaire à celle de l' <xref:System.ComponentModel.BindingList%601>. Pour plus d’informations, consultez [Comment : déclencher des notifications de modifications à l’aide d’un BindingSource et de l’interface INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Notification de modification pour les contrôles personnalisés  
 Enfin, du côté du contrôle, vous devez exposer un événement *PropertyName*Changed pour chaque propriété conçue pour être liée aux données. Les modifications apportées à la propriété de contrôle sont ensuite propagées vers la source de données liée. Pour plus d’informations, consultez [Comment : appliquer le modèle PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.ComponentModel.INotifyPropertyChanged>
- <xref:System.ComponentModel.BindingList%601>
- [Liaison de données Windows Forms](windows-forms-data-binding.md)
- [Sources de données prises en charge par les Windows Forms](data-sources-supported-by-windows-forms.md)
- [Liaison de données et Windows Forms](data-binding-and-windows-forms.md)
