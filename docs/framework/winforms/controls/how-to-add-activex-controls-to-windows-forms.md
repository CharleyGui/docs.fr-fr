---
title: 'Procédure : ajouter des contrôles ActiveX à des Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 8c4c6c3f96c49401b032e360314794cc800c0551
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987063"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Procédure : ajouter des contrôles ActiveX à des Windows Forms

Tandis que le Concepteur Windows Forms dans Visual Studio est optimisé pour héberger des contrôles de Windows Forms, vous pouvez également placer des contrôles ActiveX sur Windows Forms.

> [!CAUTION]
> Il existe des limitations de performances pour Windows Forms lors de l’ajout de contrôles ActiveX.

Avant d’ajouter des contrôles ActiveX à votre formulaire, vous devez les ajouter à la boîte à outils. Pour plus d’informations, consultez [composants com, boîte de dialogue Personnaliser la boîte à outils](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).

## <a name="add-an-activex-control-to-your-windows-form"></a>Ajouter un contrôle ActiveX à votre Windows Form

Pour ajouter un contrôle ActiveX à votre Windows Form, double-cliquez sur le contrôle dans la boîte à outils.

Visual Studio ajoute toutes les références au contrôle dans votre projet. Pour plus d’informations sur les éléments à prendre en compte lors de l’utilisation de contrôles ActiveX sur des Windows Forms, consultez [considérations relatives à l’hébergement d’un contrôle ActiveX dans un Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).

> [!NOTE]
> L’importateur de contrôles ActiveX (AxImp. exe) de Windows Forms crée des arguments d’événement d’un type différent de celui prévu lors de l’importation de bibliothèques de liens dynamiques ActiveX. Les arguments créés par Aximp. exe sont semblables à ce qui suit `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`:, `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` lorsque est attendu. N’oubliez pas que cette irrégularité n’empêche pas le code de fonctionner normalement. Pour plus d’informations, consultez [Windows Forms ActiveX Control importateur (Aximp. exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Comparaison des contrôles et des objets programmables dans divers langages et bibliothèques](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Guide pratique pour Ajouter des contrôles à Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md)
