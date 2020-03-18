---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968052"
---
### <a name="resource-manifest-file-names"></a><span data-ttu-id="e9b26-101">Noms de fichiers manifestes de ressources</span><span class="sxs-lookup"><span data-stu-id="e9b26-101">Resource manifest file names</span></span>

<span data-ttu-id="e9b26-102">À partir de .NET Core 3.0, le nom de fichier manifeste des ressources générées a changé.</span><span class="sxs-lookup"><span data-stu-id="e9b26-102">Starting in .NET Core 3.0, the generated resource manifest file name has changed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e9b26-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e9b26-103">Version introduced</span></span>

<span data-ttu-id="e9b26-104">3.0</span><span class="sxs-lookup"><span data-stu-id="e9b26-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="e9b26-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="e9b26-105">Change description</span></span>

<span data-ttu-id="e9b26-106">Avant .NET Core 3.0, lorsque les métadonnées [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) ont été définies pour une ressource (*.resx*) fichier dans le fichier du projet MSBuild, le nom manifeste généré était *Namespace.Classname.resources*.</span><span class="sxs-lookup"><span data-stu-id="e9b26-106">Prior to .NET Core 3.0, when [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata was set for a resource (*.resx*) file in the MSBuild project file, the generated manifest name was *Namespace.Classname.resources*.</span></span> <span data-ttu-id="e9b26-107">Lorsque [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) n’a pas été défini, le nom manifeste généré était *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span><span class="sxs-lookup"><span data-stu-id="e9b26-107">When [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) was not set, the generated manifest name was *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span></span>

<span data-ttu-id="e9b26-108">À partir de .NET Core 3.0, lorsqu’un fichier *.resx* est coloqué avec un fichier source du même nom, par exemple, dans les applications Windows Forms, le nom manifeste des ressources est généré à partir du nom complet du premier type dans le fichier source.</span><span class="sxs-lookup"><span data-stu-id="e9b26-108">Starting in .NET Core 3.0, when a *.resx* file is colocated with a source file of the same name, for example, in Windows Forms apps, the resource manifest name is generated from the full name of the first type in the source file.</span></span> <span data-ttu-id="e9b26-109">Par exemple, si *Type.cs* est colocated avec *Type.resx*, le nom manifeste généré est *Namespace.Classname.resources*.</span><span class="sxs-lookup"><span data-stu-id="e9b26-109">For example, if *Type.cs* is colocated with *Type.resx*, the generated manifest name is *Namespace.Classname.resources*.</span></span> <span data-ttu-id="e9b26-110">Toutefois, si vous modifiez l’un des attributs de la `EmbeddedResource` propriété pour le fichier *.resx,* le nom de fichier manifeste généré peut être différent :</span><span class="sxs-lookup"><span data-stu-id="e9b26-110">However, if you modify any of the attributes on the `EmbeddedResource` property for the *.resx* file, the generated manifest file name may be different:</span></span>

- <span data-ttu-id="e9b26-111">Si `LogicalName` l’attribut `EmbeddedResource` sur la propriété est défini, cette valeur est utilisée comme nom de fichier manifeste de ressource.</span><span class="sxs-lookup"><span data-stu-id="e9b26-111">If the `LogicalName` attribute on the `EmbeddedResource` property is set, that value is used as the resource manifest file name.</span></span>

  <span data-ttu-id="e9b26-112">Exemples :</span><span class="sxs-lookup"><span data-stu-id="e9b26-112">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  <span data-ttu-id="e9b26-113">**Nom de fichier manifeste de ressource générée**: *SomeName.resources* (indépendamment du nom ou de la culture du fichier *.resx* ou de toute autre métadonnée).</span><span class="sxs-lookup"><span data-stu-id="e9b26-113">**Generated resource manifest file name**: *SomeName.resources* (regardless of the *.resx* file name or culture or any other metadata).</span></span>

- <span data-ttu-id="e9b26-114">Si `LogicalName` elle n’est `ManifestResourceName` pas `EmbeddedResource` définie, mais l’attribut sur la propriété est défini, sa valeur, combinée avec l’extension de fichier *.ressources*, est utilisé comme nom de fichier manifeste de ressource.</span><span class="sxs-lookup"><span data-stu-id="e9b26-114">If `LogicalName` is not set, but the `ManifestResourceName` attribute on the `EmbeddedResource` property is set, its value, combined with the file extension *.resources*, is used as the resource manifest file name.</span></span>

  <span data-ttu-id="e9b26-115">Exemples :</span><span class="sxs-lookup"><span data-stu-id="e9b26-115">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  <span data-ttu-id="e9b26-116">**Nom de fichier manifeste de ressources générées**: *SomeName.resources* ou *SomeName.fr-FR.resources*.</span><span class="sxs-lookup"><span data-stu-id="e9b26-116">**Generated resource manifest file name**: *SomeName.resources* or *SomeName.fr-FR.resources*.</span></span>

- <span data-ttu-id="e9b26-117">Si les règles précédentes ne `DependentUpon` s’appliquent pas, et que l’attribut sur l’élément `EmbeddedResource` est réglé sur un fichier source, le nom type de la première classe dans le fichier source est utilisé dans le nom de fichier manifeste des ressources.</span><span class="sxs-lookup"><span data-stu-id="e9b26-117">If the previous rules don't apply, and the `DependentUpon` attribute on the `EmbeddedResource` element is set to a source file, the type name of the first class in the source file is used in the resource manifest file name.</span></span> <span data-ttu-id="e9b26-118">Plus précisément, le nom de fichier généré est *Namespace.Classname\[. Culture].ressources*.</span><span class="sxs-lookup"><span data-stu-id="e9b26-118">More specifically, the generated file name is *Namespace.Classname\[.Culture].resources*.</span></span>

  <span data-ttu-id="e9b26-119">Exemples :</span><span class="sxs-lookup"><span data-stu-id="e9b26-119">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  <span data-ttu-id="e9b26-120">**Nom de fichier manifeste de ressource générée**: *Namespace.Classname.resources* `Namespace.Classname` ou *Namespace.Classname.fr-FR.resources* (où est le nom de la première classe en *MyTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="e9b26-120">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="e9b26-121">Si les règles précédentes `EmbeddedResourceUseDependentUponConvention` ne `true` s’appliquent pas, est (la valeur par défaut pour .NET Core), et il ya un fichier source colocated avec un fichier *.resx* qui a le même nom de fichier de base, le fichier *.resx* est rendu dépendant du fichier source correspondant, et le nom généré est le même que dans la règle précédente.</span><span class="sxs-lookup"><span data-stu-id="e9b26-121">If the previous rules don't apply, `EmbeddedResourceUseDependentUponConvention` is `true` (the default for .NET Core), and there's a source file colocated with a *.resx* file that has the same base file name, the *.resx* file is made dependent upon the matching source file, and the generated name is the same as in the previous rule.</span></span> <span data-ttu-id="e9b26-122">Il s’agit de la règle des « paramètres par défaut » pour les projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e9b26-122">This is the "default settings" rule for .NET Core projects.</span></span>
  
  <span data-ttu-id="e9b26-123">Exemples :</span><span class="sxs-lookup"><span data-stu-id="e9b26-123">Examples:</span></span>
  
  <span data-ttu-id="e9b26-124">Les fichiers *MyTypes.cs* et *MyTypes.resx* ou *MyTypes.fr-FR.resx* existent dans le même dossier.</span><span class="sxs-lookup"><span data-stu-id="e9b26-124">Files *MyTypes.cs* and *MyTypes.resx* or *MyTypes.fr-FR.resx* exist in the same folder.</span></span>
  
  <span data-ttu-id="e9b26-125">**Nom de fichier manifeste de ressource générée**: *Namespace.Classname.resources* `Namespace.Classname` ou *Namespace.Classname.fr-FR.resources* (où est le nom de la première classe en *MyTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="e9b26-125">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="e9b26-126">Si aucune des règles précédentes ne s’applique, le nom de fichier manifeste de ressource générée est *RootNamespace.RelativePathWithDotsForSlashes.\[ Culture.] ressources*.</span><span class="sxs-lookup"><span data-stu-id="e9b26-126">If none of the previous rules apply, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="e9b26-127">Le chemin relatif est `Link` la valeur `EmbeddedResource` de l’attribut de l’élément s’il est défini.</span><span class="sxs-lookup"><span data-stu-id="e9b26-127">The relative path is the value of the `Link` attribute of the `EmbeddedResource` element if it's set.</span></span> <span data-ttu-id="e9b26-128">Sinon, le chemin relatif est `Identity` la `EmbeddedResource` valeur de l’attribut de l’élément.</span><span class="sxs-lookup"><span data-stu-id="e9b26-128">Otherwise, the relative path is the value of the `Identity` attribute of the `EmbeddedResource` element.</span></span> <span data-ttu-id="e9b26-129">Dans Visual Studio, c’est le chemin de la racine du projet au fichier dans Solution Explorer.</span><span class="sxs-lookup"><span data-stu-id="e9b26-129">In Visual Studio, this is the path from the project root to the file in Solution Explorer.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e9b26-130">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e9b26-130">Recommended action</span></span>

<span data-ttu-id="e9b26-131">Si vous n’êtes pas satisfait des noms manifestes générés, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="e9b26-131">If you're unsatisfied with the generated manifest names, you can:</span></span>

- <span data-ttu-id="e9b26-132">Modifiez vos métadonnées de fichiers de ressources selon l’une des règles de nommage décrites précédemment.</span><span class="sxs-lookup"><span data-stu-id="e9b26-132">Modify your resource file metadata according to one of the previously described naming rules.</span></span>

- <span data-ttu-id="e9b26-133">`EmbeddedResourceUseDependentUponConvention` Définissez `false` dans votre dossier de projet pour vous retirer complètement de la nouvelle convention :</span><span class="sxs-lookup"><span data-stu-id="e9b26-133">Set `EmbeddedResourceUseDependentUponConvention` to `false` in your project file to opt out of the new convention entirely:</span></span>

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > <span data-ttu-id="e9b26-134">Si `LogicalName` les `ManifestResourceName` attributs ou les attributs sont présents, leurs valeurs seront toujours utilisées pour le nom de fichier généré.</span><span class="sxs-lookup"><span data-stu-id="e9b26-134">If the `LogicalName` or `ManifestResourceName` attributes are present, their values will still be used for the generated file name.</span></span>

#### <a name="category"></a><span data-ttu-id="e9b26-135">Category</span><span class="sxs-lookup"><span data-stu-id="e9b26-135">Category</span></span>

<span data-ttu-id="e9b26-136">MSBuild</span><span class="sxs-lookup"><span data-stu-id="e9b26-136">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e9b26-137">API affectées</span><span class="sxs-lookup"><span data-stu-id="e9b26-137">Affected APIs</span></span>

<span data-ttu-id="e9b26-138">N/A</span><span class="sxs-lookup"><span data-stu-id="e9b26-138">N/A</span></span>
