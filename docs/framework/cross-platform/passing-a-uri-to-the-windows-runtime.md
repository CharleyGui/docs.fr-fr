---
title: Transmission d'un URI au Windows Runtime
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
ms.openlocfilehash: d48c257941b8e40ce2670e08fc0ff23cb21e3e1c
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687872"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="617eb-102">Transmission d'un URI au Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="617eb-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="617eb-103">Les méthodes Windows Runtime n'acceptent que des URI absolus.</span><span class="sxs-lookup"><span data-stu-id="617eb-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="617eb-104">Si vous transmettez un URI relatif à une méthode Windows Runtime, une <xref:System.ArgumentException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="617eb-104">If you pass a relative URI to a Windows Runtime method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="617eb-105">Voici pourquoi : quand vous utilisez la Windows Runtime dans .NET Framework code, la <xref:Windows.Foundation.Uri?displayProperty=nameWithType> classe apparaît comme <xref:System.Uri?displayProperty=nameWithType> dans IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="617eb-105">Here's why: When you use the Windows Runtime in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="617eb-106">La <xref:System.Uri?displayProperty=nameWithType> classe autorise les URI relatifs, contrairement à la <xref:Windows.Foundation.Uri?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="617eb-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="617eb-107">Cela est également vrai pour les méthodes que vous exposez dans les composants Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="617eb-107">This is also true for methods you expose in Windows Runtime Components.</span></span> <span data-ttu-id="617eb-108">Si votre composant expose une méthode qui prend un URI, la signature dans votre code inclut <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="617eb-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="617eb-109">Toutefois, pour les utilisateurs de votre composant, la signature comprend <xref:Windows.Foundation.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="617eb-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="617eb-110">Un URI transmis à votre composant doit être un URI absolu.</span><span class="sxs-lookup"><span data-stu-id="617eb-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
<span data-ttu-id="617eb-111">Cette rubrique montre comment détecter un URI absolu et comment en créer un pendant le référencement d'une ressource dans le package d'application.</span><span class="sxs-lookup"><span data-stu-id="617eb-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="617eb-112">Détection et utilisation d'un URI absolu</span><span class="sxs-lookup"><span data-stu-id="617eb-112">Detecting and using an absolute URI</span></span>  
<span data-ttu-id="617eb-113">Utilisez la <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> propriété pour vous assurer qu’un URI est absolu avant de le passer à l’Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="617eb-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the Windows Runtime.</span></span> <span data-ttu-id="617eb-114">Utiliser cette propriété est plus efficace qu'intercepter et gérer l'exception <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="617eb-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="617eb-115">Utilisation d'un URI absolu pour une ressource dans le package d'application</span><span class="sxs-lookup"><span data-stu-id="617eb-115">Using an absolute URI for a resource in the app package</span></span>  
<span data-ttu-id="617eb-116">Si vous souhaitez spécifier un URI pour une ressource qui se trouve dans votre package d'application, vous pouvez utiliser le schéma `ms-appx` ou `ms-appx-web` pour créer un URI absolu.</span><span class="sxs-lookup"><span data-stu-id="617eb-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
<span data-ttu-id="617eb-117">L’exemple suivant montre comment définir la <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> propriété pour un <xref:Windows.UI.Xaml.Controls.WebView> contrôle et la <xref:Windows.UI.Xaml.Controls.Image.Source%2A> propriété d’un <xref:Windows.UI.Xaml.Controls.Image> contrôle sur les ressources contenues dans un dossier nommé pages, à l’aide de XAML et de code.</span><span class="sxs-lookup"><span data-stu-id="617eb-117">The following example shows how to set the <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> property for a <xref:Windows.UI.Xaml.Controls.WebView> control and the <xref:Windows.UI.Xaml.Controls.Image.Source%2A> property for an <xref:Windows.UI.Xaml.Controls.Image> control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
<span data-ttu-id="617eb-118">Pour plus d’informations sur ces schémas, consultez [Schémas URI](/windows/uwp/app-resources/uri-schemes) dans le Centre de développement Windows.</span><span class="sxs-lookup"><span data-stu-id="617eb-118">For more information about these schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="617eb-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="617eb-119">See also</span></span>

- [<span data-ttu-id="617eb-120">Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="617eb-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](support-for-windows-store-apps-and-windows-runtime.md)
