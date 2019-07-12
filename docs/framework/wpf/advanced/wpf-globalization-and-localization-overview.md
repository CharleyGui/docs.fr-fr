---
title: Vue d’ensemble de la globalisation et de la localisation WPF
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: 6bccff6bf3bb061a430a9105d99f2fee3511c7fd
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859903"
---
# <a name="wpf-globalization-and-localization-overview"></a>Vue d’ensemble de la globalisation et de la localisation WPF

Quand vous limitez la disponibilité de votre produit à une seule langue, vous limitez votre clientèle potentielle à une fraction des 6,5 milliards de personnes qui constituent la population mondiale. Si vous voulez que vos applications atteignent une audience mondiale, la localisation est le meilleur moyen, et le plus rentable, pour que votre produit atteigne plus de clients.

Cette vue d’ensemble présente la globalisation et localisation dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. La globalisation consiste à concevoir et à développer des applications qui s’exécutent dans plusieurs endroits. Par exemple, la globalisation prend en charge des interfaces utilisateur localisées et des données régionales pour les utilisateurs de différentes cultures. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Fournit des fonctionnalités de conception globalisées, notamment la disposition automatique, les assemblys satellites et les attributs localisées et les commentaires.

La localisation est la traduction des ressources d’une application dans les versions localisées pour des cultures spécifiques prises en charge par l’application. Quand vous localisez dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous utilisez les API dans le <xref:System.Windows.Markup.Localizer> espace de noms. Puissance de ces API le [exemple d’outil LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016) outil de ligne de commande. Pour plus d’informations sur la génération et l’utilisation de LocBaml, consultez [localiser une Application](how-to-localize-an-application.md).

## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>Bonnes pratiques pour la globalisation et la localisation dans WPF

Vous pouvez tirer parti de la fonctionnalité de globalisation et localisation intégrée à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en suivant la conception d’interface utilisateur et les conseils présentés dans cette section concernant la localisation.

### <a name="best-practices-for-wpf-ui-design"></a>Bonnes pratiques pour la conception de l’interface utilisateur WPF

Lorsque vous concevez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– en [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], envisagez d’implémenter ces meilleures pratiques :

- Écrire votre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; Évitez de créer des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans le code. Lorsque vous créez votre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous l’exposez à travers des API de localisation intégrées.

- Évitez d’utiliser des positions absolues et des tailles fixes pour présenter le contenu ; Utilisez plutôt le dimensionnement relatif ou automatique.

  - Utilisez <xref:System.Windows.Window.SizeToContent%2A> et conservez les largeurs et hauteurs définis sur `Auto`.

  - Évitez d’utiliser <xref:System.Windows.Controls.Canvas> pour agencer [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s.

  - Utilisez <xref:System.Windows.Controls.Grid> et sa fonctionnalité de partage de taille.

- Prévoyez de l’espace supplémentaire dans les marges, car le texte localisé nécessite souvent plus d’espace. Cet espace supplémentaire permet d’accepter les caractères qui dépasseraient.

- Activer <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> sur <xref:System.Windows.Controls.TextBlock> pour éviter le découpage.

- Définissez l’attribut `xml:lang` . Cet attribut décrit la culture d’un élément spécifique et ses éléments enfants. La valeur de cette propriété modifie le comportement de plusieurs fonctionnalités dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Par exemple, elle change le comportement de la coupure des mots, la vérification orthographique, la substitution des nombres, la mise en forme des scripts complexes et la police de substitution. Consultez [globalisation pour WPF](globalization-for-wpf.md) pour plus d’informations sur la configuration de la [XML : lang dans XAML de gestion des](../../xaml-services/xml-lang-handling-in-xaml.md).

- Créer une police composite personnalisée pour obtenir un meilleur contrôle des polices qui sont utilisées pour différentes langues. Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise la police GlobalUserInterface.composite qui se trouve dans votre répertoire Windows/Fonts.

- Lorsque vous créez des applications de navigation qui peuvent être localisées dans une culture qui aligne le texte dans un format de droite à gauche, définissez explicitement la <xref:System.Windows.FlowDirection> de chaque page pour vous assurer de la page n’hérite pas <xref:System.Windows.FlowDirection> à partir de la <xref:System.Windows.Navigation.NavigationWindow>.

- Lorsque vous créez des applications de navigation autonomes hébergées en dehors d’un navigateur, définissez la <xref:System.Windows.Application.StartupUri%2A> pour votre application initiale sur un <xref:System.Windows.Navigation.NavigationWindow> au lieu de vers une page (par exemple, `<Application StartupUri="NavigationWindow.xaml">`). Cette conception vous permet de modifier le <xref:System.Windows.FlowDirection> de la fenêtre et la barre de navigation. Pour plus d’informations et un exemple, consultez [Globalization Homepage Sample](https://go.microsoft.com/fwlink/?LinkID=159990).

### <a name="best-practices-for-wpf-localization"></a>Bonnes pratiques pour la localisation WPF

Quand vous localisez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– applications reposant sur, envisagez d’implémenter ces meilleures pratiques :

- Utiliser des commentaires de localisation pour fournir le contexte supplémentaire aux localiseurs.

- Utiliser des attributs de localisation pour contrôler la localisation au lieu d’omettre de façon sélective <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés sur les éléments. Consultez [attributs de localisation et les commentaires](localization-attributes-and-comments.md) pour plus d’informations.

- Utilisez `msbuild -t:updateuid` et `-t:checkuid` pour ajouter et vérifier <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés dans votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Utilisez <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés pour effectuer le suivi des modifications entre le développement et de localisation. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés vous aident à localiser les nouvelles modifications des développements. Si vous ajoutez manuellement <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés à un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], la tâche est généralement fastidieuse et moins précis.

  - Ne pas modifier ou changer <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés une fois la localisation commencée.

  - N’utilisez pas de doublon <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés (n’oubliez pas ce Conseil Lorsque vous utilisez la commande copier-coller).

  - Définir le `UltimateResourceFallback` emplacement dans AssemblyInfo.* pour spécifier la langue appropriée (par exemple, `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`).

    Si vous décidez d’inclure votre langue source dans l’assembly principal en omettant le `<UICulture>` baliser dans votre fichier projet, définissez le `UltimateResourceFallback` emplacement que l’assembly principal au lieu du satellite (par exemple, `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`).

## <a name="localize-a-wpf-application"></a>Localiser une application WPF

Quand vous localisez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, vous disposez de plusieurs options. Par exemple, vous pouvez lier les ressources localisables dans votre application pour un [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] de fichiers, stocker le texte localisable dans les tables resx ou demander aux localiseurs d’utiliser [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichiers. Cette section décrit un flux de travail de localisation qui utilise le formulaire BAML de XAML, ce qui offre plusieurs avantages :

- Vous pouvez localiser après avoir généré.

- Vous pouvez mettre à jour vers une version plus récente du formulaire BAML de XAML avec localisations à partir d’une version antérieure du formulaire BAML de XAML afin que vous pouvez localiser en même temps que vous développez.

- Vous pouvez valider des éléments de la source d’origine et la sémantique au moment de la compilation, car le formulaire BAML de XAML est la forme compilée de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

### <a name="localization-build-process"></a>Processus de génération de la localisation

Lorsque vous développez un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, le processus de génération pour la localisation est la suivante :

- Le développeur crée et globalise le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application. Dans le fichier projet, le développeur définit `<UICulture>en-US</UICulture>` afin que lorsque l’application est compilée, un assembly principal indépendant de la langue est généré. Cet assembly a un fichier .resources.dll satellite qui contient toutes les ressources localisables. Si vous le souhaitez, vous pouvez conserver la langue source dans l’assembly principal, car nos API de localisation prennent en charge l’extraction à partir de l’assembly principal.

- Lorsque le fichier est compilé dans la build, le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est converti en formulaire BAML de XAML. Culturellement neutre `MyDialog.exe` et la culture dépendante (en anglais) `MyDialog.resources.dll` sont publiés pour le client anglophone.

### <a name="localization-workflow"></a>Flux du travail de localisation

Le processus de localisation commence après le non localisé `MyDialog.resources.dll` fichier est généré. Le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments et les propriétés dans votre original [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sont extraits à partir du formulaire BAML de XAML en paires clé-valeur à l’aide de l’API sous <xref:System.Windows.Markup.Localizer>. Les localiseurs utilisent les paires clé-valeur pour localiser l’application. Vous pouvez générer un nouveau fichier .resource.dll à partir des nouvelles valeurs une fois la localisation terminée.

Les clés des paires clé-valeur sont `x:Uid` valeurs placées par le développeur dans la version d’origine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ces `x:Uid` valeurs permettent à l’API suivre et de fusionner les modifications qui interviennent entre le développeur et le localisateur lors de la localisation. Par exemple, si le développeur modifie le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] une fois que le localisateur a commencé la localisation, vous pouvez fusionner les modifications des développements avec le travail de localisation terminé afin que le travail réalisé en traduction est perdue.

Le graphique suivant montre un flux de travail de localisation standard basé sur le formulaire BAML de XAML. Ce diagramme suppose que le développeur écrit l’application en anglais. Le développeur crée et globalise l’application WPF. Dans le fichier projet, le développeur définit `<UICulture>en-US</UICulture>` afin que lors de la génération, un assembly principal indépendant est généré avec un satellite. resources.dll contenant toutes les ressources localisables. Si vous le voulez, vous pouvez conserver la langue source dans l’assembly principal, car nos API de localisation WPF prennent en charge l’extraction à partir de l’assembly principal. Après le processus de génération, le code XAML est compilé en BAML. Le fichier MyDialog.exe.resources.dll indépendant de la culture est livré aux clients anglophones.

![Diagramme montrant le flux de travail de localisation.](./media/wpf-globalization-and-localization-overview/localization-workflow.png)

![Diagramme montrant le flux de travail non localisé.](./media/wpf-globalization-and-localization-overview/unlocalized-workflow.png)

## <a name="examples-of-wpf-localization"></a>Exemples de localisation WPF

Cette section contient des exemples d’applications localisées pour vous aider à comprendre comment générer et localiser [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.

#### <a name="run-dialog-box-example"></a>Exemple de boîte de dialogue Run

Les graphiques suivants illustrent la sortie de la **exécuter** exemple de boîte de dialogue.

**Anglais :**

![Capture d’écran affichant une boîte de dialogue Exécuter en anglais.](./media/wpf-globalization-and-localization-overview/run-dialog-box-english.png)

**Allemand :**

![Capture d’écran affichant une boîte de dialogue Exécuter allemand.](./media/wpf-globalization-and-localization-overview/run-dialog-box-german.png)

**Conception d’une boîte de dialogue Run globale**

Cet exemple produit un **exécuter** boîte de dialogue à l’aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Cette boîte de dialogue est équivalente à la **exécuter** boîte de dialogue est disponible à partir de la [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] menu Démarrer.

Voici quelques points clés pour la conception des boîtes de dialogue globales :

**Disposition automatique**

*Dans Window1.xaml :*

`<Window SizeToContent="WidthAndHeight">`

La propriété Window précédente redimensionne automatiquement la fenêtre en fonction de la taille du contenu. Cette propriété empêche la fenêtre de tronquer le contenu dont la taille augmente après la localisation ; elle supprime également l’espace superflu quand le contenu diminue en taille après la localisation.

`<Grid x:Uid="Grid_1">`

<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> les propriétés sont nécessaires afin que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localisation API fonctionne correctement.

Elles sont utilisées par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localisation API pour suivre les modifications entre le développement et la localisation de la [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés vous permettent de fusionner une version plus récente de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] avec une localisation plus ancienne de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Vous ajoutez un <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriété en exécutant `msbuild -t:updateuid RunDialog.csproj` dans un interpréteur de commandes. C’est la méthode recommandée de l’ajout <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés, car les ajouter manuellement est généralement long et moins précis. Vous pouvez vous assurer que <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> propriétés sont correctement définies en exécutant `msbuild -t:checkuid RunDialog.csproj`.

Le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est structuré à l’aide de la <xref:System.Windows.Controls.Grid> contrôle, qui est un contrôle très utile pour tirer parti de la disposition automatique dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Notez que la boîte de dialogue est divisée en trois lignes et cinq colonnes. Pas une des définitions de ligne et de colonne a une taille fixe ; Par conséquent, le [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments sont positionnés dans chaque cellule peuvent s’adapter aux augmentations et diminutions de taille lors de la localisation.

[!code-xaml[GlobalizationRunDialog#GridColumnDef](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]

Les deux premières colonnes où le **Open :** étiquette et <xref:System.Windows.Controls.ComboBox> sont placés utilisent 10 pour cent de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] largeur totale.

[!code-xaml[GlobalizationRunDialog#GridColumnDef2](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]

Notez que de l’exemple utilise la fonctionnalité de dimensionnement partagé de <xref:System.Windows.Controls.Grid>. Les trois dernières colonnes en tirent parti en se plaçant dans le même <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>. Comme vous pouvez vous y attendre d’après le nom de la propriété, ceci permet aux colonnes de partager la même taille. Par conséquent, lorsque le paramètre « Parcourir... » obtient localisé dans la chaîne plus longue « Durchsuchen... », tous les boutons se largeur au lieu d’avoir un petit bouton « OK » et un bouton « Durchsuchen... » disproportionnellement élevée.

**xml:lang**

`xml:lang="en-US"`

Notez que le [XML : lang dans XAML de gestion des](../../xaml-services/xml-lang-handling-in-xaml.md) placé sur l’élément racine de la [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Cette propriété décrit la culture d’un élément donné et de ses enfants. Cette valeur est utilisée par plusieurs fonctions dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et doit être modifiée de façon appropriée lors de la localisation. Cette valeur change le dictionnaire de langue utilisé pour la coupure et la vérification de l’orthographe des mots. Elle affecte également l’affichage des chiffres et la façon dont le système de police de base sélectionne la police à utiliser. Enfin, la propriété affecte la façon dont les nombres sont affichés et celle dont les textes écrits dans des écritures complexes sont mis en forme. La valeur par défaut est « en-US ».

**Génération d’un assembly de ressources satellite**

*Dans .csproj :*

Modifier le `.csproj` fichier, puis ajoutez la balise suivante pour un inconditionnel `<PropertyGroup>`:

`<UICulture>en-US</UICulture>`

Notez l’ajout d’un `UICulture` valeur. Lorsque cela est la valeur valide <xref:System.Globalization.CultureInfo> valeur telle qu’en-US, génération du projet génère un assembly satellite avec toutes les ressources localisables dans celui-ci.

`<Resource Include="RunIcon.JPG">`

`<Localizable>False</Localizable>`

`</Resource>`

Le `RunIcon.JPG` ne doit pas être localisé car il doit être identique pour toutes les cultures. `Localizable` a la valeur `false` afin qu’il reste dans l’assembly principal de linguistiquement neutre au lieu de l’assembly satellite. La valeur par défaut de toutes les ressources non compilables est `Localizable` défini sur `true`.

**Localisation de la boîte de dialogue Run**

**Analyser**

Après avoir généré l’application, la première étape de la localisation est d’analyser les ressources localisables en dehors de l’assembly satellite. Dans le cadre de cette rubrique, utilisez l’exemple d’outil LocBaml qui se trouve à [exemple d’outil LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016). Notez que LocBaml est seulement un exemple d’outil destiné à vous aider à démarrer dans la création d’un outil de localisation qui s’intègre dans votre processus de localisation. À l’aide de LocBaml, exécutez la commande suivante pour analyser : **LocBaml /Parse RunDialog.resources.dll/out :** pour générer un fichier « RunDialog.resources.dll.CSV ».

**Localiser**

Utilisez votre éditeur CSV préféré prenant en charge Unicode pour éditer ce fichier. Filtrez toutes les entrées avec la catégorie de localisation « None ». Vous devez voir les entrées suivantes :

|Clé de la ressource|Catégorie de localisation|Valeur|
|-|-|-|
|Button_1:System.Windows.Controls.Button.$Content|Bouton|OK|
|Button_2:System.Windows.Controls.Button.$Content|Bouton|Annuler|
|Button_3:System.Windows.Controls.Button.$Content|Bouton|Parcourir...|
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Text|Entrez le nom d’un programme, dossier, document ou ressource Internet, et Windows l’ouvrira pour vous.|
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Text|Ouvrir :|
|Window_1:System.Windows.Window.Title|Titre|Exécuter|

La Localisation de l’application en allemand nécessiterait les traductions suivantes :

|Clé de la ressource|Catégorie de localisation|Valeur|
|-|-|-|
|Button_1:System.Windows.Controls.Button.$Content|Bouton|OK|
|Button_2:System.Windows.Controls.Button.$Content|Bouton|Abbrechen|
|Button_3:System.Windows.Controls.Button.$Content|Bouton|Durchsuchen…|
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Texte|Geben Sie den Namen eines Programms, Ordners, Dokuments oder einer Internetresource an.|
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Text|Öffnen :|
|Window_1:System.Windows.Window.Title|Titre|Exécuter|

**Générer**

La dernière étape de la localisation implique la création de l’assembly satellite nouvellement localisé. Pour ce faire, utilisez la commande LocBaml suivante :

**LocBaml.exe /generate RunDialog.resources.dll /trans:RunDialog.resources.dll.CSV /out: . /cul:de-DE**

Sur allemand [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], si ce resources.dll est placé dans un dossier fr-fr à côté de l’assembly principal, cette ressource est chargée automatiquement au lieu de celle dans le dossier en-US. Si vous n’avez pas une version allemande de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] pour ce test, définir la culture sur la culture de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] vous utilisez (par exemple, `en-US`) et remplacez les DLL de ressources d’origine.

**Chargement de la ressource satellite**

|MyDialog.exe|en-US\MyDialog.resources.dll|en-US\MyDialog.resources.dll|
|------------------|------------------------------------|------------------------------------|
|Code|BAML d’origine en anglais|BAML localisé|
|Ressources indépendantes de la langue|Autres ressources en anglais|Autres ressources localisées en allemand|

Le .NET framework choisit automatiquement l’assembly de ressources satellite à charger à partir de l’application `Thread.CurrentThread.CurrentUICulture`. L’emplacement par défaut à la culture de votre [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] système d’exploitation. Par conséquent, si vous utilisez allemand [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], le fichier de-DE\MyDialog.resources.dll se charge si vous utilisez l’anglais [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], le en-US\MyDialog.resources.dll se charge. Vous pouvez définir la ressource de base par défaut pour votre application en spécifiant NeutralResourcesLanguage dans AssemblyInfo.* de votre projet. Par exemple, si vous spécifiez :

`[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`

le fichier en-US\MyDialog.resources.dll sera utilisé avec la version allemande de Windows si un fichier de-DE\MyDialog.resources.dll ou un fichier de\MyDialog.resources.dll sont tous deux indisponibles.

### <a name="microsoft-saudi-arabia-homepage"></a>Page d’accueil de Microsoft pour l’Arabie Saoudite

Les graphiques suivants montrent une page d’accueil en anglais et en arabe. Pour l’exemple complet qui produit ces graphiques, consultez [Globalization Homepage Sample](https://go.microsoft.com/fwlink/?LinkID=159990).

**Anglais :**

![Capture d’écran affichant une page d’accueil en anglais.](./media/wpf-globalization-and-localization-overview/english-home-page-sample.jpg)

**Arabe :**

![Capture d’écran affichant une page d’accueil arabe.](./media/wpf-globalization-and-localization-overview/arabic-home-page-sample.jpg)

### <a name="designing-a-global-microsoft-home-page"></a>Conception d’une page d’accueil Microsoft globale

Cette simulation du site web de Microsoft pour l’Arabie saoudite illustre les fonctionnalités de globalisation fournies pour les langues de droite à gauche. Les langages tels que l’hébreu et arabe ont un ordre de lecture de droite à gauche par conséquent, la disposition des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] doit souvent être disposé tout à fait différente de ce qu’il serait dans des langues de gauche à droite par exemple l’anglais. La localisation d’une langue de gauche à droite vers une langue de droite à gauche, ou l’inverse, peut se révéler difficile. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a été conçu pour faciliter ces localisations.

**FlowDirection**

*Homepage.xaml :*

[!code-xaml[GlobalizationHomepage#Homepage](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]

Notez que le <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété sur <xref:System.Windows.Controls.Page>. Modification de cette propriété à <xref:System.Windows.FlowDirection.RightToLeft> changera la <xref:System.Windows.FrameworkElement.FlowDirection%2A> de la <xref:System.Windows.Controls.Page> et ses éléments enfants afin que la disposition de cette [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est retournée pour devenir de droite à gauche comme l’attend un utilisateur arabe. Pouvez remplacer le comportement d’héritage en spécifiant un explicite <xref:System.Windows.FrameworkElement.FlowDirection%2A> sur n’importe quel élément. Le <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété n’est disponible sur n’importe quel <xref:System.Windows.FrameworkElement> ou élément associé au document et a la valeur implicite de <xref:System.Windows.FlowDirection.LeftToRight>.

Observez que même les pinceaux de dégradé d’arrière-plan sont correctement inversés quand la racine <xref:System.Windows.FrameworkElement.FlowDirection%2A> est modifié :

**FlowDirection="LeftToRight"**

![Capture d’écran montrant le flux de dégradé de gauche à droite.](./media/wpf-globalization-and-localization-overview/gradient-flow-left-right.png)

**FlowDirection="RightToLeft"**

![Capture d’écran montrant le flux de dégradé de droite à gauche.](./media/wpf-globalization-and-localization-overview/gradient-flow-right-left.png)

**Éviter d’utiliser des dimensions fixes pour les panneaux et les contrôles**

Jetez un coup de œil à Homepage.xaml, notez qu’en dehors de la largeur fixe et la hauteur spécifiées pour la totalité [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] situé en haut <xref:System.Windows.Controls.DockPanel>, aucune autre dimension fixe. N’utilisez pas de dimensions fixes pour éviter le découpage du texte localisé, qui peut être plus long que le texte source. Les panneaux et les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont automatiquement redimensionnés en fonction de leur contenu. La plupart des contrôles ont également des dimensions minimales et maximales que vous pouvez définir pour un meilleur contrôle (par exemple, MinWidth = « 20 »). Avec <xref:System.Windows.Controls.Grid>, vous pouvez également définir des largeurs et hauteurs relatives à l’aide de «\*» (par exemple, `Width="0.25*"`) ou utiliser sa fonctionnalité de partage de taille de cellule.

**Commentaires de localisation**

Dans de nombreux cas, le contenu peut être ambigu et difficile à traduire. Le développeur ou le concepteur a la possibilité de fournir un contexte supplémentaire et des commentaires aux localiseurs via des commentaires de localisation. Par exemple, l’élément Localization.Comments ci-dessous clarifie l’utilisation du caractère « &#124; ».

[!code-xaml[GlobalizationHomepage#LocalizationComment](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]

Ce commentaire est associé au contenu de TextBlock_1 et dans le cas de l’outil LocBaml (consultez [localiser une Application](how-to-localize-an-application.md)), il peut être consulté dans la colonne 6 de la ligne TextBlock_1 dans le fichier de sortie .csv :

|Clé de la ressource|Catégorie|Lisible|Modifiable|Commentaire|`Value`|
|-|-|-|-|-|-|
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Text|TRUE|TRUE|Ce caractère est utilisé comme règle de décoration.|&#124;|

Les commentaires peuvent être placés sur le contenu ou la propriété de n’importe quel élément en utilisant la syntaxe suivante :

[!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]

**Attributs de localisation**

Souvent, le développeur ou le responsable de la localisation doit contrôler ce que les localiseurs peuvent lire et modifier. Par exemple, vous pouvez décider que le localiseur ne doit pas traduire le nom de votre entreprise ou les mentions légales. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit des attributs qui vous permettent de définir la lisibilité, la modifiabilité et la catégorie du contenu d’un élément ou d’une propriété, que votre outil de localisation peut utiliser pour verrouiller, masquer ou trier des éléments. Pour plus d'informations, consultez <xref:System.Windows.Localization.Attributes%2A>. Pour les besoins de cet exemple, l’outil LocBaml affiche uniquement les valeurs de ces attributs. Les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont tous des valeurs par défaut pour ces attributs, mais vous pouvez les remplacez. Par exemple, l’exemple suivant remplace les attributs de localisation par défaut pour `TextBlock_1` et définit le contenu comme étant lisible mais non modifiable par les localisateurs.

[!code-xaml[LocalizationComAtt#LocalizationAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]

En plus des attributs Modifiabilité et une meilleure lisibilité [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une énumération des catégories d’interface utilisateur courantes (<xref:System.Windows.LocalizationCategory>) qui peut être utilisé pour donner aux localisateurs davantage de contexte. Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] catégories par défaut pour les contrôles de plateforme peuvent être remplacées dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ainsi :

[!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]

La localisation par défaut des attributs qui [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit peut également être remplacée par le biais de code, vous pouvez définir correctement les valeurs par défaut adéquates pour les contrôles personnalisés. Par exemple :

```csharp
[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]
public class CorporateLogo : TextBlock
{
    // ...
}
```

Les attributs d’instance définis [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ont priorité sur les valeurs définies dans le code sur les contrôles personnalisés. Pour plus d’informations sur les attributs et les commentaires, consultez [attributs de localisation et les commentaires](localization-attributes-and-comments.md).

**Police de base et polices composites**

Si vous spécifiez une police qui ne prend pas en charge une plage de points de code donnée, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] passent automatiquement à l’autre à l’aide de Global User Interface.compositefont qui se trouve dans votre répertoire Windows/Fonts. Polices composites fonctionnent comme toute autre police et peuvent être utilisées explicitement en définissant d’un élément `FontFamily` (par exemple, `FontFamily="Global User Interface"`). Vous pouvez spécifier votre propre police de base préférée en créant votre propre police composite, et en spécifiant la police à utiliser pour des plages de points de code et des langues spécifiques.

Pour plus d’informations sur les polices composites, consultez <xref:System.Windows.Media.FontFamily>.

**Localisation de la page d’accueil de Microsoft**

Vous pouvez suivre la même procédure que celle de l’exemple de boîte de dialogue Run pour localiser cette application. Le fichier .csv localisé pour l’arabe est disponible pour vous dans le [Globalization Homepage Sample](https://go.microsoft.com/fwlink/?LinkID=159990).
