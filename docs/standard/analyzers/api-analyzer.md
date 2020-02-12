---
title: Analyseur d’API .NET
description: Découvrez comment l’analyseur d’API .NET peut aider à détecter les problèmes de compatibilité de plateforme et les API déconseillées.
author: oliag
ms.date: 04/26/2019
ms.technology: dotnet-standard
ms.openlocfilehash: efbfa89f431bd02cdf86b8eff8704aec63a29b6c
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124245"
---
# <a name="net-api-analyzer"></a>Analyseur d’API .NET

L’analyseur d’API .NET est un analyseur Roslyn qui détecte les risques potentiels liés à la compatibilité des API C# sur différentes plateformes, et détecte les appels à des API déconseillées. Il peut être utile à tous les développeurs C#, quel que soit le stade du développement.

L’analyseur d’API est fourni sous la forme d’un package NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/). Dès lors que vous y faites référence dans un projet, il effectue automatiquement le monitoring du code et indique l’utilisation d’API problématiques. Vous pouvez également obtenir des suggestions sur les corrections possibles en cliquant sur l’ampoule. Le menu déroulant comprend une option permettant de supprimer les avertissements.

> [!NOTE]
> L’analyseur d’API .NET est toujours en préversion.

## <a name="prerequisites"></a>Conditions préalables requises

- Visual Studio 2017 et versions ultérieures, ou Visual Studio pour Mac (toutes les versions).

## <a name="discovering-deprecated-apis"></a>Découverte des API déconseillées

### <a name="what-are-deprecated-apis"></a>Que sont les API déconseillées ?

La famille .NET est un ensemble de grands produits, qui sont constamment mis à niveau pour mieux répondre aux besoins des clients. Il est naturel de déconseiller certaines API et de les remplacer par d’autres. Une API est considérée comme déconseillées lorsqu’il existe une meilleure solution. Une API déconseillée, qu’il ne faut pas utiliser, peut être marquée avec l’attribut <xref:System.ObsoleteAttribute>. L’inconvénient de cette approche est qu’il n'existe qu’un seul ID de diagnostic pour toutes les API obsolètes (pour C#, [CS0612](../../csharp/misc/cs0612.md)). Cela signifie que :

- Il est impossible d’avoir un document dédié à chacun des cas.
- Il n’est pas possible de supprimer certaines catégories d’avertissements. On peut soit tous les supprimer, soit n’en supprimer aucun.
- Pour informer les utilisateurs qu’une API est à présent déconseillée, il faut mettre à jour un package de ciblage ou un assembly de référence.

L’analyseur d’API utilise des codes d’erreur propres aux API, qui commencent par DE (de l’anglais « Deprecation Error »), ce qui permet de contrôler l’affichage des différents avertissements. Les API déconseillées identifiées par l’analyseur sont définies dans le référentiel [dotnet/plateforme-compat](https://github.com/dotnet/platform-compat).

### <a name="using-the-api-analyzer"></a>Utiliser l’analyseur d’API

Lorsqu’une API déconseillée, par exemple, <xref:System.Net.WebClient>, est utilisée dans un code, l’analyseur d’API la souligne d’un trait vert ondulé. Lorsque vous placez le curseur sur l’appel d’API, une ampoule donne des informations sur les API déconseillées, comme dans l’exemple suivant :

![« Capture d’écran de l’API WebClient avec une ligne verte ondulée et une ampoule à gauche »](media/api-analyzer/green-squiggle.jpg)

La fenêtre **Liste d’erreurs** contient des avertissements avec un ID unique par API déconseillée, comme dans l’exemple suivant (`DE004`) : 

![« Capture d’écran de la fenêtre Liste d’erreurs montrant l’ID et la description de l’avertissement »](media/api-analyzer/warnings-id-and-descriptions.jpg "Liste d’erreurs fenêtre qui contient des avertissements.")

En cliquant sur l’ID, vous accédez à une page web présentant des informations détaillées sur la raison pour laquelle l’API a été déconseillée, ainsi que des suggestions d’autres API utilisables.

Pour supprimer des avertissements, cliquez sur le membre en surbrillance et sélectionnez **Supprimer \<ID de diagnostic >** . Il existe deux moyens de supprimer les avertissements : 

- [localement (dans la source)](#suppressing-warnings-locally) ;
- [globalement (dans un fichier de suppression)](#suppressing-warnings-globally) – recommandé.

### <a name="suppressing-warnings-locally"></a>Supprimer les avertissements localement

Pour supprimer des avertissements localement, cliquez sur le membre dont vous souhaitez supprimer les avertissements, puis sélectionnez **Actions rapides et refactorisations** > **Supprimer *ID de diagnostic*\<ID de diagnostic >**  > **dans la source**. La directive du préprocesseur d’avertissement [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) est ajoutée à votre code source dans l’étendue définie : ![« Capture d’écran du code encadré par #pragma warning disable »](media/api-analyzer/suppress-in-source.jpg)

### <a name="suppressing-warnings-globally"></a>Supprimer les avertissements globalement

Pour supprimer des avertissements globalement, cliquez sur le membre dont vous souhaitez supprimer les avertissements, puis sélectionnez **Actions rapides et refactorisations** > **Supprimer *ID de diagnostic*\<ID de diagnostic >**  > **dans le fichier de suppression**.

![« Capture d’écran de l’API WebClient avec une ligne verte ondulée et une ampoule à gauche »](media/api-analyzer/suppress-in-sup-file.jpg)

Un fichier *GlobalSuppressions.cs* est ajouté à votre projet après la première suppression. Les nouvelles suppressions globales seront ajoutées à ce fichier.

![« Capture d’écran de l’API WebClient avec une ligne verte ondulée et une ampoule à gauche »](media/api-analyzer/suppression-file.jpg)

La suppression globale est la méthode recommandée pour garantir une utilisation cohérente de l’API d’un projet à l’autre.

## <a name="discovering-cross-platform-issues"></a>Détecter des problèmes multiplateformes

Tout comme les API déconseillées, l’analyseur identifie toutes les API non multiplateformes. Par exemple, <xref:System.Console.WindowWidth?displayProperty=nameWithType> fonctionne sous Windows, mais pas sous Linux ou macOS. L’ID de diagnostic apparaît dans la fenêtre **Liste d’erreurs**. Vous pouvez supprimer cet avertissement en cliquant avec le bouton droit et en sélectionnant **Actions rapides et refactorisations**. Contrairement au cas des API déconseillées, dans lequel deux options sont proposées (continuer d’utiliser le membre déconseillé et supprimer les avertissements, ou ne pas l’utiliser du tout), ici, si vous développez votre code pour certaines plateformes seulement, vous pouvez supprimer les avertissements de toutes les autres plateformes sur lesquelles vous n’envisagez pas d’exécuter votre code. Il vous suffit pour cela de modifier votre fichier projet et d’ajouter la propriété `PlatformCompatIgnore`, qui liste toutes les plateformes à ignorer. Les valeurs acceptées sont les suivantes : `Linux`, `macOS` et `Windows`.

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

Si votre code cible plusieurs plateformes et que vous souhaitez tirer parti d’une API non prise en charge sur certaines d'entre elles, vous pouvez protéger cette partie du code avec une instruction `if` :

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

Vous pouvez également effectuer une compilation conditionnelle par système d’exploitation/version cible de .NET Framework ; il s’agit pour le moment d’une opération [manuelle](../frameworks.md#how-to-specify-target-frameworks).

## <a name="supported-diagnostics"></a>Diagnostics pris en charge

Actuellement, l’analyseur gère les cas suivants :

- utilisation d’une API .NET Standard qui lève <xref:System.PlatformNotSupportedException> (PC001) ;
- utilisation d’une API .NET Standard non disponible sur .NET Framework 4.6.1 (PC002) ;
- utilisation d’une API native qui n’existe pas dans UWP (PC003) ;
- Utilisation des API Delegate.BeginInvoke et EndInvoke (PC004).
- utilisation d’une API marquée comme déconseillée (DEXXXX).

## <a name="ci-machine"></a>Machine de CI

Tous ces diagnostics sont disponibles non seulement dans l’IDE, mais également en ligne de commande dans le cadre de la création du projet, qui inclut le serveur de CI.

## <a name="configuration"></a>Configuration

L’utilisateur choisit le mode de traitement des diagnostics : en tant qu’avertissements, en tant qu’erreurs, en tant que suggestions ou désactivés. Par exemple, l’architecte peut décider que les problèmes de compatibilité doivent être traités comme des erreurs, que les appels à certaines API déconseillées génèrent des avertissements, tandis que les autres ne produiront que des suggestions. Vous pouvez configurer cela séparément, ID de diagnostic par ID de diagnostic et projet par projet. Pour cela, accédez au nœud **Dépendances** sous votre projet dans **l’Explorateur de solutions**. Développez les nœuds **Dépendances** > **Analyseurs** > **Microsoft.DotNet.Analyzers.Compatibility**. Cliquez avec le bouton droit sur l’ID de diagnostic, sélectionnez **Définir la gravité de l’ensemble de règles** et choisissez l’option souhaitée.

![« Capture d’écran de l’Explorateur de solutions affichant les diagnostics et la boîte de dialogue contextuelle avec la gravité de l’ensemble de règles »](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a>Voir aussi

- Billet de blog [Présentation de l’analyseur d’API](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/).
- Vidéo de démonstration sur YouTube de [l’analyseur d’API](https://youtu.be/eeBEahYXGd0).
