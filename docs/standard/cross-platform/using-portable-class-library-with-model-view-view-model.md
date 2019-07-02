---
title: Utilisation de la Bibliothèque de classes portable avec le modèle d'affichage Modèle-Affichage
ms.date: 07/18/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b53be90764c6537fb27cb1b5ed781a68e69effa0
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504679"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="f57f4-102">Utilisation de la Bibliothèque de classes portable avec le modèle d'affichage Modèle-Affichage</span><span class="sxs-lookup"><span data-stu-id="f57f4-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="f57f4-103">Vous pouvez utiliser le .NET Framework [bibliothèque de classes Portable](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) pour implémenter le modèle modèle modèle-vue-vue (MVVM) et de partager des assemblages entre plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="f57f4-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="f57f4-104">MVVM est un modèle d’application qui isole l’interface utilisateur à partir de la logique métier sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="f57f4-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="f57f4-105">Vous pouvez implémenter les modèle et afficher des classes de modèle dans un projet de bibliothèque de classes portables dans Visual Studio 2012 et ensuite créer des vues personnalisées pour différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="f57f4-105">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="f57f4-106">Cette approche vous permet d’écrire les données de modèle et une logique métier qu’une seule fois et utilisez ce code à partir de .NET Framework, Silverlight, Windows Phone, et [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] applications, comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="f57f4-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps, as shown in the following illustration.</span></span>

 ![Affiche la bibliothèque de classes Portable avec des assemblys de partage de MVVM sur plusieurs plateformes.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="f57f4-108">Cette rubrique ne fournit pas des informations générales sur le modèle MVVM.</span><span class="sxs-lookup"><span data-stu-id="f57f4-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="f57f4-109">Il fournit uniquement des informations sur l’utilisation de bibliothèque de classes Portable pour implémenter le modèle MVVM.</span><span class="sxs-lookup"><span data-stu-id="f57f4-109">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="f57f4-110">Pour plus d’informations sur le modèle MVVM, consultez le [MVVM Guide de démarrage rapide à l’aide de la 5.0 bibliothèque Prism pour WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span><span class="sxs-lookup"><span data-stu-id="f57f4-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="f57f4-111">Classes qui prennent en charge de MVVM</span><span class="sxs-lookup"><span data-stu-id="f57f4-111">Classes That Support MVVM</span></span>
 <span data-ttu-id="f57f4-112">Lorsque vous ciblez le .NET Framework 4.5, [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight ou Windows Phone 7.5 pour votre projet de bibliothèque de classes portables, les classes suivantes sont disponibles pour implémenter le modèle MVVM :</span><span class="sxs-lookup"><span data-stu-id="f57f4-112">When you target the .NET Framework 4.5, [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="f57f4-113">Classe <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f57f4-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="f57f4-114">Classe <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f57f4-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="f57f4-115">Classe <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f57f4-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="f57f4-116">Classe <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f57f4-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="f57f4-117">Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f57f4-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="f57f4-118">Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f57f4-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="f57f4-119">Classe <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f57f4-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="f57f4-120">Classe <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f57f4-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="f57f4-121">Classe <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f57f4-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="f57f4-122">Classe <xref:System.Windows.Input.ICommand?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f57f4-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="f57f4-123">Toutes les classes dans le <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> espace de noms</span><span class="sxs-lookup"><span data-stu-id="f57f4-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="f57f4-124">Implémentation MVVM</span><span class="sxs-lookup"><span data-stu-id="f57f4-124">Implementing MVVM</span></span>
 <span data-ttu-id="f57f4-125">Pour implémenter le modèle MVVM, vous généralement créer le modèle et le modèle de vue dans un projet de bibliothèque de classes Portable, car un projet de bibliothèque de classes Portable ne peut pas référencer un projet non portable.</span><span class="sxs-lookup"><span data-stu-id="f57f4-125">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="f57f4-126">Le modèle et le modèle de vue peuvent être dans le même projet ou dans des projets distincts.</span><span class="sxs-lookup"><span data-stu-id="f57f4-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="f57f4-127">Si vous utilisez des projets distincts, ajoutez une référence à partir du projet de modèle de vue au projet de modèle.</span><span class="sxs-lookup"><span data-stu-id="f57f4-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="f57f4-128">Après la compilation du modèle et afficher les projets de modèle, vous référencez ces assemblys dans l’application qui contient la vue.</span><span class="sxs-lookup"><span data-stu-id="f57f4-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="f57f4-129">Si la vue interagit uniquement avec le modèle de vue, vous ne devez référencer l’assembly qui contient le modèle de vue.</span><span class="sxs-lookup"><span data-stu-id="f57f4-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="f57f4-130">Modèle</span><span class="sxs-lookup"><span data-stu-id="f57f4-130">Model</span></span>
 <span data-ttu-id="f57f4-131">L’exemple suivant montre une classe de modèle simplifié qui peut se trouver dans un projet de bibliothèque de classes Portable.</span><span class="sxs-lookup"><span data-stu-id="f57f4-131">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="f57f4-132">L’exemple suivant montre un moyen simple de le remplir, récupérer et mettre à jour les données dans un projet de bibliothèque de classes Portable.</span><span class="sxs-lookup"><span data-stu-id="f57f4-132">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="f57f4-133">Dans une application réelle, vous récupérez les données à partir d’une source telle qu’un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f57f4-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="f57f4-134">Modèle de vue</span><span class="sxs-lookup"><span data-stu-id="f57f4-134">View Model</span></span>
 <span data-ttu-id="f57f4-135">Une classe de base pour les modèles de vue est fréquemment ajoutée lors de l’implémentation du modèle MVVM.</span><span class="sxs-lookup"><span data-stu-id="f57f4-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="f57f4-136">L’exemple suivant montre une classe de base.</span><span class="sxs-lookup"><span data-stu-id="f57f4-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="f57f4-137">Une implémentation de la <xref:System.Windows.Input.ICommand> interface est fréquemment utilisée avec le modèle MVVM.</span><span class="sxs-lookup"><span data-stu-id="f57f4-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="f57f4-138">L'exemple suivant illustre une implémentation de l'interface <xref:System.Windows.Input.ICommand>.</span><span class="sxs-lookup"><span data-stu-id="f57f4-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="f57f4-139">L’exemple suivant montre un modèle de vue simplifiée.</span><span class="sxs-lookup"><span data-stu-id="f57f4-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="f57f4-140">Vue</span><span class="sxs-lookup"><span data-stu-id="f57f4-140">View</span></span>  
 <span data-ttu-id="f57f4-141">À partir d’une application .NET Framework 4.5, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] application, application Silverlight ou application Windows Phone 7.5, vous pouvez référencer l’assembly qui contient les projets de modèle de modèle et la vue.</span><span class="sxs-lookup"><span data-stu-id="f57f4-141">From a .NET Framework 4.5 app, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="f57f4-142">Vous permet ensuite de créer une vue qui interagit avec le modèle de vue.</span><span class="sxs-lookup"><span data-stu-id="f57f4-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="f57f4-143">L’exemple suivant montre une application Windows Presentation Foundation (WPF) simplifiée qui Récupère et met à jour des données à partir du modèle de vue.</span><span class="sxs-lookup"><span data-stu-id="f57f4-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="f57f4-144">Vous pouvez créer des vues similaires dans Silverlight, Windows Phone, ou [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] applications.</span><span class="sxs-lookup"><span data-stu-id="f57f4-144">You could create similar views in Silverlight, Windows Phone, or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="f57f4-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f57f4-145">See also</span></span>

- [<span data-ttu-id="f57f4-146">Bibliothèque de classes portable</span><span class="sxs-lookup"><span data-stu-id="f57f4-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
