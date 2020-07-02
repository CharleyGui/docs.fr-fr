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
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="e7cb3-103">Procédure : implémenter l’interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="e7cb3-103">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="e7cb3-104">L’exemple de code suivant montre comment implémenter l' <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span><span class="sxs-lookup"><span data-stu-id="e7cb3-104">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="e7cb3-105">Implémentez cette interface sur les objets métier utilisés dans Windows Forms la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="e7cb3-105">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="e7cb3-106">En cas d’implémentation, l’interface communique avec un contrôle dépendant que la propriété change sur un objet métier.</span><span class="sxs-lookup"><span data-stu-id="e7cb3-106">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7cb3-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7cb3-107">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e7cb3-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7cb3-108">See also</span></span>

- [<span data-ttu-id="e7cb3-109">Procédure : appliquer le modèle PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="e7cb3-109">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="e7cb3-110">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7cb3-110">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="e7cb3-111">Comment : générer des notifications de modifications à l'aide d'un BindingSource et de l'interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="e7cb3-111">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="e7cb3-112">Notification de modifications dans la liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7cb3-112">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
