---
title: 'Procédure : Rendre persistantes et restaurer les propriétés de portée application d’une session d’application à l’autre'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application-scope properties [WPF], persisting
- persisting application-scope properties [WPF]
- properties [WPF], persisting
- restoring application-scope properties [WPF]
- properties [WPF], restoring
- application-scope properties [WPF], restoring
ms.assetid: 55d5904a-f444-4eb5-abd3-6bc74dd14226
ms.openlocfilehash: d9c2dda2745e7528902b6b1c4f46d17264d1a8d8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666728"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a><span data-ttu-id="36157-102">Procédure : Rendre persistantes et restaurer les propriétés de portée application d’une session d’application à l’autre</span><span class="sxs-lookup"><span data-stu-id="36157-102">How to: Persist and Restore Application-Scope Properties Across Application Sessions</span></span>
<span data-ttu-id="36157-103">Cet exemple montre comment rendre persistantes les propriétés de portée application lorsqu’une application s’arrête, et comment restaurer les propriétés de portée application lors du prochain lancement d’une application.</span><span class="sxs-lookup"><span data-stu-id="36157-103">This example shows how to persist application-scope properties when an application shuts down, and how to restore application-scope properties when an application is next launch.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36157-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="36157-104">Example</span></span>  
 <span data-ttu-id="36157-105">L’application conserve les propriétés de portée application et les restaure à partir du stockage isolé.</span><span class="sxs-lookup"><span data-stu-id="36157-105">The application persists application-scope properties to, and restores them from, isolated storage.</span></span> <span data-ttu-id="36157-106">Le stockage isolé est une zone de stockage protégée qui peut être utilisée en toute sécurité par des applications sans autorisation d’accès aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="36157-106">Isolated storage is a protected storage area that can safely be used by applications without file access permission.</span></span>  <span data-ttu-id="36157-107">Le fichier *app. Xaml* définit la `App_Startup` méthode en tant que gestionnaire de <xref:System.Windows.Application.Startup?displayProperty=nameWithType> l’événement, et `App_Exit` la méthode comme gestionnaire de l' <xref:System.Windows.Application.Exit?displayProperty=nameWithType> événement, comme indiqué dans les lignes en surbrillance du premier exemple.</span><span class="sxs-lookup"><span data-stu-id="36157-107">The *App.xaml* file defines the `App_Startup` method as the handler for the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event, and the `App_Exit` method as the handler for the  <xref:System.Windows.Application.Exit?displayProperty=nameWithType> event, as shown in the highlighted lines of the first example.</span></span> <span data-ttu-id="36157-108">Le deuxième exemple montre une partie des fichiers *app.Xaml.cs* et *app. Xaml. vb* qui met en surbrillance le `App_Startup` code de la méthode, qui restaure les propriétés de portée application `App_Exit` et la méthode, qui enregistre la portée de l’application. sous.</span><span class="sxs-lookup"><span data-stu-id="36157-108">The second example shows a portion of the *App.xaml.cs* and *App.xaml.vb* files that highlights the code for the `App_Startup` method, which restores application-scope properties, and the `App_Exit` method, which saves application-scope properties.</span></span>

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=14-45)]
