---
title: 'Procédure pas à pas : implémenter le mode virtuel dans le contrôle DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
ms.openlocfilehash: 5db97b321238bc371c94e627a387bd83ca31b58a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746515"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8df99-102">Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8df99-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8df99-103">Lorsque vous souhaitez afficher de très grandes quantités de données tabulaires dans un contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez affecter à la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> la valeur `true` et gérer explicitement l’interaction du contrôle avec son magasin de données.</span><span class="sxs-lookup"><span data-stu-id="8df99-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="8df99-104">Cela vous permet d’affiner les performances du contrôle dans cette situation.</span><span class="sxs-lookup"><span data-stu-id="8df99-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="8df99-105">Le contrôle <xref:System.Windows.Forms.DataGridView> fournit plusieurs événements que vous pouvez gérer pour interagir avec un magasin de données personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8df99-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="8df99-106">Cette procédure pas à pas vous guide tout au long du processus d’implémentation de ces gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="8df99-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="8df99-107">L’exemple de code de cette rubrique utilise une source de données très simple à des fins d’illustration.</span><span class="sxs-lookup"><span data-stu-id="8df99-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="8df99-108">Dans un paramètre de production, vous chargez généralement uniquement les lignes que vous devez afficher dans un cache, et vous gérez les événements de <xref:System.Windows.Forms.DataGridView> pour interagir avec le cache et le mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="8df99-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="8df99-109">Pour plus d’informations, consultez [implémentation du mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="8df99-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="8df99-110">Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Comment : implémenter le mode virtuel dans le contrôle DataGridView Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="8df99-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="8df99-111">Création du formulaire</span><span class="sxs-lookup"><span data-stu-id="8df99-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="8df99-112">Pour implémenter le mode virtuel</span><span class="sxs-lookup"><span data-stu-id="8df99-112">To implement virtual mode</span></span>  
  
1. <span data-ttu-id="8df99-113">Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient un contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="8df99-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="8df99-114">Le code suivant contient une initialisation de base.</span><span class="sxs-lookup"><span data-stu-id="8df99-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="8df99-115">Elle déclare certaines variables qui seront utilisées dans les étapes ultérieures, fournit une méthode `Main` et fournit une disposition de formulaire simple dans le constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="8df99-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. <span data-ttu-id="8df99-116">Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.Form.Load> de votre formulaire qui initialise le contrôle <xref:System.Windows.Forms.DataGridView> et remplit le magasin de données avec des exemples de valeurs.</span><span class="sxs-lookup"><span data-stu-id="8df99-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. <span data-ttu-id="8df99-117">Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CellValueNeeded> qui récupère la valeur de cellule demandée à partir du magasin de données ou de l’objet `Customer` actuellement en cours de modification.</span><span class="sxs-lookup"><span data-stu-id="8df99-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="8df99-118">Cet événement se produit chaque fois que le contrôle de <xref:System.Windows.Forms.DataGridView> doit peindre une cellule.</span><span class="sxs-lookup"><span data-stu-id="8df99-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. <span data-ttu-id="8df99-119">Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CellValuePushed> qui stocke une valeur de cellule modifiée dans l’objet `Customer` représentant la ligne modifiée.</span><span class="sxs-lookup"><span data-stu-id="8df99-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="8df99-120">Cet événement se produit chaque fois que l’utilisateur valide une modification de valeur de cellule.</span><span class="sxs-lookup"><span data-stu-id="8df99-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. <span data-ttu-id="8df99-121">Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.NewRowNeeded> qui crée un nouvel objet `Customer` représentant une ligne nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="8df99-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="8df99-122">Cet événement se produit chaque fois que l’utilisateur entre la ligne pour les nouveaux enregistrements.</span><span class="sxs-lookup"><span data-stu-id="8df99-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. <span data-ttu-id="8df99-123">Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.RowValidated> qui enregistre les lignes nouvelles ou modifiées dans le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="8df99-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="8df99-124">Cet événement se produit chaque fois que l’utilisateur modifie la ligne actuelle.</span><span class="sxs-lookup"><span data-stu-id="8df99-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. <span data-ttu-id="8df99-125">Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> qui indique si l’événement <xref:System.Windows.Forms.DataGridView.CancelRowEdit> se produit lorsque l’utilisateur signale la Reversion de ligne en appuyant deux fois sur ÉCHAP en mode édition ou une fois en dehors du mode d’édition.</span><span class="sxs-lookup"><span data-stu-id="8df99-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="8df99-126">Par défaut, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> se produit lors de la réversion de lignes lorsque des cellules de la ligne actuelle ont été modifiées, sauf si la propriété <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> a la valeur `true` dans le gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>.</span><span class="sxs-lookup"><span data-stu-id="8df99-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="8df99-127">Cet événement est utile lorsque la portée de validation est déterminée au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8df99-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. <span data-ttu-id="8df99-128">Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CancelRowEdit> qui ignore les valeurs de l’objet `Customer` représentant la ligne actuelle.</span><span class="sxs-lookup"><span data-stu-id="8df99-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="8df99-129">Cet événement se produit lorsque l’utilisateur signale la Reversion de ligne en appuyant deux fois sur ÉCHAP en mode édition ou une fois en dehors du mode d’édition.</span><span class="sxs-lookup"><span data-stu-id="8df99-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="8df99-130">Cet événement ne se produit pas si aucune cellule de la ligne actuelle n’a été modifiée ou si la valeur de la propriété <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> a été définie sur `false` dans un gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>.</span><span class="sxs-lookup"><span data-stu-id="8df99-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="8df99-131">Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.UserDeletingRow> qui supprime un objet `Customer` existant du magasin de données ou ignore un objet `Customer` non enregistré représentant une ligne nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="8df99-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="8df99-132">Cet événement se produit chaque fois que l’utilisateur supprime une ligne en cliquant sur un en-tête de ligne et en appuyant sur la touche Suppr.</span><span class="sxs-lookup"><span data-stu-id="8df99-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="8df99-133">Implémentez une classe `Customers` simple pour représenter les éléments de données utilisés par cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="8df99-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="8df99-134">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="8df99-134">Testing the Application</span></span>  
 <span data-ttu-id="8df99-135">Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.</span><span class="sxs-lookup"><span data-stu-id="8df99-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="8df99-136">Pour tester le formulaire</span><span class="sxs-lookup"><span data-stu-id="8df99-136">To test the form</span></span>  
  
- <span data-ttu-id="8df99-137">Compilez et exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="8df99-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="8df99-138">Vous verrez un contrôle de <xref:System.Windows.Forms.DataGridView> rempli avec trois enregistrements de client.</span><span class="sxs-lookup"><span data-stu-id="8df99-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="8df99-139">Vous pouvez modifier les valeurs de plusieurs cellules d’une ligne et appuyer deux fois sur ÉCHAP en mode édition et en dehors du mode d’édition pour rétablir la totalité de la ligne à ses valeurs d’origine.</span><span class="sxs-lookup"><span data-stu-id="8df99-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="8df99-140">Lorsque vous modifiez, ajoutez ou supprimez des lignes dans le contrôle, `Customer` objets dans le magasin de données sont également modifiés, ajoutés ou supprimés.</span><span class="sxs-lookup"><span data-stu-id="8df99-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8df99-141">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8df99-141">Next Steps</span></span>  
 <span data-ttu-id="8df99-142">Cette application vous offre une compréhension de base des événements que vous devez gérer pour implémenter le mode virtuel dans le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="8df99-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="8df99-143">Vous pouvez améliorer cette application de base de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="8df99-143">You can improve this basic application in a number of ways:</span></span>  
  
- <span data-ttu-id="8df99-144">Implémentez un magasin de données qui met en cache des valeurs à partir d’une base de données externe.</span><span class="sxs-lookup"><span data-stu-id="8df99-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="8df99-145">Le cache doit récupérer et ignorer les valeurs selon les besoins afin qu’il ne contienne que ce qui est nécessaire pour l’affichage tout en consommant une petite quantité de mémoire sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="8df99-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
- <span data-ttu-id="8df99-146">Ajustez les performances du magasin de données en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="8df99-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="8df99-147">Par exemple, vous souhaiterez peut-être compenser les connexions réseau lentes plutôt que les limitations de mémoire de l’ordinateur client en utilisant une taille de cache supérieure et en minimisant le nombre de requêtes de base de données.</span><span class="sxs-lookup"><span data-stu-id="8df99-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="8df99-148">Pour plus d’informations sur la mise en cache des valeurs à partir d’une base de données externe, consultez [Comment : implémenter le mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="8df99-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8df99-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8df99-149">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [<span data-ttu-id="8df99-150">Réglage des performances dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8df99-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="8df99-151">Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8df99-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="8df99-152">Implémentation du mode virtuel avec le chargement immédiat des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8df99-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="8df99-153">Guide pratique pour implémenter le mode virtuel dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8df99-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
