---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206209"
---
### <a name="resource-manifest-file-name-change"></a><span data-ttu-id="b6eb3-101">Changement de nom de fichier manifeste de ressource</span><span class="sxs-lookup"><span data-stu-id="b6eb3-101">Resource manifest file name change</span></span>

<span data-ttu-id="b6eb3-102">À compter de .NET Core 3,0, dans le cas par défaut, MSBuild génère un nom de fichier manifeste différent pour les fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-102">Starting in .NET Core 3.0, in the default case, MSBuild generates a different manifest file name for resource files.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b6eb3-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b6eb3-103">Version introduced</span></span>

<span data-ttu-id="b6eb3-104">3.0</span><span class="sxs-lookup"><span data-stu-id="b6eb3-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="b6eb3-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="b6eb3-105">Change description</span></span>

<span data-ttu-id="b6eb3-106">Avant .NET Core 3,0, si aucune `LogicalName` métadonnée, `ManifestResourceName` ou n' `DependentUpon` a été spécifiée pour un `EmbeddedResource` élément dans le fichier projet, MSBuild générait un nom de fichier manifeste dans le modèle `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` .</span><span class="sxs-lookup"><span data-stu-id="b6eb3-106">Prior to .NET Core 3.0, if no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata was specified for an `EmbeddedResource` item in the project file, MSBuild generated a manifest file name in the pattern `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources`.</span></span> <span data-ttu-id="b6eb3-107">Si `RootNamespace` n’est pas défini dans le fichier projet, sa valeur par défaut est le nom du projet.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-107">If `RootNamespace` is not defined in the project file, it defaults to the project name.</span></span> <span data-ttu-id="b6eb3-108">Par exemple, le nom de manifeste généré pour un fichier de ressources nommé *Form1. resx* dans le répertoire racine du projet était *MyProject. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-108">For example, the generated manifest name for a resource file named *Form1.resx* in the root project directory was *MyProject.Form1.resources*.</span></span>

<span data-ttu-id="b6eb3-109">À compter de .NET Core 3,0, si un fichier de ressources est colocalisé avec un fichier source portant le même nom (par exemple, *Form1. resx* et *Form1.cs*), MSBuild utilise les informations de type du fichier source pour générer le nom de fichier manifeste dans le modèle `<Namespace>.<ClassName>.resources` .</span><span class="sxs-lookup"><span data-stu-id="b6eb3-109">Starting in .NET Core 3.0, if a resource file is colocated with a source file of the same name (for example, *Form1.resx* and *Form1.cs*), MSBuild uses type information from the source file to generate the manifest file name in the pattern `<Namespace>.<ClassName>.resources`.</span></span> <span data-ttu-id="b6eb3-110">L’espace de noms et le nom de la classe sont extraits du premier type dans le fichier source colocalisé.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-110">The namespace and class name are extracted from the first type in the colocated source file.</span></span> <span data-ttu-id="b6eb3-111">Par exemple, le nom de manifeste généré pour un fichier de ressources nommé *Form1. resx* qui est colocalisé avec un fichier source nommé *Form1.cs* est *MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-111">For example, the generated manifest name for a resource file named *Form1.resx* that's colocated with a source file named *Form1.cs* is *MyNamespace.Form1.resources*.</span></span> <span data-ttu-id="b6eb3-112">Il est important de noter que la première partie du nom de fichier est différente des versions antérieures de .NET Core (*MyNamespace* au lieu de *MyProject*).</span><span class="sxs-lookup"><span data-stu-id="b6eb3-112">The key thing to note is that the first part of the file name is different to prior versions of .NET Core (*MyNamespace* instead of *MyProject*).</span></span>

> [!NOTE]
> <span data-ttu-id="b6eb3-113">Si vous avez `LogicalName` des `ManifestResourceName` `DependentUpon` métadonnées, ou spécifiées sur un `EmbeddedResource` élément dans le fichier projet, cette modification n’affecte pas ce fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-113">If you have `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata specified on an `EmbeddedResource` item in the project file, then this change does not affect that resource file.</span></span>

<span data-ttu-id="b6eb3-114">Cette modification avec rupture a été introduite avec l’ajout de la `EmbeddedResourceUseDependentUponConvention` propriété aux projets .net core.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-114">This breaking change was introduced with the addition of the `EmbeddedResourceUseDependentUponConvention` property to .NET Core projects.</span></span> <span data-ttu-id="b6eb3-115">Par défaut, les fichiers de ressources ne sont pas explicitement listés dans un fichier projet .NET Core, donc ils n’ont pas `DependentUpon` de métadonnées pour spécifier comment nommer le fichier *. Resources* généré.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-115">By default, resource files aren't explicitly listed in a .NET Core project file, so they have no `DependentUpon` metadata to specify how to name the generated *.resources* file.</span></span> <span data-ttu-id="b6eb3-116">Quand `EmbeddedResourceUseDependentUponConvention` a la valeur `true` , qui est la valeur par défaut, MSBuild recherche un fichier source colocalisé et extrait un espace de noms et un nom de classe à partir de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-116">When `EmbeddedResourceUseDependentUponConvention` is set to `true`, which is the default, MSBuild looks for a colocated source file and extracts a namespace and class name from that file.</span></span> <span data-ttu-id="b6eb3-117">Si vous affectez à la valeur `EmbeddedResourceUseDependentUponConvention` `false` , MSBuild génère le nom du manifeste conformément au comportement précédent, qui combine `RootNamespace` et le chemin d’accès relatif du fichier.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-117">If you set `EmbeddedResourceUseDependentUponConvention` to `false`, MSBuild generates the manifest name according to the previous behavior, which combines `RootNamespace` and the relative file path.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b6eb3-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b6eb3-118">Recommended action</span></span>

<span data-ttu-id="b6eb3-119">Dans la plupart des cas, aucune action n’est requise de la part du développeur, et votre application doit continuer à fonctionner.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-119">In most cases, no action is required on the part of the developer, and your app should continue to work.</span></span> <span data-ttu-id="b6eb3-120">Toutefois, si cette modification interrompt votre application, vous pouvez soit :</span><span class="sxs-lookup"><span data-stu-id="b6eb3-120">However, if this change breaks your app, you can either:</span></span>

- <span data-ttu-id="b6eb3-121">Modifiez votre code pour attendre le nouveau nom du manifeste.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-121">Change your code to expect the new manifest name.</span></span>

- <span data-ttu-id="b6eb3-122">Désactivation de la nouvelle convention d’affectation de noms en affectant à la valeur `EmbeddedResourceUseDependentUponConvention` `false` dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-122">Opt out of the new naming convention by setting `EmbeddedResourceUseDependentUponConvention` to `false` in your project file.</span></span>

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="b6eb3-123">Category</span><span class="sxs-lookup"><span data-stu-id="b6eb3-123">Category</span></span>

<span data-ttu-id="b6eb3-124">MSBuild</span><span class="sxs-lookup"><span data-stu-id="b6eb3-124">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b6eb3-125">API affectées</span><span class="sxs-lookup"><span data-stu-id="b6eb3-125">Affected APIs</span></span>

<span data-ttu-id="b6eb3-126">NON APPLICABLE</span><span class="sxs-lookup"><span data-stu-id="b6eb3-126">N/A</span></span>
