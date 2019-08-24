---
title: 'Procédure : accéder à une URL avec le contrôle WebBrowser'
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
ms.openlocfilehash: b6c1255fa17d91daaa73001fea04f26e73dba0ae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015827"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Procédure : accéder à une URL avec le contrôle WebBrowser
L’exemple de code suivant montre comment naviguer dans <xref:System.Windows.Forms.WebBrowser> le contrôle jusqu’à une URL spécifique.

 Pour déterminer à quel moment le nouveau document est entièrement chargé, <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Gérez l’événement. Pour une démonstration de cet événement, consultez [procédure: Imprimer avec un contrôle](how-to-print-with-a-webbrowser-control.md)WebBrowser.

## <a name="example"></a>Exemple

```vb
Me.webBrowser1.Navigate("http://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("http://www.microsoft.com");
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
- [Guide pratique pour Imprimer avec un contrôle WebBrowser](how-to-print-with-a-webbrowser-control.md)
