---
title: Liaison de données
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 68871db848ab46b88865e668f27f09972e8debcf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734611"
---
# <a name="windows-forms-data-binding"></a>Liaison de données Windows Forms
La liaison de données dans les Windows Forms vous permet d'afficher et de modifier les informations d'une source de données dans les contrôles du formulaire. Vous pouvez établir une liaison à une source de données traditionnelle et à presque toute structure qui contient des données.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Liaison de données et Windows Forms](data-binding-and-windows-forms.md)  
 Fournit une vue d’ensemble de la liaison de données dans les Windows Forms.  
  
 [Sources de données prises en charge par les Windows Forms](data-sources-supported-by-windows-forms.md)  
 Décrit les sources de données qui peuvent être utilisées avec Windows Forms.  
  
 [Interfaces participant à la liaison de données](interfaces-related-to-data-binding.md)  
 Décrit plusieurs interfaces utilisées avec la liaison de données Windows Forms.  
  
 [Guide pratique pour naviguer au sein des données dans les Windows Forms](how-to-navigate-data-in-windows-forms.md)  
 Montre comment parcourir les éléments dans une source de données.  
  
 [Notification de modifications dans la liaison de données Windows Forms](change-notification-in-windows-forms-data-binding.md)  
 Décrit les différents types de notifications de modifications pour la liaison de données Windows Forms.  
  
 [Guide pratique pour implémenter l'interface INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md)  
 Montre comment implémenter l'interface <xref:System.ComponentModel.INotifyPropertyChanged>. L'interface communique à un contrôle dépendant les modifications apportées aux propriétés d'un objet métier.  
  
 [Guide pratique pour appliquer le modèle PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)  
 Montre comment appliquer le modèle *PropertyName*Changed aux propriétés d’un contrôle utilisateur Windows Forms.  
  
 [Guide pratique pour implémenter l’interface ITypedList](how-to-implement-the-itypedlist-interface.md)  
 Montre comment activer la découverte du schéma pour une liste pouvant être liée en implémentant l'interface <xref:System.ComponentModel.ITypedList>.  
  
 [Guide pratique pour implémenter l'interface IListSource](how-to-implement-the-ilistsource-interface.md)  
 Montre comment implémenter l'interface <xref:System.ComponentModel.IListSource> pour créer une classe pouvant être liée qui n'implémente pas <xref:System.Collections.IList> mais fournit une liste à partir d'un autre emplacement.  
  
 [Guide pratique pour s’assurer que plusieurs contrôles liés à la même source de données restent synchronisés](multiple-controls-bound-to-data-source-synchronized.md)  
 Montre comment gérer l’événement <xref:System.Windows.Forms.BindingSource.BindingComplete> pour garantir que tous les contrôles liés à une source de données restent synchronisés.  
  
 [Guide pratique pour s'assurer que la ligne sélectionnée dans une table enfant reste au bon emplacement](ensure-the-selected-row-in-a-child-table-correct.md)  
 Montre comment s'assurer que la ligne sélectionnée dans une table enfant ne change pas quand une modification est apportée à un champ de la table parente.  
  
 Consultez également les [interfaces relatives à la liaison de données](interfaces-related-to-data-binding.md), [Comment : naviguer parmi les données dans Windows Forms](how-to-navigate-data-in-windows-forms.md)et [Comment : créer un contrôle à liaison simple dans un Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 Décrit la classe qui représente la liaison entre un composant pouvant être lié et une source de données.  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 Décrit la classe qui encapsule une source de données pour la liaison à des contrôles.  
  
## <a name="related-sections"></a>Sections connexes  
 [BindingSource, composant](./controls/bindingsource-component.md)  
 Contient une liste de rubriques qui expliquent comment utiliser le composant <xref:System.Windows.Forms.BindingSource>.  
  
 [DataGridView, contrôle](./controls/datagridview-control-windows-forms.md)  
 Fournit une liste de rubriques qui expliquent comment utiliser un contrôle datagrid pouvant être lié.  
  
 Consultez également [accès aux données dans Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).
