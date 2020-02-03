---
title: Naviguer parmi les données avec le contrôle BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
ms.openlocfilehash: 10508cb447e70cc387f9d98effa3bc4b5ccbbaa9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736002"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="41cc1-102">Comment : naviguer parmi les données avec le contrôle BindingNavigator Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41cc1-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="41cc1-103">Le contrôle <xref:System.Windows.Forms.BindingNavigator> dans Windows Forms permet aux développeurs de fournir aux utilisateurs finaux une interface utilisateur de  navigation et de manipulation de données simple sur les formulaires qu'ils créent.</span><span class="sxs-lookup"><span data-stu-id="41cc1-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="41cc1-104">Le contrôle <xref:System.Windows.Forms.BindingNavigator> est un contrôle <xref:System.Windows.Forms.ToolStrip> avec des boutons préconfigurés pour la navigation vers quatre enregistrements (premier, dernier, suivant et précédent) dans un jeu de données, ainsi que des boutons pour ajouter et supprimer des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="41cc1-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="41cc1-105">L'ajout de boutons au contrôle <xref:System.Windows.Forms.BindingNavigator> est facile, car il s'agit d'un contrôle <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="41cc1-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="41cc1-106">Pour obtenir des exemples, consultez [Comment : ajouter des boutons charger, enregistrer et annuler au contrôle Windows Forms BindingNavigator](load-save-and-cancel-bindingnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="41cc1-106">For examples, see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](load-save-and-cancel-bindingnavigator.md).</span></span>  
  
 <span data-ttu-id="41cc1-107">Pour chaque bouton sur le contrôle <xref:System.Windows.Forms.BindingNavigator>, il existe un membre correspondant du composant <xref:System.Windows.Forms.BindingSource> qui active par programmation la même fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="41cc1-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="41cc1-108">Par exemple, le bouton <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> correspond à la méthode <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> du composant <xref:System.Windows.Forms.BindingSource>, le bouton <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> correspond à la méthode <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="41cc1-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="41cc1-109">Ainsi, pour activer le contrôle <xref:System.Windows.Forms.BindingNavigator> pour parcourir des enregistrements de données, il suffit d'affecter à sa propriété <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> le composant <xref:System.Windows.Forms.BindingSource> approprié sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="41cc1-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="41cc1-110">Pour configurer le contrôle BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="41cc1-110">To set up the BindingNavigator control</span></span>  
  
1. <span data-ttu-id="41cc1-111">Ajoutez un composant <xref:System.Windows.Forms.BindingSource> nommé `bindingSource1` et deux contrôles <xref:System.Windows.Forms.TextBox> nommés `textBox1` et `textBox2`.</span><span class="sxs-lookup"><span data-stu-id="41cc1-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2. <span data-ttu-id="41cc1-112">Liez `bindingSource1` aux données et les contrôles de zone de texte à `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="41cc1-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="41cc1-113">Pour cela, collez le code suivant dans votre formulaire et appelez `LoadData` à partir de la méthode de gestion d'événements <xref:System.Windows.Forms.Form.Load> ou du constructeur du formulaire.</span><span class="sxs-lookup"><span data-stu-id="41cc1-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="41cc1-114">Ajoutez un contrôle <xref:System.Windows.Forms.BindingNavigator> nommé `bindingNavigator1` à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="41cc1-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4. <span data-ttu-id="41cc1-115">Définissez la propriété <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> pour `bindingNavigator1` et `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="41cc1-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="41cc1-116">Vous pouvez la définir avec le concepteur ou dans le code.</span><span class="sxs-lookup"><span data-stu-id="41cc1-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="41cc1-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="41cc1-117">Example</span></span>  
 <span data-ttu-id="41cc1-118">L'exemple de code suivant est l'exemple complet pour les étapes répertoriées précédemment.</span><span class="sxs-lookup"><span data-stu-id="41cc1-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41cc1-119">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="41cc1-119">Compiling the Code</span></span>  
 <span data-ttu-id="41cc1-120">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="41cc1-120">This example requires:</span></span>  
  
- <span data-ttu-id="41cc1-121">Références aux assemblys System, System.Data, System.Drawing, System.Windows.Forms et System.Xml.</span><span class="sxs-lookup"><span data-stu-id="41cc1-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41cc1-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41cc1-122">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="41cc1-123">BindingNavigator, contrôle</span><span class="sxs-lookup"><span data-stu-id="41cc1-123">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="41cc1-124">Contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="41cc1-124">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
