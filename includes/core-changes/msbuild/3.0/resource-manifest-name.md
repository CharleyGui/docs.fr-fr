---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968052"
---
### <a name="resource-manifest-file-names"></a>Noms de fichiers manifestes de ressources

À partir de .NET Core 3.0, le nom de fichier manifeste des ressources générées a changé.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="change-description"></a>Description de la modification

Avant .NET Core 3.0, lorsque les métadonnées [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) ont été définies pour une ressource (*.resx*) fichier dans le fichier du projet MSBuild, le nom manifeste généré était *Namespace.Classname.resources*. Lorsque [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) n’a pas été défini, le nom manifeste généré était *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.

À partir de .NET Core 3.0, lorsqu’un fichier *.resx* est coloqué avec un fichier source du même nom, par exemple, dans les applications Windows Forms, le nom manifeste des ressources est généré à partir du nom complet du premier type dans le fichier source. Par exemple, si *Type.cs* est colocated avec *Type.resx*, le nom manifeste généré est *Namespace.Classname.resources*. Toutefois, si vous modifiez l’un des attributs de la `EmbeddedResource` propriété pour le fichier *.resx,* le nom de fichier manifeste généré peut être différent :

- Si `LogicalName` l’attribut `EmbeddedResource` sur la propriété est défini, cette valeur est utilisée comme nom de fichier manifeste de ressource.

  Exemples :

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  **Nom de fichier manifeste de ressource générée**: *SomeName.resources* (indépendamment du nom ou de la culture du fichier *.resx* ou de toute autre métadonnée).

- Si `LogicalName` elle n’est `ManifestResourceName` pas `EmbeddedResource` définie, mais l’attribut sur la propriété est défini, sa valeur, combinée avec l’extension de fichier *.ressources*, est utilisé comme nom de fichier manifeste de ressource.

  Exemples :

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  **Nom de fichier manifeste de ressources générées**: *SomeName.resources* ou *SomeName.fr-FR.resources*.

- Si les règles précédentes ne `DependentUpon` s’appliquent pas, et que l’attribut sur l’élément `EmbeddedResource` est réglé sur un fichier source, le nom type de la première classe dans le fichier source est utilisé dans le nom de fichier manifeste des ressources. Plus précisément, le nom de fichier généré est *Namespace.Classname\[. Culture].ressources*.

  Exemples :

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  **Nom de fichier manifeste de ressource générée**: *Namespace.Classname.resources* `Namespace.Classname` ou *Namespace.Classname.fr-FR.resources* (où est le nom de la première classe en *MyTypes.cs*).

- Si les règles précédentes `EmbeddedResourceUseDependentUponConvention` ne `true` s’appliquent pas, est (la valeur par défaut pour .NET Core), et il ya un fichier source colocated avec un fichier *.resx* qui a le même nom de fichier de base, le fichier *.resx* est rendu dépendant du fichier source correspondant, et le nom généré est le même que dans la règle précédente. Il s’agit de la règle des « paramètres par défaut » pour les projets .NET Core.
  
  Exemples :
  
  Les fichiers *MyTypes.cs* et *MyTypes.resx* ou *MyTypes.fr-FR.resx* existent dans le même dossier.
  
  **Nom de fichier manifeste de ressource générée**: *Namespace.Classname.resources* `Namespace.Classname` ou *Namespace.Classname.fr-FR.resources* (où est le nom de la première classe en *MyTypes.cs*).

- Si aucune des règles précédentes ne s’applique, le nom de fichier manifeste de ressource générée est *RootNamespace.RelativePathWithDotsForSlashes.\[ Culture.] ressources*. Le chemin relatif est `Link` la valeur `EmbeddedResource` de l’attribut de l’élément s’il est défini. Sinon, le chemin relatif est `Identity` la `EmbeddedResource` valeur de l’attribut de l’élément. Dans Visual Studio, c’est le chemin de la racine du projet au fichier dans Solution Explorer.

#### <a name="recommended-action"></a>Action recommandée

Si vous n’êtes pas satisfait des noms manifestes générés, vous pouvez :

- Modifiez vos métadonnées de fichiers de ressources selon l’une des règles de nommage décrites précédemment.

- `EmbeddedResourceUseDependentUponConvention` Définissez `false` dans votre dossier de projet pour vous retirer complètement de la nouvelle convention :

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > Si `LogicalName` les `ManifestResourceName` attributs ou les attributs sont présents, leurs valeurs seront toujours utilisées pour le nom de fichier généré.

#### <a name="category"></a>Category

MSBuild

#### <a name="affected-apis"></a>API affectées

N/A
