---
title: Transmission d'un URI au Windows Runtime
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c489ec893ea335c8fafc904cf2a12162580ec266
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025437"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Transmission d'un URI au Windows Runtime
Les méthodes Windows Runtime n'acceptent que des URI absolus. Si vous passez un URI relatif à une méthode Windows Runtime, un <xref:System.ArgumentException> exception est levée. En voici les raisons : Lorsque vous utilisez le Runtime Windows dans le code .NET Framework, le <xref:Windows.Foundation.Uri?displayProperty=nameWithType> classe apparaît sous la forme <xref:System.Uri?displayProperty=nameWithType> dans Intellisense. Le <xref:System.Uri?displayProperty=nameWithType> classe autorise les URI relatifs, mais la <xref:Windows.Foundation.Uri?displayProperty=nameWithType> n’est pas le cas de classe. Cela vaut également pour les méthodes que vous exposez dans les composants Windows Runtime. Si votre composant expose une méthode qui prend un URI, la signature dans votre code inclut <xref:System.Uri?displayProperty=nameWithType>. Toutefois, pour les utilisateurs de votre composant, la signature inclut <xref:Windows.Foundation.Uri?displayProperty=nameWithType>. Un URI transmis à votre composant doit être un URI absolu.  
  
Cette rubrique montre comment détecter un URI absolu et comment en créer un pendant le référencement d'une ressource dans le package d'application.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Détection et utilisation d'un URI absolu  
Utilisez le <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> propriété pour vous assurer qu’un URI est absolu avant de le transmettre à l’exécution de Windows. Utiliser cette propriété est plus efficace qu'intercepter et gérer l'exception <xref:System.ArgumentException>.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Utilisation d'un URI absolu pour une ressource dans le package d'application  
Si vous souhaitez spécifier un URI pour une ressource qui se trouve dans votre package d'application, vous pouvez utiliser le schéma `ms-appx` ou `ms-appx-web` pour créer un URI absolu.  
  
L’exemple suivant montre comment définir le <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> propriété pour un <xref:Windows.UI.Xaml.Controls.WebView> contrôle et le <xref:Windows.UI.Xaml.Controls.Image.Source%2A> propriété pour un <xref:Windows.UI.Xaml.Controls.Image> contrôle aux ressources qui sont contenus dans un dossier nommé Pages, à l’aide de XAML et code.  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
Pour plus d’informations sur ces schémas, consultez [modèles URI](/windows/uwp/app-resources/uri-schemes) dans le centre de développement Windows.  
  
## <a name="see-also"></a>Voir aussi

- [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
