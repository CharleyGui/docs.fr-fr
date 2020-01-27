---
title: Héberger le contenu Direct3D9 dans WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: e65b0c59268b44abed289e54181bf0bda9355664
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742609"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF

Cette procédure pas à pas montre comment héberger du contenu Direct3D9 dans une application Windows Presentation Foundation (WPF).

Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :

- Créez un projet WPF pour héberger le contenu Direct3D9.

- Importez le contenu Direct3D9.

- Affichez le contenu Direct3D9 à l’aide de la classe <xref:System.Windows.Interop.D3DImage>.

 Quand vous aurez terminé, vous saurez comment héberger le contenu Direct3D9 dans une application WPF.

## <a name="prerequisites"></a>Prerequisites

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Visual Studio.

- DirectX SDK 9 ou version ultérieure.

- DLL qui contient le contenu Direct3D9 dans un format compatible WPF. Pour plus d’informations, consultez [interopérabilité WPF et Direct3D9](wpf-and-direct3d9-interoperation.md) et [procédure pas à pas : création de contenu Direct3D9 pour l’hébergement dans WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).

## <a name="creating-the-wpf-project"></a>Création du projet WPF

La première étape consiste à créer le projet pour l’application WPF.

### <a name="to-create-the-wpf-project"></a>Pour créer le projet WPF

Créez un projet d’application WPF dans Visual C# `D3DHost`. Pour plus d’informations, consultez [Procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

MainWindow. xaml s’ouvre dans le Concepteur WPF.

## <a name="importing-the-direct3d9-content"></a>Importation du contenu Direct3D9

Vous importez le contenu Direct3D9 à partir d’une DLL non managée à l’aide de l’attribut `DllImport`.

### <a name="to-import-direct3d9-content"></a>Pour importer du contenu Direct3D9

1. Ouvrez MainWindow.xaml.cs dans l’éditeur de code.

2. Remplacez le code généré automatiquement par le code suivant.

    [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]

## <a name="hosting-the-direct3d9-content"></a>Hébergement du contenu Direct3D9

Enfin, utilisez la classe <xref:System.Windows.Interop.D3DImage> pour héberger le contenu Direct3D9.

### <a name="to-host-the-direct3d9-content"></a>Pour héberger le contenu Direct3D9

1. Dans MainWindow. xaml, remplacez le code XAML généré automatiquement par le code XAML suivant.

    [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]

2. créer le projet ;

3. Copiez la DLL qui contient le contenu Direct3D9 dans le dossier bin/debug.

4. Appuyez sur F5 pour exécuter le projet.

    Le contenu Direct3D9 s’affiche dans l’application WPF.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.D3DImage>
- [Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
