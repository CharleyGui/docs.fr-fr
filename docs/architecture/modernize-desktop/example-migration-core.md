---
title: Exemple de migration vers .NET Core 3.1
description: Illustrant comment migrer un exemple d’application ciblant .NET Framework vers .NET Core 3,1.
ms.date: 05/12/2020
ms.openlocfilehash: ef8a0c24ec81a21eb89411ed4c9a543d4d70d89f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423382"
---
# <a name="example-of-migrating-to-net-core-31"></a>Exemple de migration vers .NET Core 3.1

Dans ce chapitre, nous présentons des recommandations pratiques pour vous aider à effectuer une migration de votre application existante de .NET Framework à .NET Core.

Nous présentons un processus bien structuré que vous pouvez suivre et les éléments les plus importants à prendre en compte à chaque étape.

Nous documentons ensuite un processus de migration pas à pas pour un exemple d’application de bureau à partir de WinForms et des versions de WPF.

## <a name="migration-process-overview"></a>Vue d’ensemble du processus de migration

Le processus de migration se compose de quatre étapes séquentielles :

1. **Préparation**: comprenez les dépendances du projet pour avoir une idée de ce qui est avant. Dans cette étape, vous allez passer le projet actuel dans un État qui simplifie le point de démarrage de la migration.

2. **Migrer le fichier projet :** les projets .net Core utilisent le nouveau format de projet de style SDK. Créez un nouveau fichier projet avec ce format ou mettez à jour celui dont vous avez besoin pour utiliser le style du kit de développement logiciel (SDK).

3. **Correction du code et de la génération :** Générez le code dans .NET Core en ce qui concerne les différences au niveau de l’API entre .NET Framework et .NET Core. Si nécessaire, mettez à jour les packages tiers avec ceux qui prennent en charge .NET Core.

4. **Exécuter et tester :** Il peut y avoir des différences qui n’apparaissent pas jusqu’au moment de l’exécution. Donc, n’oubliez pas d’exécuter l’application et de tester que tout fonctionne comme prévu.

### <a name="preparation"></a>Préparation

#### <a name="migrate-packagesconfig-file"></a>Migrer le fichier Packages. config

Dans une application .NET Framework, toutes les références aux packages externes sont déclarées dans le fichier *packages. config* . Dans .NET Core, il n’est plus nécessaire d’utiliser le fichier *packages. config* . Utilisez plutôt la propriété [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) dans le fichier projet pour spécifier les packages NuGet pour votre application.

Par conséquent, vous devez passer d’un format à un autre. Vous pouvez effectuer la mise à jour manuellement, en utilisant les dépendances contenues dans le fichier *packages. config* et en les migrant vers le fichier projet au `PackageReference` format. Vous pouvez également laisser Visual Studio faire le travail pour vous : cliquez avec le bouton droit sur le fichier *packages. config* et sélectionnez l’option **migrer les packages. config vers PackageReference** .

#### <a name="verify-every-dependency-compatibility-in-net-core"></a>Vérifier chaque compatibilité de dépendance dans .NET Core

Une fois que vous avez migré les références du package, vous devez vérifier la compatibilité de chaque référence. Vous pouvez explorer les dépendances de chaque package NuGet utilisé par votre application sur [NuGet.org](https://www.nuget.org/). Si le package possède des dépendances de .NET Standard, il va travailler sur .NET Core, car .NET Core 3,1 [prend en charge](../../standard/net-standard.md#net-implementation-support) toutes les versions de .NET standard. L’illustration suivante montre les dépendances du `Castle.Windsor` Package :

![Capture d’écran des dépendances NuGet pour le package Castle. Windsor](./media/example-migration-core/nuget-dependencies.png)

Pour vérifier la compatibilité du package, vous pouvez utiliser l’outil <http://fuget.org> qui fournit des informations plus détaillées sur les versions et les dépendances.

Le projet peut peut-être référencer des versions de package plus anciennes qui ne prennent pas en charge .NET Core, mais vous pouvez trouver des versions plus récentes qui le prennent en charge. Par conséquent, la mise à jour des packages vers des versions plus récentes est généralement une bonne recommandation. Toutefois, vous devez tenir compte du fait que la mise à jour de la version du package peut entraîner des modifications avec rupture qui vous obligent à mettre à jour votre code.

Que se passe-t-il si vous ne trouvez pas de version compatible ? Que se passe-t-il si vous ne souhaitez pas mettre à jour la version d’un package en raison de ces modifications avec rupture ? Ne vous inquiétez pas, car il est possible de dépendre .NET Framework packages d’une application .NET Core. N’oubliez pas de le tester de manière intensive, car cela peut provoquer des erreurs d’exécution si le package externe appelle une API qui n’est pas disponible sur .NET Core. C’est très utile lorsque vous utilisez un ancien package qui n’est pas mis à jour et que vous pouvez simplement recibler pour travailler sur .NET Core.

#### <a name="check-for-api-compatibility"></a>Vérifier la compatibilité des API

Étant donné que la surface de l’API dans .NET Framework et .NET Core est similaire, mais pas identique, vous devez vérifier les API qui sont disponibles sur .NET Core et celles qui ne le sont pas. Vous pouvez utiliser l’outil Analyseur de portabilité .NET pour déterminer les API utilisées qui ne sont pas présentes sur .NET Core. Il examine le niveau binaire de votre application, extrait toutes les API appelées, puis répertorie les API qui ne sont pas disponibles sur votre Framework cible (.NET Core 3,1 dans le cas présent).

Vous trouverez plus d’informations sur cet outil à l’adresse suivante :

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

Un aspect intéressant de cet outil est qu’il ne couvre que les différences par rapport à votre propre code et non le code des packages externes, que vous ne pouvez pas modifier. N’oubliez pas que vous devez avoir mis à jour la plupart de ces packages pour qu’ils fonctionnent avec .NET Core.

### <a name="migrate-project-file"></a>Migrer le fichier projet

#### <a name="create-the-new-net-core-project"></a>Créer le projet .NET Core

Dans la plupart des cas, vous souhaiterez mettre à jour votre projet existant vers le nouveau format .NET Core. Toutefois, vous pouvez également créer un nouveau projet tout en conservant l’ancien. Le principal inconvénient de la mise à jour de l’ancien projet est que vous perdez la prise en charge du concepteur, ce qui peut être important pour vous. Si vous souhaitez continuer à utiliser le concepteur, vous devez créer un projet .NET Core en parallèle avec l’ancien et partager des ressources. Si vous avez besoin de modifier des éléments d’interface utilisateur dans le concepteur, vous pouvez basculer vers l’ancien projet. Et étant donné que les ressources sont liées, elles sont également mises à jour dans le projet .NET Core.

Le [projet de type SDK](../../core/project-sdk/msbuild-props.md) pour .net Core est beaucoup plus simple que le format de projet de .NET Framework. Outre les entrées mentionnées précédemment `PackageReference` , vous n’avez pas besoin d’en faire plus. Le nouveau format de projet inclut certaines extensions de fichier [par défaut](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects), telles que les `.cs` `.xaml` fichiers et, sans qu’il soit nécessaire de les inclure explicitement dans le fichier projet.

#### <a name="assemblyinfo-considerations"></a>Considérations relatives à Assembly.info

Les attributs sont générés automatiquement dans les projets .NET Core. Si le projet contient un fichier *AssemblyInfo.cs* , les définitions sont dupliquées, ce qui entraîne des conflits de compilation. Vous pouvez supprimer l’ancien fichier *AssemblyInfo.cs* ou désactiver la génération en ajoutant l’entrée suivante dans le fichier projet .net Core :

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a>Ressources

Les ressources incorporées sont automatiquement incluses, mais les ressources ne le sont pas. vous devez donc migrer les ressources vers le nouveau fichier projet.

#### <a name="package-references"></a>Références de package

Avec l’option **migrer les packages. config vers PackageReference** , vous pouvez facilement déplacer vos références de package externes vers le nouveau format mentionné précédemment.

#### <a name="update-package-references"></a>Mettre à jour les références de package

Mettez à jour les versions des packages que vous avez détectés comme étant compatibles, comme indiqué dans la section précédente.

### <a name="fix-the-code-and-build"></a>Corriger le code et générer

#### <a name="microsoftwindowscompatibility"></a>Microsoft. Windows. Compatibility

Si votre application dépend d’API qui ne sont pas disponibles sur .NET Core, telles que le registre, les ACL ou WCF, vous devez inclure une référence au `Microsoft.Windows.Compatibility` package pour ajouter ces API spécifiques à Windows. Ils fonctionnent sur .NET Core, mais ne sont pas inclus, car ils ne sont pas multiplateformes.

Il existe un outil appelé analyseur d’API ( <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> ) qui vous aide à identifier les API qui ne sont pas compatibles avec votre code.

#### <a name="use-if-directives"></a>Utiliser des \# directives if

Si vous avez besoin de chemins d’exécution différents pour cibler .NET Framework et .NET Core, vous devez utiliser des constantes de compilation. Ajoutez des \# directives if à votre code pour conserver la même base de code pour les deux cibles.

#### <a name="technologies-not-available-on-net-core"></a>Technologies non disponibles sur .NET Core

Certaines technologies ne sont pas disponibles sur .NET Core, par exemple :

* AppDomains
* Communication à distance
* Sécurité d'accès du code
* Serveur WCF
* Flux de travail Windows

C’est la raison pour laquelle vous devez remplacer ces technologies si vous les utilisez dans votre application. Pour plus d’informations, consultez l’article [technologies .NET Framework non disponibles sur .net Core](../../core/porting/net-framework-tech-unavailable.md) .

#### <a name="regenerate-autogenerated-clients"></a>Régénérer les clients générés automatiquement

Si votre application utilise du code généré automatiquement, tel qu’un client WCF, vous devrez peut-être régénérer ce code pour cibler .NET Core. Parfois, vous pouvez trouver des références manquantes, car elles ne sont pas incluses dans le jeu d’assemblys .NET Core par défaut. À l’aide d’un outil tel que <https://apisof.net/> , vous pouvez facilement localiser l’assembly dans lequel réside la référence manquante, puis l’ajouter à partir de NuGet.

#### <a name="rolling-back-package-versions"></a>Restauration de versions de package

En règle générale, nous avons indiqué précédemment que vous souhaitez mieux mettre à jour chaque version de package pour qu’elle soit compatible avec .NET Core. Toutefois, vous pouvez constater que le ciblage d’une version mise à jour et compatible d’un assembly n’est pas payant. Si le coût de la modification n’est pas acceptable, vous pouvez envisager de restaurer les versions des packages en gardant celles que vous utilisez sur .NET Framework. Bien qu’ils ne ciblent pas .NET Core, ils doivent fonctionner correctement sauf s’ils appellent des API non prises en charge.

### <a name="run-and-test"></a>Exécuter et tester

Une fois que votre application est en cours d’élaboration sans erreur, vous pouvez démarrer la dernière étape de la migration en testant chaque fonctionnalité.

Dans cette étape finale, vous trouverez plusieurs problèmes différents selon la complexité de votre application et les dépendances et les API que vous utilisez.

Par exemple, si vous utilisez des fichiers de configuration (*app. config*), vous risquez de rencontrer des erreurs au moment de l’exécution, comme des sections de configuration absentes. L’utilisation du `Microsoft.Extensions.Configuration` package NuGet doit corriger cette erreur.

Une autre raison pour les erreurs est l’utilisation `BeginInvoke` des `EndInvoke` méthodes et, car elles ne sont pas prises en charge sur .net core. Ils ne sont pas pris en charge sur .NET Core, car ils ont une dépendance vis-à-vis de la communication à distance, qui n’existe pas sur .NET Core. Pour résoudre ce problème, essayez d’utiliser le `await` mot clé (si disponible) ou la <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> méthode.

Vous pouvez utiliser des analyseurs de compatibilité pour vous permettre d’identifier les API et les modèles de code dans votre code qui peuvent potentiellement provoquer des problèmes au moment de l’exécution avec .NET Core. Accédez à <http://github.com/dotnet/platform-compat> et utilisez l’analyseur d’API .net sur votre projet.

## <a name="migrating-a-windows-forms-application"></a>Migration d’une application Windows Forms

Pour illustrer le processus de migration complet d’une application Windows Forms, nous avons choisi de migrer l’exemple d’application eShop disponible à l’adresse <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> . Vous pouvez trouver le résultat final de la migration à l’adresse <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> .

Cette application affiche un catalogue de produits et permet à l’utilisateur de naviguer, de filtrer et de rechercher des produits. Du point de vue de l’architecture, l’application s’appuie sur un service WCF externe qui sert de façade à une base de données principale.

Vous pouvez voir la fenêtre principale de l’application dans l’image suivante :

![Fenêtre d’application principale](./media/example-migration-core/main-application-window.png)

Si vous ouvrez le fichier de projet *. csproj* , vous pouvez voir ce qui suit :

![Capture d’écran du contenu du fichier csproj](./media/example-migration-core/csproj-file.png)

Comme mentionné précédemment, le projet .NET Core a un style plus compact et vous devez migrer la structure du projet vers le nouveau style de kit SDK .NET Core.

Dans le Explorateur de solutions, cliquez avec le bouton droit sur le projet Windows Forms et sélectionnez **décharger le projet**  >  **modifier**.

Vous pouvez maintenant mettre à jour le fichier. csproj. Vous allez supprimer tout le contenu et le remplacer par le code suivant :

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWindowsForms>true</UseWindowsForms>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

Enregistrez et rechargez le projet. Vous avez maintenant terminé la mise à jour du fichier projet et le projet cible .NET Core.

Si vous compilez le projet à ce stade, vous trouverez des erreurs liées à la référence du client WCF. Étant donné que ce code est généré automatiquement, vous devez le régénérer pour cibler .NET Core.

![Capture d’écran des erreurs de compilation dans Visual Studio](./media/example-migration-core/winforms-compilation-errors.png)

Supprimez le fichier *Reference.cs* et générez un nouveau client de service.

Cliquez avec le bouton droit sur **services connectés** , puis sélectionnez l’option **Ajouter un service connecté** .

![Capture d’écran du menu Services connectés avec l’option Ajouter un service connecté sélectionnée](./media/example-migration-core/add-connected-service.png)

La fenêtre Services connectés s’ouvre. Sélectionnez l’option **service Web Microsoft WCF** .

![Capture d’écran de la fenêtre Services connectés](./media/example-migration-core/connected-services-window.png)

Si vous avez le service WCF dans la même solution que dans cet exemple, vous pouvez sélectionner l’option **Discover** au lieu de spécifier une URL de service.

![Capture d’écran de la fenêtre Configurer la référence de service Web WCF](./media/example-migration-core/configure-wcf-reference.png)

Une fois le service localisé, l’outil reflète le contrat d’API implémenté par le service. Modifiez le nom de l’espace de noms `eShopServiceReference` comme indiqué dans l’image suivante :

![Capture d’écran du contrat d’API et de l’espace de noms modifié](./media/example-migration-core/api-contract-namespace.png)

Sélectionnez le bouton **Terminer** . Après un certain temps, vous verrez le code généré.

Vous devez voir trois fichiers générés automatiquement :

1. *Prise en main*: lien vers GitHub pour fournir des informations sur WCF.
2. *ConnectedService. JSON*: paramètres de configuration pour la connexion au service.
3. *Reference.cs*: code du client WCF réel.

![Capture d’écran de la fenêtre de Explorateur de solutions avec les trois fichiers générés automatiquement](./media/example-migration-core/autogenerated-files.png)

Si vous recompilez, vous verrez de nombreuses erreurs provenant des fichiers *. cs* dans le dossier *d’assistance* . Ce dossier était présent dans la version de .NET Framework, mais il n’est pas inclus dans l’ancien *. csproj*. Mais avec le nouveau projet de type SDK, chaque fichier de code présent sous l’emplacement du fichier projet est inclus par défaut. Autrement dit, le nouveau projet .NET Core tente de compiler les fichiers dans le dossier *d’assistance* . Étant donné que ce dossier n’est pas nécessaire, vous pouvez le supprimer en toute sécurité.

Si vous compilez à nouveau le projet et que vous l’exécutez, vous ne verrez pas les images du produit. Le problème vient du fait que le chemin d’accès aux fichiers a été légèrement modifié. Pour résoudre ce problème, vous devez ajouter un autre niveau de profondeur dans le chemin d’accès, en mettant à jour la ligne dans le fichier `CatalogView.cs` :

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

to

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

Après cette modification, vous pouvez vérifier que l’application est lancée et s’exécute comme prévu sur .NET Core.

## <a name="migrating-a-wpf-application"></a>Migration d’une application WPF

Nous allons utiliser l' `Shop.ClassicWPF` exemple d’application pour effectuer la migration. L’illustration suivante montre une capture d’écran de l’application avant la migration :

![Exemple d’application avant la migration](./media/example-migration-core/app-before-migration.png)

Cette application utilise une base de données SQL Server Express locale pour contenir les informations du catalogue de produits. Cette base de données est accessible directement à partir de l’application WPF.

Tout d’abord, vous devez mettre à jour le fichier *. csproj* avec le nouveau style de kit de développement logiciel (SDK) utilisé par les applications .net core. Suivez les mêmes étapes que celles décrites dans la Windows Forms migration : vous déchargez le projet, ouvrez le fichier *. csproj* , mettez à jour son contenu, puis rechargez le projet.

Dans ce cas, supprimez tout le contenu du fichier *. csproj* et remplacez-le par le code suivant :

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWPF>true</UseWPF>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

Si vous rechargez le projet et le compilez, vous obtiendrez l’erreur suivante :

![Capture d’écran des erreurs de compilation dans Visual Studio](./media/example-migration-core/wpf-compilation-error.png)

Étant donné que vous avez supprimé tout le contenu *. csproj* , vous avez perdu une spécification de référence de projet présente dans l’ancien projet. Vous devez simplement ajouter cette ligne au fichier *. csproj* pour inclure la référence du projet :

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

Vous pouvez également laisser Visual Studio vous aider en cliquant avec le bouton droit sur le nœud **dépendances** et en sélectionnant **Ajouter une référence de projet**. Sélectionnez le projet dans la solution, puis cliquez sur **OK**:

![Capture d’écran de la boîte de dialogue Gestionnaire de références avec le projet eShop. SqlProvider sélectionné](./media/example-migration-core/reference-manager.png)

Une fois que vous avez ajouté la référence de projet manquante, l’application se compile et s’exécute comme prévu sur .NET Core.

>[!div class="step-by-step"]
>[Précédent](windows-migration.md) 
> [Suivant](deploy-modern-applications.md)
