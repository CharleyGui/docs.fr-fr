---
title: Utilisation de la Bibliothèque de classes portable avec le modèle d'affichage Modèle-Affichage
ms.date: 07/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
ms.openlocfilehash: e8bce469fd09de02ef6ab30e21ae20a9b9f71325
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259268"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="ca191-102">Utilisation de la Bibliothèque de classes portable avec le modèle d'affichage Modèle-Affichage</span><span class="sxs-lookup"><span data-stu-id="ca191-102">Using Portable Class Library with Model-View-View Model</span></span>

<span data-ttu-id="ca191-103">Vous pouvez utiliser la [bibliothèque de classes Portable](portable-class-library.md) .NET Framework pour implémenter le modèle MVVM (Model-View-View Model) et partager des assemblys sur plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="ca191-103">You can use the .NET Framework [Portable Class Library](portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="ca191-104">MVVM est un modèle d’application qui isole l’interface utilisateur de la logique métier sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="ca191-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="ca191-105">Vous pouvez implémenter les classes Model et View Model dans un projet de bibliothèque de classes portables dans Visual Studio 2012, puis créer des vues personnalisées pour différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="ca191-105">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="ca191-106">Cette approche vous permet d’écrire le modèle de données et la logique métier une seule fois, et d’utiliser ce code à partir des applications du Windows Store .NET Framework, Silverlight, Windows Phone et Windows 8. x, comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="ca191-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and Windows 8.x Store apps, as shown in the following illustration.</span></span>

 ![Affiche la bibliothèque de classes portable avec les assemblys de partage MVVM sur les plateformes.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="ca191-108">Cette rubrique ne fournit pas d’informations générales sur le modèle MVVM.</span><span class="sxs-lookup"><span data-stu-id="ca191-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="ca191-109">Il fournit uniquement des informations sur l’utilisation de la bibliothèque de classes portables pour implémenter MVVM.</span><span class="sxs-lookup"><span data-stu-id="ca191-109">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="ca191-110">Pour plus d’informations sur MVVM, consultez le Guide de [démarrage rapide de MVVM à l’aide de la bibliothèque Prism 5,0 pour WPF](/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span><span class="sxs-lookup"><span data-stu-id="ca191-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="ca191-111">Classes qui prennent en charge MVVM</span><span class="sxs-lookup"><span data-stu-id="ca191-111">Classes That Support MVVM</span></span>

 <span data-ttu-id="ca191-112">Quand vous ciblez le .NET Framework 4,5, .NET pour les applications du Windows 8. x Store, Silverlight ou Windows Phone 7,5 pour votre projet de bibliothèque de classes portables, les classes suivantes sont disponibles pour implémenter le modèle MVVM :</span><span class="sxs-lookup"><span data-stu-id="ca191-112">When you target the .NET Framework 4.5, .NET for Windows 8.x Store apps, Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="ca191-113">Classe <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca191-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="ca191-114">Classe <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca191-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="ca191-115">Classe <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca191-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="ca191-116">Classe <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca191-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="ca191-117">Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca191-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="ca191-118">Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca191-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="ca191-119">Classe <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca191-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="ca191-120">Classe <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca191-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="ca191-121">Classe <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca191-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="ca191-122">Classe <xref:System.Windows.Input.ICommand?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ca191-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="ca191-123">Toutes les classes de l' <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> espace de noms</span><span class="sxs-lookup"><span data-stu-id="ca191-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="ca191-124">Implémentation de MVVM</span><span class="sxs-lookup"><span data-stu-id="ca191-124">Implementing MVVM</span></span>

 <span data-ttu-id="ca191-125">Pour implémenter MVVM, vous créez généralement le modèle et le modèle de vue dans un projet de bibliothèque de classes portables, car un projet de bibliothèque de classes portables ne peut pas faire référence à un projet non portable.</span><span class="sxs-lookup"><span data-stu-id="ca191-125">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="ca191-126">Le modèle et le modèle de vue peuvent se trouver dans le même projet ou dans des projets distincts.</span><span class="sxs-lookup"><span data-stu-id="ca191-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="ca191-127">Si vous utilisez des projets distincts, ajoutez une référence du projet de modèle de vue au projet de modèle.</span><span class="sxs-lookup"><span data-stu-id="ca191-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="ca191-128">Après avoir compilé le modèle et les projets de modèle de vue, vous référencez ces assemblys dans l’application qui contient la vue.</span><span class="sxs-lookup"><span data-stu-id="ca191-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="ca191-129">Si la vue interagit uniquement avec le modèle de vue, il vous suffit de référencer l’assembly qui contient le modèle de vue.</span><span class="sxs-lookup"><span data-stu-id="ca191-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="ca191-130">Modèle</span><span class="sxs-lookup"><span data-stu-id="ca191-130">Model</span></span>

 <span data-ttu-id="ca191-131">L’exemple suivant montre une classe de modèle simplifiée qui peut résider dans un projet de bibliothèque de classes portables.</span><span class="sxs-lookup"><span data-stu-id="ca191-131">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="ca191-132">L’exemple suivant illustre une méthode simple pour remplir, récupérer et mettre à jour les données dans un projet de bibliothèque de classes portable.</span><span class="sxs-lookup"><span data-stu-id="ca191-132">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="ca191-133">Dans une application réelle, vous récupérez les données d’une source, par exemple un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ca191-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="ca191-134">Afficher le modèle</span><span class="sxs-lookup"><span data-stu-id="ca191-134">View Model</span></span>

 <span data-ttu-id="ca191-135">Une classe de base pour les modèles de vue est fréquemment ajoutée lors de l’implémentation du modèle MVVM.</span><span class="sxs-lookup"><span data-stu-id="ca191-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="ca191-136">L’exemple suivant montre une classe de base.</span><span class="sxs-lookup"><span data-stu-id="ca191-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="ca191-137">Une implémentation de l' <xref:System.Windows.Input.ICommand> interface est fréquemment utilisée avec le modèle MVVM.</span><span class="sxs-lookup"><span data-stu-id="ca191-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="ca191-138">L'exemple suivant illustre une implémentation de l'interface <xref:System.Windows.Input.ICommand>.</span><span class="sxs-lookup"><span data-stu-id="ca191-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="ca191-139">L’exemple suivant montre un modèle de vue simplifié.</span><span class="sxs-lookup"><span data-stu-id="ca191-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="ca191-140">Affichage</span><span class="sxs-lookup"><span data-stu-id="ca191-140">View</span></span>  

 <span data-ttu-id="ca191-141">À partir d’une application .NET Framework 4,5, d’une application Windows 8. x Store, d’une application basée sur Silverlight ou d’une application Windows Phone 7,5, vous pouvez référencer l’assembly qui contient les projets de modèle et de modèle de vue.</span><span class="sxs-lookup"><span data-stu-id="ca191-141">From a .NET Framework 4.5 app, Windows 8.x Store app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="ca191-142">Vous créez ensuite une vue qui interagit avec le modèle de vue.</span><span class="sxs-lookup"><span data-stu-id="ca191-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="ca191-143">L’exemple suivant montre une application simplifiée Windows Presentation Foundation (WPF) qui récupère et met à jour les données à partir du modèle de vue.</span><span class="sxs-lookup"><span data-stu-id="ca191-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="ca191-144">Vous pouvez créer des affichages similaires dans les applications du Windows Store Silverlight, Windows Phone ou Windows 8. x.</span><span class="sxs-lookup"><span data-stu-id="ca191-144">You could create similar views in Silverlight, Windows Phone, or Windows 8.x Store apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ca191-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca191-145">See also</span></span>

- [<span data-ttu-id="ca191-146">Bibliothèque de classes portable</span><span class="sxs-lookup"><span data-stu-id="ca191-146">Portable Class Library</span></span>](portable-class-library.md)
