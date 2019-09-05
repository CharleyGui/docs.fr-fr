---
title: Élément <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 011793006f2aff32486fbe4537b46517e0a2b888
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252302"
---
# <a name="supportportability-element"></a><span data-ttu-id="26afa-102">\<supportPortability >, élément</span><span class="sxs-lookup"><span data-stu-id="26afa-102">\<supportPortability> Element</span></span>
<span data-ttu-id="26afa-103">Spécifie qu’une application peut référencer le même assembly dans deux implémentations différentes du .NET Framework, en désactivant le comportement par défaut qui traite les assemblys de façon équivalente à des fins de portabilité des applications.</span><span class="sxs-lookup"><span data-stu-id="26afa-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
<span data-ttu-id="26afa-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="26afa-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="26afa-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="26afa-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="26afa-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="26afa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="26afa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<supportPortability >**</span><span class="sxs-lookup"><span data-stu-id="26afa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26afa-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26afa-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26afa-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="26afa-109">Attributes and Elements</span></span>  

<span data-ttu-id="26afa-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="26afa-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26afa-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="26afa-111">Attributes</span></span>  
  
|<span data-ttu-id="26afa-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="26afa-112">Attribute</span></span>|<span data-ttu-id="26afa-113">Description</span><span class="sxs-lookup"><span data-stu-id="26afa-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26afa-114">PKT</span><span class="sxs-lookup"><span data-stu-id="26afa-114">PKT</span></span>|<span data-ttu-id="26afa-115">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="26afa-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="26afa-116">Spécifie le jeton de clé publique de l’assembly affecté, sous la forme d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="26afa-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="26afa-117">enabled</span><span class="sxs-lookup"><span data-stu-id="26afa-117">enabled</span></span>|<span data-ttu-id="26afa-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="26afa-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="26afa-119">Spécifie si la prise en charge de la portabilité entre les implémentations de l’assembly de .NET Framework spécifié doit être activée.</span><span class="sxs-lookup"><span data-stu-id="26afa-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="26afa-120">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="26afa-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="26afa-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="26afa-121">Value</span></span>|<span data-ttu-id="26afa-122">Description</span><span class="sxs-lookup"><span data-stu-id="26afa-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="26afa-123">true</span><span class="sxs-lookup"><span data-stu-id="26afa-123">true</span></span>|<span data-ttu-id="26afa-124">Active la prise en charge de la portabilité entre les implémentations de l’assembly de .NET Framework spécifié.</span><span class="sxs-lookup"><span data-stu-id="26afa-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="26afa-125">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="26afa-125">This is the default.</span></span>|  
|<span data-ttu-id="26afa-126">false</span><span class="sxs-lookup"><span data-stu-id="26afa-126">false</span></span>|<span data-ttu-id="26afa-127">Désactive la prise en charge de la portabilité entre les implémentations de l’assembly de .NET Framework spécifié.</span><span class="sxs-lookup"><span data-stu-id="26afa-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="26afa-128">Cela permet à l’application d’avoir des références à plusieurs implémentations de l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="26afa-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26afa-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="26afa-129">Child Elements</span></span>  

<span data-ttu-id="26afa-130">Aucun.</span><span class="sxs-lookup"><span data-stu-id="26afa-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26afa-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="26afa-131">Parent Elements</span></span>  
  
|<span data-ttu-id="26afa-132">Élément</span><span class="sxs-lookup"><span data-stu-id="26afa-132">Element</span></span>|<span data-ttu-id="26afa-133">Description</span><span class="sxs-lookup"><span data-stu-id="26afa-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="26afa-134">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="26afa-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="26afa-135">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="26afa-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="26afa-136">Contient des informations à propos de la redirection des versions d'assemblys et de l'emplacement de ces derniers.</span><span class="sxs-lookup"><span data-stu-id="26afa-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26afa-137">Notes</span><span class="sxs-lookup"><span data-stu-id="26afa-137">Remarks</span></span>  

<span data-ttu-id="26afa-138">À partir de la .NET Framework 4, la prise en charge est automatiquement fournie pour les applications qui peuvent utiliser l’une des deux implémentations du .NET Framework, par exemple l’implémentation .NET Framework ou l’implémentation .NET Framework pour Silverlight.</span><span class="sxs-lookup"><span data-stu-id="26afa-138">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="26afa-139">Les deux implémentations d’un assembly .NET Framework particulier sont considérées comme équivalentes par le Binder d’assembly.</span><span class="sxs-lookup"><span data-stu-id="26afa-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="26afa-140">Dans certains scénarios, cette fonctionnalité de portabilité des applications provoque des problèmes.</span><span class="sxs-lookup"><span data-stu-id="26afa-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="26afa-141">Dans ces scénarios, l' `<supportPortability>` élément peut être utilisé pour désactiver la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="26afa-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
<span data-ttu-id="26afa-142">Un tel scénario est un assembly qui doit référencer à la fois l’implémentation de .NET Framework et la .NET Framework pour l’implémentation Silverlight d’un assembly de référence particulier.</span><span class="sxs-lookup"><span data-stu-id="26afa-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="26afa-143">Par exemple, un concepteur XAML écrit en Windows Presentation Foundation (WPF) devra peut-être référencer à la fois l’implémentation du Bureau WPF, l’interface utilisateur du concepteur et le sous-ensemble de WPF inclus dans l’implémentation Silverlight.</span><span class="sxs-lookup"><span data-stu-id="26afa-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="26afa-144">Par défaut, les références séparées provoquent une erreur du compilateur parce que la liaison d’assembly considère les deux assemblys comme équivalents.</span><span class="sxs-lookup"><span data-stu-id="26afa-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="26afa-145">Cet élément désactive le comportement par défaut et permet à la compilation de se dérouler correctement.</span><span class="sxs-lookup"><span data-stu-id="26afa-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="26afa-146">Pour que le compilateur passe les informations à la logique de liaison d’assembly du Common Language Runtime, vous devez utiliser l' `/appconfig` option du compilateur pour spécifier l’emplacement du fichier app. config qui contient cet élément.</span><span class="sxs-lookup"><span data-stu-id="26afa-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26afa-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="26afa-147">Example</span></span>  

<span data-ttu-id="26afa-148">L’exemple suivant permet à une application d’avoir des références à l’implémentation de .NET Framework et à la .NET Framework pour l’implémentation Silverlight de tout assembly .NET Framework qui existe dans les deux implémentations.</span><span class="sxs-lookup"><span data-stu-id="26afa-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="26afa-149">L' `/appconfig` option de compilateur doit être utilisée pour spécifier l’emplacement de ce fichier app. config.</span><span class="sxs-lookup"><span data-stu-id="26afa-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26afa-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26afa-150">See also</span></span>

- [<span data-ttu-id="26afa-151">/appconfig (C# options du compilateur)</span><span class="sxs-lookup"><span data-stu-id="26afa-151">/appconfig (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="26afa-152">[Vue d’ensemble de l’unification des assemblys .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="26afa-152">[.NET Framework Assembly Unification Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
