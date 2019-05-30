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
ms.openlocfilehash: 1a8c2b6ca9701f5eec4a8f43eaae531a0cfc18c1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377711"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a>Utilisation de la Bibliothèque de classes portable avec le modèle d'affichage Modèle-Affichage
Vous pouvez utiliser le .NET Framework [bibliothèque de classes Portable](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) pour implémenter le modèle modèle modèle-vue-vue (MVVM) et de partager des assemblages entre plusieurs plateformes.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM est un modèle d’application qui isole l’interface utilisateur à partir de la logique métier sous-jacente. Vous pouvez implémenter les classes de modèle model et view dans un [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] de projet dans Visual Studio 2012 et ensuite créer des vues personnalisées pour différentes plateformes. Cette approche vous permet d’écrire les données de modèle et une logique métier qu’une seule fois et utilisez ce code à partir de .NET Framework, Silverlight, Windows Phone, et [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] applications, comme indiqué dans l’illustration suivante.

 ![Affiche la bibliothèque de classes Portable avec des assemblys de partage de MVVM sur plusieurs plateformes.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 Cette rubrique ne fournit pas des informations générales sur le modèle MVVM. Il fournit uniquement des informations sur l’utilisation [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] pour implémenter le modèle MVVM. Pour plus d’informations sur le modèle MVVM, consultez le [MVVM Guide de démarrage rapide à l’aide de la 5.0 bibliothèque Prism pour WPF](https://docs.microsoft.com/previous-versions/msp-n-p/gg430857(v=pandp.40)).

## <a name="classes-that-support-mvvm"></a>Classes qui prennent en charge de MVVM
 Lorsque vous ciblez le .NET Framework 4.5, [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Silverlight ou Windows Phone 7.5 pour votre [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projet, les classes suivantes sont disponibles pour implémenter le modèle MVVM :

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

- Toutes les classes dans le <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> espace de noms

## <a name="implementing-mvvm"></a>Implémentation MVVM
 Pour implémenter le modèle MVVM, vous créez généralement le modèle et le modèle de vue dans un [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] de projet, car un [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projet ne peut pas référencer un projet non portable. Le modèle et le modèle de vue peuvent être dans le même projet ou dans des projets distincts. Si vous utilisez des projets distincts, ajoutez une référence à partir du projet de modèle de vue au projet de modèle.

 Après la compilation du modèle et afficher les projets de modèle, vous référencez ces assemblys dans l’application qui contient la vue. Si la vue interagit uniquement avec le modèle de vue, vous ne devez référencer l’assembly qui contient le modèle de vue.

### <a name="model"></a>Modèle
 L’exemple suivant montre une classe de modèle simplifié qui peut se trouver dans un [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projet.

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 L’exemple suivant montre un moyen simple de le remplir, récupérer et mettre à jour les données dans un [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projet. Dans une application réelle, vous récupérez les données à partir d’une source telle qu’un service Windows Communication Foundation (WCF).

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>Modèle de vue
 Une classe de base pour les modèles de vue est fréquemment ajoutée lors de l’implémentation du modèle MVVM. L’exemple suivant montre une classe de base.

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 Une implémentation de la <xref:System.Windows.Input.ICommand> interface est fréquemment utilisée avec le modèle MVVM. L'exemple suivant illustre une implémentation de l'interface <xref:System.Windows.Input.ICommand>.

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 L’exemple suivant montre un modèle de vue simplifiée.

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Vue  
 À partir d’une application .NET Framework 4.5, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] application, application Silverlight ou application Windows Phone 7.5, vous pouvez référencer l’assembly qui contient les projets de modèle de modèle et la vue.  Vous permet ensuite de créer une vue qui interagit avec le modèle de vue. L’exemple suivant montre une application Windows Presentation Foundation (WPF) simplifiée qui Récupère et met à jour des données à partir du modèle de vue. Vous pouvez créer des vues similaires dans Silverlight, Windows Phone, ou [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] applications.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque de classes portable](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)
