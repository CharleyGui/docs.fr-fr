---
title: Liaison de données
description: Découvrez comment utiliser la liaison de données dans Windows Forms pour afficher et modifier les informations d’une source de données dans les contrôles du formulaire.
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 3dfce24147caf9b138916ca8dc3b7a9010439f58
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325539"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="11f5a-103">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11f5a-103">Windows Forms Data Binding</span></span>
<span data-ttu-id="11f5a-104">La liaison de données dans les Windows Forms vous permet d'afficher et de modifier les informations d'une source de données dans les contrôles du formulaire.</span><span class="sxs-lookup"><span data-stu-id="11f5a-104">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="11f5a-105">Vous pouvez établir une liaison à une source de données traditionnelle et à presque toute structure qui contient des données.</span><span class="sxs-lookup"><span data-stu-id="11f5a-105">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11f5a-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="11f5a-106">In This Section</span></span>  
 [<span data-ttu-id="11f5a-107">Liaison de données et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11f5a-107">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)  
 <span data-ttu-id="11f5a-108">Fournit une vue d’ensemble de la liaison de données dans les Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="11f5a-108">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="11f5a-109">Sources de données prises en charge par les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11f5a-109">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="11f5a-110">Décrit les sources de données qui peuvent être utilisées avec Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="11f5a-110">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="11f5a-111">Interfaces participant à la liaison de données</span><span class="sxs-lookup"><span data-stu-id="11f5a-111">Interfaces Related to Data Binding</span></span>](interfaces-related-to-data-binding.md)  
 <span data-ttu-id="11f5a-112">Décrit plusieurs interfaces utilisées avec la liaison de données Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="11f5a-112">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="11f5a-113">Procédure : parcourir les données dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11f5a-113">How to: Navigate Data in Windows Forms</span></span>](how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="11f5a-114">Montre comment parcourir les éléments dans une source de données.</span><span class="sxs-lookup"><span data-stu-id="11f5a-114">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="11f5a-115">Notification de modifications dans la liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11f5a-115">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="11f5a-116">Décrit les différents types de notifications de modifications pour la liaison de données Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="11f5a-116">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="11f5a-117">Procédure : implémenter l’interface INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="11f5a-117">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="11f5a-118">Montre comment implémenter l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="11f5a-118">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="11f5a-119">L'interface communique à un contrôle dépendant les modifications apportées aux propriétés d'un objet métier.</span><span class="sxs-lookup"><span data-stu-id="11f5a-119">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="11f5a-120">Procédure : appliquer le modèle PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="11f5a-120">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="11f5a-121">Montre comment appliquer le modèle *PropertyName*Changed aux propriétés d’un contrôle utilisateur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="11f5a-121">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="11f5a-122">Procédure : implémenter l’interface ITypedList</span><span class="sxs-lookup"><span data-stu-id="11f5a-122">How to: Implement the ITypedList Interface</span></span>](how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="11f5a-123">Montre comment activer la découverte du schéma pour une liste pouvant être liée en implémentant l'interface <xref:System.ComponentModel.ITypedList>.</span><span class="sxs-lookup"><span data-stu-id="11f5a-123">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="11f5a-124">Procédure : implémenter l’interface IListSource</span><span class="sxs-lookup"><span data-stu-id="11f5a-124">How to: Implement the IListSource Interface</span></span>](how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="11f5a-125">Montre comment implémenter l'interface <xref:System.ComponentModel.IListSource> pour créer une classe pouvant être liée qui n'implémente pas <xref:System.Collections.IList> mais fournit une liste à partir d'un autre emplacement.</span><span class="sxs-lookup"><span data-stu-id="11f5a-125">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="11f5a-126">Procédure : vérifier que plusieurs contrôles liés à la même source de données restent synchronisés</span><span class="sxs-lookup"><span data-stu-id="11f5a-126">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="11f5a-127">Montre comment gérer l’événement <xref:System.Windows.Forms.BindingSource.BindingComplete> pour garantir que tous les contrôles liés à une source de données restent synchronisés.</span><span class="sxs-lookup"><span data-stu-id="11f5a-127">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="11f5a-128">Procédure : vérifier que la ligne sélectionnée dans une table enfant reste à la bonne position</span><span class="sxs-lookup"><span data-stu-id="11f5a-128">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="11f5a-129">Montre comment s'assurer que la ligne sélectionnée dans une table enfant ne change pas quand une modification est apportée à un champ de la table parente.</span><span class="sxs-lookup"><span data-stu-id="11f5a-129">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="11f5a-130">Consultez également les [interfaces relatives à la liaison de données](interfaces-related-to-data-binding.md), [Comment : naviguer parmi les données dans Windows Forms](how-to-navigate-data-in-windows-forms.md)et [Comment : créer un contrôle à liaison simple dans un Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="11f5a-130">Also see [Interfaces Related to Data Binding](interfaces-related-to-data-binding.md), [How to: Navigate Data in Windows Forms](how-to-navigate-data-in-windows-forms.md), and [How to: Create a Simple-Bound Control on a Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="11f5a-131">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="11f5a-131">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="11f5a-132">Décrit la classe qui représente la liaison entre un composant pouvant être lié et une source de données.</span><span class="sxs-lookup"><span data-stu-id="11f5a-132">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="11f5a-133">Décrit la classe qui encapsule une source de données pour la liaison à des contrôles.</span><span class="sxs-lookup"><span data-stu-id="11f5a-133">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="11f5a-134">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="11f5a-134">Related Sections</span></span>  
 [<span data-ttu-id="11f5a-135">Composant BindingSource</span><span class="sxs-lookup"><span data-stu-id="11f5a-135">BindingSource Component</span></span>](./controls/bindingsource-component.md)  
 <span data-ttu-id="11f5a-136">Contient une liste de rubriques qui expliquent comment utiliser le composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="11f5a-136">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="11f5a-137">Contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="11f5a-137">DataGridView Control</span></span>](./controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="11f5a-138">Fournit une liste de rubriques qui expliquent comment utiliser un contrôle datagrid pouvant être lié.</span><span class="sxs-lookup"><span data-stu-id="11f5a-138">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="11f5a-139">Consultez également [accès aux données dans Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="11f5a-139">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
