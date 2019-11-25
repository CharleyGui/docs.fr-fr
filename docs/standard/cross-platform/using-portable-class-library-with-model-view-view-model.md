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
ms.openlocfilehash: 445cf4178b90719f923b66a7778f60c1bc846766
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204974"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="9f2ff-102">Utilisation de la Bibliothèque de classes portable avec le modèle d'affichage Modèle-Affichage</span><span class="sxs-lookup"><span data-stu-id="9f2ff-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="9f2ff-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="9f2ff-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="9f2ff-105">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-105">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="9f2ff-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and Windows 8.x Store apps, as shown in the following illustration.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and Windows 8.x Store apps, as shown in the following illustration.</span></span>

 ![Shows the Portable Class Library with MVVM sharing assemblies across platforms.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="9f2ff-108">This topic does not provide general information about the MVVM pattern.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="9f2ff-109">It only provides information about how to use Portable Class Library to implement MVVM.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-109">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="9f2ff-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span><span class="sxs-lookup"><span data-stu-id="9f2ff-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="9f2ff-111">Classes That Support MVVM</span><span class="sxs-lookup"><span data-stu-id="9f2ff-111">Classes That Support MVVM</span></span>
 <span data-ttu-id="9f2ff-112">When you target the .NET Framework 4.5, [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span><span class="sxs-lookup"><span data-stu-id="9f2ff-112">When you target the .NET Framework 4.5, [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="9f2ff-113">Classe <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f2ff-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="9f2ff-114">Classe <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f2ff-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="9f2ff-115">Classe <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f2ff-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="9f2ff-116">Classe <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f2ff-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="9f2ff-117">Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f2ff-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="9f2ff-118">Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f2ff-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="9f2ff-119">Classe <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f2ff-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="9f2ff-120">Classe <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f2ff-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="9f2ff-121">Classe <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f2ff-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="9f2ff-122">Classe <xref:System.Windows.Input.ICommand?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f2ff-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="9f2ff-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span><span class="sxs-lookup"><span data-stu-id="9f2ff-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="9f2ff-124">Implementing MVVM</span><span class="sxs-lookup"><span data-stu-id="9f2ff-124">Implementing MVVM</span></span>
 <span data-ttu-id="9f2ff-125">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-125">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="9f2ff-126">The model and view model can be in the same project or in separate projects.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="9f2ff-127">If you use separate projects, add a reference from the view model project to the model project.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="9f2ff-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="9f2ff-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="9f2ff-130">Modèle</span><span class="sxs-lookup"><span data-stu-id="9f2ff-130">Model</span></span>
 <span data-ttu-id="9f2ff-131">The following example shows a simplified model class that could reside in a Portable Class Library project.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-131">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="9f2ff-132">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-132">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="9f2ff-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="9f2ff-134">View Model</span><span class="sxs-lookup"><span data-stu-id="9f2ff-134">View Model</span></span>
 <span data-ttu-id="9f2ff-135">A base class for view models is frequently added when implementing the MVVM pattern.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="9f2ff-136">The following example shows a base class.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="9f2ff-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="9f2ff-138">L'exemple suivant illustre une implémentation de l'interface <xref:System.Windows.Input.ICommand>.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="9f2ff-139">The following example shows a simplified view model.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="9f2ff-140">Vue</span><span class="sxs-lookup"><span data-stu-id="9f2ff-140">View</span></span>  
 <span data-ttu-id="9f2ff-141">From a .NET Framework 4.5 app, Windows 8.x Store app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-141">From a .NET Framework 4.5 app, Windows 8.x Store app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="9f2ff-142">You then create a view that interacts with the view model.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="9f2ff-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="9f2ff-144">You could create similar views in Silverlight, Windows Phone, or Windows 8.x Store apps.</span><span class="sxs-lookup"><span data-stu-id="9f2ff-144">You could create similar views in Silverlight, Windows Phone, or Windows 8.x Store apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="9f2ff-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f2ff-145">See also</span></span>

- [<span data-ttu-id="9f2ff-146">Bibliothèque de classes portable</span><span class="sxs-lookup"><span data-stu-id="9f2ff-146">Portable Class Library</span></span>](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
