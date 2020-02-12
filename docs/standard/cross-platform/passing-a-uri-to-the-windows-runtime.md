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
ms.openlocfilehash: 71d427c2d602efbd92dc0128b1fada85a987904a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123621"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Transmission d'un URI au Windows Runtime
Les méthodes Windows Runtime n'acceptent que des URI absolus. Si vous transmettez un URI relatif à une méthode Windows Runtime, une exception <xref:System.ArgumentException> est levée. Voici pourquoi : quand vous utilisez la Windows Runtime dans .NET Framework code, la classe <xref:Windows.Foundation.Uri?displayProperty=nameWithType> apparaît comme <xref:System.Uri?displayProperty=nameWithType> dans IntelliSense. La classe <xref:System.Uri?displayProperty=nameWithType> autorise les URI relatifs, contrairement à la classe <xref:Windows.Foundation.Uri?displayProperty=nameWithType>. Cela est également vrai pour les méthodes que vous exposez dans les composants Windows Runtime. Si votre composant expose une méthode qui prend un URI, la signature dans votre code inclut <xref:System.Uri?displayProperty=nameWithType>. Toutefois, pour les utilisateurs de votre composant, la signature comprend <xref:Windows.Foundation.Uri?displayProperty=nameWithType>. Un URI transmis à votre composant doit être un URI absolu.  
  
Cette rubrique montre comment détecter un URI absolu et comment en créer un pendant le référencement d'une ressource dans le package d'application.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Détection et utilisation d'un URI absolu  
Utilisez la propriété <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> pour vous assurer qu’un URI est absolu avant de le passer à l’Windows Runtime. Utiliser cette propriété est plus efficace qu'intercepter et gérer l'exception <xref:System.ArgumentException>.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Utilisation d'un URI absolu pour une ressource dans le package d'application  
Si vous souhaitez spécifier un URI pour une ressource qui se trouve dans votre package d'application, vous pouvez utiliser le schéma `ms-appx` ou `ms-appx-web` pour créer un URI absolu.  
  
L’exemple suivant montre comment définir la propriété <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> pour un contrôle <xref:Windows.UI.Xaml.Controls.WebView> et la propriété <xref:Windows.UI.Xaml.Controls.Image.Source%2A> pour un contrôle <xref:Windows.UI.Xaml.Controls.Image> sur les ressources contenues dans un dossier nommé pages, à l’aide de XAML et de code.  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
Pour plus d’informations sur ces schémas, consultez [schémas d’URI](/windows/uwp/app-resources/uri-schemes) dans le centre de développement Windows.  
  
## <a name="see-also"></a>Voir aussi

- [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
