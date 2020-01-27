---
title: Refléter les mises à jour de la source de données dans le contrôle avec BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
ms.openlocfilehash: f98296b477dbb674cdbdbd8d03e291dd6ca0c8a3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742441"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a><span data-ttu-id="8dfa0-102">Comment : répercuter des mises à jour de source de données dans un contrôle Windows Forms avec le BindingSource</span><span class="sxs-lookup"><span data-stu-id="8dfa0-102">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>
<span data-ttu-id="8dfa0-103">Quand vous utilisez des contrôles liés aux données, vous devez parfois répondre à des modifications de la source de données lorsque celle-ci ne déclenche pas d'événements de modification de liste.</span><span class="sxs-lookup"><span data-stu-id="8dfa0-103">When you use data-bound controls, you sometimes have to respond to changes in the data source when the data source does not raise list-changed events.</span></span> <span data-ttu-id="8dfa0-104">Quand vous utilisez le composant <xref:System.Windows.Forms.BindingSource> pour lier votre source de données à un contrôle Windows Forms, vous pouvez signaler au contrôle que votre source de données a changé en appelant la méthode <xref:System.Windows.Forms.BindingSource.ResetBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="8dfa0-104">When you use the <xref:System.Windows.Forms.BindingSource> component to bind your data source to a Windows Forms control, you can notify the control that your data source has changed by calling the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dfa0-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="8dfa0-105">Example</span></span>  
 <span data-ttu-id="8dfa0-106">L'exemple de code suivant montre comment utiliser la méthode <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> pour informer un contrôle lié d'une mise à jour dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="8dfa0-106">The following code example demonstrates using the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method to notify a bound control about an update in the data source.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8dfa0-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8dfa0-107">Compiling the Code</span></span>  
 <span data-ttu-id="8dfa0-108">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="8dfa0-108">This example requires:</span></span>  
  
- <span data-ttu-id="8dfa0-109">des références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="8dfa0-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dfa0-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8dfa0-110">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="8dfa0-111">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="8dfa0-111">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="8dfa0-112">Comment : lier un contrôle Windows Forms à un type</span><span class="sxs-lookup"><span data-stu-id="8dfa0-112">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
