---
title: Attributs courants (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 7988dad410c6e51869ec9d7e40d94e874443a5f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399755"
---
# <a name="common-attributes-c"></a><span data-ttu-id="bcaf3-102">Attributs courants (C#)</span><span class="sxs-lookup"><span data-stu-id="bcaf3-102">Common Attributes (C#)</span></span>
<span data-ttu-id="bcaf3-103">Cette rubrique décrit les attributs le plus couramment utilisés dans les programmes C#.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
- [<span data-ttu-id="bcaf3-104">Attributs globaux</span><span class="sxs-lookup"><span data-stu-id="bcaf3-104">Global Attributes</span></span>](#Global)  
  
- [<span data-ttu-id="bcaf3-105">Attribut obsolète</span><span class="sxs-lookup"><span data-stu-id="bcaf3-105">Obsolete Attribute</span></span>](#Obsolete)  
  
- [<span data-ttu-id="bcaf3-106">Attribut Conditional</span><span class="sxs-lookup"><span data-stu-id="bcaf3-106">Conditional Attribute</span></span>](#Conditional)  
  
- [<span data-ttu-id="bcaf3-107">Attributs Info De l’appelant</span><span class="sxs-lookup"><span data-stu-id="bcaf3-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
## <a name="Global"></a> <span data-ttu-id="bcaf3-108">Attributs globaux</span><span class="sxs-lookup"><span data-stu-id="bcaf3-108">Global Attributes</span></span>  
 <span data-ttu-id="bcaf3-109">La plupart des attributs sont appliqués à des éléments de langage spécifiques, tels que les classes ou les méthodes. Toutefois, certains attributs sont globaux : ils s’appliquent à la totalité d’un assembly ou d’un module.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="bcaf3-110">Par exemple, l’attribut <xref:System.Reflection.AssemblyVersionAttribute> peut être utilisé pour incorporer des informations de version dans un assembly, de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="bcaf3-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="bcaf3-111">Les attributs globaux apparaissent dans le code source après toute directive `using` de niveau supérieur et avant toute déclaration de type, de module ou d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="bcaf3-112">Les attributs globaux peuvent apparaître dans plusieurs fichiers sources, mais les fichiers doivent être compilés en un seul passage.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="bcaf3-113">Dans les projets C#, les attributs globaux sont placés dans le fichier AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="bcaf3-114">Les attributs d’assembly sont des valeurs qui fournissent des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="bcaf3-115">Ils sont répartis dans les catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="bcaf3-115">They fall into the following categories:</span></span>  
  
- <span data-ttu-id="bcaf3-116">Attributs d’identité de l’assembly</span><span class="sxs-lookup"><span data-stu-id="bcaf3-116">Assembly identity attributes</span></span>  
  
- <span data-ttu-id="bcaf3-117">Attributs d’informations</span><span class="sxs-lookup"><span data-stu-id="bcaf3-117">Informational attributes</span></span>  
  
- <span data-ttu-id="bcaf3-118">Attributs de manifeste de l’assembly</span><span class="sxs-lookup"><span data-stu-id="bcaf3-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="bcaf3-119">Attributs d’identité de l’assembly</span><span class="sxs-lookup"><span data-stu-id="bcaf3-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="bcaf3-120">Trois attributs (avec un nom fort, le cas échéant), déterminent l’identité d’un assembly : nom, version et culture.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="bcaf3-121">Ces attributs constituent le nom complet de l’assembly et sont obligatoires quand vous le référencez le code.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="bcaf3-122">Vous pouvez définir la version et la culture d’un assembly en utilisant des attributs.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="bcaf3-123">Toutefois, la valeur de nom est définie par le compilateur, l’IDE de Visual Studio dans la [boîte de dialogue Informations sur l’assembly](/visualstudio/ide/reference/assembly-information-dialog-box) ou l’utilitaire Assembly Linker (Al.exe) lors de la création de l’assembly, en fonction du fichier qui contient le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="bcaf3-124">L’attribut <xref:System.Reflection.AssemblyFlagsAttribute> spécifie si plusieurs copies de l’assembly peuvent coexister.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="bcaf3-125">Le tableau suivant présente les attributs d’identité.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="bcaf3-126">Attribut</span><span class="sxs-lookup"><span data-stu-id="bcaf3-126">Attribute</span></span>|<span data-ttu-id="bcaf3-127">Objectif</span><span class="sxs-lookup"><span data-stu-id="bcaf3-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="bcaf3-128">Décrit intégralement l’identité d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="bcaf3-129">Spécifie la version d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="bcaf3-130">Spécifie la culture prise en charge par l'assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="bcaf3-131">Spécifie si un assembly prend en charge l’exécution côte à côte sur le même ordinateur, dans le même processus ou dans le même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="bcaf3-132">Attributs d’informations</span><span class="sxs-lookup"><span data-stu-id="bcaf3-132">Informational Attributes</span></span>  
 <span data-ttu-id="bcaf3-133">Vous pouvez utiliser les attributs d’informations pour fournir des informations supplémentaires sur le produit ou la société de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="bcaf3-134">Le tableau suivant présente les attributs d’informations définis dans l’espace de noms <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="bcaf3-135">Attribut</span><span class="sxs-lookup"><span data-stu-id="bcaf3-135">Attribute</span></span>|<span data-ttu-id="bcaf3-136">Objectif</span><span class="sxs-lookup"><span data-stu-id="bcaf3-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="bcaf3-137">Définit un attribut personnalisé qui spécifie un nom de produit pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="bcaf3-138">Définit un attribut personnalisé qui spécifie une marque pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="bcaf3-139">Définit un attribut personnalisé qui spécifie une version d’informations pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="bcaf3-140">Définit un attribut personnalisé qui spécifie un nom de société pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="bcaf3-141">Définit un attribut personnalisé qui spécifie un copyright pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="bcaf3-142">Demande au compilateur d’utiliser un numéro de version spécifique pour la ressource de la version du fichier Win32.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="bcaf3-143">Indique si l’assembly est conforme à la spécification CLS (Common Language Specification).</span><span class="sxs-lookup"><span data-stu-id="bcaf3-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="bcaf3-144">Attributs de manifeste de l’assembly</span><span class="sxs-lookup"><span data-stu-id="bcaf3-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="bcaf3-145">Vous pouvez utiliser les attributs de manifeste de l’assembly pour fournir des informations dans le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="bcaf3-146">Cela inclut le titre, la description, l’alias par défaut et la configuration.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="bcaf3-147">Le tableau suivant présente les attributs de manifeste de l’assembly définis dans l’espace de noms <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="bcaf3-148">Attribut</span><span class="sxs-lookup"><span data-stu-id="bcaf3-148">Attribute</span></span>|<span data-ttu-id="bcaf3-149">Objectif</span><span class="sxs-lookup"><span data-stu-id="bcaf3-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="bcaf3-150">Définit un attribut personnalisé qui spécifie un titre d’assembly pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="bcaf3-151">Définit un attribut personnalisé qui spécifie une description d’assembly pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="bcaf3-152">Définit un attribut personnalisé qui spécifie une configuration d’assembly (telles que retail ou debug) pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="bcaf3-153">Définit un alias par défaut convivial pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
## <a name="Obsolete"></a><span data-ttu-id="bcaf3-154">Attribut obsolète</span><span class="sxs-lookup"><span data-stu-id="bcaf3-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="bcaf3-155">L’attribut `Obsolete` est utilisé pour marquer une entité de programme comme étant une entité dont l’utilisation n’est plus recommandée.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="bcaf3-156">Chaque utilisation d’une entité marquée comme obsolète génère par la suite un avertissement ou une erreur, selon la façon dont l’attribut est configuré.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="bcaf3-157">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="bcaf3-157">For example:</span></span>  
  
```csharp  
[System.Obsolete("use class B")]  
class A  
{  
    public void Method() { }  
}  
class B  
{  
    [System.Obsolete("use NewMethod", true)]  
    public void OldMethod() { }  
    public void NewMethod() { }  
}  
```  
  
 <span data-ttu-id="bcaf3-158">Dans cet exemple, l’attribut `Obsolete` est appliqué à la classe `A` et à la méthode `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="bcaf3-159">Comme le deuxième argument du constructeur d’attribut appliqué à `B.OldMethod` a la valeur `true`, l’utilisation de cette méthode entraîne une erreur du compilateur, alors que l’utilisation de la classe `A` n’entraîne qu’un avertissement.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="bcaf3-160">Toutefois, l’appel de `B.NewMethod` ne produit aucun avertissement ni aucune erreur.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="bcaf3-161">La chaîne fournie comme premier argument au constructeur d’attribut est affichée dans l’avertissement ou dans l’erreur.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="bcaf3-162">Par exemple, utilisé avec les définitions précédentes, le code suivant génère deux avertissements et une erreur :</span><span class="sxs-lookup"><span data-stu-id="bcaf3-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="bcaf3-163">Deux avertissements pour la classe `A` sont générés : un pour la déclaration de la référence de classe et un pour le constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="bcaf3-164">L’attribut `Obsolete` peut être utilisé sans arguments, mais il est recommandé d’inclure une explication sur la raison pour laquelle l’élément est obsolète et d’indiquer quoi utiliser en remplacement.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="bcaf3-165">`Obsolete` est un attribut à usage unique et peut être appliqué à toute entité qui autorise des attributs.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="bcaf3-166">`Obsolete` est un alias pour <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
## <a name="Conditional"></a><span data-ttu-id="bcaf3-167">Attribut conditionnel</span><span class="sxs-lookup"><span data-stu-id="bcaf3-167">Conditional Attribute</span></span>  
 <span data-ttu-id="bcaf3-168">Avec l’attribut `Conditional`, l’exécution d’une méthode dépend d’un identificateur de prétraitement.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="bcaf3-169">L’attribut `Conditional` est un alias pour <xref:System.Diagnostics.ConditionalAttribute>, et peut être appliqué à une méthode ou une classe d’attributs.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="bcaf3-170">Dans cet exemple, `Conditional` est appliqué à une méthode pour activer ou désactiver l’affichage d’informations de diagnostic spécifiques au programme :</span><span class="sxs-lookup"><span data-stu-id="bcaf3-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```csharp  
#define TRACE_ON  
using System;  
using System.Diagnostics;  
  
public class Trace  
{  
    [Conditional("TRACE_ON")]  
    public static void Msg(string msg)  
    {  
        Console.WriteLine(msg);  
    }  
}  
  
public class ProgramClass  
{  
    static void Main()  
    {  
        Trace.Msg("Now in Main...");  
        Console.WriteLine("Done.");  
    }  
}  
```  
  
 <span data-ttu-id="bcaf3-171">Si l’identificateur `TRACE_ON` n’est pas défini, aucune sortie de trace n’est affichée.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="bcaf3-172">L’attribut `Conditional` est souvent utilisé avec l’identificateur `DEBUG` pour activer la trace et enregistrer des fonctionnalités pour les versions Debug, mais pas pour les versions Release, de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="bcaf3-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="bcaf3-173">Quand une méthode marquée comme conditionnelle est appelée, la présence ou l’absence du symbole de prétraitement spécifié détermine si l’appel est inclus ou omis.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="bcaf3-174">Si le symbole est défini, l’appel est inclus ; sinon, il est omis.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="bcaf3-175">`Conditional` offre une solution à la fois plus efficace, plus élégante et moins sujette aux erreurs que les méthodes englobantes contenues dans les blocs `#if…#endif`, tels que le suivant :</span><span class="sxs-lookup"><span data-stu-id="bcaf3-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="bcaf3-176">Une méthode conditionnelle doit figurer dans une déclaration de classe ou de struct, et ne doit pas avoir de valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="bcaf3-177">Utilisation de plusieurs identificateurs</span><span class="sxs-lookup"><span data-stu-id="bcaf3-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="bcaf3-178">Si une méthode comporte plusieurs attributs `Conditional`, un appel à cette dernière est inclus si l’un des symboles conditionnels au moins est défini (en d’autres termes, si les symboles sont liés logiquement par l’opérateur OR).</span><span class="sxs-lookup"><span data-stu-id="bcaf3-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="bcaf3-179">Dans cet exemple, la présence de `A` ou de `B` entraîne un appel de méthode :</span><span class="sxs-lookup"><span data-stu-id="bcaf3-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="bcaf3-180">Pour lier logiquement les symboles au moyen de l’opérateur AND, vous pouvez définir des méthodes conditionnelles en série.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="bcaf3-181">Par exemple, la deuxième méthode ci-dessous ne s’exécute que si `A` et `B` sont définis :</span><span class="sxs-lookup"><span data-stu-id="bcaf3-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```csharp
[Conditional("A")]  
static void DoIfA()  
{  
    DoIfAandB();  
}  
  
[Conditional("B")]  
static void DoIfAandB()  
{  
    // Code to execute when both A and B are defined...  
}  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="bcaf3-182">Utilisation de Conditional avec des classes d’attributs</span><span class="sxs-lookup"><span data-stu-id="bcaf3-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="bcaf3-183">L’attribut `Conditional` peut également être appliqué à une définition de classe d’attributs.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="bcaf3-184">Dans cet exemple, l’attribut personnalisé `Documentation` n’ajoute des informations aux métadonnées que si DEBUG est défini.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
public class Documentation : System.Attribute  
{  
    string text;  
  
    public Documentation(string text)  
    {  
        this.text = text;  
    }  
}  
  
class SampleClass  
{  
    // This attribute will only be included if DEBUG is defined.  
    [Documentation("This method displays an integer.")]  
    static void DoWork(int i)  
    {  
        System.Console.WriteLine(i.ToString());  
    }  
}  
```  
  
## <a name="CallerInfo"></a><span data-ttu-id="bcaf3-185">Attributs Info De l’appelant</span><span class="sxs-lookup"><span data-stu-id="bcaf3-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="bcaf3-186">À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="bcaf3-187">Vous pouvez obtenir le chemin du fichier de code source, le numéro de ligne dans le code source, ainsi que le nom de membre de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="bcaf3-188">Pour obtenir des informations de membre de l’appelant, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="bcaf3-189">Chaque paramètre facultatif spécifie une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="bcaf3-190">Le tableau suivant répertorie les attributs d'informations de l'appelant définis dans l'espace de noms <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="bcaf3-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="bcaf3-191">Attribut</span><span class="sxs-lookup"><span data-stu-id="bcaf3-191">Attribute</span></span>|<span data-ttu-id="bcaf3-192">Description</span><span class="sxs-lookup"><span data-stu-id="bcaf3-192">Description</span></span>|<span data-ttu-id="bcaf3-193">Type</span><span class="sxs-lookup"><span data-stu-id="bcaf3-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="bcaf3-194">Chemin d’accès complet du fichier source qui contient l’appelant.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="bcaf3-195">C’est le chemin au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="bcaf3-196">Numéro de ligne dans le fichier source à partir duquel la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="bcaf3-197">Nom de la méthode ou nom de la propriété de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="bcaf3-197">Method name or property name of the caller.</span></span> <span data-ttu-id="bcaf3-198">Pour plus d’informations, consultez [Informations relatives à l’appelant (C#)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="bcaf3-198">For more information, see [Caller Information (C#)](../caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="bcaf3-199">Pour plus d’informations sur les attributs d’informations de l’appelant, consultez [Informations relatives à l’appelant (C#)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="bcaf3-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcaf3-200">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcaf3-200">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="bcaf3-201">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="bcaf3-201">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="bcaf3-202">Attributs</span><span class="sxs-lookup"><span data-stu-id="bcaf3-202">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="bcaf3-203">Réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="bcaf3-203">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="bcaf3-204">Accès à des attributs à l’aide de la réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="bcaf3-204">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
