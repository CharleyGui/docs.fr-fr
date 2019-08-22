---
title: Élément <compilers>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 53dc67d0046ef2f184535f373c5bf19c484c505a
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664321"
---
# <a name="compilers-element"></a><span data-ttu-id="aa6e7-102">\<compilateurs > élément</span><span class="sxs-lookup"><span data-stu-id="aa6e7-102">\<compilers> Element</span></span>
<span data-ttu-id="aa6e7-103">Conteneur des éléments de configuration du compilateur ; contient zéro ou plusieurs éléments [\<compiler>](compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="aa6e7-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="aa6e7-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="aa6e7-104">\<configuration></span></span>  
<span data-ttu-id="aa6e7-105">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="aa6e7-105">\<system.codedom></span></span>  
<span data-ttu-id="aa6e7-106">\<compilateurs > élément</span><span class="sxs-lookup"><span data-stu-id="aa6e7-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa6e7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa6e7-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa6e7-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="aa6e7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aa6e7-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="aa6e7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa6e7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="aa6e7-110">Attributes</span></span>  
 <span data-ttu-id="aa6e7-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="aa6e7-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aa6e7-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="aa6e7-112">Child Elements</span></span>  
  
|<span data-ttu-id="aa6e7-113">Élément</span><span class="sxs-lookup"><span data-stu-id="aa6e7-113">Element</span></span>|<span data-ttu-id="aa6e7-114">Description</span><span class="sxs-lookup"><span data-stu-id="aa6e7-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa6e7-115">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="aa6e7-115">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="aa6e7-116">Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="aa6e7-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aa6e7-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="aa6e7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="aa6e7-118">Élément</span><span class="sxs-lookup"><span data-stu-id="aa6e7-118">Element</span></span>|<span data-ttu-id="aa6e7-119">Description</span><span class="sxs-lookup"><span data-stu-id="aa6e7-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa6e7-120">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="aa6e7-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="aa6e7-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa6e7-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="aa6e7-122">\<System. CodeDom >, élément</span><span class="sxs-lookup"><span data-stu-id="aa6e7-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="aa6e7-123">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="aa6e7-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa6e7-124">Notes</span><span class="sxs-lookup"><span data-stu-id="aa6e7-124">Remarks</span></span>  
 <span data-ttu-id="aa6e7-125">L’élément compilers > contient les paramètres de configuration du compilateur pour les fournisseurs de langages sur un ordinateur. [ \<](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="aa6e7-125">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="aa6e7-126">Chaque élément de [> du compilateur spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique. \<](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="aa6e7-126">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="aa6e7-127">Le .NET Framework définit les paramètres initiaux du fournisseur de langage et du compilateur dans le fichier de configuration de l’ordinateur (machine. config).</span><span class="sxs-lookup"><span data-stu-id="aa6e7-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="aa6e7-128">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aa6e7-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="aa6e7-129">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="aa6e7-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="aa6e7-130">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="aa6e7-130">Configuration File</span></span>  
 <span data-ttu-id="aa6e7-131">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="aa6e7-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa6e7-132">Exemples</span><span class="sxs-lookup"><span data-stu-id="aa6e7-132">Example</span></span>  
 <span data-ttu-id="aa6e7-133">L’exemple suivant illustre un élément de configuration du compilateur classique.</span><span class="sxs-lookup"><span data-stu-id="aa6e7-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa6e7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa6e7-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="aa6e7-135">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="aa6e7-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="aa6e7-136">Schéma des paramètres du fournisseur de langage et du compilateur</span><span class="sxs-lookup"><span data-stu-id="aa6e7-136">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="aa6e7-137">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="aa6e7-137">\<compiler> Element</span></span>](compiler-element.md)
