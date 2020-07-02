---
title: 'Procédure : implémenter l’interface INotifyPropertyChanged'
description: Découvrez comment implémenter l’interface INotifyPropertyChanged sur les objets métier utilisés dans Windows Forms la liaison de données.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 83d2ef32787d2dbcd877bc77dcede10111098f8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619266"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Procédure : implémenter l’interface INotifyPropertyChanged
L’exemple de code suivant montre comment implémenter l' <xref:System.ComponentModel.INotifyPropertyChanged> interface. Implémentez cette interface sur les objets métier utilisés dans Windows Forms la liaison de données. En cas d’implémentation, l’interface communique avec un contrôle dépendant que la propriété change sur un objet métier.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : appliquer le modèle PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)
- [Liaison de données Windows Forms](windows-forms-data-binding.md)
- [Comment : générer des notifications de modifications à l'aide d'un BindingSource et de l'interface INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md)
- [Notification de modifications dans la liaison de données Windows Forms](change-notification-in-windows-forms-data-binding.md)
