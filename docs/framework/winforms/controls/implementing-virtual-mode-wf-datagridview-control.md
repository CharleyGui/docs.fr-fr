---
title: 'Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms'
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
ms.openlocfilehash: 9e7fb3a42b56c40f713d73e3734142f4aab335f4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649993"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e3897-102">Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3897-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e3897-103">Lorsque vous souhaitez afficher de très grandes quantités de données tabulaires dans un <xref:System.Windows.Forms.DataGridView> contrôle, vous pouvez définir le <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> propriété `true` et gérer explicitement l’interaction du contrôle avec son magasin de données.</span><span class="sxs-lookup"><span data-stu-id="e3897-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="e3897-104">Cela vous permet d’optimiser les performances du contrôle dans cette situation.</span><span class="sxs-lookup"><span data-stu-id="e3897-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="e3897-105">Le <xref:System.Windows.Forms.DataGridView> contrôle fournit plusieurs événements que vous pouvez gérer pour interagir avec un magasin de données personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e3897-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="e3897-106">Cette procédure pas à pas vous guide tout au long du processus d’implémentation de ces gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="e3897-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="e3897-107">L’exemple de code dans cette rubrique utilise une source de données très simple à titre d’illustration.</span><span class="sxs-lookup"><span data-stu-id="e3897-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="e3897-108">Dans un environnement de production, vous chargez en général uniquement les lignes que vous avez besoin d’afficher dans un cache et de traiter <xref:System.Windows.Forms.DataGridView> événements manipuler et mettre à jour le cache.</span><span class="sxs-lookup"><span data-stu-id="e3897-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="e3897-109">Pour plus d’informations, consultez [implémentation du Mode virtuel avec le chargement de données juste à temps dans le contrôle de DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="e3897-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="e3897-110">Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Guide pratique pour Implémenter le Mode virtuel dans les Windows Forms DataGridView Control](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e3897-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="e3897-111">Création du formulaire</span><span class="sxs-lookup"><span data-stu-id="e3897-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="e3897-112">Pour implémenter le mode virtuel</span><span class="sxs-lookup"><span data-stu-id="e3897-112">To implement virtual mode</span></span>  
  
1. <span data-ttu-id="e3897-113">Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient un <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="e3897-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="e3897-114">Le code suivant contient une initialisation de base.</span><span class="sxs-lookup"><span data-stu-id="e3897-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="e3897-115">Il déclare des variables qui seront utilisés dans les étapes ultérieures, fournit un `Main` (méthode) et fournit une disposition de formulaire simple dans le constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="e3897-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. <span data-ttu-id="e3897-116">Implémenter un gestionnaire pour votre formulaire <xref:System.Windows.Forms.Form.Load> événement qui initialise le <xref:System.Windows.Forms.DataGridView> contrôler et remplit le magasin de données avec des exemples de valeurs.</span><span class="sxs-lookup"><span data-stu-id="e3897-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. <span data-ttu-id="e3897-117">Implémenter un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.CellValueNeeded> événement qui Récupère la valeur de cellule demandée à partir du magasin de données ou le `Customer` objet en cours de modification.</span><span class="sxs-lookup"><span data-stu-id="e3897-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="e3897-118">Cet événement se produit chaque fois que le <xref:System.Windows.Forms.DataGridView> contrôle doit peindre une cellule.</span><span class="sxs-lookup"><span data-stu-id="e3897-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. <span data-ttu-id="e3897-119">Implémenter un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.CellValuePushed> événement qui stocke une valeur de cellule modifiée dans le `Customer` objet qui représente la ligne modifiée.</span><span class="sxs-lookup"><span data-stu-id="e3897-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="e3897-120">Cet événement se produit chaque fois que l’utilisateur valide une modification de valeur de cellule.</span><span class="sxs-lookup"><span data-stu-id="e3897-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. <span data-ttu-id="e3897-121">Implémenter un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.NewRowNeeded> événement qui crée un `Customer` objet représentant une ligne nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="e3897-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="e3897-122">Cet événement se produit chaque fois que l’utilisateur entre dans la ligne pour les nouveaux enregistrements.</span><span class="sxs-lookup"><span data-stu-id="e3897-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. <span data-ttu-id="e3897-123">Implémenter un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.RowValidated> événement qui enregistre les lignes nouvelles ou modifiées dans le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="e3897-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="e3897-124">Cet événement se produit lorsque l’utilisateur modifie la ligne actuelle.</span><span class="sxs-lookup"><span data-stu-id="e3897-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. <span data-ttu-id="e3897-125">Implémenter un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> événement qui indique si le <xref:System.Windows.Forms.DataGridView.CancelRowEdit> événement se produit lorsque l’utilisateur signale une inversion de ligne en appuyant sur ÉCHAP deux fois en mode édition ou qu’une seule fois à l’extérieur en mode édition.</span><span class="sxs-lookup"><span data-stu-id="e3897-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="e3897-126">Par défaut, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> se produit après inversion de ligne lorsque toutes les cellules de la ligne actuelle ont été modifiées, sauf si le <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> propriété est définie sur `true` dans le <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="e3897-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="e3897-127">Cet événement est utile lorsque la portée de validation est déterminée au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e3897-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. <span data-ttu-id="e3897-128">Implémenter un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.CancelRowEdit> événement qui ignore les valeurs de la `Customer` objet représentant la ligne actuelle.</span><span class="sxs-lookup"><span data-stu-id="e3897-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="e3897-129">Cet événement se produit lorsque l’utilisateur signale une inversion de ligne en appuyant sur ÉCHAP deux fois en mode édition ou qu’une seule fois à l’extérieur en mode édition.</span><span class="sxs-lookup"><span data-stu-id="e3897-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="e3897-130">Cet événement ne se produit pas si aucune cellule dans la ligne actuelle a été modifiée ou si la valeur de la <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> propriété a été définie sur `false` dans un <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="e3897-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="e3897-131">Implémenter un gestionnaire pour le <xref:System.Windows.Forms.DataGridView.UserDeletingRow> événement qui supprime un `Customer` objet à partir du magasin de données ou ignore un non enregistrées `Customer` objet représentant une ligne nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="e3897-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="e3897-132">Cet événement se produit chaque fois que l’utilisateur supprime une ligne en cliquant sur un en-tête de ligne et en appuyant sur la touche SUPPR.</span><span class="sxs-lookup"><span data-stu-id="e3897-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="e3897-133">Implémenter une simple `Customers` classe pour représenter les éléments de données utilisés par cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="e3897-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="e3897-134">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="e3897-134">Testing the Application</span></span>  
 <span data-ttu-id="e3897-135">Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.</span><span class="sxs-lookup"><span data-stu-id="e3897-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="e3897-136">Pour tester le formulaire</span><span class="sxs-lookup"><span data-stu-id="e3897-136">To test the form</span></span>  
  
- <span data-ttu-id="e3897-137">Compilez et exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="e3897-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="e3897-138">Vous verrez un <xref:System.Windows.Forms.DataGridView> contrôle rempli avec trois enregistrements de client.</span><span class="sxs-lookup"><span data-stu-id="e3897-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="e3897-139">Vous pouvez modifier les valeurs de plusieurs cellules dans une ligne et appuyez sur ÉCHAP deux fois en mode édition et une fois en dehors du mode d’édition pour rétablir la ligne entière pour ses valeurs d’origine.</span><span class="sxs-lookup"><span data-stu-id="e3897-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="e3897-140">Lorsque vous modifiez, ajouter ou supprimer des lignes dans le contrôle, `Customer` objets dans le magasin de données soient modifiés, ajoutés ou supprimés.</span><span class="sxs-lookup"><span data-stu-id="e3897-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e3897-141">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e3897-141">Next Steps</span></span>  
 <span data-ttu-id="e3897-142">Cette application vous donne une compréhension élémentaire des événements que vous devez gérer pour implémenter le mode virtuel dans le <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="e3897-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e3897-143">Vous pouvez améliorer cette application de base de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="e3897-143">You can improve this basic application in a number of ways:</span></span>  
  
- <span data-ttu-id="e3897-144">Implémenter un magasin de données qui met en cache les valeurs à partir d’une base de données externe.</span><span class="sxs-lookup"><span data-stu-id="e3897-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="e3897-145">Le cache doit récupérer et ignorer les valeurs en fonction des besoins afin qu’il contienne uniquement ce qui est nécessaire pour l’affichage tout en consommant une petite quantité de mémoire sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="e3897-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
- <span data-ttu-id="e3897-146">Optimiser les performances de la banque de données selon vos besoins.</span><span class="sxs-lookup"><span data-stu-id="e3897-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="e3897-147">Par exemple, vous souhaiterez peut-être compenser pour les connexions réseau lentes plutôt que des limitations de mémoire d’ordinateur du client en utilisant une plus grande taille de cache et en réduisant le nombre de requêtes de base de données.</span><span class="sxs-lookup"><span data-stu-id="e3897-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="e3897-148">Pour plus d’informations sur la mise en cache des valeurs à partir d’une base de données externe, consultez [Comment : Implémenter le Mode virtuel avec le chargement de données juste-à-temps dans les Windows Forms DataGridView Control](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="e3897-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3897-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3897-149">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [<span data-ttu-id="e3897-150">Réglage des performances dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3897-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e3897-151">Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3897-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e3897-152">Implémentation du mode virtuel avec le chargement immédiat des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3897-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="e3897-153">Guide pratique pour Implémenter le Mode virtuel dans le contrôle de DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3897-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
