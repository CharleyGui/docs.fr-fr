---
title: Attributs courants (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 58de23280f2e8765d945ac765d9455a89c45c9cb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642403"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="283cb-102">Attributs courants (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="283cb-102">Common Attributes (Visual Basic)</span></span>
<span data-ttu-id="283cb-103">Cette rubrique décrit les attributs qui sont couramment utilisés dans les programmes Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="283cb-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>  
  
- [<span data-ttu-id="283cb-104">Attributs globaux</span><span class="sxs-lookup"><span data-stu-id="283cb-104">Global Attributes</span></span>](#Global)  
  
- [<span data-ttu-id="283cb-105">Attribut Obsolete</span><span class="sxs-lookup"><span data-stu-id="283cb-105">Obsolete Attribute</span></span>](#Obsolete)  
  
- [<span data-ttu-id="283cb-106">Attribut Conditional</span><span class="sxs-lookup"><span data-stu-id="283cb-106">Conditional Attribute</span></span>](#Conditional)  
  
- [<span data-ttu-id="283cb-107">Attributs d’informations de l’appelant</span><span class="sxs-lookup"><span data-stu-id="283cb-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
- [<span data-ttu-id="283cb-108">Attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="283cb-108">Visual Basic Attributes</span></span>](#VB)  
  
## <a name="Global"></a> <span data-ttu-id="283cb-109">Attributs globaux</span><span class="sxs-lookup"><span data-stu-id="283cb-109">Global Attributes</span></span>  
 <span data-ttu-id="283cb-110">La plupart des attributs sont appliqués à des éléments de langage spécifiques, tels que les classes ou les méthodes. Toutefois, certains attributs sont globaux : ils s’appliquent à la totalité d’un assembly ou d’un module.</span><span class="sxs-lookup"><span data-stu-id="283cb-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="283cb-111">Par exemple, l’attribut <xref:System.Reflection.AssemblyVersionAttribute> peut être utilisé pour incorporer des informations de version dans un assembly, de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="283cb-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 <span data-ttu-id="283cb-112">Les attributs globaux apparaissent dans le code source après n’importe quel niveau supérieur `Imports` instructions et avant les déclarations de type, de module ou d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="283cb-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="283cb-113">Les attributs globaux peuvent apparaître dans plusieurs fichiers sources, mais les fichiers doivent être compilés en un seul passage.</span><span class="sxs-lookup"><span data-stu-id="283cb-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="283cb-114">Pour les projets Visual Basic, les attributs globaux sont généralement placés dans le fichier AssemblyInfo.vb (le fichier est créé automatiquement lorsque vous créez un projet dans Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="283cb-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>  
  
 <span data-ttu-id="283cb-115">Les attributs d’assembly sont des valeurs qui fournissent des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="283cb-116">Ils sont répartis dans les catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="283cb-116">They fall into the following categories:</span></span>  
  
- <span data-ttu-id="283cb-117">Attributs d’identité de l’assembly</span><span class="sxs-lookup"><span data-stu-id="283cb-117">Assembly identity attributes</span></span>  
  
- <span data-ttu-id="283cb-118">Attributs d’informations</span><span class="sxs-lookup"><span data-stu-id="283cb-118">Informational attributes</span></span>  
  
- <span data-ttu-id="283cb-119">Attributs de manifeste de l’assembly</span><span class="sxs-lookup"><span data-stu-id="283cb-119">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="283cb-120">Attributs d’identité de l’assembly</span><span class="sxs-lookup"><span data-stu-id="283cb-120">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="283cb-121">Trois attributs (avec un nom fort, le cas échéant), déterminent l’identité d’un assembly : nom, version et culture.</span><span class="sxs-lookup"><span data-stu-id="283cb-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="283cb-122">Ces attributs constituent le nom complet de l’assembly et sont obligatoires quand vous le référencez le code.</span><span class="sxs-lookup"><span data-stu-id="283cb-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="283cb-123">Vous pouvez définir la version et la culture d’un assembly en utilisant des attributs.</span><span class="sxs-lookup"><span data-stu-id="283cb-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="283cb-124">Toutefois, la valeur de nom est définie par le compilateur, l’IDE de Visual Studio dans la [boîte de dialogue Informations sur l’assembly](/visualstudio/ide/reference/assembly-information-dialog-box) ou l’utilitaire Assembly Linker (Al.exe) lors de la création de l’assembly, en fonction du fichier qui contient le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="283cb-125">L’attribut <xref:System.Reflection.AssemblyFlagsAttribute> spécifie si plusieurs copies de l’assembly peuvent coexister.</span><span class="sxs-lookup"><span data-stu-id="283cb-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="283cb-126">Le tableau suivant présente les attributs d’identité.</span><span class="sxs-lookup"><span data-stu-id="283cb-126">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="283cb-127">Attribut</span><span class="sxs-lookup"><span data-stu-id="283cb-127">Attribute</span></span>|<span data-ttu-id="283cb-128">Objectif</span><span class="sxs-lookup"><span data-stu-id="283cb-128">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="283cb-129">Décrit intégralement l’identité d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-129">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="283cb-130">Spécifie la version d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-130">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="283cb-131">Spécifie la culture prise en charge par l'assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-131">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="283cb-132">Spécifie si un assembly prend en charge l’exécution côte à côte sur le même ordinateur, dans le même processus ou dans le même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="283cb-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="283cb-133">Attributs d’informations</span><span class="sxs-lookup"><span data-stu-id="283cb-133">Informational Attributes</span></span>  
 <span data-ttu-id="283cb-134">Vous pouvez utiliser les attributs d’informations pour fournir des informations supplémentaires sur le produit ou la société de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="283cb-135">Le tableau suivant présente les attributs d’informations définis dans l’espace de noms <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="283cb-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="283cb-136">Attribut</span><span class="sxs-lookup"><span data-stu-id="283cb-136">Attribute</span></span>|<span data-ttu-id="283cb-137">Objectif</span><span class="sxs-lookup"><span data-stu-id="283cb-137">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="283cb-138">Définit un attribut personnalisé qui spécifie un nom de produit pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="283cb-139">Définit un attribut personnalisé qui spécifie une marque pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="283cb-140">Définit un attribut personnalisé qui spécifie une version d’informations pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="283cb-141">Définit un attribut personnalisé qui spécifie un nom de société pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="283cb-142">Définit un attribut personnalisé qui spécifie un copyright pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="283cb-143">Demande au compilateur d’utiliser un numéro de version spécifique pour la ressource de la version du fichier Win32.</span><span class="sxs-lookup"><span data-stu-id="283cb-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="283cb-144">Indique si l’assembly est conforme à la spécification CLS (Common Language Specification).</span><span class="sxs-lookup"><span data-stu-id="283cb-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="283cb-145">Attributs de manifeste de l’assembly</span><span class="sxs-lookup"><span data-stu-id="283cb-145">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="283cb-146">Vous pouvez utiliser les attributs de manifeste de l’assembly pour fournir des informations dans le manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="283cb-147">Cela inclut le titre, la description, l’alias par défaut et la configuration.</span><span class="sxs-lookup"><span data-stu-id="283cb-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="283cb-148">Le tableau suivant présente les attributs de manifeste de l’assembly définis dans l’espace de noms <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="283cb-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="283cb-149">Attribut</span><span class="sxs-lookup"><span data-stu-id="283cb-149">Attribute</span></span>|<span data-ttu-id="283cb-150">Objectif</span><span class="sxs-lookup"><span data-stu-id="283cb-150">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="283cb-151">Définit un attribut personnalisé qui spécifie un titre d’assembly pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="283cb-152">Définit un attribut personnalisé qui spécifie une description d’assembly pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="283cb-153">Définit un attribut personnalisé qui spécifie une configuration d’assembly (telles que retail ou debug) pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="283cb-154">Définit un alias par défaut convivial pour un manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="283cb-154">Defines a friendly default alias for an assembly manifest</span></span>|  
  
## <a name="Obsolete"></a> <span data-ttu-id="283cb-155">Attribut Obsolete</span><span class="sxs-lookup"><span data-stu-id="283cb-155">Obsolete Attribute</span></span>  
 <span data-ttu-id="283cb-156">L’attribut `Obsolete` est utilisé pour marquer une entité de programme comme étant une entité dont l’utilisation n’est plus recommandée.</span><span class="sxs-lookup"><span data-stu-id="283cb-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="283cb-157">Chaque utilisation d’une entité marquée comme obsolète génère par la suite un avertissement ou une erreur, selon la façon dont l’attribut est configuré.</span><span class="sxs-lookup"><span data-stu-id="283cb-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="283cb-158">Exemple :</span><span class="sxs-lookup"><span data-stu-id="283cb-158">For example:</span></span>  
  
```vb  
<System.Obsolete("use class B")>   
Class A  
    Sub Method()  
    End Sub  
End Class  
  
Class B  
    <System.Obsolete("use NewMethod", True)>   
    Sub OldMethod()  
    End Sub  
  
    Sub NewMethod()  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="283cb-159">Dans cet exemple, l’attribut `Obsolete` est appliqué à la classe `A` et à la méthode `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="283cb-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="283cb-160">Comme le deuxième argument du constructeur d’attribut appliqué à `B.OldMethod` a la valeur `true`, l’utilisation de cette méthode entraîne une erreur du compilateur, alors que l’utilisation de la classe `A` n’entraîne qu’un avertissement.</span><span class="sxs-lookup"><span data-stu-id="283cb-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="283cb-161">Toutefois, l’appel de `B.NewMethod` ne produit aucun avertissement ni aucune erreur.</span><span class="sxs-lookup"><span data-stu-id="283cb-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="283cb-162">La chaîne fournie comme premier argument au constructeur d’attribut est affichée dans l’avertissement ou dans l’erreur.</span><span class="sxs-lookup"><span data-stu-id="283cb-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="283cb-163">Par exemple, utilisé avec les définitions précédentes, le code suivant génère deux avertissements et une erreur :</span><span class="sxs-lookup"><span data-stu-id="283cb-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 <span data-ttu-id="283cb-164">Deux avertissements pour la classe `A` sont générés : un pour la déclaration de la référence de classe et un pour le constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="283cb-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="283cb-165">L’attribut `Obsolete` peut être utilisé sans arguments, mais il est recommandé d’inclure une explication sur la raison pour laquelle l’élément est obsolète et d’indiquer quoi utiliser en remplacement.</span><span class="sxs-lookup"><span data-stu-id="283cb-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="283cb-166">`Obsolete` est un attribut à usage unique et peut être appliqué à toute entité qui autorise des attributs.</span><span class="sxs-lookup"><span data-stu-id="283cb-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="283cb-167">`Obsolete` est un alias pour <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="283cb-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
## <a name="Conditional"></a> <span data-ttu-id="283cb-168">Attribut Conditional</span><span class="sxs-lookup"><span data-stu-id="283cb-168">Conditional Attribute</span></span>  
 <span data-ttu-id="283cb-169">Avec l’attribut `Conditional`, l’exécution d’une méthode dépend d’un identificateur de prétraitement.</span><span class="sxs-lookup"><span data-stu-id="283cb-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="283cb-170">L’attribut `Conditional` est un alias pour <xref:System.Diagnostics.ConditionalAttribute>, et peut être appliqué à une méthode ou une classe d’attributs.</span><span class="sxs-lookup"><span data-stu-id="283cb-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="283cb-171">Dans cet exemple, `Conditional` est appliqué à une méthode pour activer ou désactiver l’affichage d’informations de diagnostic spécifiques au programme :</span><span class="sxs-lookup"><span data-stu-id="283cb-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```vb  
#Const TRACE_ON = True  
Imports System  
Imports System.Diagnostics  
Module TestConditionalAttribute  
    Public Class Trace  
        <Conditional("TRACE_ON")>   
        Public Shared Sub Msg(ByVal msg As String)  
            Console.WriteLine(msg)  
        End Sub  
  
    End Class  
  
    Sub Main()  
        Trace.Msg("Now in Main...")  
        Console.WriteLine("Done.")  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="283cb-172">Si l’identificateur `TRACE_ON` n’est pas défini, aucune sortie de trace n’est affichée.</span><span class="sxs-lookup"><span data-stu-id="283cb-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="283cb-173">L’attribut `Conditional` est souvent utilisé avec l’identificateur `DEBUG` pour activer la trace et enregistrer des fonctionnalités pour les versions Debug, mais pas pour les versions Release, de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="283cb-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 <span data-ttu-id="283cb-174">Quand une méthode marquée comme conditionnelle est appelée, la présence ou l’absence du symbole de prétraitement spécifié détermine si l’appel est inclus ou omis.</span><span class="sxs-lookup"><span data-stu-id="283cb-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="283cb-175">Si le symbole est défini, l’appel est inclus ; sinon, il est omis.</span><span class="sxs-lookup"><span data-stu-id="283cb-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="283cb-176">`Conditional` offre une solution à la fois plus efficace, plus élégante et moins sujette aux erreurs que les méthodes englobantes contenues dans les blocs `#if…#endif`, tels que le suivant :</span><span class="sxs-lookup"><span data-stu-id="283cb-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 <span data-ttu-id="283cb-177">Une méthode conditionnelle doit figurer dans une déclaration de classe ou de struct, et ne doit pas avoir de valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="283cb-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="283cb-178">Utilisation de plusieurs identificateurs</span><span class="sxs-lookup"><span data-stu-id="283cb-178">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="283cb-179">Si une méthode comporte plusieurs attributs `Conditional`, un appel à cette dernière est inclus si l’un des symboles conditionnels au moins est défini (en d’autres termes, si les symboles sont liés logiquement par l’opérateur OR).</span><span class="sxs-lookup"><span data-stu-id="283cb-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="283cb-180">Dans cet exemple, la présence de `A` ou de `B` entraîne un appel de méthode :</span><span class="sxs-lookup"><span data-stu-id="283cb-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 <span data-ttu-id="283cb-181">Pour lier logiquement les symboles au moyen de l’opérateur AND, vous pouvez définir des méthodes conditionnelles en série.</span><span class="sxs-lookup"><span data-stu-id="283cb-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="283cb-182">Par exemple, la deuxième méthode ci-dessous ne s’exécute que si `A` et `B` sont définis :</span><span class="sxs-lookup"><span data-stu-id="283cb-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```vb  
<Conditional("A")>   
Shared Sub DoIfA()  
    DoIfAandB()  
End Sub  
  
<Conditional("B")>   
Shared Sub DoIfAandB()  
    ' Code to execute when both A and B are defined...  
End Sub  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="283cb-183">Utilisation de Conditional avec des classes d’attributs</span><span class="sxs-lookup"><span data-stu-id="283cb-183">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="283cb-184">L’attribut `Conditional` peut également être appliqué à une définition de classe d’attributs.</span><span class="sxs-lookup"><span data-stu-id="283cb-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="283cb-185">Dans cet exemple, l’attribut personnalisé `Documentation` n’ajoute des informations aux métadonnées que si DEBUG est défini.</span><span class="sxs-lookup"><span data-stu-id="283cb-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Public Class Documentation  
    Inherits System.Attribute  
    Private text As String  
    Sub New(ByVal doc_text As String)  
        text = doc_text  
    End Sub  
End Class  
  
Class SampleClass  
    ' This attribute will only be included if DEBUG is defined.  
    <Documentation("This method displays an integer.")>   
    Shared Sub DoWork(ByVal i As Integer)  
        System.Console.WriteLine(i)  
    End Sub  
End Class  
```  
  
## <a name="CallerInfo"></a> <span data-ttu-id="283cb-186">Attributs d’informations de l’appelant</span><span class="sxs-lookup"><span data-stu-id="283cb-186">Caller Info Attributes</span></span>  
 <span data-ttu-id="283cb-187">À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode.</span><span class="sxs-lookup"><span data-stu-id="283cb-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="283cb-188">Vous pouvez obtenir le chemin du fichier de code source, le numéro de ligne dans le code source, ainsi que le nom de membre de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="283cb-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="283cb-189">Pour obtenir des informations de membre de l’appelant, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="283cb-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="283cb-190">Chaque paramètre facultatif spécifie une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="283cb-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="283cb-191">Le tableau suivant répertorie les attributs d'informations de l'appelant définis dans l'espace de noms <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="283cb-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="283cb-192">Attribut</span><span class="sxs-lookup"><span data-stu-id="283cb-192">Attribute</span></span>|<span data-ttu-id="283cb-193">Description</span><span class="sxs-lookup"><span data-stu-id="283cb-193">Description</span></span>|<span data-ttu-id="283cb-194">Type</span><span class="sxs-lookup"><span data-stu-id="283cb-194">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="283cb-195">Chemin d’accès complet du fichier source qui contient l’appelant.</span><span class="sxs-lookup"><span data-stu-id="283cb-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="283cb-196">C’est le chemin au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="283cb-196">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="283cb-197">Numéro de ligne dans le fichier source à partir duquel la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="283cb-197">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="283cb-198">Nom de la méthode ou nom de la propriété de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="283cb-198">Method name or property name of the caller.</span></span> <span data-ttu-id="283cb-199">Pour plus d’informations, consultez [les informations de l’appelant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="283cb-199">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="283cb-200">Pour plus d’informations sur les attributs d’informations de l’appelant, consultez [les informations de l’appelant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="283cb-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
## <a name="VB"></a> <span data-ttu-id="283cb-201">Attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="283cb-201">Visual Basic Attributes</span></span>  
 <span data-ttu-id="283cb-202">Le tableau suivant répertorie les attributs qui sont spécifiques à Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="283cb-202">The following table lists the attributes that are specific to Visual Basic.</span></span>  
  
|<span data-ttu-id="283cb-203">Attribut</span><span class="sxs-lookup"><span data-stu-id="283cb-203">Attribute</span></span>|<span data-ttu-id="283cb-204">Objectif</span><span class="sxs-lookup"><span data-stu-id="283cb-204">Purpose</span></span>|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="283cb-205">Indique au compilateur que la classe doit être exposée en tant qu’objet COM.</span><span class="sxs-lookup"><span data-stu-id="283cb-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="283cb-206">Autorise les membres de module d’être accessibles à l’aide uniquement de la qualification nécessaire pour le module.</span><span class="sxs-lookup"><span data-stu-id="283cb-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="283cb-207">Spécifie la taille d’une chaîne de longueur fixe dans une structure à utiliser avec le fichier d’entrée et de sortie de fonctions.</span><span class="sxs-lookup"><span data-stu-id="283cb-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="283cb-208">Spécifie la taille d’un tableau fixe dans une structure à utiliser avec le fichier d’entrée et de sortie de fonctions.</span><span class="sxs-lookup"><span data-stu-id="283cb-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|  
  
### <a name="comclassattribute"></a><span data-ttu-id="283cb-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="283cb-209">COMClassAttribute</span></span>  
 <span data-ttu-id="283cb-210">Utilisez `COMClassAttribute` pour simplifier le processus de création de composants COM à partir de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="283cb-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="283cb-211">Les objets COM sont très différents des assemblys .NET Framework et sans `COMClassAttribute`, vous devez suivre plusieurs étapes pour générer un objet COM à partir de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="283cb-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="283cb-212">Pour les classes marquées avec `COMClassAttribute`, le compilateur effectue la plupart de ces étapes automatiquement.</span><span class="sxs-lookup"><span data-stu-id="283cb-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>  
  
### <a name="hidemodulenameattribute"></a><span data-ttu-id="283cb-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="283cb-213">HideModuleNameAttribute</span></span>  
 <span data-ttu-id="283cb-214">Utilisez `HideModuleNameAttribute` pour autoriser les membres de module d’être accessibles à l’aide uniquement de la qualification nécessaire pour le module.</span><span class="sxs-lookup"><span data-stu-id="283cb-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>  
  
### <a name="vbfixedstringattribute"></a><span data-ttu-id="283cb-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="283cb-215">VBFixedStringAttribute</span></span>  
 <span data-ttu-id="283cb-216">Utilisez `VBFixedStringAttribute` pour forcer Visual Basic pour créer une chaîne de longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="283cb-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="283cb-217">Sont des chaînes de longueur variable par défaut, et cet attribut est utile pour stocker des chaînes dans des fichiers.</span><span class="sxs-lookup"><span data-stu-id="283cb-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="283cb-218">Le code suivant illustre cela :</span><span class="sxs-lookup"><span data-stu-id="283cb-218">The following code demonstrates this:</span></span>  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a><span data-ttu-id="283cb-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="283cb-219">VBFixedArrayAttribute</span></span>  
 <span data-ttu-id="283cb-220">Utilisez `VBFixedArrayAttribute` pour déclarer des tableaux sont de taille fixe.</span><span class="sxs-lookup"><span data-stu-id="283cb-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="283cb-221">Comme les chaînes de Visual Basic, les tableaux sont de longueur variable par défaut.</span><span class="sxs-lookup"><span data-stu-id="283cb-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="283cb-222">Cet attribut est utile lors de la sérialisation ou écrire des données dans des fichiers.</span><span class="sxs-lookup"><span data-stu-id="283cb-222">This attribute is useful when serializing or writing data to files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="283cb-223">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="283cb-223">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="283cb-224">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="283cb-224">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="283cb-225">Attributs</span><span class="sxs-lookup"><span data-stu-id="283cb-225">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="283cb-226">Réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="283cb-226">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="283cb-227">Accéder à des attributs à l’aide de la réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="283cb-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
