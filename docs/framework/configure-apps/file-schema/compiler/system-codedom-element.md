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
ms.openlocfilehash: 19f37095bd01b76fda8b1e29423c413dbdb06a65
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168916"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="bacbb-102">\<System. CodeDom >, élément</span><span class="sxs-lookup"><span data-stu-id="bacbb-102">\<system.codedom> Element</span></span>
<span data-ttu-id="bacbb-103">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="bacbb-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[<span data-ttu-id="bacbb-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="bacbb-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="bacbb-105">&nbsp;&nbsp; **\<System. CodeDom >**</span><span class="sxs-lookup"><span data-stu-id="bacbb-105">&nbsp;&nbsp;**\<system.codedom>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bacbb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bacbb-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bacbb-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bacbb-107">Attributes and Elements</span></span>  
 <span data-ttu-id="bacbb-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bacbb-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bacbb-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="bacbb-109">Attributes</span></span>  
 <span data-ttu-id="bacbb-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bacbb-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bacbb-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bacbb-111">Child Elements</span></span>  
  
|<span data-ttu-id="bacbb-112">Élément</span><span class="sxs-lookup"><span data-stu-id="bacbb-112">Element</span></span>|<span data-ttu-id="bacbb-113">Description</span><span class="sxs-lookup"><span data-stu-id="bacbb-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bacbb-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="bacbb-114">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="bacbb-115">Conteneur des éléments de configuration du compilateur ; contient zéro ou plusieurs éléments [\<compiler>](compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="bacbb-115">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bacbb-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bacbb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="bacbb-117">Élément</span><span class="sxs-lookup"><span data-stu-id="bacbb-117">Element</span></span>|<span data-ttu-id="bacbb-118">Description</span><span class="sxs-lookup"><span data-stu-id="bacbb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bacbb-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="bacbb-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="bacbb-120">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bacbb-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bacbb-121">Notes</span><span class="sxs-lookup"><span data-stu-id="bacbb-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="bacbb-122">.NET Framework version 2,0</span><span class="sxs-lookup"><span data-stu-id="bacbb-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="bacbb-123"><xref:Microsoft.CSharp.CSharpCodeProvider> L' [ \<élément System. CodeDom >](system-codedom-element.md) contient des paramètres de configuration du compilateur pour les fournisseurs de langages installés sur un ordinateur en plus des fournisseurs par défaut installés avec le .NET Framework, tels que et. <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="bacbb-123">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="bacbb-124">Les compilateurs [ \<>](compilers-element.md) élément contiennent zéro, un ou plusieurs [ \<éléments > du compilateur](compiler-element.md) .</span><span class="sxs-lookup"><span data-stu-id="bacbb-124">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="bacbb-125">Chaque élément de [> du compilateur spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique. \<](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="bacbb-125">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="bacbb-126">Les développeurs et les fournisseurs de compilateur peuvent ajouter des paramètres de configuration au fichier de configuration de l’ordinateur ( <xref:System.CodeDom.Compiler.CodeDomProvider> machine. config) pour une nouvelle implémentation.</span><span class="sxs-lookup"><span data-stu-id="bacbb-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="bacbb-127">Utilisez la <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> méthode pour énumérer par programme les fournisseurs de langages par défaut et les fournisseurs de langages identifiés par les paramètres de configuration du compilateur sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bacbb-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bacbb-128">Dans les versions 1,0 et 1,1 du .NET Framework, les fournisseurs de langages par défaut fournis par le .NET Framework [ \<](compilers-element.md) sont identifiés dans l’élément >s de compilateurs.</span><span class="sxs-lookup"><span data-stu-id="bacbb-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="bacbb-129">Dans la .NET Framework version 2,0, les fournisseurs de langages par défaut ne sont pas identifiés dans les [ \<compilateurs >](compilers-element.md) élément, mais peuvent être énumérés <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> à l’aide de la méthode.</span><span class="sxs-lookup"><span data-stu-id="bacbb-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="bacbb-130">.NET Framework les versions 1,0 et 1,1</span><span class="sxs-lookup"><span data-stu-id="bacbb-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="bacbb-131">L’élément System [. CodeDom > contient les paramètres de configuration du compilateur pour les fournisseurs de langages sur un ordinateur. \<](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="bacbb-131">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="bacbb-132">Les compilateurs [ \<>](compilers-element.md) élément contiennent zéro, un ou plusieurs [ \<éléments > du compilateur](compiler-element.md) .</span><span class="sxs-lookup"><span data-stu-id="bacbb-132">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="bacbb-133">Chaque élément de [> du compilateur spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique. \<](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="bacbb-133">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="bacbb-134">Le .NET Framework définit les paramètres de compilateur initiaux dans le fichier de configuration de l’ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="bacbb-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="bacbb-135">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="bacbb-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="bacbb-136">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bacbb-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="bacbb-137">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="bacbb-137">Configuration File</span></span>  
 <span data-ttu-id="bacbb-138">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="bacbb-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bacbb-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="bacbb-139">Example</span></span>  
 <span data-ttu-id="bacbb-140">L’exemple suivant illustre une configuration de compilateur classique.</span><span class="sxs-lookup"><span data-stu-id="bacbb-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bacbb-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bacbb-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="bacbb-142">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="bacbb-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bacbb-143">Schéma des paramètres du fournisseur de langage et du compilateur</span><span class="sxs-lookup"><span data-stu-id="bacbb-143">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bacbb-144">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="bacbb-144">\<compiler> Element</span></span>](compiler-element.md)
