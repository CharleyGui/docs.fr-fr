---
title: Migration vers Windows 10
description: Présentation approfondie des fonctionnalités de Windows 10, telles que l’empaquetage et les îlots XAML.
ms.date: 09/16/2019
ms.openlocfilehash: cd17088b086a32fd3bb37e617d3a1047acedde0e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423207"
---
# <a name="windows-10-migration"></a>Migration vers Windows 10

Considérez la situation suivante : vous disposez d’une application de bureau qui a été développée dans Windows 7 jours. Il utilise la technologie WPF disponible à ce moment-là et fonctionne bien, mais il possède une interface utilisateur et des comportements obsolètes quand vous l’exécutez sur Windows 10. C’est comme lorsque vous regardez un film futur comme une matrice et que vous voyez Neo à l’aide de l’appareil Nokia 8110. Le film fonctionne bien après 20 ans, mais il est préférable de tirer parti d’une modernisation d’appareils.

Avec la sortie de Windows 10, Microsoft a introduit de nombreuses innovations pour prendre en charge des scénarios tels que les tablettes et les appareils tactiles, et pour offrir la meilleure expérience aux utilisateurs pour un système d’exploitation Microsoft. Vous pouvez par exemple :

- Connectez-vous avec votre visage à l’aide de Windows Hello.
- Utilisez un stylet pour dessiner ou écrire du texte qui est automatiquement reconnu et numériquement.
- Exécutez des modèles IA personnalisés localement basés sur le Cloud à l’aide de WinML.

Toutes ces fonctionnalités sont activées pour les développeurs Windows via des bibliothèques Windows Runtime (WinRT). Vous pouvez tirer parti de ces fonctionnalités dans vos applications de bureau existantes, car les bibliothèques sont exposées aussi bien aux .NET Framework qu’à .NET Core. Vous pouvez même moderniser votre interface utilisateur avec l’utilisation d’îlots XAML et améliorer les visuels et le comportement de vos applications en fonction des heures.

Une chose importante à noter ici est que vous n’avez pas besoin d’abandonner .NET Framework technologie pour suivre ce chemin de modernisation. Vous pouvez rester en toute sécurité et bénéficier de tous les avantages de Windows 10 sans avoir à migrer vers .NET Core. Vous bénéficiez ainsi de la puissance et de la flexibilité nécessaire pour choisir votre chemin de modernisation.

## <a name="winrt-apis"></a>API WinRT

Les API WinRT sont des interfaces de programmation d’applications (API) orientées objet et bien structurées qui permettent aux développeurs Windows 10 d’accéder à tout ce que le système d’exploitation doit offrir. Grâce aux API WinRT, vous pouvez intégrer des fonctionnalités telles que des notifications push, des API de périphérique, Microsoft Ink et WinML, entre autres sur vos applications de bureau.

En général, les API WinRT peuvent être appelées à partir d’une application de bureau classique. Toutefois, deux zones principales présentent une exception à cette règle :

* API qui requièrent une identité de package.
* API nécessitant une visualisation comme XAML ou la composition.

### <a name="universal-windows-platform-uwp-packages"></a>Packages plateforme Windows universelle (UWP)

#### <a name="application-package-identity"></a>Identité du package d’application

Les applications UWP disposent d’un système de déploiement dans lequel le système d’exploitation gère l’installation et la désinstallation de l’application. Cela nécessite que l’installation soit déclarative, ce qui signifie qu’aucun code utilisateur n’est exécuté lors de l’installation. Au lieu de cela, tout ce que l’application veut intégrer au système, tel que les protocoles, les types de fichiers et les extensions, est déclaré dans le manifeste de l’application. Au moment du déploiement, le pipeline de déploiement configure ces points d’intégration. La seule façon pour le système d’exploitation de gérer toutes ces fonctionnalités et d’effectuer le suivi de chaque « package » pour avoir une identité, un identificateur unique pour l’application.

Certaines API WinRT requièrent que cette identité de package fonctionne comme prévu. Toutefois, les applications de bureau classiques, comme les applications natives C++ ou .NET, utilisent des systèmes de déploiement différents qui ne nécessitent pas d’identité de package. Si vous souhaitez utiliser ces API WinRT dans votre application de bureau, vous devez leur fournir une identité de package.

Une façon de procéder consiste à créer un projet d’empaquetage supplémentaire. Dans le projet de Packaging, vous pointez sur le projet de code source d’origine et spécifiez les informations d’identité que vous souhaitez fournir.Si vous installez le package et exécutez l’application installée, vous obtiendrez automatiquement une identification permettant à votre code d’appeler toutes les API WinRT nécessitant une identité.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">
    <Identity Name="YOUR-APP-GUID "
              Publisher="CN=YOUR COMPANY"
              Version="1.x.x.x" />
</Package>
```

Vous pouvez vérifier les API qui ont besoin d’une identité d’application empaquetée en inspectant si le type qui contient l’API est marqué avec l’attribut [DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute) .Si c’est le cas, vous pouvez appeler si à partir d’une application de bureau traditionnelle non comprise. Dans le cas contraire, vous devez convertir votre application de bureau classique en UWP à l’aide d’un projet de Packaging.

<https://docs.microsoft.com/windows/desktop/apiindex/uwp-apis-callable-from-a-classic-desktop-app>

#### <a name="benefits-of-packaging"></a>Avantages de l’empaquetage

Outre l’accès à ces API, vous bénéficiez d’avantages supplémentaires en créant un package d’application Windows pour votre application de bureau, notamment :

* **Déploiement rationalisé**. Les applications ont une expérience de déploiement optimale qui garantit que les utilisateurs peuvent installer une application en toute confiance et la mettre à jour. Si un utilisateur choisit de désinstaller l’application, celle-ci est entièrement supprimée sans aucune trace à gauche, ce qui empêche le problème de la table ROT Windows.

* **Mises à jour automatiques et licences**. Votre application peut participer aux fonctionnalités intégrées de gestion des licences et de mise à jour automatique de Microsoft Store. La mise à jour automatique est un mécanisme extrêmement fiable et efficace, car seules les parties modifiées de fichiers sont téléchargées.

* **Augmentation de la portée et simplification de la monétisation**. Peut-être pas votre cas, mais si vous choisissez de distribuer votre application via le Microsoft Store vous atteignez des millions d’utilisateurs de Windows 10.

* **Ajout de fonctionnalités UWP**. Vous pouvez ajouter des fonctionnalités UWP au package de votre application à votre propre rythme.

#### <a name="prepare-for-packaging"></a>Préparer l’empaquetage

Avant de commencer à empaqueter votre application de bureau, vous devez prendre en compte certains points avant de commencer le processus. Votre application doit respecter les règles et stratégies de Microsoft Store et s’exécuter dans le modèle d’application UWP. Par exemple, il doit s’exécuter sur le .NET Framework 4.6.2 ou version ultérieure et écrit dans la `HKEY_CURRENT_USER` ruche du Registre, et les dossiers AppData seront virtualisés à un emplacement local de l’application spécifique à l’utilisateur.

L’objectif de conception de l’empaquetage est de séparer l’état de l’application de l’état du système tout en conservant la compatibilité avec d’autres applications. Windows 10 remplit cet objectif en plaçant l’application à l’intérieur d’un package UWP. Il détecte et redirige certaines modifications apportées au système de fichiers et au registre au moment de l’exécution afin de garantir la promesse d’une installation approuvée et propre, ainsi que du comportement de désinstallation d’une application fournie par l’empaquetage.

Les packages que vous créez pour votre application de bureau sont des applications de bureau uniquement et de confiance totale qui ne sont pas mises en sandbox, bien qu’il y ait une virtualisation légère appliquée à l’application pour les écritures dans `HKCU` et `AppData` . Cette virtualisation leur permet d’interagir avec d’autres applications de la même façon que les applications de bureau classiques.

##### <a name="installation"></a>Installation

Les packages d’application sont installés sous *% ProgramFiles% \\ WindowsApps \\ package_name*, avec l’exécutable intitulé  `app_name.exe` . Chaque dossier de package contient un manifeste (nommé `AppxManifest.xml` ) qui contient un espace de noms XML spécial pour les applications empaquetées. Dans ce fichier manifeste se trouve un  `<EntryPoint>`   élément qui fait référence à l’application de confiance totale. Lorsque cette application est lancée, elle ne s’exécute pas dans un conteneur d’application, mais elle s’exécute en tant qu’utilisateur normalement.

Après le déploiement, les fichiers du package sont marqués en lecture seule et fortement verrouillés par le système d’exploitation. Windows empêche le lancement des applications si ces fichiers sont falsifiés.

##### <a name="file-system"></a>Système de fichiers

Le système d’exploitation prend en charge différents niveaux d’opérations de système de fichiers pour les applications de bureau empaquetées, en fonction de l’emplacement du dossier.

Lorsque vous tentez d’accéder au dossier *AppData* de l’utilisateur, le système crée un emplacement privé par utilisateur et par application en arrière-plan. Cela crée l’illusion que l’application empaquetée modifie le *AppData* réel lorsqu’il modifie en fait une copie privée. En redirigeant les écritures de cette façon, le système peut suivre toutes les modifications de fichier effectuées par l’application. Il peut ensuite nettoyer tous ces fichiers lors de la désinstallation de la réduction du système « rot » et fournir une meilleure expérience de suppression d’application pour l’utilisateur.

##### <a name="registry"></a>Registre

Les packages d’application contiennent un fichier Registry. dat, qui sert d’équivalent logique de  `HKLM\Software`   dans le registre réel. À l’exécution, ce Registre virtuel fusionne le contenu de cette ruche dans la ruche du système natif afin de fournir un affichage unique des deux.

Toutes les écritures sont conservées lors de la mise à niveau du package et ne sont supprimées que lorsque l’application est désinstallée.

##### <a name="uninstallation"></a>Désinstallation

Lorsque l’utilisateur désinstalle un package, tous les fichiers et dossiers situés sous  `C:\Program Files\WindowsApps\package_name` sont supprimés, ainsi que toutes les écritures redirigées vers AppData ou le Registre qui ont été capturées pendant le processus.

Pour plus d’informations sur la façon dont une application empaquetée gère l’installation, l’accès aux fichiers, le registre et la désinstallation, consultez <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes> .

Vous pouvez obtenir la liste complète des éléments à vérifier <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare> .

## <a name="how-to-add-winrt-apis-to-your-desktop-project"></a>Comment ajouter des API WinRT à votre projet de bureau

Dans cette section, vous trouverez une procédure pas à pas sur l’intégration des notifications Toast dans une application WPF existante. Bien qu’il soit simple du point de vue du code, il permet d’illustrer l’ensemble du processus. Les notifications sont l’une des nombreuses API WinRT disponibles que vous pouvez utiliser dans l’application .NET. Dans ce cas, l’API requiert une identité de package. Ce processus est plus simple si les API ne nécessitent pas d’identité de package.

Prenons un exemple d’application WPF existant qui lit des fichiers et affiche son contenu à l’écran. L’objectif est d’afficher une notification Toast au démarrage de l’application.

![Capture d’écran de l’exemple d’application en cours d’exécution](./media/windows-migration/sample-application.png)

Tout d’abord, vous devez consulter le lien suivant pour savoir si l’API Windows 10 que vous allez utiliser requiert une identité de package :

<https://docs.microsoft.com/windows/apps/desktop/modernize/desktop-to-uwp-supported-api>

Notre exemple utilise l' <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> API qui requiert une identité empaquetée :

![Classe de notification dans la documentation Microsoft](./media/windows-migration/notification-class-documentation.png)

Pour accéder à l’API WinRT, ajoutez une référence au `Microsoft.Windows.SDK.Contracts`   package NuGet. ce package fera la magie en arrière-plan (consultez les détails à l’adresse <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/> ).

Vous êtes maintenant prêt à commencer à ajouter du code.

Créez une `ShowToastNotification` méthode qui sera appelée au démarrage de l’application. Il génère simplement une notification toast à partir d’un modèle XML :

```csharp
private void ShowNotification(string title, string content, string image)
{
    string xmlString = $@"<toast><visual><binding template = 'ToastGeneric'><text>{title}</text><text>{content}</text><image src=>'{image}'</image></binding></visual></toast>";
    XmlDocument toastXml = new XmlDocument();
    toastXml.LoadXml(xmlString);
    ToastNotification toast = new ToastNotification(toastXml);
    ToastNotificationManager.CreateToastNotifier().Show(toast);
}
```

Bien que le projet soit généré, il y a des erreurs, car l’API notifications requiert une identité de package et vous ne l’avez pas fournie. L’ajout d’un projet de Packaging Windows à la solution permet de résoudre le problème :

![Capture d’écran de la boîte de dialogue Ajouter un nouveau projet dans Visual Studio](./media/windows-migration/add-packaging-project.png)

Sélectionnez la version minimale de Windows que vous souhaitez prendre en charge et la version que vous ciblez. Toutes les API WinRT ne sont pas prises en charge dans toutes les versions de Windows 10. Chaque mise à jour de Windows 10 ajoute de nouvelles API qui sont uniquement disponibles à partir de cette version. la prise en charge de niveau supérieur n’est pas disponible.

![Sélection de la version minimale de Windows](./media/windows-migration/select-versions.png)

L’étape suivante consiste à ajouter l’application WPF au projet de Packaging Windows en ajoutant une référence de projet :

![Ajout d’une application WPF au projet de Packaging Windows](./media/windows-migration/add-application.png)

![Gestionnaire de références](./media/windows-migration/reference-manager.png)

Un projet de Packaging Windows peut empaqueter plusieurs applications. vous devez donc définir celle qui correspond au point d’entrée :

![Définition du point d’entrée](./media/windows-migration/set-entry-point.png)

L’étape suivante consiste à définir le projet WPF comme projet de démarrage dans la configuration de la solution. Vous pouvez appuyer sur F5 pour compiler et générer et afficher les résultats.

![Exemple d’application en cours d’exécution et présentant des résultats](./media/windows-migration/sample-app-result.png)

Nous allons générer le package afin de pouvoir installer votre application. Cliquez avec le bouton droit sur **Store**  >  **créer des packages d’application**.

![Boîte de dialogue créer des packages d’application](./media/windows-migration/create-app-packages.png)

Sélectionnez l’option chargement pour déployer l’application à partir de votre ordinateur :

![Sélection de l’option chargement](./media/windows-migration/select-sideloading-option.png)

Sélectionnez l’architecture d’application de votre application :

![Sélection de l’architecture de l’application](./media/windows-migration/select-app-architecture.png)

Enfin, créez le package en cliquant sur **créer**.

## <a name="xaml-islands"></a>XAML Islands

Les îlots XAML sont un ensemble de composants qui permettent aux développeurs de bureau Windows d’utiliser les contrôles XAML UWP sur leurs applications Win32 existantes, y compris Windows Forms et WPF.

![Structure des îlots XAML](./media/windows-migration/xaml-islands.png)

Vous pouvez créer une image de votre application Win32 avec vos contrôles standard et parmi eux un « îlot » d’interfaces utilisateur UWP contenant des contrôles du monde moderne. Le concept est similaire à la présence d’un iFrame dans une page Web qui affiche le contenu d’un`different page.`

Outre l’ajout de fonctionnalités à partir des API Windows 10, vous pouvez ajouter des éléments de code XAML UWP à l’intérieur de votre application à l’aide des îlots XAML.

La mise à jour de Windows 10 1903 introduit un ensemble d’API qui permet d’héberger le contenu XAML UWP dans les fenêtres Win32. Seules les applications qui s’exécutent sur Windows 10 1903 peuvent utiliser des îlots XAML.

### <a name="the-road-to-xaml-islands"></a>La route vers les îles XAML

La route vers les îlots XAML a débuté dans 2012 lorsque Microsoft a introduit les API WinRT comme infrastructure pour moderniser les applications Win32 (Windows Forms, WPF et les applications Win32 natives). Toutefois, les nouveaux contrôles d’interface utilisateur à l’intérieur de WinRT étaient disponibles pour les nouvelles applications, mais pas pour ceux qui existent déjà.

Dans 2015, avec Windows 10, UWP est né. UWP vous permet de créer des applications qui fonctionnent sur des appareils Windows tels que XBox, mobile et Desktop. Un an plus tard, Microsoft a annoncé le pont de bureau (anciennement projet Centennial). Desktop Bridge est un ensemble d’outils qui permettaient aux développeurs d’intégrer leurs applications Win32 existantes à la Microsoft Store. D’autres fonctionnalités ont été ajoutées dans 2017, ce qui permet aux développeurs d’améliorer leurs applications Win32 en tirant parti de certaines des nouvelles API Windows 10, comme les vignettes dynamiques et les notifications sur le centre de maintenance. Mais pourtant, aucun nouveau contrôle d’interface utilisateur.

Au niveau de la build 2018, Microsoft a annoncé aux développeurs qu’ils utilisent les nouveaux contrôles XAML Windows 10 dans leurs applications Win32 actuelles, sans migrer complètement leurs applications vers UWP. Elle a été personnalisée comme des îlots de la série UWP.

### <a name="how-it-works"></a>Fonctionnement

La mise à jour de Windows 10 1903 introduit plusieurs API d’hébergement XAML. Deux d’entre eux sont `WindowsXamlManager`   et  `DesktopWindowXamlSource` .

La  `WindowsXamlManager`   classe gère l’infrastructure XAML UWP. Sa `InitializeForCurrentThread` méthode charge l’infrastructure XAML UWP dans le thread actuel de l’application Win32.

 `DesktopWindowXamlSource`   Est l’instance de votre contenu d’îlot XAML. Il possède la `Content` propriété, que vous êtes chargé d’instancier et de définir. Le `DesktopWindowXamlSource`   restitue et obtient son entrée à partir d’un HWND. Il doit savoir à quel autre HWND il attachera l’îlot XAML, et vous êtes responsable du dimensionnement et du positionnement du HWND du parent.

Les développeurs WPF ou Windows Forms ne traitent généralement pas HWND à l’intérieur de leur code. il peut donc être difficile de comprendre et de gérer les pointeurs HWND et les câbles sous-jacents pour communiquer des mondes Win32 et UWP.

#### <a name="the-xaml-islands-net-wrappers"></a>Wrappers .NET des îlots XAML

La boîte à outils de la communauté Windows a défini les wrappers .NET des îlots XAML pour WPF ou Windows Forms qui facilitent l’utilisation des îlots XAML. Ces wrappers gèrent les HWND, la gestion du focus, entre autres choses. Les développeurs Windows Forms et WPF doivent utiliser ces wrappers.

Le kit de connaissances de la communauté Windows propose deux types de contrôles : les contrôles encapsulés et les contrôles d’hébergement.

##### <a name="wrapped-controls"></a>Contrôles encapsulés

Ces contrôles encapsulés encapsulent certains contrôles UWP dans des contrôles Windows Forms ou WPF, masquant les concepts UWP pour ces développeurs. Ces contrôles sont les suivants :

* WebView et WebViewCompatible
* InkCanvas et InkToolbar
* MediaPlayerElement
* MapControl

Ajoutez le `Microsoft.Toolkit.Wpf.UI.Controls` package à votre projet, incluez la référence à l’espace de noms et commencez à les utiliser.

```xml
<Window
        ...
        xmlns:uwpControls="clr-namespace:Microsoft.Toolkit.Wpf.UI.Controls;assembly=Microsoft.Toolkit.Wpf.UI.Controls">
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="\*"/>
    </Grid.RowDefinitions>
    <uwpControls:InkToolbar TargetInkCanvas="{x:Reference Name=inkCanvas}"/>
    <uwpControls:InkCanvas Grid.Row="1" x:Name="inkCanvas" />
</Grid>
```

##### <a name="hosting-controls"></a>Hébergement de contrôles

La puissance des îlots XAML s’étend à la plupart des contrôles internes, des contrôles tiers et des contrôles personnalisés développés pour UWP, qui peuvent être intégrés à Windows Forms et WPF en tant que « îlots » avec une interface utilisateur entièrement fonctionnelle. Le `WindowsXamlHost` contrôle pour WPF et Windows Forms permet d’y parvenir.

Par exemple, pour utiliser le `WindowsXamlHost` contrôle dans WPF, ajoutez une référence au `Microsoft.Toolkit.Wpf.UI.XamlHost` package fourni par le kit de pratiques de la communauté Windows.

Une fois que vous avez placé votre `WindowsXamlHost` code dans votre code d’interface utilisateur, spécifiez le type UWP que vous souhaitez charger. Vous pouvez choisir d’utiliser un contrôle encapsulé comme un `Button` ou un contrôle plus complexe composé de plusieurs contrôles, qui sont un contrôle UWP personnalisé.

L’exemple suivant montre comment ajouter un UWP `Button` :

```xml
<Window
        ...
        xmlns:xamlhost="clr-namespace:Microsoft.Toolkit.Wpf.UI.XamlHost;assembly=Microsoft.Toolkit.Wpf.UI.XamlHost">

<xamlhost:WindowsXamlHost x:Name="myUwpButton"
                          InitialTypeName="Windows.UI.Xaml.Controls.Button" />
```

Il y a une recommandation claire sur la façon d’aborder ce point et il est préférable de disposer d’un îlot XAML unique et plus grand contenant un contrôle composite personnalisé que d’avoir plusieurs îlots avec un seul contrôle sur chacun.

L’une des principales fonctionnalités de XAML est la liaison et fonctionne entre votre code Win32 et l’îlot. Ainsi, vous pouvez lier, par exemple, un Win32 `Textbox` avec un UWP `Textbox` . Un point important à prendre en compte est que ces liaisons sont des liaisons unidirectionnelles, de UWP à Win32. par conséquent, si vous mettez à jour le `Textbox` à l’intérieur de l’îlot XAML, la zone de texte Win32 est mise à jour, mais pas l’inverse.

Pour voir une procédure pas à pas sur l’utilisation des îlots XAML, consultez :

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-standard-control-with-xaml-islands>

#### <a name="adding-uwp-xaml-custom-controls"></a>Ajout de contrôles personnalisés de XAML UWP

Un contrôle personnalisé XAML est un contrôle (ou contrôle utilisateur) créé par vous ou par des tiers (y compris des contrôles WinUI 2. x). Pour héberger un contrôle UWP personnalisé dans une Windows Forms ou une application WPF, vous avez besoin des éléments suivants :

- Pour utiliser le `WindowsXamlHost` contrôle UWP dans votre application .net Core 3. x.
- Pour créer un projet d’application UWP qui définit un `XamlApplication` objet.

Votre projet WPF ou Windows Forms doit avoir accès à une instance de la `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` classe fournie par le kit de pratiques de la communauté Windows. Cet objet joue le rôle de fournisseur de métadonnées racine pour le chargement des métadonnées des types XAML UWP personnalisés dans les assemblys du répertoire actif de votre application. La méthode recommandée consiste à ajouter un projet application vide (Windows universel) à la même solution que votre projet WPF ou Windows Forms et à modifier la classe d’application par défaut de ce projet.

Le contrôle XAML UWP personnalisé peut être inclus dans cette application UWP ou dans un projet de bibliothèque de classes UWP indépendant que vous référencez dans la même solution que votre projet WPF ou Windows Forms.

Vous pouvez consulter une description détaillée du processus pas à pas à l’adresse suivante :

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

#### <a name="the-windows-ui-library-winui-2"></a>Bibliothèque de l’interface utilisateur Windows (WinUI 2)

Outre les contrôles Windows 10 fournis avec le système d’exploitation, la même équipe XAML UWP fournit également des contrôles supplémentaires dans la bibliothèque de l’interface utilisateur Windows (**WinUI 2**). WinUI 2 fournit des contrôles et des fonctionnalités d’interface utilisateur natifs de Microsoft pour les applications Windows UWP. ces contrôles peuvent être utilisés dans des îlots XAML.

WinUI 2 est open source et vous pouvez trouver des informations à l’adresse <https://github.com/microsoft/microsoft-ui-xaml> .

L’article suivant montre comment héberger un contrôle XAML UWP à partir de la bibliothèque WinUI 2 :<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

### <a name="do-you-need-xaml-islands"></a>Avez-vous besoin d’îlots XAML

Les îlots XAML sont destinés aux applications Win32 existantes qui souhaitent améliorer leur expérience utilisateur en tirant parti de nouveaux contrôles et comportements UWP sans réécriture complète de l’application. Vous pouvez déjà [tirer parti des API Windows 10](/windows/uwp/porting/desktop-to-uwp-enhance), mais jusqu’à ce qu’elles jusqu’à des îlots XAML, seules les API non liées à l’interface utilisateur.

Si vous développez une nouvelle application Windows, une [application UWP](/windows/uwp/get-started/universal-application-platform-guide)   est probablement la bonne approche.

### <a name="the-road-ahead-xaml-islands-winui-30"></a>Les îles de la chaussée à l’avance XAML : WinUI 3,0

Depuis Windows 8, la plateforme d’interface utilisateur Windows, y compris l’infrastructure d’interface utilisateur XAML, la couche de composition visuelle et le traitement d’entrée ont été intégrés à Windows. Cela signifie que pour tirer parti des dernières améliorations apportées aux technologies d’interface utilisateur, vous devez effectuer une mise à niveau vers la dernière version de l’interface utilisateur, ce qui ralentit le rythme d’innovation quand vous développez vos applications. Pour découpler ces deux cycles d’évolution et encourager l’innovation, Microsoft travaille activement au projet WinUI.

À partir de l’interface WinUI 2 dans 2018, Microsoft a commencé à expédier de nouveaux contrôles et fonctionnalités de l’interface utilisateur XAML sous forme de packages NuGet distincts qui s’appuient sur le kit de développement logiciel (SDK) UWP.

![Structure de l’WinUI 2,0](./media/windows-migration/winui2.png)

WinUI 3 est en cours de développement actif et élargit de manière importante l’étendue d’WinUI pour inclure la plateforme d’interface utilisateur complète, qui sera entièrement découplée à partir du kit de développement logiciel (SDK) UWP :

![Structure de l’WinUI 3,0](./media/windows-migration/winui3.png)

L’infrastructure XAML sera désormais développée sur GitHub et livrée hors bande sous forme de packages [NuGet](/nuget/what-is-nuget)   .

Les API XAML UWP existantes fournies dans le cadre du système d’exploitation ne recevront plus de nouvelles mises à jour de fonctionnalités. Ils recevront toujours les mises à jour de sécurité et les correctifs critiques conformément au cycle de vie de la prise en charge de Windows 10.

Le plateforme Windows universelle contient plus que l’infrastructure XAML (par exemple, le modèle d’application et de sécurité, le pipeline multimédia, les intégrations de l’interpréteur de commandes Xbox et Windows 10, la prise en charge étendue des appareils) et continuera à évoluer. Toutes les nouvelles fonctionnalités XAML seront simplement développées et fournies dans le cadre de l’appel à la fonction WinUI.

#### <a name="winui-3-in-desktop-app-and-winui-xaml-islands"></a>WinUI 3 dans une application de bureau et des îlots XAML WinUI

Comme vous pouvez le voir, WinUI 3 est l’évolution du XAML UWP et fonctionne naturellement dans le modèle d’application UWP et dans toutes ses exigences (MSIX Package ID, sandbox, CoreWindow, etc.). Pour utiliser uniquement WinUI 3 dans un modèle d’application Win32, le contenu WinUI doit être hébergé par une autre infrastructure d’interface utilisateur (Windows Forms, WPF, etc.) à l’aide des **îlots XAML WinUI**. C’est le bon chemin d’accès si vous souhaitez faire évoluer vos technologies d’application et de combinaison. Toutefois, si vous souhaitez remplacer l’ancienne interface utilisateur pour WinUI, votre application ne doit pas charger d’infrastructure d’interface utilisateur pour héberger WinUI uniquement.

WinUI 3 répond à ces commentaires critiques **en ajoutant WinUI dans les applications de bureau**. Cela permettra aux applications Win32 d’utiliser WinUI 3 comme infrastructure d’interface utilisateur autonome ; Il n’est pas nécessaire de charger Windows Forms ou WPF.

Dans cette agrégation, WinUI 3 permet aux développeurs de mélanger facilement et de faire correspondre la bonne combinaison de :

* Modèle d’application : UWP, Win32
* Plateforme : .NET Core ou native
* Langage : .NET (C \# , Visual Basic), C++ standard
* Empaquetage : MSIX, AppX pour le Microsoft Store, unpacked
* Interop : utilisez WinUI 3 pour étendre des applications WPF, WinForms et MFC existantes à l’aide des îlots XAML WinUI.

Si vous souhaitez en savoir plus, Microsoft partage cette feuille de route dans <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md> .

>[!div class="step-by-step"]
>[Précédent](migrate-modern-applications.md) 
> [Suivant](example-migration-core.md)
