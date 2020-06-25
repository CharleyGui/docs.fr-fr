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
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Comment : naviguer vers une URL avec un contrôle WebBrowser
L’exemple de code suivant montre comment naviguer <xref:System.Windows.Forms.WebBrowser> dans le contrôle jusqu’à une URL spécifique.

 Pour déterminer à quel moment le nouveau document est entièrement chargé, gérez l' <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> événement. Pour une démonstration de cet événement, consultez [Comment : imprimer avec un contrôle WebBrowser](how-to-print-with-a-webbrowser-control.md).

## <a name="example"></a>Exemple

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a>Compilation du code
 Cet exemple nécessite :

- un contrôle <xref:System.Windows.Forms.WebBrowser> nommé `webBrowser1` ;

- des références aux assemblys `System` et `System.Windows.Forms`.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [WebBrowser, contrôle](webbrowser-control-windows-forms.md)
- [Guide pratique pour imprimer avec un contrôle WebBrowser](how-to-print-with-a-webbrowser-control.md)
