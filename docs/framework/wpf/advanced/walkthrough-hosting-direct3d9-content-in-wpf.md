---
title: 'Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: cff14f03a75717c657785cb8fe5a1de2077faf86
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605405"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF
Cette procédure pas à pas montre comment héberger du contenu Direct3D9 dans une application Windows Presentation Foundation (WPF).  
  
 Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :  
  
- Créez un projet WPF pour héberger le contenu Direct3D9.  
  
- Importer le contenu Direct3D9.  
  
- Afficher le contenu Direct3D9 à l’aide de la <xref:System.Windows.Interop.D3DImage> classe.  
  
 Lorsque vous avez terminé, vous saurez comment héberger du contenu Direct3D9 dans une application WPF.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
- Visual Studio.  
  
- DirectX SDK 9 ou version ultérieur.  
  
- Une DLL qui contient le contenu Direct3D9 dans un format compatible avec WPF. Pour plus d’informations, consultez [interopérabilité WPF et Direct3D9](wpf-and-direct3d9-interoperation.md) et [procédure pas à pas : Création de contenu de Direct3D9 à héberger dans WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
## <a name="creating-the-wpf-project"></a>Création du projet WPF  
 La première étape consiste à créer le projet d’application WPF.  
  
#### <a name="to-create-the-wpf-project"></a>Pour créer le projet WPF  
  
- Créer un nouveau projet d’Application WPF dans Visual c# nommé `D3DHost`. Pour plus d’informations, consultez [Procédure pas à pas : Ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
     MainWindow.xaml s’ouvre dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
## <a name="importing-the-direct3d9-content"></a>L’importation du contenu Direct3D9  
 Vous importez le contenu Direct3D9 à partir d’une DLL non managée à l’aide de la `DllImport` attribut.  
  
#### <a name="to-import-direct3d9-content"></a>Pour importer le contenu Direct3D9  
  
1. Ouvrez MainWindow.xaml.cs dans l’éditeur de Code.  
  
2. Remplacez le code généré automatiquement par le code suivant.  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a>Hébergement du contenu Direct3D9  
 Enfin, utilisez la <xref:System.Windows.Interop.D3DImage> classe pour héberger le contenu Direct3D9.  
  
#### <a name="to-host-the-direct3d9-content"></a>Pour héberger le contenu Direct3D9  
  
1. Dans MainWindow.xaml, remplacez le XAML généré automatiquement par le XAML suivant.  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2. Générez le projet.  
  
3. Copiez la DLL qui contient le contenu Direct3D9 dans le dossier bin/Debug.  
  
4. Appuyez sur F5 pour exécuter le projet.  
  
     Le contenu Direct3D9 s’affiche dans l’application WPF.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.D3DImage>
- [Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
