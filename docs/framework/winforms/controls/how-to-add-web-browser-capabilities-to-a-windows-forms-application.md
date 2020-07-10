---
title: Ajouter des fonctionnalités de navigateur Web à l’application
description: Découvrez comment ajouter des fonctionnalités de navigateur Web à une application Windows Forms avec le contrôle WebBrowser.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
ms.openlocfilehash: a5a33961ac8301bda86bb5f34e65ac159308987f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174547"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="3fbd1-103">Comment ajouter des fonctionnalités de navigateur Web à une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3fbd1-103">How to add web browser capabilities to a Windows Forms application</span></span>

<span data-ttu-id="3fbd1-104">Avec le contrôle <xref:System.Windows.Forms.WebBrowser>, vous pouvez ajouter des fonctionnalités de navigateur web à votre application.</span><span class="sxs-lookup"><span data-stu-id="3fbd1-104">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="3fbd1-105">Le contrôle fonctionne comme un navigateur web par défaut.</span><span class="sxs-lookup"><span data-stu-id="3fbd1-105">The control works like a Web browser by default.</span></span> <span data-ttu-id="3fbd1-106">Après avoir chargé une URL initiale en définissant la propriété <xref:System.Windows.Forms.WebBrowser.Url%2A>, vous pouvez naviguer en cliquant sur des liens hypertexte ou en utilisant des raccourcis clavier pour parcourir l'historique de navigation.</span><span class="sxs-lookup"><span data-stu-id="3fbd1-106">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="3fbd1-107">Par défaut, vous pouvez accéder à d'autres fonctionnalités de navigateur via le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="3fbd1-107">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="3fbd1-108">Vous pouvez aussi ouvrir de nouveaux documents en les déposant sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="3fbd1-108">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="3fbd1-109">Le contrôle <xref:System.Windows.Forms.WebBrowser> possède également plusieurs propriétés, méthodes et événements que vous pouvez utiliser pour implémenter des fonctionnalités d'interface utilisateur semblables à celles d'Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="3fbd1-109">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>

<span data-ttu-id="3fbd1-110">L’exemple de code suivant implémente une barre d’adresses, des boutons de navigateur courants, un menu **Fichier**, une barre d’état et une barre de titre qui affiche le titre de la page actuelle.</span><span class="sxs-lookup"><span data-stu-id="3fbd1-110">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>

## <a name="example"></a><span data-ttu-id="3fbd1-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="3fbd1-111">Example</span></span>

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a><span data-ttu-id="3fbd1-112">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="3fbd1-112">Compile the code</span></span>

<span data-ttu-id="3fbd1-113">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="3fbd1-113">This example requires:</span></span>

- <span data-ttu-id="3fbd1-114">des références aux assemblys `System`, `System.Drawing` et `System.Windows.Forms`.</span><span class="sxs-lookup"><span data-stu-id="3fbd1-114">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fbd1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fbd1-115">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="3fbd1-116">WebBrowser, contrôle</span><span class="sxs-lookup"><span data-stu-id="3fbd1-116">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
