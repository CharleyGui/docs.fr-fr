---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206209"
---
### <a name="resource-manifest-file-name-change"></a>Changement de nom de fichier manifeste de ressource

À compter de .NET Core 3,0, dans le cas par défaut, MSBuild génère un nom de fichier manifeste différent pour les fichiers de ressources.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="change-description"></a>Description de la modification

Avant .NET Core 3,0, si aucune `LogicalName` métadonnée, `ManifestResourceName` ou n' `DependentUpon` a été spécifiée pour un `EmbeddedResource` élément dans le fichier projet, MSBuild générait un nom de fichier manifeste dans le modèle `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` . Si `RootNamespace` n’est pas défini dans le fichier projet, sa valeur par défaut est le nom du projet. Par exemple, le nom de manifeste généré pour un fichier de ressources nommé *Form1. resx* dans le répertoire racine du projet était *MyProject. Form1. Resources*.

À compter de .NET Core 3,0, si un fichier de ressources est colocalisé avec un fichier source portant le même nom (par exemple, *Form1. resx* et *Form1.cs*), MSBuild utilise les informations de type du fichier source pour générer le nom de fichier manifeste dans le modèle `<Namespace>.<ClassName>.resources` . L’espace de noms et le nom de la classe sont extraits du premier type dans le fichier source colocalisé. Par exemple, le nom de manifeste généré pour un fichier de ressources nommé *Form1. resx* qui est colocalisé avec un fichier source nommé *Form1.cs* est *MyNamespace. Form1. Resources*. Il est important de noter que la première partie du nom de fichier est différente des versions antérieures de .NET Core (*MyNamespace* au lieu de *MyProject*).

> [!NOTE]
> Si vous avez `LogicalName` des `ManifestResourceName` `DependentUpon` métadonnées, ou spécifiées sur un `EmbeddedResource` élément dans le fichier projet, cette modification n’affecte pas ce fichier de ressources.

Cette modification avec rupture a été introduite avec l’ajout de la `EmbeddedResourceUseDependentUponConvention` propriété aux projets .net core. Par défaut, les fichiers de ressources ne sont pas explicitement listés dans un fichier projet .NET Core, donc ils n’ont pas `DependentUpon` de métadonnées pour spécifier comment nommer le fichier *. Resources* généré. Quand `EmbeddedResourceUseDependentUponConvention` a la valeur `true` , qui est la valeur par défaut, MSBuild recherche un fichier source colocalisé et extrait un espace de noms et un nom de classe à partir de ce fichier. Si vous affectez à la valeur `EmbeddedResourceUseDependentUponConvention` `false` , MSBuild génère le nom du manifeste conformément au comportement précédent, qui combine `RootNamespace` et le chemin d’accès relatif du fichier.

#### <a name="recommended-action"></a>Action recommandée

Dans la plupart des cas, aucune action n’est requise de la part du développeur, et votre application doit continuer à fonctionner. Toutefois, si cette modification interrompt votre application, vous pouvez soit :

- Modifiez votre code pour attendre le nouveau nom du manifeste.

- Désactivation de la nouvelle convention d’affectation de noms en affectant à la valeur `EmbeddedResourceUseDependentUponConvention` `false` dans votre fichier projet.

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a>Category

MSBuild

#### <a name="affected-apis"></a>API affectées

NON APPLICABLE
