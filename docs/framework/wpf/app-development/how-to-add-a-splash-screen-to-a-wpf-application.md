---
title: Comment ajouter un écran de démarrage
description: Découvrez comment ajouter une fenêtre de démarrage ou un écran de démarrage à une application Windows Presentation Foundation (WPF).
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 0d0cf2e2a550320650c3b4a0c257071a0403c32b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617958"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Comment : ajouter un écran de démarrage dans une application WPF

Cette rubrique montre comment ajouter une fenêtre de démarrage ou un *écran*de démarrage à une application Windows Presentation Foundation (WPF).

## <a name="to-add-an-existing-image-as-a-splash-screen"></a>Pour ajouter une image existante sous la forme d’un écran de démarrage

1. Créez ou recherchez une image que vous souhaitez utiliser pour l’écran de démarrage. Vous pouvez utiliser n’importe quel format d’image pris en charge par le composant WIC (Windows Imaging Component). Par exemple, vous pouvez utiliser le format BMP, GIF, JPEG, PNG ou TIFF.

2. Ajoutez le fichier image au projet d’application WPF.

3. Dans **Explorateur de solutions**, sélectionnez l’image.

4. Dans la Fenêtre Propriétés, cliquez sur la flèche déroulante de la propriété **action de génération** .

5. Sélectionnez **SplashScreen** dans la liste déroulante.

6. Appuyez sur **F5** pour générer et exécuter l’application.

     L’image de l’écran de démarrage s’affiche au centre de l’écran, puis disparaît lorsque la fenêtre principale de l’application s’affiche.

## <a name="to-exclude-the-splash-screen-from-build"></a>Pour exclure l’écran de démarrage de la Build

1. Dans **Explorateur de solutions**, sélectionnez l’image de l’écran de démarrage.

2. Dans la fenêtre **Propriétés** , affectez à **action de génération** la valeur **aucun**.

## <a name="to-remove-the-splash-screen-from-an-application"></a>Pour supprimer l’écran de démarrage d’une application

Dans **Explorateur de solutions**, supprimez l’image de l’écran de démarrage.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.SplashScreen>
- [Procédure : ajouter des éléments existants à un projet](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))
