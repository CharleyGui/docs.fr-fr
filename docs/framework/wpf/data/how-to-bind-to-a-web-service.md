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
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="9c164-102">Comment : effectuer une liaison à un service Web</span><span class="sxs-lookup"><span data-stu-id="9c164-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="9c164-103">Cet exemple montre comment effectuer une liaison à des objets retournés par les appels de méthode de service Web.</span><span class="sxs-lookup"><span data-stu-id="9c164-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c164-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c164-104">Example</span></span>  
 <span data-ttu-id="9c164-105">Cet exemple utilise le service de contenu MSDN/TechNet Publishing System (MTPS) pour récupérer la liste des langues prises en charge par un document spécifié.</span><span class="sxs-lookup"><span data-stu-id="9c164-105">This example uses the MSDN/TechNet Publishing System (MTPS) Content Service to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="9c164-106">Avant d’appeler un service Web, vous devez créer une référence à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="9c164-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="9c164-107">Pour créer une référence Web au service MTPS à l’aide de Visual Studio, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9c164-107">To create a Web reference to the MTPS service using Visual Studio, follow the following steps:</span></span>  
  
1. <span data-ttu-id="9c164-108">Ouvrez votre projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c164-108">Open your project in Visual Studio.</span></span>  
  
2. <span data-ttu-id="9c164-109">Dans le menu **projet** , cliquez sur **Ajouter une référence Web**.</span><span class="sxs-lookup"><span data-stu-id="9c164-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3. <span data-ttu-id="9c164-110">Dans la boîte de dialogue, définissez l' **URL** sur [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span><span class="sxs-lookup"><span data-stu-id="9c164-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4. <span data-ttu-id="9c164-111">Appuyez sur **Go** , puis sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="9c164-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="9c164-112">Ensuite, vous appelez la méthode de service Web et définissez la <xref:System.Windows.FrameworkElement.DataContext%2A> du contrôle ou de la fenêtre approprié (e) sur l’objet retourné.</span><span class="sxs-lookup"><span data-stu-id="9c164-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="9c164-113">La méthode `GetContent` du service MTPS utilise une référence à l’objet `getContentRequest`.</span><span class="sxs-lookup"><span data-stu-id="9c164-113">The `GetContent` method of the MTPS service takes a reference to the `getContentRequest` object.</span></span> <span data-ttu-id="9c164-114">Par conséquent, l’exemple suivant configure d’abord un objet de requête :</span><span class="sxs-lookup"><span data-stu-id="9c164-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="9c164-115">Une fois la <xref:System.Windows.FrameworkElement.DataContext%2A> définie, vous pouvez créer des liaisons aux propriétés de l’objet sur lequel la <xref:System.Windows.FrameworkElement.DataContext%2A> a été définie.</span><span class="sxs-lookup"><span data-stu-id="9c164-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="9c164-116">Dans cet exemple, le <xref:System.Windows.FrameworkElement.DataContext%2A> est défini sur l’objet `getContentResponse` retourné par la méthode `GetContent`.</span><span class="sxs-lookup"><span data-stu-id="9c164-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the `getContentResponse` object returned by the `GetContent` method.</span></span> <span data-ttu-id="9c164-117">Dans l’exemple suivant, le <xref:System.Windows.Controls.ItemsControl> se lie à et affiche les valeurs de `locale` de `availableVersionsAndLocales` de `getContentResponse`.</span><span class="sxs-lookup"><span data-stu-id="9c164-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the `locale` values of `availableVersionsAndLocales` of `getContentResponse`.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="9c164-118">Pour plus d’informations sur la structure des `getContentResponse`, consultez la [documentation relative au service de contenu](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span><span class="sxs-lookup"><span data-stu-id="9c164-118">For information about the structure of `getContentResponse`, see [Content Service documentation](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c164-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c164-119">See also</span></span>

- [<span data-ttu-id="9c164-120">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="9c164-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="9c164-121">Vue d'ensemble des sources de liaison</span><span class="sxs-lookup"><span data-stu-id="9c164-121">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="9c164-122">Rendre des données disponibles pour la liaison en XAML</span><span class="sxs-lookup"><span data-stu-id="9c164-122">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
