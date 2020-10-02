---
title: Présentation du déploiement de ReadyToRun
description: Découvrez les déploiements ReadyToRun et les raisons pour lesquelles vous devez envisager de l’utiliser dans le cadre de la publication de votre application avec .NET 5 et .NET Core 3,0 et versions ultérieures.
author: davidwr
ms.author: davidwr
ms.date: 09/21/2020
ms.openlocfilehash: b4052a0c0f4ed9f6cfd273abe5ef45d018bd0ae0
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654962"
---
# <a name="readytorun-compilation"></a>Compilation ReadyToRun

Le temps de démarrage et la latence de l’application .NET peuvent être améliorés en compilant vos assemblys d’application au format ReadyToRun (R2R). R2R est une forme de compilation ahead-of-time (AOT).

Les fichiers binaires R2R améliorent les performances de démarrage en réduisant la quantité de travail que le compilateur juste-à-temps (JIT) doit faire lorsque votre application est chargée. Les fichiers binaires contiennent du code natif similaire à ce que la compilation JIT produirait. Cependant, les fichiers binaires R2R sont plus grands, car ils contiennent à la fois le code du langage intermédiaire (IL), qui est toujours nécessaire pour certains scénarios, et la version native du même code. R2R est disponible uniquement lorsque vous publiez une application qui cible des environnements d’exécution spécifiques (RID) tels que Linux x64 ou Windows x64.

Pour compiler votre projet en tant que ReadyToRun, l’application doit être publiée avec la propriété PublishReadyToRun définie sur true.

Il existe deux façons de publier votre application en tant que ReadyToRun :

01. Spécifiez l’indicateur PublishReadyToRun directement à la commande dotnet publish. Pour plus d’informations, consultez [dotnet Publish](../tools/dotnet-publish.md) .

    ```dotnetcli
    dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
    ```

02. Spécifier la propriété dans le projet

    - Ajoutez le `<PublishReadyToRun>` paramètre à votre projet.

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

    - Publiez l’application sans paramètres spéciaux.

    ```dotnetcli
    dotnet publish -c Release -r win-x64
    ```

## <a name="impact-of-using-the-readytorun-feature"></a>Impact de l’utilisation de la fonctionnalité ReadyToRun

La compilation à l’avance a un impact complexe sur les performances des applications, ce qui peut être difficile à prédire. En général, la taille d’un assembly est comprise entre deux et trois fois plus grand. Cette augmentation de la taille physique du fichier peut réduire les performances de chargement de l’assembly à partir du disque et augmenter la plage de travail du processus. Toutefois, en retour, le nombre de méthodes compilées au moment de l’exécution est généralement réduit de façon significative. Le résultat est que la plupart des applications qui tirent de grandes quantités de code reçoivent des avantages en matière de performances en activant ReadyToRun. Les applications, qui ont de petites quantités de code ne subiront probablement pas une amélioration significative de l’activation de ReadyToRun, car les bibliothèques du Runtime .NET ont déjà été précompilées avec ReadyToRun.

L’amélioration du démarrage décrite ici s’applique non seulement au démarrage de l’application, mais également à la première utilisation du code dans l’application. Par exemple, ReadyToRun peut être utilisé pour réduire la latence de la réponse de la première utilisation de l’API Web dans une application ASP.NET.

### <a name="interaction-with-tiered-compilation"></a>Interaction avec la compilation à plusieurs niveaux

La génération anticipée n’est pas aussi hautement optimisée que le code produit par le JIT. Pour résoudre ce problème, la compilation à plusieurs niveaux remplace les méthodes ReadyToRun couramment utilisées par les méthodes générées juste-à-temps.

## <a name="how-is-the-set-of-precompiled-assemblies-chosen"></a>Comment l’ensemble d’assemblys précompilés est-il choisi ?

Le kit de développement logiciel (SDK) précompile les assemblys qui sont distribués avec l’application. Pour les applications autonomes, cet ensemble d’assemblys inclut le Framework. Les binaires C++/CLI ne sont pas éligibles pour la compilation ReadyToRun.

## <a name="how-is-the-set-of-methods-to-precompile-chosen"></a>Comment l’ensemble de méthodes à précompiler est-il choisi ?

Le compilateur tente de précompiler autant de méthodes que possible. Toutefois, différentes raisons pour lesquelles il n’est pas prévu d’utiliser la fonctionnalité ReadyToRun empêchent l’exécution du JIT.

Ces raisons peuvent inclure, mais ne sont pas limitées à :

- Utilisation de types génériques définis dans des assemblys séparés
- Interopérabilité avec du code natif
- Utilisation des intrinsèques matériels que le compilateur ne peut pas prouver pouvoir utiliser sur un ordinateur cible
- Certains modèles de langage intermédiaire inhabituels
- Création de méthodes dynamiques via la réflexion, ou LINQ

## <a name="cross-platformarchitecture-restrictions"></a>Restrictions d’architecture/de multiplateforme

Pour certaines plateformes du kit de développement logiciel (SDK), le compilateur ReadyToRun peut effectuer une compilation croisée pour d’autres plateformes cibles. Les cibles de compilation prises en charge sont décrites dans le tableau ci-dessous.

| Plateforme du Kit de développement logiciel (SDK) | Plateformes cibles prises en charge |
| ------------ | --------------------------- |
| Windows X64  | Windows x86, Windows x64, Windows ARM32, Windows ARM64 |
| Windows x86  | Windows x86, Windows ARM32 |
| Linux X64    | Linux x86, Linux x64, Linux ARM32, Linux ARM64 |
| Linux ARM32  | Linux ARM32 |
| ARM64 Linux  | ARM64 Linux |
| macOS x64    | macOS x64 |
