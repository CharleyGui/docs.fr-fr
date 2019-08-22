---
title: Élément <compiler>
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: 80eea3373e2f4b7e45ebeb31dd6552ea02c109e1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659731"
---
# <a name="compiler-element"></a><span data-ttu-id="c1d52-102">\<Élément de > du compilateur</span><span class="sxs-lookup"><span data-stu-id="c1d52-102">\<compiler> Element</span></span>

<span data-ttu-id="c1d52-103">Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="c1d52-103">Specifies the compiler configuration attributes for a language provider.</span></span>

<span data-ttu-id="c1d52-104">\<élément de configuration \<> élément System. CodeDom \<> les compilateurs > \<élément > du compilateur</span><span class="sxs-lookup"><span data-stu-id="c1d52-104">\<configuration Element> \<system.codedom Element> \<compilers Element> \<compiler> Element</span></span>

## <a name="syntax"></a><span data-ttu-id="c1d52-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1d52-105">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1d52-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c1d52-106">Attributes and Elements</span></span>

<span data-ttu-id="c1d52-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c1d52-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1d52-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="c1d52-108">Attributes</span></span>

|<span data-ttu-id="c1d52-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c1d52-109">Attribute</span></span>|<span data-ttu-id="c1d52-110">Description</span><span class="sxs-lookup"><span data-stu-id="c1d52-110">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="c1d52-111">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="c1d52-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c1d52-112">Spécifie des arguments supplémentaires spécifiques au compilateur pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="c1d52-112">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="c1d52-113">Les valeurs de l' `compilerOptions` attribut sont généralement répertoriées dans une rubrique Options du compilateur pour le compilateur.</span><span class="sxs-lookup"><span data-stu-id="c1d52-113">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="c1d52-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="c1d52-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="c1d52-115">Fournit une liste séparée par des points-virgules des extensions de nom de fichier utilisées par les fichiers sources pour le fournisseur de langages.</span><span class="sxs-lookup"><span data-stu-id="c1d52-115">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="c1d52-116">Par exemple, «. cs».</span><span class="sxs-lookup"><span data-stu-id="c1d52-116">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="c1d52-117">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="c1d52-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="c1d52-118">Fournit une liste séparée par des points-virgules des noms de langage pris en charge par le fournisseur de langages.</span><span class="sxs-lookup"><span data-stu-id="c1d52-118">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="c1d52-119">Par exemple, «c#; CS; CSharp».</span><span class="sxs-lookup"><span data-stu-id="c1d52-119">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="c1d52-120">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="c1d52-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="c1d52-121">Spécifie le nom de type du fournisseur de langages, y compris le nom de l’assembly contenant l’implémentation du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c1d52-121">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="c1d52-122">Le nom de type doit satisfaire aux spécifications définies dans [spécification de noms de types qualifiés complets](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="c1d52-122">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="c1d52-123">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="c1d52-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c1d52-124">Spécifie le niveau d’avertissement du compilateur par défaut; détermine le niveau auquel le fournisseur de langages traite les avertissements de compilation comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="c1d52-124">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c1d52-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c1d52-125">Child Elements</span></span>

|<span data-ttu-id="c1d52-126">Élément</span><span class="sxs-lookup"><span data-stu-id="c1d52-126">Element</span></span>|<span data-ttu-id="c1d52-127">Description</span><span class="sxs-lookup"><span data-stu-id="c1d52-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1d52-128">\<providerOption >, élément</span><span class="sxs-lookup"><span data-stu-id="c1d52-128">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="c1d52-129">Spécifie les attributs de version du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="c1d52-129">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c1d52-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c1d52-130">Parent Elements</span></span>

|<span data-ttu-id="c1d52-131">Élément</span><span class="sxs-lookup"><span data-stu-id="c1d52-131">Element</span></span>|<span data-ttu-id="c1d52-132">Description</span><span class="sxs-lookup"><span data-stu-id="c1d52-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1d52-133">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="c1d52-133">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="c1d52-134">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c1d52-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="c1d52-135">\<System. CodeDom >, élément</span><span class="sxs-lookup"><span data-stu-id="c1d52-135">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="c1d52-136">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="c1d52-136">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="c1d52-137">\<compilateurs > élément</span><span class="sxs-lookup"><span data-stu-id="c1d52-137">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="c1d52-138">Conteneur pour les éléments de configuration du compilateur; contient zéro ou plusieurs `<compiler>` éléments.</span><span class="sxs-lookup"><span data-stu-id="c1d52-138">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c1d52-139">Notes</span><span class="sxs-lookup"><span data-stu-id="c1d52-139">Remarks</span></span>

<span data-ttu-id="c1d52-140">Chaque `<compiler>` élément spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique.</span><span class="sxs-lookup"><span data-stu-id="c1d52-140">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="c1d52-141">Le fournisseur étend la <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> classe pour un langage spécifique; l' `<compiler>` élément définit le compilateur et les paramètres du générateur de code pour le fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="c1d52-141">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="c1d52-142">Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c1d52-142">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="c1d52-143">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="c1d52-143">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="c1d52-144">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c1d52-144">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="c1d52-145">Les éléments du compilateur dans le fichier de configuration Web ou d’application peuvent compléter ou substituer les paramètres dans le fichier de configuration de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c1d52-145">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="c1d52-146">Si plusieurs implémentations de fournisseur sont configurées pour le même nom de langue ou la même extension de fichier, la dernière configuration correspondante remplace tous les fournisseurs configurés précédents pour ce nom de langue ou cette extension de fichier.</span><span class="sxs-lookup"><span data-stu-id="c1d52-146">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="c1d52-147">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="c1d52-147">Configuration File</span></span>

<span data-ttu-id="c1d52-148">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="c1d52-148">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="c1d52-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="c1d52-149">Example</span></span>

<span data-ttu-id="c1d52-150">L’exemple suivant illustre un élément de configuration de compilateur classique:</span><span class="sxs-lookup"><span data-stu-id="c1d52-150">The following example illustrates a typical compiler configuration element:</span></span>

```xml
<configuration>
  <system.codedom>
    <compilers>
      <!-- zero or more compiler elements -->
      <compiler
        language="c#;cs;csharp"
        extension=".cs"
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"
        compilerOptions="/optimize"
        warningLevel="1" />
    </compilers>
  </system.codedom>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c1d52-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1d52-151">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="c1d52-152">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="c1d52-152">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c1d52-153">\<compilateurs > élément</span><span class="sxs-lookup"><span data-stu-id="c1d52-153">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="c1d52-154">Spécification des noms de types complets</span><span class="sxs-lookup"><span data-stu-id="c1d52-154">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="c1d52-155">[compiler, élément de compilateurs pour compilation (schéma des paramètres ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c1d52-155">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
