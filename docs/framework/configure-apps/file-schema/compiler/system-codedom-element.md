---
title: <system.codedom>, élément
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 43bc3c40bfc0b0ce4c0b18683092faf8b67e1c04
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927691"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="62edd-102">\<System. CodeDom >, élément</span><span class="sxs-lookup"><span data-stu-id="62edd-102">\<system.codedom> Element</span></span>
<span data-ttu-id="62edd-103">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="62edd-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="62edd-104">\<Élément de > de configuration</span><span class="sxs-lookup"><span data-stu-id="62edd-104">\<configuration> Element</span></span>  
<span data-ttu-id="62edd-105">\<System. CodeDom >, élément</span><span class="sxs-lookup"><span data-stu-id="62edd-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62edd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62edd-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62edd-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="62edd-107">Attributes and Elements</span></span>  
 <span data-ttu-id="62edd-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="62edd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62edd-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="62edd-109">Attributes</span></span>  
 <span data-ttu-id="62edd-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="62edd-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="62edd-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="62edd-111">Child Elements</span></span>  
  
|<span data-ttu-id="62edd-112">Élément</span><span class="sxs-lookup"><span data-stu-id="62edd-112">Element</span></span>|<span data-ttu-id="62edd-113">Description</span><span class="sxs-lookup"><span data-stu-id="62edd-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62edd-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="62edd-114">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="62edd-115">Conteneur des éléments de configuration du compilateur ; contient zéro ou plusieurs éléments [\<compiler>](compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="62edd-115">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62edd-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="62edd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="62edd-117">Élément</span><span class="sxs-lookup"><span data-stu-id="62edd-117">Element</span></span>|<span data-ttu-id="62edd-118">Description</span><span class="sxs-lookup"><span data-stu-id="62edd-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62edd-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="62edd-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="62edd-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="62edd-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62edd-121">Notes</span><span class="sxs-lookup"><span data-stu-id="62edd-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="62edd-122">.NET Framework version 2,0</span><span class="sxs-lookup"><span data-stu-id="62edd-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="62edd-123"><xref:Microsoft.CSharp.CSharpCodeProvider> L' [ \<élément System. CodeDom >](system-codedom-element.md) contient des paramètres de configuration du compilateur pour les fournisseurs de langages installés sur un ordinateur en plus des fournisseurs par défaut installés avec le .NET Framework, tels que et. <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="62edd-123">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="62edd-124">Les compilateurs [ \<>](compilers-element.md) élément contiennent zéro, un ou plusieurs [ \<éléments > du compilateur](compiler-element.md) .</span><span class="sxs-lookup"><span data-stu-id="62edd-124">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="62edd-125">Chaque élément de [> du compilateur spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique. \<](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="62edd-125">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="62edd-126">Les développeurs et les fournisseurs de compilateur peuvent ajouter des paramètres de configuration au fichier de configuration de l’ordinateur ( <xref:System.CodeDom.Compiler.CodeDomProvider> machine. config) pour une nouvelle implémentation.</span><span class="sxs-lookup"><span data-stu-id="62edd-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="62edd-127">Utilisez la <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> méthode pour énumérer par programme les fournisseurs de langages par défaut et les fournisseurs de langages identifiés par les paramètres de configuration du compilateur sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="62edd-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62edd-128">Dans les versions 1,0 et 1,1 du .NET Framework, les fournisseurs de langages par défaut fournis par le .NET Framework [ \<](compilers-element.md) sont identifiés dans l’élément >s de compilateurs.</span><span class="sxs-lookup"><span data-stu-id="62edd-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="62edd-129">Dans la .NET Framework version 2,0, les fournisseurs de langages par défaut ne sont pas identifiés dans les [ \<compilateurs >](compilers-element.md) élément, mais peuvent être énumérés <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> à l’aide de la méthode.</span><span class="sxs-lookup"><span data-stu-id="62edd-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="62edd-130">.NET Framework les versions 1,0 et 1,1</span><span class="sxs-lookup"><span data-stu-id="62edd-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="62edd-131">L’élément System [. CodeDom > contient les paramètres de configuration du compilateur pour les fournisseurs de langages sur un ordinateur. \<](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="62edd-131">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="62edd-132">Les compilateurs [ \<>](compilers-element.md) élément contiennent zéro, un ou plusieurs [ \<éléments > du compilateur](compiler-element.md) .</span><span class="sxs-lookup"><span data-stu-id="62edd-132">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="62edd-133">Chaque élément de [> du compilateur spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique. \<](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="62edd-133">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="62edd-134">Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="62edd-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="62edd-135">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="62edd-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="62edd-136">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="62edd-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="62edd-137">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="62edd-137">Configuration File</span></span>  
 <span data-ttu-id="62edd-138">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="62edd-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62edd-139">Exemples</span><span class="sxs-lookup"><span data-stu-id="62edd-139">Example</span></span>  
 <span data-ttu-id="62edd-140">L’exemple suivant illustre une configuration de compilateur classique.</span><span class="sxs-lookup"><span data-stu-id="62edd-140">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="62edd-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62edd-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="62edd-142">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="62edd-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="62edd-143">Schéma des paramètres du fournisseur de langage et du compilateur</span><span class="sxs-lookup"><span data-stu-id="62edd-143">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="62edd-144">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="62edd-144">\<compiler> Element</span></span>](compiler-element.md)
