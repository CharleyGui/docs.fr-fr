---
title: "Procédure pas à pas : localisation d'une application hybride"
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 69aa5ae145ffe378b7a4547e5a33826965bf7894
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111112"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a>Procédure pas à pas : localisation d'une application hybride

Ce pas-là vous montre comment [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localiser les éléments d’une application hybride basée sur Windows Forms.

Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création du projet d’hôte Windows Forms.

- Ajout de contenu localisable

- Activation de la localisation

- Assignation d’identificateurs de ressource

- Utilisation de l’outil LocBaml pour produire un assembly satellite

Pour une liste complète du code des tâches illustrées dans cette procédure pas à pas, voir [Localisation d’un échantillon d’application hybride](https://go.microsoft.com/fwlink/?LinkID=160015).

Quand vous aurez terminé, vous disposerez d’une application hybride localisée.

## <a name="prerequisites"></a>Prérequis

Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Visual Studio 2017

## <a name="creating-the-windows-forms-host-project"></a>Création du projet hôte Windows Forms

La première étape consiste à créer le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projet d’application Windows Forms et à ajouter un élément avec du contenu que vous localiserez.

### <a name="to-create-the-host-project"></a>Pour créer le projet hôte

1. Créez un projet **WPF App** nommé `LocalizingWpfInWf`.  (**Fichier** > **Nouveau** > **projet** > Visual**CMD** ou Visual **Basic** > Classic**Desktop** > **WPF Application**).

2. Ajoutez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> un `SimpleControl` élément appelé au projet.

3. Utilisez <xref:System.Windows.Forms.Integration.ElementHost> le contrôle `SimpleControl` pour placer un élément sur le formulaire. Pour plus d’informations, voir [Procédure pas à pas : Hébergez un contrôle composite WPF 3D dans windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).

## <a name="adding-localizable-content"></a>Ajout de contenu localisable

Ensuite, vous ajouterez un contrôle d’étiquette Windows Forms et définissez le contenu de l’élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sur une chaîne localisable.

### <a name="to-add-localizable-content"></a>Pour ajouter du contenu localisable

1. Dans **Solution Explorer**, double clic **SimpleControl.xaml** pour l’ouvrir dans le WPF Designer.

2. Définissez le <xref:System.Windows.Controls.Button> contenu du contrôle à l’aide du code suivant.

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. Dans **Solution Explorer**, double clic **Form1** pour l’ouvrir dans le Concepteur de formulaires Windows.

4. Ouvrez la boîte à **outils** et **l’étiquette** en double clic pour ajouter un contrôle d’étiquette au formulaire. Affectez à sa propriété <xref:System.Windows.Forms.Control.Text%2A> la valeur `"Hello"`.

5. Appuyez sur **F5** pour construire et exécuter l’application.

     L’élément `SimpleControl` et le contrôle de l’étiquette affichent le texte **"Bonjour".**

## <a name="enabling-localization"></a>Activation de la localisation

Le Concepteur Windows Forms comprend des paramètres permettant d’activer la localisation dans un assembly satellite.

### <a name="to-enable-localization"></a>Pour activer la localisation

1. Dans **Solution Explorer**, double clic **Form1.cs** de l’ouvrir dans le Concepteur de formulaires Windows.

2. Dans la fenêtre **Propriétés,** définissez la valeur de `true`la propriété **localisable** du formulaire à .

3. Dans la fenêtre **Propriétés,** définissez la valeur de la propriété **de langue** à **l’espagnol (Espagne)**.

4. Dans le Concepteur Windows Forms, sélectionnez le contrôle d’étiquette.

5. Dans la fenêtre **Propriétés,** <xref:System.Windows.Forms.Control.Text%2A> définissez `"Hola"`la valeur de la propriété à .

     Un nouveau fichier de ressources nommé Form1.es-ES.resx est ajouté au projet.

6. Dans **Solution Explorer**, cliquez à droite **Form1.cs** et cliquez sur Code **de vue** pour l’ouvrir dans l’éditeur de code.

7. Copiez le code `Form1` suivant dans le `InitializeComponent`constructeur, avant l’appel à .

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. Dans **Solution Explorer**, cliquez à droite **LocalizingWpfInWf** et cliquez sur **Unload Project**.

     Le nom du projet est étiqueté **(indisponible).**

9. Cliquez à droite **LocalizingWpfInWf**, et cliquez sur **Edit LocalizingWpfInWf.csproj**.

     Le fichier projet s’ouvre dans l’éditeur de code.

10. Copiez la ligne `PropertyGroup` suivante dans la première dans le fichier du projet.

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. Enregistrez, puis fermez le fichier projet.

12. Dans **Solution Explorer**, cliquez à droite **LocalizingWpfInWf** et cliquez sur **Reload Project**.

## <a name="assigning-resource-identifiers"></a>Assignation d’identificateurs de ressource

Vous pouvez mapper votre contenu localisable à des assemblys de ressources en utilisant des identificateurs de ressource. L’application MsBuild.exe assigne automatiquement les `updateuid` identifiants de ressources lorsque vous spécifiez l’option.

### <a name="to-assign-resource-identifiers"></a>Pour assigner des identificateurs de ressource

1. À partir du menu Démarrer, ouvrez l’invite de commande de développeur pour Visual Studio.

2. Utilisez la commande suivante pour assigner des identificateurs de ressource à votre contenu localisable.

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. Dans **Solution Explorer**, double clic **SimpleControl.xaml** pour l’ouvrir dans l’éditeur de code. Vous verrez que `msbuild` la commande `Uid` a ajouté l’attribut à tous les éléments. Cela facilite la localisation par l’assignation des identificateurs de ressource.

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. Appuyez sur **F6** pour générer la solution.

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a>Utilisation de LocBaml pour produire un assembly satellite

Votre contenu localisé est stocké dans un *assemblage satellite*uniquement en ressources. Utilisez l’outil de commande LocBaml.exe pour produire [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] un assemblage localisé pour votre contenu.

### <a name="to-produce-a-satellite-assembly"></a>Pour produire un assembly satellite

1. Copiez LocBaml.exe dans le dossier obj\Debug de votre projet. Pour plus d’informations, voir [Localize an Application](how-to-localize-an-application.md).

2. Dans la fenêtre d’invite de commandes, utilisez la commande suivante pour extraire les chaînes de ressources dans un fichier temporaire.

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. Ouvrez le fichier temp.csv avec Visual Studio ou un autre éditeur de texte. Remplacer la `"Hello"` chaîne par `"Hola"`sa traduction espagnole, .

4. Enregistrez le fichier temp.csv.

5. Utilisez la commande suivante pour générer le fichier de ressources localisé.

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     Le fichier LocalizingWpfInWf.g.es-ES.resources est créé dans le dossier obj\Debug.

6. Utilisez la commande suivante pour générer l’assembly satellite localisé.

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     Le fichier LocalizingWpfInWf.resources.dll est créé dans le dossier obj\Debug.

7. Copiez le fichier LocalizingWpfInWf.resources.dll dans le dossier du projet bin\Debug\es-ES. Remplacez le fichier existant.

8. Exécutez LocalizingWpfInWf.exe, qui se trouve dans le dossier bin\Debug de votre projet. Ne regénérez pas l’application, car cela aura pour effet de remplacer l’assembly satellite.

     L’application affiche les chaînes localisées au lieu des chaînes en anglais.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Localiser une application](how-to-localize-an-application.md)
- [Procédure pas à pas : localisation de Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
