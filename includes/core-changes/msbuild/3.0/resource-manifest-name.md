---
ms.openlocfilehash: 276268d31670b5e7dcd0ae9c0b7a61c3c38ca663
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451883"
---
### <a name="resource-manifest-file-names"></a>Noms des fichiers manifestes de ressources

À compter de .NET Core 3,0, le nom du fichier manifeste de la ressource générée a changé.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="change-description"></a>Modifier la description

Avant .NET Core 3,0, quand les métadonnées [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) étaient définies pour un fichier de ressources ( *. resx*) dans le fichier projet MSBuild, le nom du manifeste généré était *namespace. ClassName. Resources*. Quand [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) n’a pas été défini, le nom du manifeste généré était *namespace. ClassName. FolderPathRelativeToRoot. culture. Resources*.

À compter de .NET Core 3,0, lorsqu’un fichier *. resx* est colocalisé avec un fichier source portant le même nom, par exemple dans Windows Forms Apps, le nom du manifeste de la ressource est généré à partir du nom complet du premier type dans le fichier source. Par exemple, si *type.cs* est colocalisé avec *type. resx*, le nom du manifeste généré est *namespace. ClassName. Resources*. Toutefois, si vous modifiez l’un des attributs de la propriété `EmbeddedResource` pour le fichier *. resx* , le nom du fichier manifeste généré peut être différent :

- Si l’attribut `LogicalName` sur la propriété `EmbeddedResource` est défini, cette valeur est utilisée comme nom de fichier manifeste de la ressource.

  Exemples :

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **Nom du fichier manifeste de la ressource généré**: *nom. Resources* (indépendamment du nom du fichier *. resx* ou de la culture ou de toute autre métadonnée).

- Si `LogicalName` n’est pas défini, mais que l’attribut `ManifestResourceName` de la propriété `EmbeddedResource` est défini, sa valeur, associée à l’extension de fichier *. Resources*, est utilisée comme nom de fichier manifeste de la ressource.

  Exemples :

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **Nom du fichier manifeste de la ressource généré**: *nom. Resources* ou *somename.fr-fr. Resources*.

- Si les règles précédentes ne s’appliquent pas et que l’attribut `DependentUpon` sur l’élément `EmbeddedResource` a la valeur d’un fichier source, le nom de type de la première classe dans le fichier source est utilisé dans le nom du fichier manifeste de la ressource. Plus précisément, le nom de fichier généré est *namespace. Classname\[. Culture]. Resources*.

  Exemples :

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **Nom du fichier manifeste de la ressource généré**: *namespace. ClassName. Resources* ou *namespace.ClassName.fr-fr. resources* (où `Namespace.Classname` est le nom de la première classe dans *myTypes.cs*).

- Si les règles précédentes ne s’appliquent pas, `EmbeddedResourceUseDependentUponConvention` est `true` (valeur par défaut pour .NET Core) et un fichier source est colocalisé avec un fichier *. resx* qui porte le même nom de fichier de base, le fichier *. resx* est rendu dépendant du fichier source correspondant, et le nom généré est le même que dans la règle précédente. Il s’agit de la règle « paramètres par défaut » pour les projets .NET Core.
  
  Exemples :
  
  Les fichiers *myTypes.cs* et *myTypes. resx* ou *myTypes.fr-fr. resx* se trouvent dans le même dossier.
  
  **Nom du fichier manifeste de la ressource généré**: *namespace. ClassName. Resources* ou *namespace.ClassName.fr-fr. resources* (où `Namespace.Classname` est le nom de la première classe dans *myTypes.cs*).
    
- Si aucune des règles précédentes ne s’applique, le nom du fichier manifeste de la ressource générée est *RootNamespace. RelativePathWithDotsForSlashes.\[culture.] ressources*. Le chemin d’accès relatif est la valeur de l’attribut `Link` de l’élément `EmbeddedResource` s’il est défini. Dans le cas contraire, le chemin d’accès relatif est la valeur de l’attribut `Identity` de l’élément `EmbeddedResource`. Dans Visual Studio, il s’agit du chemin d’accès entre la racine du projet et le fichier dans Explorateur de solutions.

#### <a name="recommended-action"></a>Action recommandée

Si vous n’êtes pas satisfait des noms de manifeste générés, vous pouvez :

- Modifiez les métadonnées de votre fichier de ressources en fonction de l’une des règles d’affectation de noms décrites précédemment.

- Définissez `EmbeddedResourceUseDependentUponConvention` sur `false` dans votre fichier projet pour refuser entièrement la nouvelle Convention :

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > Si les attributs `LogicalName` ou `ManifestResourceName` sont présents, leurs valeurs sont toujours utilisées pour le nom de fichier généré.

#### <a name="category"></a>Category

MSBuild

#### <a name="affected-apis"></a>API affectées

N/A
