---
title: Utilisation de contrôles WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9883e9d31fc9e3e2ec3ca06b4fc830bcdc338ae
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460695"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Utiliser des contrôles WPF dans les applications Windows Forms

Vous pouvez utiliser des contrôles Windows Presentation Foundation (WPF) dans des applications basées sur Windows Forms. Bien qu’il s’agisse de deux technologies de vue différentes, elles interagissent correctement.

Le Concepteur Windows Forms dans Visual Studio fournit un environnement de conception visuelle pour l’hébergement de contrôles Windows Presentation Foundation. Un contrôle WPF est hébergé par un contrôle Windows Forms spécial nommé <xref:System.Windows.Forms.Integration.ElementHost>. Ce contrôle permet au contrôle WPF de participer à la mise en page du formulaire et de recevoir des messages du clavier et de la souris. Au moment du design, vous pouvez réorganiser le contrôle <xref:System.Windows.Forms.Integration.ElementHost> comme vous le feriez pour n’importe quel contrôle Windows Forms.

Vous pouvez également utiliser des contrôles de Windows Forms dans des applications WPF. Pour plus d’informations, consultez [conception XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

## <a name="see-also"></a>Voir aussi

- [Interopérabilité entre WPF et Windows Forms](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)
