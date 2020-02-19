---
title: 'Comment : effectuer une liaison à un service Web'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
ms.openlocfilehash: 3a3f6edc974448ddab9fe30e97bdc1130d3b97dc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449970"
---
# <a name="how-to-bind-to-a-web-service"></a>Comment : effectuer une liaison à un service Web
Cet exemple montre comment effectuer une liaison à des objets retournés par les appels de méthode de service Web.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le service de contenu MSDN/TechNet Publishing System (MTPS) pour récupérer la liste des langues prises en charge par un document spécifié.  
  
 Avant d’appeler un service Web, vous devez créer une référence à celui-ci. Pour créer une référence Web au service MTPS à l’aide de Visual Studio, procédez comme suit :  
  
1. Ouvrez votre projet dans Visual Studio.  
  
2. Dans le menu **projet** , cliquez sur **Ajouter une référence Web**.  
  
3. Dans la boîte de dialogue, définissez l' **URL** sur [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).  
  
4. Appuyez sur **Go** , puis sur **Ajouter une référence**.  
  
 Ensuite, vous appelez la méthode de service Web et définissez la <xref:System.Windows.FrameworkElement.DataContext%2A> du contrôle ou de la fenêtre approprié (e) sur l’objet retourné. La méthode `GetContent` du service MTPS utilise une référence à l’objet `getContentRequest`. Par conséquent, l’exemple suivant configure d’abord un objet de requête :  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 Une fois la <xref:System.Windows.FrameworkElement.DataContext%2A> définie, vous pouvez créer des liaisons aux propriétés de l’objet sur lequel la <xref:System.Windows.FrameworkElement.DataContext%2A> a été définie. Dans cet exemple, le <xref:System.Windows.FrameworkElement.DataContext%2A> est défini sur l’objet `getContentResponse` retourné par la méthode `GetContent`. Dans l’exemple suivant, le <xref:System.Windows.Controls.ItemsControl> se lie à et affiche les valeurs de `locale` de `availableVersionsAndLocales` de `getContentResponse`.  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 Pour plus d’informations sur la structure des `getContentResponse`, consultez la [documentation relative au service de contenu](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d'ensemble des sources de liaison](binding-sources-overview.md)
- [Rendre des données disponibles pour la liaison en XAML](how-to-make-data-available-for-binding-in-xaml.md)
