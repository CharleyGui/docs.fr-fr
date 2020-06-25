---
title: 'Comment : naviguer vers une URL avec un contrôle WebBrowser'
description: Découvrez comment utiliser la Windows Forms contrôle WebBrowser. Navigate pour accéder à une URL spécifique. Découvrez également comment déterminer quand le nouveau document est chargé.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: e6ad360cc73a84ca040869832bb59d354cb78bd5
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325571"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="9437e-104">Comment : naviguer vers une URL avec un contrôle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="9437e-104">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="9437e-105">L’exemple de code suivant montre comment naviguer <xref:System.Windows.Forms.WebBrowser> dans le contrôle jusqu’à une URL spécifique.</span><span class="sxs-lookup"><span data-stu-id="9437e-105">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>

 <span data-ttu-id="9437e-106">Pour déterminer à quel moment le nouveau document est entièrement chargé, gérez l' <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> événement.</span><span class="sxs-lookup"><span data-stu-id="9437e-106">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="9437e-107">Pour une démonstration de cet événement, consultez [Comment : imprimer avec un contrôle WebBrowser](how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="9437e-107">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>

## <a name="example"></a><span data-ttu-id="9437e-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="9437e-108">Example</span></span>

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a><span data-ttu-id="9437e-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="9437e-109">Compiling the Code</span></span>
 <span data-ttu-id="9437e-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="9437e-110">This example requires:</span></span>

- <span data-ttu-id="9437e-111">un contrôle <xref:System.Windows.Forms.WebBrowser> nommé `webBrowser1` ;</span><span class="sxs-lookup"><span data-stu-id="9437e-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>

- <span data-ttu-id="9437e-112">des références aux assemblys `System` et `System.Windows.Forms`.</span><span class="sxs-lookup"><span data-stu-id="9437e-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="9437e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9437e-113">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="9437e-114">WebBrowser, contrôle</span><span class="sxs-lookup"><span data-stu-id="9437e-114">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="9437e-115">Guide pratique pour imprimer avec un contrôle WebBrowser</span><span class="sxs-lookup"><span data-stu-id="9437e-115">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
