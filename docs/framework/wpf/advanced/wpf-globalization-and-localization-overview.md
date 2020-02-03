---
title: Présentation de la globalisation et de la localisation
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: 9be6245d7429466490d9dac93c5b94d70bde30bd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744479"
---
# <a name="wpf-globalization-and-localization-overview"></a>Vue d’ensemble de la globalisation et de la localisation WPF

Quand vous limitez la disponibilité de votre produit à une seule langue, vous limitez votre clientèle potentielle à une fraction des 6,5 milliards de personnes qui constituent la population mondiale. Si vous voulez que vos applications atteignent une audience mondiale, la localisation est le meilleur moyen, et le plus rentable, pour que votre produit atteigne plus de clients.

Cette vue d’ensemble présente la globalisation et la localisation dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. La globalisation consiste à concevoir et à développer des applications qui s’exécutent dans plusieurs endroits. Par exemple, la globalisation prend en charge des interfaces utilisateur localisées et des données régionales pour les utilisateurs de différentes cultures. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit des fonctionnalités de conception globalisées, notamment la disposition automatique, les assemblys satellites, les attributs localisés et les commentaires.

La localisation est la traduction des ressources d’une application dans les versions localisées pour des cultures spécifiques prises en charge par l’application. Lorsque vous localisez dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous utilisez les API de l’espace de noms <xref:System.Windows.Markup.Localizer>. Ces API alimentent l’exemple d’outil de ligne de commande de l' [outil LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016) . Pour plus d’informations sur la génération et l’utilisation de LocBaml, consultez [localiser une application](how-to-localize-an-application.md).

## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>Bonnes pratiques pour la globalisation et la localisation dans WPF

Vous pouvez tirer le meilleur parti des fonctionnalités de globalisation et de localisation intégrées à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en suivant les conseils relatifs à la conception et à la localisation de l’interface utilisateur fournis par cette section.

### <a name="best-practices-for-wpf-ui-design"></a>Bonnes pratiques pour la conception de l’interface utilisateur WPF

Lorsque vous concevez une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]basée sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], envisagez d’implémenter ces meilleures pratiques :

- Écrivez votre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; Évitez de créer des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans le code. Lorsque vous créez votre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous l’exposez via des API de localisation intégrées.

- Évitez d’utiliser des positions absolues et des tailles fixes pour disposer le contenu ; Utilisez plutôt le dimensionnement relatif ou automatique.

  - Utilisez <xref:System.Windows.Window.SizeToContent%2A> et conservez les largeurs et hauteurs définis sur `Auto`.

  - Évitez d’utiliser des <xref:System.Windows.Controls.Canvas> pour disposer [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s.

  - Utilisez <xref:System.Windows.Controls.Grid> et sa fonctionnalité de partage de taille.

- Prévoyez de l’espace supplémentaire dans les marges, car le texte localisé nécessite souvent plus d’espace. Cet espace supplémentaire permet d’accepter les caractères qui dépasseraient.

- Activez <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> sur <xref:System.Windows.Controls.TextBlock> pour éviter le découpage.

- Définissez l’attribut `xml:lang` . Cet attribut décrit la culture d’un élément spécifique et de ses éléments enfants. La valeur de cette propriété modifie le comportement de plusieurs fonctionnalités dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Par exemple, elle change le comportement de la coupure des mots, la vérification orthographique, la substitution des nombres, la mise en forme des scripts complexes et la police de substitution. Pour plus d’informations sur la définition de la [gestion XML : lang en XAML,](../../../desktop-wpf/xaml-services/xml-language-handling.md)consultez [globalisation pour WPF](globalization-for-wpf.md) .

- Créez une police composite personnalisée pour obtenir un meilleur contrôle des polices utilisées dans différentes langues. Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise la police GlobalUserInterface. composite dans votre répertoire Windows/Fonts.

- Lorsque vous créez des applications de navigation qui peuvent être localisées dans une culture qui présente du texte dans un format de droite à gauche, définissez explicitement la <xref:System.Windows.FlowDirection> de chaque page pour vous assurer que la page n’hérite pas <xref:System.Windows.FlowDirection> de la <xref:System.Windows.Navigation.NavigationWindow>.

- Lorsque vous créez des applications de navigation autonomes hébergées en dehors d’un navigateur, définissez le <xref:System.Windows.Application.StartupUri%2A> de votre application initiale sur un <xref:System.Windows.Navigation.NavigationWindow> plutôt que sur une page (par exemple, `<Application StartupUri="NavigationWindow.xaml">`). Cette conception vous permet de modifier la <xref:System.Windows.FlowDirection> de la fenêtre et de la barre de navigation. Pour plus d’informations et un exemple, consultez [exemple de page d’accueil de globalisation](https://go.microsoft.com/fwlink/?LinkID=159990).

### <a name="best-practices-for-wpf-localization"></a>Bonnes pratiques pour la localisation WPF

Lorsque vous localisez des applications basées sur des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], envisagez d’implémenter ces meilleures pratiques :

- Utilisez les commentaires de localisation pour fournir un contexte supplémentaire aux localisateurs.

- Utilisez les attributs de localisation pour contrôler la localisation au lieu d’omettre de manière sélective les propriétés de <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> sur les éléments. Pour plus d’informations [, consultez attributs et commentaires de localisation](localization-attributes-and-comments.md) .

- Utilisez `msbuild -t:updateuid` et `-t:checkuid` pour ajouter et vérifier <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés de votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Utilisez <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés pour suivre les modifications entre le développement et la localisation. les propriétés de <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vous aident à localiser de nouvelles modifications de développement. Si vous ajoutez manuellement des propriétés de <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> à un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], la tâche est généralement fastidieuse et moins précise.

  - Ne modifiez pas ou ne modifiez pas <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés une fois que vous avez commencé la localisation.

  - N’utilisez pas de propriétés de <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> dupliquées (souvenez-vous de ce Conseil quand vous utilisez la commande copier-coller).

  - Définissez l’emplacement du `UltimateResourceFallback` dans AssemblyInfo. * pour spécifier la langue appropriée pour le secours (par exemple, `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`).

    Si vous décidez d’inclure votre langue source dans l’assembly principal en omettant la balise `<UICulture>` dans votre fichier projet, définissez l’emplacement du `UltimateResourceFallback` en tant qu’assembly principal au lieu du satellite (par exemple, `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`).

## <a name="localize-a-wpf-application"></a>Localiser une application WPF

Lorsque vous localisez une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous avez plusieurs options. Par exemple, vous pouvez lier les ressources localisables dans votre application à un fichier XML, stocker du texte localisable dans les tables resx ou demander à votre Localisateur d’utiliser [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichiers. Cette section décrit un flux de travail de localisation qui utilise le formulaire BAML de XAML, qui offre plusieurs avantages :

- Vous pouvez localiser une fois que vous avez créé.

- Vous pouvez mettre à jour vers une version plus récente de la forme BAML de XAML avec les localisations d’une version antérieure du formulaire BAML de XAML afin que vous puissiez localiser en même temps que vous développez.

- Vous pouvez valider les éléments et la sémantique de la source d’origine au moment de la compilation, car la forme BAML de XAML est la forme compilée de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

### <a name="localization-build-process"></a>Processus de génération de la localisation

Lorsque vous développez une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], le processus de génération de la localisation est le suivant :

- Le développeur crée et globalise l’application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Dans le fichier projet, le développeur définit `<UICulture>en-US</UICulture>` afin que, lorsque l’application est compilée, un assembly principal indépendant du langage soit généré. Cet assembly a un fichier .resources.dll satellite qui contient toutes les ressources localisables. Si vous le souhaitez, vous pouvez conserver la langue source dans l’assembly principal, car nos API de localisation prennent en charge l’extraction à partir de l’assembly principal.

- Quand le fichier est compilé dans la build, le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est converti au format BAML de XAML. Le `MyDialog.exe` culturellement neutre et les fichiers `MyDialog.resources.dll` dépendants de la culture (anglais) sont diffusés au client anglophone.

### <a name="localization-workflow"></a>Flux du travail de localisation

Le processus de localisation commence après la génération du fichier de `MyDialog.resources.dll` non localisé. Les éléments et propriétés de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] d’origine sont extraits de la forme BAML de XAML dans des paires clé-valeur à l’aide des API sous <xref:System.Windows.Markup.Localizer>. Les localiseurs utilisent les paires clé-valeur pour localiser l’application. Vous pouvez générer un nouveau fichier .resource.dll à partir des nouvelles valeurs une fois la localisation terminée.

Les clés des paires clé-valeur sont `x:Uid` valeurs placées par le développeur dans le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]d’origine. Ces valeurs `x:Uid` permettent à l’API de suivre et de fusionner les modifications qui se produisent entre le développeur et le localisateur pendant la localisation. Par exemple, si le développeur modifie la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] une fois que le localisateur a commencé à localiser, vous pouvez fusionner la modification de développement avec le travail de localisation déjà terminé afin de perdre le travail de traduction minimal.

Le graphique suivant montre un flux de travail de localisation standard basé sur le formulaire BAML de XAML. Ce diagramme part du principe que le développeur écrit l’application en anglais. Le développeur crée et globalise l’application WPF. Dans le fichier projet, le développeur définit `<UICulture>en-US</UICulture>` afin que, lors de la génération, un assembly principal indépendant de la langue soit généré avec un fichier. resources. dll satellite contenant toutes les ressources localisables. Si vous le voulez, vous pouvez conserver la langue source dans l’assembly principal, car nos API de localisation WPF prennent en charge l’extraction à partir de l’assembly principal. Après le processus de génération, le code XAML est compilé en BAML. Le fichier MyDialog.exe.resources.dll indépendant de la culture est livré aux clients anglophones.

![Diagramme montrant le flux de travail de localisation.](./media/wpf-globalization-and-localization-overview/localization-workflow.png)

![Diagramme montrant le flux de travail non localisé.](./media/wpf-globalization-and-localization-overview/unlocalized-workflow.png)

## <a name="examples-of-wpf-localization"></a>Exemples de localisation WPF

Cette section contient des exemples d’applications localisées pour vous aider à comprendre comment créer et localiser des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

#### <a name="run-dialog-box-example"></a>Exemple de boîte de dialogue Run

Les graphiques suivants montrent la sortie de l’exemple de la boîte de dialogue **exécuter** .

**Anglais :**

![Capture d’écran montrant une boîte de dialogue d’exécution en anglais.](./media/wpf-globalization-and-localization-overview/run-dialog-box-english.png)

**Allemand :**

![Capture d’écran montrant une boîte de dialogue d’exécution allemande.](./media/wpf-globalization-and-localization-overview/run-dialog-box-german.png)

**Conception d’une boîte de dialogue Run globale**

Cet exemple génère une boîte de dialogue **exécuter** à l’aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Cette boîte de dialogue est équivalente à la boîte de dialogue **exécuter** disponible dans le menu Démarrer de Microsoft Windows.

Voici quelques points clés pour la conception des boîtes de dialogue globales :

**Disposition automatique**

*Dans Window1.xaml :*

`<Window SizeToContent="WidthAndHeight">`

La propriété Window précédente redimensionne automatiquement la fenêtre en fonction de la taille du contenu. Cette propriété empêche la fenêtre de tronquer le contenu dont la taille augmente après la localisation ; elle supprime également l’espace superflu quand le contenu diminue en taille après la localisation.

`<Grid x:Uid="Grid_1">`

<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés sont nécessaires pour que les API de localisation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fonctionnent correctement.

Ils sont utilisés par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API de localisation pour suivre les modifications entre le développement et la localisation du [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. les propriétés de <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> vous permettent de fusionner une version plus récente du [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] avec une localisation plus ancienne de l' [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Vous ajoutez une propriété <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> en exécutant `msbuild -t:updateuid RunDialog.csproj` dans un interpréteur de commandes. Il s’agit de la méthode recommandée pour ajouter des propriétés de <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>, car leur ajout manuel est généralement long et moins précis. Vous pouvez vérifier que les propriétés de <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> sont correctement définies en exécutant `msbuild -t:checkuid RunDialog.csproj`.

La [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est structurée à l’aide du contrôle <xref:System.Windows.Controls.Grid>, qui est un contrôle utile pour tirer parti de la disposition automatique dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Notez que la boîte de dialogue est divisée en trois lignes et cinq colonnes. L’une des définitions de ligne et de colonne n’a pas une taille fixe ; par conséquent, les éléments [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] positionnés dans chaque cellule peuvent s’adapter pour augmenter ou diminuer la taille lors de la localisation.

[!code-xaml[GlobalizationRunDialog#GridColumnDef](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]

Les deux premières colonnes où l’étiquette **Open :** et <xref:System.Windows.Controls.ComboBox> sont placées utilisent 10 pour cent de la largeur totale [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].

[!code-xaml[GlobalizationRunDialog#GridColumnDef2](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]

Notez que l’exemple utilise la fonctionnalité de dimensionnement partagé de <xref:System.Windows.Controls.Grid>. Les trois dernières colonnes tirent parti de cela en les plaçant dans le même <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>. Comme vous pouvez vous y attendre d’après le nom de la propriété, ceci permet aux colonnes de partager la même taille. Par conséquent, lorsque le bouton « Parcourir... » est localisée dans la chaîne plus longue « Durchsuchen... », tous les boutons augmentent en largeur au lieu d’avoir un petit bouton « OK » et un « Durchsuchen... » de grande taille disproportionnée... bouton.

**XML : lang**

`xml:lang="en-US"`

Notez la [gestion de XML : lang en XAML](../../../desktop-wpf/xaml-services/xml-language-handling.md) placée à l’élément racine du [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Cette propriété décrit la culture d’un élément donné et de ses enfants. Cette valeur est utilisée par plusieurs fonctionnalités de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et doit être modifiée de manière appropriée lors de la localisation. Cette valeur change le dictionnaire de langue utilisé pour la coupure et la vérification de l’orthographe des mots. Elle affecte également l’affichage des chiffres et la façon dont le système de police de base sélectionne la police à utiliser. Enfin, la propriété affecte la façon dont les nombres sont affichés et celle dont les textes écrits dans des écritures complexes sont mis en forme. La valeur par défaut est « en-US ».

**Génération d’un assembly de ressources satellite**

*Dans .csproj :*

Modifiez le fichier `.csproj` et ajoutez la balise suivante à un `<PropertyGroup>`non conditionnel :

`<UICulture>en-US</UICulture>`

Notez l’ajout d’une valeur `UICulture`. Lorsque cette valeur est définie sur une valeur de <xref:System.Globalization.CultureInfo> valide telle que en-US, la génération du projet génère un assembly satellite avec toutes les ressources localisables qu’il contient.

`<Resource Include="RunIcon.JPG">`

`<Localizable>False</Localizable>`

`</Resource>`

La `RunIcon.JPG` n’a pas besoin d’être localisée, car elle doit être identique pour toutes les cultures. `Localizable` est défini sur `false` afin qu’il reste dans l’assembly principal indépendant de la langue et non dans l’assembly satellite. La valeur par défaut de toutes les ressources noncompilable est `Localizable` définie sur `true`.

**Localisation de la boîte de dialogue Run**

**Analyser**

Après avoir généré l’application, la première étape de la localisation est d’analyser les ressources localisables en dehors de l’assembly satellite. Pour les besoins de cette rubrique, utilisez l’exemple d’outil LocBaml qui se trouve dans l' [exemple d’outil LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016). Notez que LocBaml est seulement un exemple d’outil destiné à vous aider à démarrer dans la création d’un outil de localisation qui s’intègre dans votre processus de localisation. À l’aide de LocBaml, exécutez la commande suivante pour analyser : **LocBaml/parse RunDialog. resources. dll/out :** pour générer un fichier « RunDialog. resources. dll. csv ».

**Localiser**

Utilisez votre éditeur CSV préféré prenant en charge Unicode pour éditer ce fichier. Filtrez toutes les entrées avec la catégorie de localisation « None ». Vous devez voir les entrées suivantes :

|Clé de la ressource|Catégorie de localisation|Valeur|
|-|-|-|
|Button_1:System.Windows.Controls.Button.$Content|Button|OK|
|Button_2:System.Windows.Controls.Button.$Content|Button|Annuler|
|Button_3:System.Windows.Controls.Button.$Content|Button|Parcourir...|
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Texte|Entrez le nom d’un programme, dossier, document ou ressource Internet, et Windows l’ouvrira pour vous.|
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Texte|Ouvrir :|
|Window_1:System.Windows.Window.Title|Titre|Exécuter|

La Localisation de l’application en allemand nécessiterait les traductions suivantes :

|Clé de la ressource|Catégorie de localisation|Valeur|
|-|-|-|
|Button_1:System.Windows.Controls.Button.$Content|Button|OK|
|Button_2:System.Windows.Controls.Button.$Content|Button|Abbrechen|
|Button_3:System.Windows.Controls.Button.$Content|Button|Durchsuchen…|
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Texte|Geben Sie den Namen eines Programms, Ordners, Dokuments oder einer Internetresource an.|
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Texte|Ouvrir :|
|Window_1:System.Windows.Window.Title|Titre|Exécuter|

**Générer**

La dernière étape de la localisation implique la création de l’assembly satellite nouvellement localisé. Pour ce faire, utilisez la commande LocBaml suivante :

**LocBaml.exe /generate RunDialog.resources.dll /trans:RunDialog.resources.dll.CSV /out: . /cul:de-DE**

Sur les fenêtres allemandes, si ce fichier Resources. dll est placé dans un dossier de-DE à côté de l’assembly principal, cette ressource est chargée automatiquement au lieu de celle figurant dans le dossier en-US. Si vous ne disposez pas d’une version allemande de Windows pour tester cela, définissez la culture sur la culture de Windows que vous utilisez (par exemple, `en-US`) et remplacez la DLL de ressources d’origine.

**Chargement de la ressource satellite**

|MyDialog.exe|en-US\MyDialog.resources.dll|en-US\MyDialog.resources.dll|
|------------------|------------------------------------|------------------------------------|
|Code|BAML d’origine en anglais|BAML localisé|
|Ressources indépendantes de la langue|Autres ressources en anglais|Autres ressources localisées en allemand|

Le .NET Framework choisit automatiquement l’assembly de ressources satellites à charger en fonction de l' `Thread.CurrentThread.CurrentUICulture`de l’application. Par défaut, il s’agit de la culture de votre système d’exploitation Windows. Par conséquent, si vous utilisez des fenêtres en allemand, le fichier de-DE\MyDialog.resources.dll se charge, si vous utilisez des fenêtres en anglais, le en-US\MyDialog.resources.dll est chargé. Vous pouvez définir la ressource de base par défaut pour votre application en spécifiant NeutralResourcesLanguage dans AssemblyInfo.* de votre projet. Par exemple, si vous spécifiez :

`[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`

le fichier en-US\MyDialog.resources.dll sera utilisé avec la version allemande de Windows si un fichier de-DE\MyDialog.resources.dll ou un fichier de\MyDialog.resources.dll sont tous deux indisponibles.

### <a name="microsoft-saudi-arabia-homepage"></a>Page d’accueil de Microsoft pour l’Arabie Saoudite

Les graphiques suivants montrent une page d’accueil en anglais et en arabe. Pour obtenir l’exemple complet qui produit ces graphiques, consultez [exemple de page d’accueil de globalisation](https://go.microsoft.com/fwlink/?LinkID=159990).

**Anglais :**

![Capture d’écran montrant une page d’hébergement en anglais.](./media/wpf-globalization-and-localization-overview/english-home-page-sample.jpg)

**Arabe :**

![Capture d’écran montrant une page d’hébergement en arabe.](./media/wpf-globalization-and-localization-overview/arabic-home-page-sample.jpg)

### <a name="designing-a-global-microsoft-home-page"></a>Conception d’une page d’hébergement Microsoft globale

Cette simulation du site web de Microsoft pour l’Arabie saoudite illustre les fonctionnalités de globalisation fournies pour les langues de droite à gauche. Les langues telles que l’hébreu et l’arabe ont un ordre de lecture de droite à gauche, de sorte que la disposition des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] doit souvent être très différente de celle des langues de gauche à droite, par exemple l’anglais. La localisation d’une langue de gauche à droite vers une langue de droite à gauche, ou l’inverse, peut se révéler difficile. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a été conçu pour faciliter ces localisations.

**FlowDirection**

*Homepage.xaml :*

[!code-xaml[GlobalizationHomepage#Homepage](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]

Notez la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> sur <xref:System.Windows.Controls.Page>. La modification de cette propriété en <xref:System.Windows.FlowDirection.RightToLeft> modifiera la <xref:System.Windows.FrameworkElement.FlowDirection%2A> du <xref:System.Windows.Controls.Page> et de ses éléments enfants afin que la disposition de ce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] soit retournée de droite à gauche, comme l’attendait un utilisateur arabe. Il est possible de substituer le comportement d’héritage en spécifiant une <xref:System.Windows.FrameworkElement.FlowDirection%2A> explicite sur un élément. La propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> est disponible sur n’importe quel <xref:System.Windows.FrameworkElement> ou élément lié à un document et a une valeur implicite de <xref:System.Windows.FlowDirection.LeftToRight>.

Notez que même les pinceaux de dégradé d’arrière-plan sont correctement retournées lorsque le <xref:System.Windows.FrameworkElement.FlowDirection%2A> racine est modifié :

**FlowDirection="LeftToRight"**

![Capture d’écran montrant le déroulement du dégradé de gauche à droite.](./media/wpf-globalization-and-localization-overview/gradient-flow-left-right.png)

**FlowDirection="RightToLeft"**

![Capture d’écran montrant le dégradé de droite à gauche.](./media/wpf-globalization-and-localization-overview/gradient-flow-right-left.png)

**Éviter d’utiliser des dimensions fixes pour les panneaux et les contrôles**

Jetez un coup d’œil à homepage. xaml, Notez qu’en dehors de la largeur et de la hauteur fixes spécifiées pour l’ensemble du [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] en haut <xref:System.Windows.Controls.DockPanel>, il n’existe aucune autre dimension fixe. N’utilisez pas de dimensions fixes pour éviter le découpage du texte localisé, qui peut être plus long que le texte source. Les panneaux et les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont automatiquement redimensionnés en fonction de leur contenu. La plupart des contrôles ont également des dimensions minimales et maximales que vous pouvez définir pour davantage de contrôle (par exemple, MinWidth = "20"). Avec <xref:System.Windows.Controls.Grid>, vous pouvez également définir des largeurs et des hauteurs relatives à l’aide de «\*» (par exemple, `Width="0.25*"`) ou utiliser la fonctionnalité de partage de taille de cellule.

**Commentaires de localisation**

Dans de nombreux cas, le contenu peut être ambigu et difficile à traduire. Le développeur ou le concepteur a la possibilité de fournir un contexte supplémentaire et des commentaires aux localiseurs via des commentaires de localisation. Par exemple, l’élément Localization.Comments ci-dessous clarifie l’utilisation du caractère « &#124; ».

[!code-xaml[GlobalizationHomepage#LocalizationComment](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]

Ce commentaire est associé au contenu de TextBlock_1 et, dans le cas de l’outil LocBaml, (voir [localiser une application](how-to-localize-an-application.md)), il peut être consulté dans la 6ème colonne de la ligne TextBlock_1 dans le fichier output. csv :

|Clé de la ressource|Catégorie|Lisible|Modifiable|Commentaire|Valeur|
|-|-|-|-|-|-|
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Texte|TRUE|TRUE|Ce caractère est utilisé comme règle de décoration.|&#124;|

Les commentaires peuvent être placés sur le contenu ou la propriété de n’importe quel élément en utilisant la syntaxe suivante :

[!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]

**Attributs de localisation**

Souvent, le développeur ou le responsable de la localisation doit contrôler ce que les localiseurs peuvent lire et modifier. Par exemple, vous pouvez décider que le localiseur ne doit pas traduire le nom de votre entreprise ou les mentions légales. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit des attributs qui vous permettent de définir la lisibilité, la modifiabilité et la catégorie du contenu d’un élément ou d’une propriété, que votre outil de localisation peut utiliser pour verrouiller, masquer ou trier des éléments. Pour plus d'informations, consultez <xref:System.Windows.Localization.Attributes%2A>. Pour les besoins de cet exemple, l’outil LocBaml affiche uniquement les valeurs de ces attributs. Les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont tous des valeurs par défaut pour ces attributs, mais vous pouvez les remplacez. Par exemple, l’exemple suivant remplace les attributs de localisation par défaut pour `TextBlock_1` et définit le contenu comme étant accessible en lecture mais non modifiable pour les localiseurs.

[!code-xaml[LocalizationComAtt#LocalizationAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]

En plus des attributs de lisibilité et de modifiabilité, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une énumération des catégories d’interface utilisateur courantes (<xref:System.Windows.LocalizationCategory>) qui peuvent être utilisées pour fournir davantage de contexte aux localiseurs. Les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] catégories par défaut pour les contrôles de plateforme peuvent également être remplacées dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] :

[!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]

Les attributs de localisation par défaut que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit peuvent également être remplacés par le biais du code, de sorte que vous pouvez définir correctement les valeurs par défaut appropriées pour les contrôles personnalisés. Par exemple :

```csharp
[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]
public class CorporateLogo : TextBlock
{
    // ...
}
```

Les attributs par instance définis dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ont priorité sur les valeurs définies dans le code des contrôles personnalisés. Pour plus d’informations sur les attributs et les commentaires, consultez [attributs et commentaires de localisation](localization-attributes-and-comments.md).

**Police de base et polices composites**

Si vous spécifiez une police qui ne prend pas en charge une plage de point de contenu donnée, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est automatiquement secours à celle qui est utilisée par l’interface utilisateur globale. compositefont qui se trouve dans votre répertoire Windows/Fonts. Les polices composites fonctionnent exactement comme n’importe quelle autre police et peuvent être utilisées de manière explicite en définissant le `FontFamily` d’un élément (par exemple, `FontFamily="Global User Interface"`). Vous pouvez spécifier votre propre police de base préférée en créant votre propre police composite, et en spécifiant la police à utiliser pour des plages de points de code et des langues spécifiques.

Pour plus d’informations sur les polices composites, consultez <xref:System.Windows.Media.FontFamily>.

**Localisation de la page d’accueil de Microsoft**

Vous pouvez suivre la même procédure que celle de l’exemple de boîte de dialogue Run pour localiser cette application. Le fichier. csv localisé pour l’arabe est disponible dans l’exemple de la [page d’accueil de globalisation](https://go.microsoft.com/fwlink/?LinkID=159990).
