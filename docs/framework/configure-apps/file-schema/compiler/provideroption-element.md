---
title: Élément <providerOption>
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: 37f4d8c5eeacd82f8fc37179c478d026ca25f459
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664301"
---
# <a name="provideroption-element"></a><span data-ttu-id="22367-102">\<providerOption >, élément</span><span class="sxs-lookup"><span data-stu-id="22367-102">\<providerOption> Element</span></span>
<span data-ttu-id="22367-103">Spécifie les attributs de version du compilateur pour un fournisseur de langages.</span><span class="sxs-lookup"><span data-stu-id="22367-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
 <span data-ttu-id="22367-104">\<> de l’élément de configuration</span><span class="sxs-lookup"><span data-stu-id="22367-104">\<configuration Element></span></span>  
<span data-ttu-id="22367-105">\<System. CodeDom, élément ></span><span class="sxs-lookup"><span data-stu-id="22367-105">\<system.codedom Element></span></span>  
<span data-ttu-id="22367-106">\<compilateurs, élément ></span><span class="sxs-lookup"><span data-stu-id="22367-106">\<compilers Element></span></span>  
<span data-ttu-id="22367-107">\<Élément de > du compilateur</span><span class="sxs-lookup"><span data-stu-id="22367-107">\<compiler> Element</span></span>  
<span data-ttu-id="22367-108">\<providerOption >, élément</span><span class="sxs-lookup"><span data-stu-id="22367-108">\<providerOption> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22367-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22367-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22367-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="22367-110">Attributes and Elements</span></span>  
 <span data-ttu-id="22367-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="22367-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22367-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="22367-112">Attributes</span></span>  
  
|<span data-ttu-id="22367-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="22367-113">Attribute</span></span>|<span data-ttu-id="22367-114">Description</span><span class="sxs-lookup"><span data-stu-id="22367-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="22367-115">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="22367-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="22367-116">Spécifie le nom de l’option; par exemple, «CompilerVersion».</span><span class="sxs-lookup"><span data-stu-id="22367-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="22367-117">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="22367-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="22367-118">Spécifie la valeur de l’option. par exemple, «v 3.5».</span><span class="sxs-lookup"><span data-stu-id="22367-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22367-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="22367-119">Child Elements</span></span>  
 <span data-ttu-id="22367-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="22367-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22367-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="22367-121">Parent Elements</span></span>  
  
|<span data-ttu-id="22367-122">Élément</span><span class="sxs-lookup"><span data-stu-id="22367-122">Element</span></span>|<span data-ttu-id="22367-123">Description</span><span class="sxs-lookup"><span data-stu-id="22367-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22367-124">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="22367-124">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="22367-125">Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22367-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="22367-126">\<System. CodeDom >, élément</span><span class="sxs-lookup"><span data-stu-id="22367-126">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="22367-127">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="22367-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="22367-128">\<compilateurs > élément</span><span class="sxs-lookup"><span data-stu-id="22367-128">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="22367-129">Conteneur pour les éléments de configuration du compilateur; contient zéro ou plusieurs `<compiler>` éléments.</span><span class="sxs-lookup"><span data-stu-id="22367-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="22367-130">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="22367-130">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="22367-131">Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="22367-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22367-132">Notes</span><span class="sxs-lookup"><span data-stu-id="22367-132">Remarks</span></span>  
 <span data-ttu-id="22367-133">Dans la version 3,5, .NET Framework les fournisseurs de code Code Document Object Model (CodeDom) peuvent prendre en charge des options spécifiques `<providerOption>` au fournisseur à l’aide de l’élément.</span><span class="sxs-lookup"><span data-stu-id="22367-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="22367-134">Le .NET Framework 3,5 inclut des assemblys .NET Framework 2,0 mis à jour et fournit de nouveaux assemblys de version 3,5 qui contiennent de nouveaux types.</span><span class="sxs-lookup"><span data-stu-id="22367-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="22367-135">Les fournisseurs C# de code Microsoft et Visual Basic sont contenus dans les assemblys .NET Framework 2,0, mais ils ont été mis à jour pour prendre en charge les compilateurs de version 3,5.</span><span class="sxs-lookup"><span data-stu-id="22367-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="22367-136">Par défaut, les fournisseurs de code mis à jour génèrent du code pour la version 2,0 des compilateurs.</span><span class="sxs-lookup"><span data-stu-id="22367-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="22367-137">Vous pouvez utiliser l' `<providerOption>` élément pour remplacer la version du compilateur cible par 3,5.</span><span class="sxs-lookup"><span data-stu-id="22367-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="22367-138">Pour ce faire, spécifiez «CompilerVersion» pour `name` l’attribut et «v 3.5» pour `value` l’attribut.</span><span class="sxs-lookup"><span data-stu-id="22367-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="22367-139">Vous devez faire précéder le numéro de version d’un «v» en minuscules.</span><span class="sxs-lookup"><span data-stu-id="22367-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="22367-140">Vous pouvez rendre la spécification de version globale en ajoutant `<providerOption>` l’élément au fichier .NET Framework 2,0 machine. config ou racine Web. config.</span><span class="sxs-lookup"><span data-stu-id="22367-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="22367-141">Si vous mettez à jour la version du compilateur par défaut à 3,5 dans le fichier machine. config, vous pouvez la remodifier en 2,0 pour chaque application en utilisant `<providerOption>` l’élément dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="22367-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="22367-142">Les implémenteurs de fournisseurs de code CodeDom peuvent traiter des options personnalisées en fournissant `providerOptions` un constructeur qui <xref:System.Collections.Generic.IDictionary%602>accepte un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="22367-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22367-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="22367-143">Example</span></span>  
 <span data-ttu-id="22367-144">L’exemple suivant montre comment spécifier que la C# version 3,5 du fournisseur de code doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="22367-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22367-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22367-145">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="22367-146">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="22367-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="22367-147">\<compilateurs > élément</span><span class="sxs-lookup"><span data-stu-id="22367-147">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="22367-148">Spécification des noms de types complets</span><span class="sxs-lookup"><span data-stu-id="22367-148">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="22367-149">[compiler, élément de compilateurs pour compilation (schéma des paramètres ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="22367-149">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
