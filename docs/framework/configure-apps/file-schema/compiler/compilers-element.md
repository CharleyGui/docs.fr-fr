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
ms.openlocfilehash: 1aa096e185ae7f5957f173c03e221a31f30d5200
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172942"
---
# <a name="compilers-element"></a><span data-ttu-id="b6976-102">Élément \<compilers></span><span class="sxs-lookup"><span data-stu-id="b6976-102">\<compilers> Element</span></span>

<span data-ttu-id="b6976-103">Conteneur pour les éléments de configuration du compilateur ; contient zéro ou plusieurs [\<compiler>](compiler-element.md) éléments.</span><span class="sxs-lookup"><span data-stu-id="b6976-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**

## <a name="syntax"></a><span data-ttu-id="b6976-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6976-104">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6976-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b6976-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b6976-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b6976-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6976-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="b6976-107">Attributes</span></span>  

 <span data-ttu-id="b6976-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b6976-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b6976-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b6976-109">Child Elements</span></span>  
  
|<span data-ttu-id="b6976-110">Élément</span><span class="sxs-lookup"><span data-stu-id="b6976-110">Element</span></span>|<span data-ttu-id="b6976-111">Description</span><span class="sxs-lookup"><span data-stu-id="b6976-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6976-112">\<compiler> Appartient</span><span class="sxs-lookup"><span data-stu-id="b6976-112">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="b6976-113">Spécifie les attributs de configuration du compilateur pour un fournisseur de langage.</span><span class="sxs-lookup"><span data-stu-id="b6976-113">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6976-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b6976-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b6976-115">Élément</span><span class="sxs-lookup"><span data-stu-id="b6976-115">Element</span></span>|<span data-ttu-id="b6976-116">Description</span><span class="sxs-lookup"><span data-stu-id="b6976-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6976-117">\<configuration> Appartient</span><span class="sxs-lookup"><span data-stu-id="b6976-117">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="b6976-118">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b6976-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="b6976-119">\<system.codedom> Appartient</span><span class="sxs-lookup"><span data-stu-id="b6976-119">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="b6976-120">Spécifie les paramètres de configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="b6976-120">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6976-121">Notes</span><span class="sxs-lookup"><span data-stu-id="b6976-121">Remarks</span></span>  

 <span data-ttu-id="b6976-122">L' [\<compilers>](compilers-element.md) élément contient les paramètres de configuration du compilateur pour les fournisseurs de langages sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b6976-122">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="b6976-123">Chaque [\<compiler>](compiler-element.md) élément spécifie les attributs de configuration du compilateur pour un fournisseur de langages spécifique.</span><span class="sxs-lookup"><span data-stu-id="b6976-123">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="b6976-124">Le .NET Framework définit les paramètres initiaux du fournisseur de langage et du compilateur dans le fichier de configuration de l’ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b6976-124">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="b6976-125">Les développeurs et les éditeurs de compilateurs peuvent ajouter des paramètres de configuration pour une nouvelle implémentation <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b6976-125">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="b6976-126">Utilisez la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> pour énumérer par programmation les paramètres de configuration du compilateur et du fournisseur de langage sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b6976-126">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b6976-127">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="b6976-127">Configuration File</span></span>  

 <span data-ttu-id="b6976-128">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur et dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="b6976-128">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6976-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6976-129">Example</span></span>  

 <span data-ttu-id="b6976-130">L’exemple suivant illustre un élément de configuration du compilateur classique.</span><span class="sxs-lookup"><span data-stu-id="b6976-130">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b6976-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6976-131">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="b6976-132">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="b6976-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b6976-133">Schéma des paramètres du fournisseur de langage et du compilateur</span><span class="sxs-lookup"><span data-stu-id="b6976-133">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b6976-134">\<compiler> Appartient</span><span class="sxs-lookup"><span data-stu-id="b6976-134">\<compiler> Element</span></span>](compiler-element.md)
