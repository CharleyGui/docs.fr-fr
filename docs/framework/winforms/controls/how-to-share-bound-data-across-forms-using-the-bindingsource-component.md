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
ms.openlocfilehash: 28eceaec72053d70885d54bc09179cff743ff71c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591438"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="b5e94-102">Procédure : partager des données liées entre formulaires à l’aide du composant BindingSource</span><span class="sxs-lookup"><span data-stu-id="b5e94-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="b5e94-103">Vous pouvez facilement partager des données entre des formulaires à l'aide du composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="b5e94-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="b5e94-104">Par exemple, vous souhaiterez peut-être afficher un formulaire en lecture seule qui résume les données de la source de données et un autre formulaire modifiable qui contient des informations détaillées sur l'élément actuellement sélectionné dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="b5e94-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="b5e94-105">Cet exemple illustre ce scénario.</span><span class="sxs-lookup"><span data-stu-id="b5e94-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5e94-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5e94-106">Example</span></span>  
 <span data-ttu-id="b5e94-107">L'exemple de code suivant montre comment partager un <xref:System.Windows.Forms.BindingSource> et ses données liées entre des formulaires.</span><span class="sxs-lookup"><span data-stu-id="b5e94-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="b5e94-108">Dans cet exemple, le <xref:System.Windows.Forms.BindingSource> partagé est passé au constructeur du formulaire enfant.</span><span class="sxs-lookup"><span data-stu-id="b5e94-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="b5e94-109">Le formulaire enfant permet à l'utilisateur de modifier les données de l'élément actuellement sélectionné dans le formulaire principal.</span><span class="sxs-lookup"><span data-stu-id="b5e94-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5e94-110">L'événement <xref:System.Windows.Forms.BindingSource.BindingComplete> pour le composant <xref:System.Windows.Forms.BindingSource> est géré dans l'exemple pour garantir que les deux formulaires restent synchronisés.</span><span class="sxs-lookup"><span data-stu-id="b5e94-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="b5e94-111">Pour plus d’informations à ce sujet, consultez [Comment : S’assurer que plusieurs contrôles liés à la même Source de données restent synchronisés](../multiple-controls-bound-to-data-source-synchronized.md).</span><span class="sxs-lookup"><span data-stu-id="b5e94-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b5e94-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b5e94-112">Compiling the Code</span></span>  
 <span data-ttu-id="b5e94-113">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="b5e94-113">This example requires:</span></span>  
  
- <span data-ttu-id="b5e94-114">Références aux assemblys System, System.Windows.Forms, System.Drawing, System.Data et System.Xml.</span><span class="sxs-lookup"><span data-stu-id="b5e94-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e94-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5e94-115">See also</span></span>

- [<span data-ttu-id="b5e94-116">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="b5e94-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="b5e94-117">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5e94-117">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="b5e94-118">Guide pratique pour Gérer les erreurs et Exceptions qui se produisent avec Databinding</span><span class="sxs-lookup"><span data-stu-id="b5e94-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
