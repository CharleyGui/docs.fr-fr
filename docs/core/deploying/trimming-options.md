---
title: Options de suppression
description: Découvrez comment contrôler le découpage des applications autonomes.
author: sbomer
ms.author: svbomer
ms.date: 08/25/2020
ms.openlocfilehash: d6081a24cc18e424b55d40e152f519c680f11aa0
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271878"
---
# <a name="trimming-options"></a>Options de suppression

Les propriétés et les éléments MSBuild suivants influencent le comportement des [déploiements autonomes tronqués](trim-self-contained.md). Certaines des options mentionnent `ILLink` , qui est le nom de l’outil sous-jacent qui implémente la suppression. Pour plus d’informations sur l' `ILLink` outil en ligne de commande, consultez [options de illink](https://github.com/mono/linker/blob/master/docs/illink-options.md).

## <a name="enable-trimming"></a>Activer la suppression

- `<PublishTrimmed>true</PublishTrimmed>`

   Activez la suppression lors de la publication, avec les paramètres par défaut définis par le kit de développement logiciel (SDK).

Lors de l’utilisation de `Microsoft.NET.Sdk` , cette opération effectue une suppression au niveau de l’assembly des assemblys du Framework à partir du pack d’exécution netcoreapp. Le code d’application et les bibliothèques non Framework ne sont pas supprimés. D’autres kits de développement logiciel (SDK) peuvent définir des valeurs par défaut différentes.

## <a name="trimming-granularity"></a>Granularité de suppression

Les paramètres de granularité suivants contrôlent la façon dont le langage intermédiaire inutilisé de manière agressive est ignoré. Cela peut être défini en tant que propriété ou en tant que métadonnées sur un [assembly individuel](#trimmed-assemblies).

- `<TrimMode>copyused</TrimMode>`

   Activez la suppression au niveau de l’assembly, qui conservera un assembly entier si une partie de celui-ci est utilisée (de façon interprétée de manière statique).

- `<TrimMode>link</TrimMode>`

    Activez la suppression au niveau du membre, qui supprime les membres inutilisés des types.

Les assemblys avec des `<IsTrimmable>true</IsTrimmable>` métadonnées, mais pas explicites `TrimMode` , utilisent le global `TrimMode` . La valeur par défaut `TrimMode` de `Microsoft.NET.Sdk` est `copyused` .

## <a name="trimmed-assemblies"></a>Assemblys tronqués

Lors de la publication d’une application tronquée, le kit de développement logiciel (SDK) calcule un `ItemGroup` appelé `ManagedAssemblyToLink` qui représente le jeu de fichiers à traiter pour la suppression. `ManagedAssemblyToLink` peut avoir des métadonnées qui contrôlent le comportement de suppression par assembly. Pour définir ces métadonnées, créez une cible qui s’exécute avant la `PrepareForILLink` cible intégrée. Cet exemple montre comment activer la suppression des `MyAssembly` éléments suivants :

```xml
<Target Name="ConfigureTrimming"
        BeforeTargets="PrepareForILLink">
  <ItemGroup>
    <ManagedAssemblyToLink Condition="'%(Filename)' == 'MyAssembly'">
      <IsTrimmable>true</IsTrimmable>
    </ManagedAssemblyToLink>
  </ItemGroup>
</Target>
```

N’ajoutez pas ou ne supprimez pas d’éléments dans `ManagedAssemblyToLink` , car le kit de développement logiciel (SDK) calcule cet ensemble lors de la publication et s’attend à ce qu’il ne soit pas modifié. Les métadonnées prises en charge sont les suivantes :

- `<IsTrimmable>true</IsTrimmable>`

  Contrôle si l’assembly donné est tronqué.

- `<TrimMode>copyused</TrimMode>` ou `<TrimMode>link</TrimMode>`

  Contrôler la [granularité](#trimming-granularity) de la suppression de cet assembly. Cela est prioritaire par rapport au global `TrimMode` . La définition `TrimMode` d’un assembly implique `<IsTrimmable>true</IsTrimmable>` .

## <a name="root-assemblies"></a>Assemblys racines

Tous les assemblys qui n’ont pas de `<IsTrimmable>true</IsTrimmable>` données sont considérés comme des racines pour l’analyse, ce qui signifie qu’elles sont conservées et toutes leurs dépendances comprises statiquement. Les assemblys supplémentaires peuvent être « enracinés » par nom (sans l' `.dll` extension) :

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="MyAssembly" />
</ItemGroup>
```

## <a name="root-descriptors"></a>Descripteurs racines

Une autre façon de spécifier des racines pour l’analyse consiste à utiliser un fichier XML qui utilise le [format de descripteur](https://github.com/mono/linker/blob/master/docs/data-formats.md#descriptor-format)de l’éditeur de liens. Cela vous permet d’obtenir des membres spécifiques à la racine au lieu d’un assembly entier.

```xml
<ItemGroup>
  <TrimmerRootDescriptor Include="MyRoots.xml" />
</ItemGroup>
```

Par exemple, `MyRoots.xml` peut être la racine d’une méthode spécifique qui est accessible de manière dynamique par l’application :

```xml
<linker>
  <assembly fullname="MyAssembly">
    <type fullname="MyAssembly.MyClass">
      <method name="DynamicallyAccessedMethod" />
    </type>
  </assembly>
</linker>
```

## <a name="analysis-warnings"></a>Avertissements d’analyse

La suppression supprimera IL qui n’est pas accessible de manière statique. Les applications qui utilisent la réflexion ou d’autres modèles qui créent des dépendances dynamiques peuvent être interrompues par la suppression. Pour signaler ces modèles :

- `<SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>`

    Activez les avertissements d’analyse de découpage.

Cela inclut les avertissements relatifs à l’application entière, y compris votre propre code, votre propre code de bibliothèque et votre code d’infrastructure.

## <a name="warning-versions"></a>Versions d’avertissement

L’analyse de découpage respecte la [`AnalysisLevel`](../project-sdk/msbuild-props.md#analysislevel) propriété qui contrôle la version des avertissements d’analyse dans le kit de développement logiciel (SDK). Il existe une autre propriété qui contrôle la version des avertissements d’analyse de suppression indépendamment (comme `WarningLevel` pour le compilateur) :

- `<ILLinkWarningLevel>5</ILLinkWarningLevel>`

    Émet uniquement les avertissements du niveau donné ou inférieurs. Cela peut consister `9999` à inclure toutes les versions d’avertissement.

## <a name="suppressing-warnings"></a>Supprimer les avertissements

Les [codes d’avertissement](https://github.com/mono/linker/blob/master/docs/error-codes.md#warning-codes) individuels peuvent être supprimés à l’aide des propriétés MSBuild habituelles respectées par chaîne d’outils, notamment `NoWarn` ,, `WarningsAsErrors` `WarningsNotAsErrors` et `TreatWarningsAsErrors` . Il existe une option supplémentaire qui contrôle le comportement de l’avertissement en tant qu’erreur ILLink indépendamment :

- `<ILLinkTreatWarningsAsErrors>false</ILLinkTreatWarningsAsErrors>`

    Ne pas traiter les avertissements ILLink comme des erreurs. Cela peut être utile pour éviter d’activer les avertissements d’analyse de suppression dans des erreurs lors du traitement des avertissements du compilateur en tant qu’erreurs de manière globale.

## <a name="removing-symbols"></a>Suppression de symboles

Les symboles sont normalement tronqués pour correspondre aux assemblys tronqués. Vous pouvez également supprimer tous les symboles :

- `<TrimmerRemoveSymbols>true</TrimmerRemoveSymbols>`

    Supprimer les symboles de l’application rognée, y compris les fichiers PDB incorporés et les fichiers PDB séparés. Cela s’applique à la fois au code d’application et à toutes les dépendances qui accompagnent les symboles.

Le kit de développement logiciel (SDK) permet également de désactiver la prise en charge du débogueur à l’aide de la propriété `DebuggerSupport` . Lorsque la prise en charge du débogueur est désactivée, la suppression supprime automatiquement les symboles (la `TrimmerRemoveSymbols` valeur par défaut est true).
