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
# <a name="using-portable-class-library-with-model-view-view-model"></a>Utilisation de la Bibliothèque de classes portable avec le modèle d'affichage Modèle-Affichage

Vous pouvez utiliser la [bibliothèque de classes Portable](portable-class-library.md) .NET Framework pour implémenter le modèle MVVM (Model-View-View Model) et partager des assemblys sur plusieurs plateformes.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM est un modèle d’application qui isole l’interface utilisateur de la logique métier sous-jacente. Vous pouvez implémenter les classes Model et View Model dans un projet de bibliothèque de classes portables dans Visual Studio 2012, puis créer des vues personnalisées pour différentes plateformes. Cette approche vous permet d’écrire le modèle de données et la logique métier une seule fois, et d’utiliser ce code à partir des applications du Windows Store .NET Framework, Silverlight, Windows Phone et Windows 8. x, comme indiqué dans l’illustration suivante.

 ![Affiche la bibliothèque de classes portable avec les assemblys de partage MVVM sur les plateformes.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 Cette rubrique ne fournit pas d’informations générales sur le modèle MVVM. Il fournit uniquement des informations sur l’utilisation de la bibliothèque de classes portables pour implémenter MVVM. Pour plus d’informations sur MVVM, consultez le Guide de [démarrage rapide de MVVM à l’aide de la bibliothèque Prism 5,0 pour WPF](/previous-versions/msp-n-p/gg430857(v=pandp.40)).

## <a name="classes-that-support-mvvm"></a>Classes qui prennent en charge MVVM

 Quand vous ciblez le .NET Framework 4,5, .NET pour les applications du Windows 8. x Store, Silverlight ou Windows Phone 7,5 pour votre projet de bibliothèque de classes portables, les classes suivantes sont disponibles pour implémenter le modèle MVVM :

- Classe <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>

- Classe <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>

- Classe <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType>

- Classe <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType>

- Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType>

- Classe <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType>

- Classe <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType>

- Classe <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType>

- Classe <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType>

- Classe <xref:System.Windows.Input.ICommand?displayProperty=nameWithType>

- Toutes les classes de l' <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> espace de noms

## <a name="implementing-mvvm"></a>Implémentation de MVVM

 Pour implémenter MVVM, vous créez généralement le modèle et le modèle de vue dans un projet de bibliothèque de classes portables, car un projet de bibliothèque de classes portables ne peut pas faire référence à un projet non portable. Le modèle et le modèle de vue peuvent se trouver dans le même projet ou dans des projets distincts. Si vous utilisez des projets distincts, ajoutez une référence du projet de modèle de vue au projet de modèle.

 Après avoir compilé le modèle et les projets de modèle de vue, vous référencez ces assemblys dans l’application qui contient la vue. Si la vue interagit uniquement avec le modèle de vue, il vous suffit de référencer l’assembly qui contient le modèle de vue.

### <a name="model"></a>Modèle

 L’exemple suivant montre une classe de modèle simplifiée qui peut résider dans un projet de bibliothèque de classes portables.

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 L’exemple suivant illustre une méthode simple pour remplir, récupérer et mettre à jour les données dans un projet de bibliothèque de classes portable. Dans une application réelle, vous récupérez les données d’une source, par exemple un service Windows Communication Foundation (WCF).

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>Afficher le modèle

 Une classe de base pour les modèles de vue est fréquemment ajoutée lors de l’implémentation du modèle MVVM. L’exemple suivant montre une classe de base.

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 Une implémentation de l' <xref:System.Windows.Input.ICommand> interface est fréquemment utilisée avec le modèle MVVM. L'exemple suivant illustre une implémentation de l'interface <xref:System.Windows.Input.ICommand>.

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 L’exemple suivant montre un modèle de vue simplifié.

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Affichage  

 À partir d’une application .NET Framework 4,5, d’une application Windows 8. x Store, d’une application basée sur Silverlight ou d’une application Windows Phone 7,5, vous pouvez référencer l’assembly qui contient les projets de modèle et de modèle de vue.  Vous créez ensuite une vue qui interagit avec le modèle de vue. L’exemple suivant montre une application simplifiée Windows Presentation Foundation (WPF) qui récupère et met à jour les données à partir du modèle de vue. Vous pouvez créer des affichages similaires dans les applications du Windows Store Silverlight, Windows Phone ou Windows 8. x.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque de classes portable](portable-class-library.md)
