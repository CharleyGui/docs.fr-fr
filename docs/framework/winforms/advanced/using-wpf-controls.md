---
title: Utilisation de contrôles WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e05ec7fc503565333a4d05662a4e40d8d1193af
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197460"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Utiliser des contrôles WPF dans les applications Windows Forms

Vous pouvez utiliser des contrôles Windows Presentation Foundation (WPF) dans des applications basées sur Windows Forms. Bien qu’il s’agisse de deux technologies de vue différentes, elles interagissent correctement.

Le Concepteur Windows Forms dans Visual Studio fournit un environnement de conception visuelle pour l’hébergement de contrôles Windows Presentation Foundation. Un contrôle WPF est hébergé par un contrôle Windows Forms spécial nommé <xref:System.Windows.Forms.Integration.ElementHost>. Ce contrôle permet au contrôle WPF de participer à la mise en page du formulaire et de recevoir des messages du clavier et de la souris. Au moment du design, vous pouvez réorganiser le contrôle <xref:System.Windows.Forms.Integration.ElementHost> comme vous le feriez pour n’importe quel contrôle Windows Forms.

Vous pouvez également utiliser des contrôles de Windows Forms dans des applications WPF. Pour plus d’informations, consultez [conception XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

## <a name="see-also"></a>Voir aussi

- [Interopérabilité entre WPF et Windows Forms](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)
