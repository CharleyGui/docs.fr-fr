---
title: Guide pratique pour localiser une application
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: 7e034e92e1ff2b9bec0eaf8e0f3330f7a832a7e5
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095162"
---
# <a name="how-to-localize-an-application"></a>Guide pratique pour localiser une application
Ce didacticiel explique comment créer une application localisée à l'aide de l'outil LocBaml.  
  
> [!NOTE]
> L'outil LocBaml n'est pas une application prête pour la production. Il est présenté comme un exemple qui fait appel à un certain nombre d'API de localisation et montre comment vous pouvez écrire un outil de localisation.  
  
<a name="Introduction"></a>   
## <a name="overview"></a>Vue d’ensemble  
 Ce document vous propose une approche pas à pas pour localiser une application. Tout d'abord, vous allez préparer votre application de façon à pouvoir extraire le texte qui sera traduit. Une fois le texte traduit, vous le fusionnerez dans une nouvelle copie de l'application d'origine.  
  
<a name="Requirements"></a>   
## <a name="requirements"></a>Spécifications  
 Au cours de cette discussion, vous allez utiliser Microsoft Build Engine (MSBuild), qui est un compilateur qui s’exécute à partir de la ligne de commande.  
  
 De même, vous serez invité à utiliser un fichier de projet. Pour obtenir des instructions sur l’utilisation de MSBuild et des fichiers projet, consultez [génération et déploiement](../app-development/building-and-deploying-wpf-applications.md).  
  
 Tous les exemples fournis dans ce document sont de culture en-US (anglais américain). Vous pouvez ainsi parcourir les différentes étapes des exemples sans avoir à installer une autre langue.  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a>Créer un exemple d'application  
 Dans cette étape, vous allez préparer votre application en vue de sa localisation. L'exemple HelloApp, qui est fourni dans les exemples [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], sera utilisé dans les exemples de code fournis dans ce document. Si vous souhaitez utiliser cet exemple, téléchargez les fichiers [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] à partir de l' [exemple d’outil LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).  
  
1. Développez votre application jusqu'au point où vous voulez démarrer la localisation.  
  
2. Spécifiez le langage de développement dans le fichier projet de sorte que MSBuild génère un assembly principal et un assembly satellite (un fichier avec l’extension. resources. dll) pour contenir les ressources de langage neutre. Le fichier de projet de l'exemple HelloApp s'intitule HelloApp.csproj. Dans ce fichier, vous trouverez le langage de développement identifié comme suit :  
  
     `<UICulture>en-US</UICulture>`  
  
3. Ajoutez des UID à vos fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Les UID permettent de suivre les modifications apportées aux fichiers et d'identifier les éléments qui doivent être traduits. Pour ajouter des UID à vos fichiers, exécutez **updateuid** sur votre fichier projet :  
  
     **MSBuild-t :updateuid HelloApp. csproj**  
  
     Pour vérifier que vous n’avez pas d’UID ou d’UID en double, exécutez **checkuid**:  
  
     **MSBuild-t :checkuid HelloApp. csproj**  
  
     Après l’exécution de **updateuid**, vos fichiers doivent contenir des UID. Par exemple, dans le fichier Pane1.xaml de HelloApp, vous devez trouver les éléments suivants :  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a>Créer l'assembly satellite de ressources de langage neutre  
 Après avoir configuré l'application pour générer un assembly satellite de ressources de langage neutre, vous devez générer l'application. Cela a pour effet de générer l'assembly d'application principal, ainsi que l'assembly satellite de ressources de langage neutre dont a besoin LocBaml pour la localisation. Pour générer l’application :  
  
1. Compilez HelloApp pour créer une bibliothèque de liens dynamiques (DLL) :  
  
     **msbuild helloapp.csproj**  
  
2. L'assembly d'application principal nouvellement créé, HelloApp.exe, se trouve dans le dossier suivant :  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. L'assembly satellite de ressources de langage neutre nouvellement créé, HelloApp.resources.dll, est créé dans le dossier suivant :  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a>Générer l'outil LocBaml  
  
1. Tous les fichiers nécessaires à la génération de LocBaml se trouvent dans les exemples [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Téléchargez les C# fichiers à partir de l' [exemple d’outil LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).  
  
2. Dans la ligne de commande, exécutez le fichier de projet (locbaml.csproj) pour générer l'outil :  
  
     **msbuild locbaml.csproj**  
  
3. Accédez au répertoire Bin\Release pour trouver le fichier exécutable nouvellement créé (locbaml.exe). Exemple : C:\LocBaml\Bin\Release\locbaml.exe.  
  
4. Les options que vous pouvez spécifier pendant l'exécution de LocBaml sont les suivantes :  
  
    - **Parse** ou **-p : analyse les** fichiers BAML, les ressources ou les fichiers dll pour générer un fichier. csv ou. txt.  
  
    - **generate** ou **-g :** génère un fichier binaire localisé à l’aide d’un fichier traduit.  
  
    - **out** ou **-o** {*répertoirefichiers*] **:** nom du fichier de sortie.  
  
    - **culture** ou **-cul** {*culture*] **:** paramètres régionaux des assemblys de sortie.  
  
    - **translation** ou **-TRANS** {*translation. csv*] **:** fichier traduit ou localisé.  
  
    - **asmpath** ou **-asmpath :** {*répertoirefichiers*] **:** si votre code [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] contient des contrôles personnalisés, vous devez fournir le **asmpath** à l’assembly de contrôle personnalisé.  
  
    - **nologo:** N’affiche aucun logo ni information de droits d’auteur.  
  
    - **verbose:** Affiche des informations en mode détaillé.  
  
    > [!NOTE]
    > Si vous avez besoin d’une liste des options lorsque vous exécutez l’outil, tapez **LocBaml. exe** et appuyez sur entrée.  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a>Utiliser LocBaml pour analyser un fichier  
 Maintenant que vous avez créé l'outil LocBaml, vous êtes prêt à l'utiliser pour analyser HelloApp.resources.dll et ainsi extraire le texte qui sera localisé.  
  
1. Copiez LocBaml.exe dans le dossier bin\debug de votre application, là où l'assembly d'application principal a été créé.  
  
2. Pour analyser le fichier d'assembly satellite et stocker la sortie sous forme de fichier .csv, utilisez la commande suivante :  
  
     **LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**  
  
    > [!NOTE]
    > Si le fichier d'entrée, HelloApp.resources.dll, n'est pas dans le même répertoire que LocBaml.exe, déplacez l'un des deux fichiers de telle sorte qu'ils se trouvent dans le même répertoire.  
  
3. Quand vous exécutez LocBaml pour analyser les fichiers, la sortie se compose de sept champs délimités par des virgules (fichiers .csv) ou des tabulations (fichiers .txt). Voici le fichier .csv analysé pour HelloApp.resources.dll :

   | |
   |-|
   |HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;|
   |HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World|
   |HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World|

   Les sept champs sont les suivants :  
  
   1. **BAML Name**. Nom de la ressource BAML par rapport à l'assembly satellite de langage source.  
  
   2. **Resource Key**. Identificateur de la ressource localisée.  
  
   3. **Catégorie**. Type de valeur. Consultez [attributs et commentaires de localisation](localization-attributes-and-comments.md).  
  
   4. **Lisibilité** : Indique si la valeur peut être lue par un localisateur. Consultez [attributs et commentaires de localisation](localization-attributes-and-comments.md).  
  
   5. **Modifiabilité** : Indique si la valeur peut être modifiée par un localisateur. Consultez [attributs et commentaires de localisation](localization-attributes-and-comments.md).  
  
   6. **Comments**. Description supplémentaire de la valeur pour aider à déterminer comment une valeur est localisée. Consultez [attributs et commentaires de localisation](localization-attributes-and-comments.md).  
  
   7. **Valeur**. valeur de texte à traduire dans la culture souhaitée.  
  
   Le tableau suivant montre comment ces champs sont mappés par rapport aux valeurs délimitées du fichier .csv :  
  
   |BAML name|Resource key|Category|Lisibilité|Modifiability|Commentaires|Valeur|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |HelloApp.g.en-US.resources:window1.baml|Stack1:System.Windows.Controls.StackPanel.$Content|Ignorer|FALSE|FALSE||#Text1;#Text2|
   |HelloApp.g.en-US.resources:window1.baml|Text1:System.Windows.Controls.TextBlock.$Content|None|TRUE|TRUE||Hello World|
   |HelloApp.g.en-US.resources:window1.baml|Text2:System.Windows.Controls.TextBlock.$Content|None|TRUE|TRUE||Goodbye World|
  
   Notez que toutes les valeurs du champ de **Commentaires** ne contiennent aucune valeur ; Si un champ n’a pas de valeur, il est vide. Notez également que l’élément de la première ligne n’est ni lisible ni modifiable et qu’il a « ignore » comme valeur de **catégorie** , ce qui indique que la valeur n’est pas localisable.  
  
4. Pour faciliter la découverte des éléments localisables dans les fichiers analysés, en particulier dans les fichiers volumineux, vous pouvez trier ou filtrer les éléments par **catégorie**, **lisibilité**et **modifiabilité**. Par exemple, vous pouvez filtrer les valeurs illisibles et non modifiables.  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a>Traduire le contenu localisable  
 Utilisez n'importe quel outil à votre disposition pour traduire le contenu extrait. Une bonne façon de procéder consiste à écrire les ressources dans un fichier. csv et à les afficher dans Microsoft Excel, en apportant des modifications de traduction à la dernière colonne (valeur).  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a>Utiliser LocBaml pour générer un nouveau fichier .resources.dll  
 Le contenu qui a été identifié en analysant HelloApp.resources.dll avec LocBaml a été traduit et doit être fusionné dans l'application d'origine. Utilisez l’option **generate** ou **-g** pour générer un nouveau fichier. resources. dll.  
  
1. Utilisez la syntaxe suivante pour générer un nouveau fichier HelloApp.resources.dll. Indiquez la culture en-US (/cul:en-US).  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**  
  
    > [!NOTE]
    > Si le fichier d'entrée, Hello.csv, n'est pas dans le même répertoire que l'exécutable, LocBaml.exe, déplacez l'un des deux fichiers de telle sorte qu'ils se trouvent dans le même répertoire.  
  
2. Remplacez l'ancien fichier HelloApp.resources.dll dans le répertoire C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll par le fichier HelloApp.resources.dll que vous venez de créer.  
  
3. « Hello World » et « Goodbye World » doivent maintenant être traduits dans votre application.  
  
4. Pour traduire dans une autre culture, utilisez celle qui correspond à la langue d'arrivée de la traduction. L'exemple suivant montre comment traduire en français du Canada :  
  
     **LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**  
  
5. Dans le même assembly que l'assembly d'application principal, créez un dossier propre à la culture pour héberger le nouvel assembly satellite. Pour le français du Canada, le dossier s'intitulerait fr-CA.  
  
6. Copiez l'assembly satellite généré dans le nouveau dossier.  
  
7. Pour tester le nouvel assembly satellite, vous devez modifier la culture sous laquelle votre application s'exécutera. Vous pouvez le faire de deux façons :  
  
    - Modifiez les paramètres régionaux de votre système d’exploitation (**Démarrez** &#124; **le panneau** &#124; de configuration **Options régionales et linguistiques**).  
  
    - Dans votre application, ajoutez le code suivant à App.xaml.cs :  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a>Quelques conseils pour utiliser LocBaml  
  
- Tous les assemblys dépendants qui définissent des contrôles personnalisés doivent être copiés dans le répertoire local de LocBaml ou installés dans le GAC. Cela est nécessaire, car l’API de localisation doit avoir accès aux assemblys dépendants lorsqu’elle lit le XAML binaire (BAML).  
  
- Si l'assembly principal est signé, la DLL de ressources générée doit l'être également pour pouvoir être chargée.  
  
- La version de la DLL de ressources localisées doit être synchronisée avec l'assembly principal.  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a>Étapes suivantes  
 Vous connaissez à présent les rudiments de l'outil LocBaml.  Vous êtes normalement en mesure de créer un fichier contenant des UID. À l'aide de l'outil LocBaml, vous devez être en mesure d'analyser un fichier pour extraire le contenu localisable, et une fois le contenu traduit, vous devez pouvoir générer un fichier .resources.dll qui fusionne le contenu traduit. Bien que non exhaustive, cette rubrique vous donne les moyens de localiser vos applications à l'aide LocBaml.  
  
## <a name="see-also"></a>Voir aussi

- [Globalisation pour WPF](globalization-for-wpf.md)
- [Vue d’ensemble de l’utilisation de la disposition automatique](use-automatic-layout-overview.md)
