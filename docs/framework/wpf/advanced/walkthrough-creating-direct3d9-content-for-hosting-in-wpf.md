---
title: Créer du contenu Direct3D9 pour l’hébergement
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 847ee74da5b295c2c9d3824b3df74f94bc98a4db
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76727917"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>Procédure pas à pas : création de contenu Direct3D9 à héberger dans WPF
Cette procédure pas à pas montre comment créer du contenu Direct3D9 qui convient à l’hébergement dans une application Windows Presentation Foundation (WPF). Pour plus d’informations sur l’hébergement de contenu Direct3D9 dans des applications WPF, consultez [interopérabilité WPF et Direct3D9](wpf-and-direct3d9-interoperation.md).

 Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :

- Créez un projet Direct3D9.

- Configurez le projet Direct3D9 pour l’hébergement dans une application WPF.

 Quand vous aurez terminé, vous disposerez d’une DLL qui contient le contenu Direct3D9 à utiliser dans une application WPF.

## <a name="prerequisites"></a>Composants requis
 Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Visual Studio 2010.

- DirectX SDK 9 ou version ultérieure.

## <a name="creating-the-direct3d9-project"></a>Création du projet Direct3D9
 La première étape consiste à créer et à configurer le projet Direct3D9.

#### <a name="to-create-the-direct3d9-project"></a>Pour créer le projet Direct3D9

1. Créez un projet Win32 dans C++ `D3DContent`nommé.

     L’Assistant application Win32 s’ouvre et affiche l’écran d’accueil.

2. Cliquez sur **Suivant**.

     L’écran Paramètres de l’application s’affiche.

3. Dans la section **type d’application :** , sélectionnez l’option **dll** .

4. Cliquez sur **Terminer**.

     Le projet D3DContent est généré.

5. Dans Explorateur de solutions, cliquez avec le bouton droit sur le projet D3DContent, puis sélectionnez **Propriétés**.

     La boîte de dialogue **pages de propriétés de D3DContent** s’ouvre.

6. Sélectionnez le nœud **CC++ /** .

7. Dans le champ **autres répertoires Include** , spécifiez l’emplacement du dossier include DirectX. L’emplacement par défaut de ce dossier est le chemin%ProgramFiles%\Microsoft DirectX SDK (*version*) \Include.

8. Double-cliquez sur le nœud **éditeur de liens** pour le développer.

9. Dans le champ **répertoires** de bibliothèques supplémentaires, spécifiez l’emplacement du dossier de bibliothèques DirectX. L’emplacement par défaut de ce dossier est le chemin%ProgramFiles%\Microsoft DirectX SDK (*version*) \Lib\x86.

10. Sélectionnez le nœud **d’entrée** .

11. Dans le champ **dépendances supplémentaires** , ajoutez les fichiers `d3d9.lib` et `d3dx9.lib`.

12. Dans Explorateur de solutions, ajoutez un nouveau fichier de définition de module (. def) nommé `D3DContent.def` au projet.

## <a name="creating-the-direct3d9-content"></a>Création du contenu Direct3D9
 Pour obtenir des performances optimales, votre contenu Direct3D9 doit utiliser des paramètres particuliers. Le code suivant montre comment créer une surface Direct3D9 qui a les meilleures caractéristiques de performances. Pour plus d’informations, consultez [Considérations sur les performances pour l’interopérabilité entre Direct3D9 et WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).

#### <a name="to-create-the-direct3d9-content"></a>Pour créer le contenu Direct3D9

1. À l’aide de Explorateur de solutions C++ , ajoutez trois classes au projet, nommées ci-dessous.

     `CRenderer` (avec destructeur virtuel)

     `CRendererManager`

     `CTriangleRenderer`

2. Ouvrez Renderr. h dans l’éditeur de code et remplacez le code généré automatiquement par le code suivant.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3. Ouvrez Renderr. cpp dans l’éditeur de code et remplacez le code généré automatiquement par le code suivant.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4. Ouvrez RendererManager. h dans l’éditeur de code et remplacez le code généré automatiquement par le code suivant.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5. Ouvrez RendererManager. cpp dans l’éditeur de code et remplacez le code généré automatiquement par le code suivant.

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6. Ouvrez TriangleRenderer. h dans l’éditeur de code et remplacez le code généré automatiquement par le code suivant.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7. Ouvrez TriangleRenderer. cpp dans l’éditeur de code et remplacez le code généré automatiquement par le code suivant.

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8. Ouvrez stdafx. h dans l’éditeur de code et remplacez le code généré automatiquement par le code suivant.

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. Ouvrez DllMain. cpp dans l’éditeur de code et remplacez le code généré automatiquement par le code suivant.

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. Ouvrez D3DContent. def dans l’éditeur de code.

11. Remplacez le code généré automatiquement par le code suivant.

    ```cpp
    LIBRARY "D3DContent"

    EXPORTS

    SetSize
    SetAlpha
    SetNumDesiredSamples
    SetAdapter

    GetBackBufferNoRef
    Render
    Destroy
    ```

12. créer le projet ;

## <a name="next-steps"></a>Étapes suivantes

- Hébergez le contenu Direct3D9 dans une application WPF. Pour plus d’informations, consultez [procédure pas à pas : Hébergement de contenu Direct3D9 dans WPF](walkthrough-hosting-direct3d9-content-in-wpf.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.D3DImage>
- [Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
