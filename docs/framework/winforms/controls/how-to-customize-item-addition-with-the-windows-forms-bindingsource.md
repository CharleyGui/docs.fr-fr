---
title: Personnaliser l’ajout d’éléments avec le composant BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 7d74fe6b4bbb1ddb94b359f5ba3ae32ed398d1dd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738315"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="fae20-102">Comment : personnaliser l'ajout d'éléments avec le composant BindingSource Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fae20-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="fae20-103">Quand vous utilisez un composant <xref:System.Windows.Forms.BindingSource> pour lier un contrôle Windows Forms à une source de données, vous pouvez être contraint de personnaliser la création de nouveaux éléments.</span><span class="sxs-lookup"><span data-stu-id="fae20-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="fae20-104">Le composant <xref:System.Windows.Forms.BindingSource> simplifie cette personnalisation en fournissant l'événement <xref:System.Windows.Forms.BindingSource.AddingNew> , qui est généralement déclenché quand le contrôle lié doit créer un élément.</span><span class="sxs-lookup"><span data-stu-id="fae20-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="fae20-105">Votre gestionnaire d'événements peut fournir tout comportement personnalisé nécessaire (par exemple, appeler une méthode sur un service web ou obtenir un nouvel objet à partir d'une fabrique de classe).</span><span class="sxs-lookup"><span data-stu-id="fae20-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fae20-106">Quand un élément est ajouté en gérant l'événement <xref:System.Windows.Forms.BindingSource.AddingNew> , cet ajout ne peut pas être annulé.</span><span class="sxs-lookup"><span data-stu-id="fae20-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fae20-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="fae20-107">Example</span></span>  
 <span data-ttu-id="fae20-108">L'exemple suivant montre comment lier un contrôle <xref:System.Windows.Forms.DataGridView> à une fabrique de classe à l'aide d'un composant <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="fae20-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="fae20-109">Quand l'utilisateur clique sur la nouvelle ligne du contrôle <xref:System.Windows.Forms.DataGridView> , l'événement <xref:System.Windows.Forms.BindingSource.AddingNew> est déclenché.</span><span class="sxs-lookup"><span data-stu-id="fae20-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="fae20-110">Le gestionnaire d'événements crée un objet `DemoCustomer` , qui est affecté à la propriété <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fae20-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="fae20-111">Cela provoque l'ajout du nouvel objet `DemoCustomer` à la liste du composant <xref:System.Windows.Forms.BindingSource> et son affichage sur la nouvelle ligne du contrôle <xref:System.Windows.Forms.DataGridView> .</span><span class="sxs-lookup"><span data-stu-id="fae20-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fae20-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="fae20-112">Compiling the Code</span></span>  
 <span data-ttu-id="fae20-113">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="fae20-113">This example requires:</span></span>  
  
- <span data-ttu-id="fae20-114">Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="fae20-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae20-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fae20-115">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="fae20-116">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="fae20-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="fae20-117">Comment : lier un contrôle Windows Forms à un type</span><span class="sxs-lookup"><span data-stu-id="fae20-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
