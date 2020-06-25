---
title: Vue d'ensemble du contrôle WebBrowser
description: Découvrez comment utiliser le contrôle WebBrowser pour combiner en toute transparence des contrôles Web avec des contrôles Windows Forms dans une application unique.
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: 6a0548bb0f5905d8f848ab13fb82d32b50caa891
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325741"
---
# <a name="webbrowser-control-overview"></a>Vue d'ensemble du contrôle WebBrowser
Le <xref:System.Windows.Forms.WebBrowser> contrôle fournit un wrapper managé pour le contrôle ActiveX WebBrowser. Le wrapper managé vous permet d’afficher des pages Web dans vos applications clientes Windows Forms. Vous pouvez utiliser le <xref:System.Windows.Forms.WebBrowser> contrôle pour dupliquer la fonctionnalité de navigation Web d’Internet Explorer dans votre application ou vous pouvez désactiver la fonctionnalité Internet Explorer par défaut et utiliser le contrôle comme simple visionneuse de documents html. Vous pouvez également utiliser le contrôle pour ajouter des éléments d’interface utilisateur DHTML à votre formulaire et masquer le fait qu’ils soient hébergés dans le <xref:System.Windows.Forms.WebBrowser> contrôle. Cette approche vous permet de combiner en toute transparence des contrôles Web avec des contrôles de Windows Forms dans une application unique.  
  
## <a name="frequently-used-properties-methods-and-events"></a>Propriétés, méthodes et événements fréquemment utilisés  
 Le <xref:System.Windows.Forms.WebBrowser> contrôle possède plusieurs propriétés, méthodes et événements que vous pouvez utiliser pour implémenter des contrôles disponibles dans Internet Explorer. Par exemple, vous pouvez utiliser la `Navigate` méthode pour implémenter une barre d’adresses, et les `GoBack` méthodes,, et `GoForward` `Stop` `Refresh` pour implémenter des boutons de navigation sur une barre d’outils. Vous pouvez gérer l' `Navigated` événement pour mettre à jour la barre d’adresses avec la valeur de la `Url` propriété et la barre de titre avec la valeur de la `DocumentTitle` propriété.  
  
 Si vous souhaitez générer votre propre contenu de page dans votre application, vous pouvez définir la `DocumentText` propriété. Si vous êtes familiarisé avec le modèle DOM (Document Object Model) HTML, vous pouvez également manipuler le contenu de la page Web actuelle par le biais de la `Document` propriété. Cette propriété vous permet de stocker et de modifier des documents en mémoire au lieu de naviguer entre les fichiers.  
  
 La `Document` propriété vous permet également d’appeler des méthodes implémentées dans du code de script de page Web à partir de votre code d’application cliente. Pour accéder au code de votre application cliente à partir de votre code de script, définissez la `ObjectForScripting` propriété. L’objet que vous spécifiez est accessible par votre code de script en tant qu' `window.external` objet.  
  
|Nom|Description|  
|----------|-----------------|  
|Propriété <xref:System.Windows.Forms.WebBrowser.Document%2A>|Obtient un objet qui fournit l’accès managé au modèle DOM (Document Object Model) HTML de la page Web actuelle.|  
|Événement<xref:System.Windows.Forms.WebBrowser.DocumentCompleted>|Se produit lors du chargement d’une page Web.|  
|Propriété <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>|Obtient ou définit le contenu HTML de la page Web actuelle.|  
|Propriété <xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A>|Obtient le titre de la page Web actuelle.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.GoBack%2A>|Accède à la page précédente dans l’historique.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.GoForward%2A>|Accède à la page suivante de l’historique.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.Navigate%2A>|Accède à l'URL spécifiée.|  
|Événement<xref:System.Windows.Forms.WebBrowser.Navigating>|Se produit avant le début de la navigation, ce qui permet d’annuler l’action.|  
|Propriété <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A>|Obtient ou définit un objet que le code de script de page Web peut utiliser pour communiquer avec votre application.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.Print%2A>|Imprime la page Web actuelle.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.Refresh%2A>|Recharge la page Web actuelle.|  
|Méthode <xref:System.Windows.Forms.WebBrowser.Stop%2A>|Arrête la navigation en cours et arrête les éléments de page dynamiques tels que les sons et les animations.|  
|Propriété <xref:System.Windows.Forms.WebBrowser.Url%2A>|Obtient ou définit l’URL de la page Web actuelle. La définition de cette propriété permet de naviguer dans le contrôle jusqu’à la nouvelle URL.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>
- <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>
- <xref:System.Windows.Forms.WebBrowserEncryptionLevel>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>
- <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>
- <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>
- <xref:System.Windows.Forms.WebBrowserReadyState>
- <xref:System.Windows.Forms.WebBrowserRefreshOption>
- [Guide pratique pour naviguer vers une URL avec un contrôle WebBrowser](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Guide pratique pour imprimer avec un contrôle WebBrowser](how-to-print-with-a-webbrowser-control.md)
- [Guide pratique pour ajouter des fonctionnalités de navigateur Web à une application Windows Forms](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)
- [Guide pratique pour créer une visionneuse de documents HTML dans une application Windows Forms](how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)
- [Guide pratique pour implémenter la communication bidirectionnelle entre le code DHTML et le code d'application cliente](implement-two-way-com-between-dhtml-and-client.md)
- [Sécurité WebBrowser](webbrowser-security.md)
