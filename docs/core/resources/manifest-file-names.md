---
title: Comment MSBuild génère des noms de fichiers manifestes
description: Décrit les facteurs qui influencent le nom d’un fichier manifeste de ressources généré par MSBuild au moment de la compilation.
ms.date: 05/08/2020
ms.topic: conceptual
ms.openlocfilehash: 383bf6a077b0631e70ddaa4721b20e992127a73c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83232325"
---
# <a name="how-resource-manifest-files-are-named"></a>Nom des fichiers manifestes de ressources

Lorsque MSBuild compile un projet .NET Core, les fichiers de ressources XML, qui ont l’extension de fichier *. resx* , sont convertis en fichiers *. Resources* binaires. Les fichiers binaires sont incorporés dans la sortie du compilateur et peuvent être lus par le <xref:System.Resources.ResourceManager> . Cet article explique comment MSBuild choisit un nom pour chaque fichier *. Resources* .

> [!TIP]
> Si vous ajoutez explicitement un élément de ressource à votre fichier projet et qu’il est également [inclus avec le modèles glob par défaut pour .net Core](../project-sdk/overview.md#default-compilation-includes), vous obtiendrez une erreur de Build. Pour inclure manuellement les fichiers de ressources en tant qu' `EmbeddedResource` éléments, affectez la valeur `EnableDefaultEmbeddedResourceItems` false à la propriété.

## <a name="default-name"></a>Nom par défaut

Dans .NET Core 3,0 et versions ultérieures, le nom par défaut d’un manifeste de ressource est utilisé lorsque les deux conditions suivantes sont remplies :

- Le fichier de ressources n’est pas explicitement inclus dans le fichier projet en tant qu' `EmbeddedResource` élément avec les `LogicalName` `ManifestResourceName` `DependentUpon` métadonnées, ou.
- La `EmbeddedResourceUseDependentUponConvention` propriété n’a pas la valeur `false` dans le fichier projet. Par défaut, cette propriété est définie sur `true`. Pour plus d’informations, consultez [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).

Si le fichier de ressources est colocalisé avec un fichier source (*. cs* ou *. vb*) du même nom de fichier racine, le nom complet du premier type défini dans le fichier source est utilisé pour le nom du fichier manifeste. Par exemple, si `MyNamespace.Form1` est le premier type défini dans *Form1.cs*et que *Form1.cs* est colocalisé avec *Form1. resx*, le nom du manifeste généré pour ce fichier de ressources est *MyNamespace. Form1. Resources*.

## <a name="logicalname-metadata"></a>Métadonnées LogicalName

Si un fichier de ressources est explicitement inclus dans le fichier projet en tant qu' `EmbeddedResource` élément avec des `LogicalName` métadonnées, la `LogicalName` valeur est utilisée comme nom de manifeste. `LogicalName`est prioritaire sur toutes les autres métadonnées ou paramètres.

Par exemple, le nom du manifeste du fichier de ressources qui est défini dans l’extrait de code du fichier projet suivant est *nom. Resources*.

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

-ou-

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a>Métadonnées ManifestResourceName

Si un fichier de ressources est explicitement inclus dans le fichier projet en tant qu' `EmbeddedResource` élément avec des `ManifestResourceName` métadonnées (et qu' `LogicalName` il est absent), la `ManifestResourceName` valeur, associée à l’extension de fichier *. Resources*, est utilisée comme nom de fichier manifeste.

Par exemple, le nom du manifeste du fichier de ressources qui est défini dans l’extrait de code du fichier projet suivant est *nom. Resources*.

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

Le nom du manifeste pour le fichier de ressources défini dans l’extrait de code du fichier projet suivant est *somename.fr-fr. Resources*.

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a>Métadonnées DependentUpon

Si un fichier de ressources est explicitement inclus dans le fichier projet en tant qu' `EmbeddedResource` élément avec des `DependentUpon` métadonnées (et `LogicalName` et `ManifestResourceName` sont absents), les informations du fichier source défini par `DependentUpon` sont utilisées pour le nom de fichier manifeste de la ressource. Plus précisément, le nom du premier type défini dans le fichier source est utilisé dans le nom du manifeste comme suit : *namespace. ClassName \[ . Culture]. Resources*.

Par exemple, le nom du manifeste pour le fichier de ressources qui est défini dans l’extrait de code du fichier projet suivant est *namespace. ClassName. Resources* (où `Namespace.Classname` est la première classe qui est définie dans *myTypes.cs*).

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

Le nom du manifeste pour le fichier de ressources défini dans l’extrait de code du fichier projet suivant est *namespace.ClassName.fr-fr. Resources* (où `Namespace.Classname` est la première classe définie dans *myTypes.cs*).

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a>Propriété EmbeddedResourceUseDependentUponConvention

Si `EmbeddedResourceUseDependentUponConvention` a la valeur `false` dans le fichier projet, chaque nom de fichier manifeste de ressource est basé sur l’espace de noms racine du projet et le chemin d’accès relatif de la racine du projet au fichier *. resx* . Plus précisément, le nom du fichier manifeste de la ressource générée est *RootNamespace. RelativePathWithDotsForSlashes. \[ Culture.] ressources*. Il s’agit également de la logique utilisée pour générer les noms des manifestes dans les versions de .NET Core antérieures à 3,0.

> [!NOTE]
>
> - Si `RootNamespace` n’est pas défini, le nom du projet est utilisé par défaut.
> - Si `LogicalName` `ManifestResourceName` `DependentUpon` les métadonnées, ou sont spécifiées pour un `EmbeddedResource` élément dans le fichier projet, cette règle de nommage ne s’applique pas à ce fichier de ressources.

## <a name="see-also"></a>Voir aussi

- [Fonctionnement de l’attribution de noms aux ressources de manifeste](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [Propriétés MSBuild pour les projets kit SDK .NET Core](../project-sdk/msbuild-props.md)
- [Modifications avec rupture MSBuild](../compatibility/msbuild.md)
